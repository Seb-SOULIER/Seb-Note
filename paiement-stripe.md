- Créer les entités Order, Product et User
- Ajouter le champ 'reference' dans Product
- Créer les propriétés de Order:
    - user (ManyToOne)
    - products (ManyToMany)
    - reference
    - stripeToken
    - brandStripe
    - last4Stripe
    - idChargeStripe
    - statusStripe
    - createdAt
    - updatedAt
    - price
- Ajouter const DEVISE = 'eur'; dans l'entité Order
- Créer un compte sur [stripe](https://stripe.com)
    - pour acceder au mode live, clique sur 'Activer mon compte'
````
composer require stripe/stripe-php
````
- Créer Services/StripeService.php
```php
<?php

namespace App\Services;

class StripeService
{
    private $privateKey;
    
    private $em;
    
    public function __construct(EntityManagerInterface $em)
    {
        $this->em = $em;
        
        if ($_ENV['APP_ENV'] === 'dev') {
            $this->privateKey = $_ENV['STRIPE_SECRET_KEY_TEST'];
        } else {
            $this->privateKey = $_ENV['STRIPE_SECRET_KEY_LIVE'];
        }
    }
    
    public function paymentIntent(array $products)
    {
        \Stripe\Stripe::setApiKey($this->privateKey);
        
        $orderPrice = $this->calculateOrderPrice($products);
        
        return \Stripe\PaymentIntent::create([
            'amount' => $orderPrice,
            'currency' => Order::DEVISE,
            'payment_method_types' => ['card']
        ]);
    }
    
    public function payment(
        $amount,
        $currency,
        array $stripeParameter
    ) {
        \Stripe\Stripe::setApiKey($this->privateKey);
        $payment_intent = null;
        
        if (isset($stripeParameter['stripeIntentId'])) {
            $payment_intent = \Stripe\PaymentIntent::retrieve($stripeParameter['stripeIntentId']);
        }
        
        if ($stripeParameter['stripeIntentStatus'] === 'succeeded') {
            //TODO
        } else {
            $payment_intent->cancel();
        }
        
        return $payment_intent;
    }
    
    public function stripe(array $stripeParameter, array $products) 
    {
        $orderPrice = $this->calculateOrderPrice($products);
        
        return $this->payment(
            $orderPrice,
            Order::DEVISE,
            $stripeParameter
        );
    }
    
    public function calculateOrderPrice($products)
    {
        $productRepository = $this->em->getRepository(Product::class);
        $orderPrice = 0;
        
        if (!empty($products)) {
            foreach ($products as $product) {
                $currentProduct = $productRepository->findOneBy(['id' => $product['id']]);
                $price = $currentProduct->getPrice();
                $quantity = $product['quantity'];
                $orderPrice += ($price * $quantity) * 100;
            }
        }
        
        return $orderPrice;
    }
}
```

- Ajoute les clés API dans .env.local (Onglet Developers)
````
//La clé test pour le mode dev, la clé live pour le mode prod
###> stripe ###
STRIPE_PUBLIC_KEY_TEST=
STRIPE_SECRET_KEY_TEST=

STRIPE_PUBLIC_KEY_LIVE=
STRIPE_SECRET_KEY_LIVE=
````
- Créer src\Manager\ProductManager.php
```php
<?php
    
namespace App\Manager;

class ProductManager
{
    private $em;
    
    protected StripeService;
    
    public function __construct(
        EntityManagerInterface $em,
        StripeService $stripeService
    ) {
        $this->em = $em;
        $this->stripeService = $stripeService;
    }
    
    public function getProductsFromSession($productsFromSession)
    {
        $productRepository = $this->em->getRepository(Product::class);
        $products = [];

        if (!empty($productsFromSession)) {
            foreach ($productsFromSession as $product) {
                $currentProduct = $productRepository->findOneBy(['id' => $product['id']]);
                $products[] = $currentProduct;
            }
        }
        
        return $products;
    }
    
    public function intentSecret(array $products)
    {
       $intent = $this->stripeService->paymentIntent($products);
        
        return $intent['client_secret'] ?? null;
    }
    
    public function stripe(array $stripeParameter, array $products)
    {
        $resource = null;
        $data = $this->stripeService->stripe($stripeParameter, $products);
        
        if ($data) {
            $resource = [
                'stripeBrand' => $data['charges']['data'][0]['payment_method_details']['card']['brand'],
                'stripeLast4' => $data['charges']['data'][0]['payment_method_details']['card']['last4'],
                'StripeId' => $data['charges']['data'][0]['id'],
                'stripeStatus' => $data['charges']['data'][0]['status'],
                'stripeToken' => $data['client_secret']
            ];
        }
        
        return $resource;
    }
    
    public function createSubscription(
        array $resource,
        array $products,
        User $user
    ) {
        $stripeService = new StripeService;
        $order = new Order();
        $order->setUser($user);
        foreach ($this->getProductsFromSession($products) as $product) {
            $order->addProduct($product);
        }
        $order->setPrice($stripeService->calculateOrderPrice($products));
        $order->setReference(uniqid('', false));
        $order->setBrandStripe($resource['stripeBrand']);
        $order->setLast4Stripe($resource['stripeLast4']);
        $order->setIdChargeStripe($resource['stripeId']);
        $order->setStripeToken($resource['stripeToken']);
        $order->setStatusStripe($resource['stripeStatus']);
        $order->setUpdatedAt(new \Datetime());
        $order->setCreatedAt(new \Datetime());
        
        $this->em->persist($order);
        $this->em->flush();
    }
}

```
- Dans CartController
```php
/**
 * @Route("/user/payment/show", name="payment", methods={"GET", "POST"})
 */
public function payment(
    SessionInterface $session,
    ProductManager $productManager
): Response {
    $cart = $session->get('cart', []);
    $products = [];
    
    foreach ($cart as $productId => $quantity){
        $products[] = [
            'id' => $productId,
            'quantity' => $quantity
        ];
    }
    
    
    if (!$this->getUser()) {
        return $this->redirectToRoute('app_login');
    }
    
    return $this->render('cart/payment.html.twig', [
        'user' => $this->getUser(),
        'intentSecret' => $productManager->intentSecret($products),
        'products' => $products
    ]);
}

/**
 * @Route("/user/subscription/payment/load", name="subscription_payment", methods={"GET", "POST"})
 */
public function subscription(
    SessionInterface $session,
    Request $request,
    ProductManager $productManager
) {
    $user = $this->getUser();
    $cart = $session->get('cart', []);
    $products = [];
    
    foreach ($cart as $productId => $quantity) {
        $products[] = [
            'id' => $productId,
            'quantity' => $quantity
        ];
    }
    
    if ($request->request) {
         $resource = $productManager->stripe($_POST, $products);
        
        if (null !== $resource) {
            $productManager->createSubscription($resource, $products, $user);
            
            return $this->render('cart/response.html.twig', [
                'products' => $products
            ]);
        }
    }

    return $this->redirectToRoute('payment');
}
```
### Côté FRONT
- Dans cart/payment.html.twig
```twig
<form action="{{ path("subscription_payment") }}" method="post" id="payment-form">
    <div class="form-row">
        <div id="card-elements"></div>
        <script src="https://js.stripe.com/v3/"></script>
        <div id="card-errors" role="alert"></div>
    </div>
    <button>
        Valider la Commande
    </button>
</form>

{% block javascripts %}
<script>
    {% if app_environement == 'dev' %}
        let stripeToken = "{{ stripe_public_key_test }}";
    {% else %}
        let stripeToken = "{{ stripe_public_key_live }}";
    {% endif %}
    
    //On a accès à l'objet Stripe grâce au script du dessus
    let stripe = Stripe(stripeToken);
    //elements() permet d'associer stripe à un formulaire
    let elements = stripe.elements();
    let subscription = "{{ product.id }}";
    let clientSecret = "{{ intentSecret }}";
    let cardholderName = "{{ app.user.lastname }}"
    let cardholderEmail = "{{ app.user.email }}"
    //On stylise le formulaire de paiement
    let styleCustom = {
        base: {
            fontSize: '16px',
            color: '#253323'
        }
    }
    
    let card = elements.create('card', {style: styleCustome});
    //On créer l'élément dans la div
    card.mount("#card-elements");
    
    //Message d'erreur
    card.addEventListener('change', function(event){
        let displayError = document.getElementById('card-errors');
        
        if (event.error) {
            displayError.textContent = event.error.message;
        } else {
            displayError.textContent = "";
        }
    });
    
    let form = document.getElementById('payment-form');
    
    form.addEventListener('submit', function(event) {
        event.preventDefault();
        
        stripe.handleCardPayment(
            clientSecret,
            card,
            {
                payment_method_data: {
                    billing_details: {
                        name: cardholderName,
                        email: cardholderEmail
                    }
                }
            }
        ).then((result) => {
            if (result.error) {
                //display error
            } else if ('paymentIntent' in result) {
                stripeTokenHandler(result.paymentIntent);
            }
        })
    });
    
    function stripeTokenHandler(intent) {
        let form = document.getElementById('payment-form');
        
        let InputIntentId = document.createElement('input');
        let InputIntentPaymentMethod = document.createElement('input');
        let InputIntentStatus = document.createElement('input');
        let InputSubscription = document.createElement('input');
        
        InputIntentId.setAttribute('type', 'hidden');
        InputIntentId.setAttribute('name', 'stripeIntentId');
        InputIntentId.setAttribute('value', intent.id);
        
        InputIntentPaymentMethod.setAttribute('type', 'hidden');
        InputIntentPaymentMethod.setAttribute('name', 'stripeIntentPaymentMethod');
        InputIntentPaymentMethod.setAttribute('value', intent.payment_method);
        
        InputIntentStatus.setAttribute('type', 'hidden');
        InputIntentStatus.setAttribute('name', 'stripeIntentStatus');
        InputIntentStatus.setAttribute('value', intent.status);
        
        InputSubscription.setAttribute('type', 'hidden');
        InputSubscription.setAttribute('name', 'subscription');
        InputSubscription.setAttribute('value', subscription);
        
        form.appendChild(InputIntentId);
        form.appendChild(InputIntentPaymentMethod);
        form.appendChild(InputIntentStatus);
        form.appendChild(InputSubscription);
        form.submit();
    }
</script>
{% endblock %}
```

- Dans config/packages/twig.yaml
```yml
twig:
    globals:
        app_environement: '%env(APP_ENV)%'
        stripe_public_key_test: '%env(STRIPE_PUBLIC_KEY_TEST)%'
        stripe_public_key_live: '%env(STRIPE_PUBLIC_KEY_LIVE)%'
```

- Côté CSS, on doit styliser le formulaire depuis la classe .StripeElement, sinon le formulaire n'apparait pas
```css
.StripeElement {
    box-sizing: border-box;
    height: 100px;
    width: 100%;
    padding: 10px 12px;
    border: 1px solid transparent;
    border-radius: 4px;
    background-color: white;
    box-shadow: 0 1px 3px 0 #e6ebf1;
    transition: box-shadow 150ms ease;
}

.StripeElement--focus {
    box-shadow: 0 1px 3px 0 #cfd7df;
}

.StripeElement--invalid {
    border-color: #0A9B01;
}

.StripeElement--webkit-autofill {
    background-color: #fefde5 !important;
}
```
- Pour tester le formulaire en dev
    - 4242 4242 4242 4242
