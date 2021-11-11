````
symfony console make:controller CartController
````
On créer la méthode add()
````php
/**
 * @Route("/add/{id}", name="add")
 */
public function add(Product $product, SessionInterface $session)
{
    $cart = $session->get("cart", []);
    $id = $product->getId();
    
    if (!empty($cart[$id])) {
        $cart[$id]++;
    } else {
        $cart[$id] = 1;
    }
    //sauvegarde de la session
    $session->set("cart", $cart);
        
    return $this->redirectToRoute("cart_index");
}
````
On associe le bouton ajouter au panier à la route de add()

On récupère les données sur index()
````php
public function index(SessionInterface $session, ProductRepository $productRepository)
{
    $cart = $session->get("cart", []);
    
    $data = [];
    $total = 0;
    
    foreach($cart as $id => $quantity) {
        $product = $productRepository->find($id);
        $data[] = [
            "product" => $product,
            "quantity" => $quantity
        ];
        $total += $product->getPrice() * $quantity;
    }
    
    return $this->render("cart/index.html.twig", compact
        ("data", "total"));
}
````
On créer la méthode remove()
````php
/**
 * @Route("/remove/{id}", name="remove")
 */
public function remove(Product $produit, SessionInterface $session)
{
    $cart = $session->get("cart", []);
    $id = $product->getId();
    
    if (!empty($cart[$id])) {
        if ($cart[$id] > 1) {
            $cart[$id]--;
        } else {
            unset($cart[$id]);
        }
    }
    //sauvegarde de la session
    $session->set("cart", $cart)
        
    $this->redirectToRoute("cart_index")
}
````

On créer la méthode delete()
````php
/**
 * @Route("/delete/{id}", name="delete")
 */
public function delete(Product $produit, SessionInterface $session)
{
    $cart = $session->get("cart", []);
    $id = $product->getId();
    
    if (!empty($cart[$id])) {
        unset($cart[$id]);
    }
    //sauvegarde de la session
    $session->set("cart", $cart)
        
    $this->redirectToRoute("cart_index")
}
````

On créer les boutons pour ajouter, enlever ou supprimer un produit du panier

Si on veux ajouter un bouton pour supprimer tout le panier
````php
/**
 * @Route("/deleteAll", name="delete_all")
 */
public function deleteAll(SessionInterface $session)
{
    $session->remove("cart)
        
    $this->redirectToRoute("cart_index")
}
````
