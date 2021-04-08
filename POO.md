## Instanciation

$date = new MaDate();  
$date => objet et MaDate => Class

// Propriéte  
$date->days;  
$date->months  

// Méthode  
$date -> days( )
$date -> addDays(2)

Objet = personne  
Attributs = taille,nom,sexe,...  
Méthodes = manger, boire, dormir,...  
Class = structure commmune aux objets créé a partir d'elle.  

## exemple
```php
<?php
   class Personne
  {
    // Attributs
    public $nom;
    public $prenom;
    public $dateDeNaissance;
    public $taille;
    public $sexe;
 
    // Constantes
    const NOMBRE_DE_BRAS = 2;
    const NOMBRE_DE_JAMBES = 2;
    const NOMBRE_DE_YEUX = 2;
    const NOMBRE_DE_PIEDS = 2;
    const NOMBRE_DE_MAINS = 2;
 
    // Méthodes  
    public function __construct() { }
 
    public function boire()
    {
      echo 'La personne boit<br/>';
    }
 
    public function manger()
    {
      echo 'La personne mange<br/>';
    }
  }
```
### Les attributs  
Comme nous l'avons expliqué au début de ce cours, les attributs sont les caractéristiques propres d'un objet. Toute personne possède un nom, un prenom, une date de naissance, une taille, un sexe... Tous ces éléments caractérisent un être humain.

Par cet exemple, nous déclarons les attributs de notre classe public. Nous expliquerons dans un tutoriel suivant les trois niveaux de visibilité (public, private et protected) qui peuvent être appliqués à un attribut.

Le mot-clé public permet de rendre l'attribut accessible depuis l'extérieur de la classe.

En programmation orientée objet, un attribut n'est ni plus ni moins qu'une variable.

Notez également que nous avons juste déclaré les attributs. En revanche, aucun type ni aucune valeur ne leur ont été attribués. Ils sont donc par défaut initialisés à la valeur NULL.

Remarque : deux classes différentes peuvent avoir les même attibuts sans risque de conflit.

### Les constantes  
Il est aussi possible de déclarer des constantes propres à la classe. Contrairement au mode procédural de programmation, une constante est déclarée avec le mot-clé const.

Remarque : une constante doit être déclarée et initialisée avec sa valeur en même temps.

### Le constructeur   
Le constructeur est une méthode particulière. C'est elle qui est appelée implicitement à la création de l'objet (instanciation).

Dans notre exemple, le constructeur n'a ni paramètre ni instruction. Le programmeur est libre de définir des paramètres obligatoires à passer au constructeur ainsi qu'un groupe d'instructions à exécuter à l'instanciation de la classe. Nous nous en passerons pour simplifier notre exemple.

Remarque : en PHP, la surcharge de constructeur et de méthodes n'est pas possible. On ne peut définir qu'une seule et unique fois la même méthode.

### Les méthodes  
Les méthodes sont les actions que l'on peut appliquer à un objet. Il s'agit en fait de fonctions qui peuvent prendre ou non des paramètres et retourner ou non des valeurs / objets. S'agissant d'actions, nous vous conseillons de les nommer avec un verbe à l'infinitif.

Elles se déclarent de la même manière que des fonctions traditionnelles.

Au même titre que les attributs, on déclare une méthode avec un niveau de visibilité. Le mot-clé public
indique que l'on pourra appliquer la méthode en dehors de la classe, c'est à dire sur l'objet lui même.

Remarque : deux classes différentes peuvent avoir les mêmes méthodes sans risque de conflit. 

## Instanciation d'une classe
L'instanciation d'une classe est la phase de création des objets issus de cette classe. Lorsque l'on instancie une classe, on utilise le mot-clé new suivant du nom de la classe. Cette instruction appelle la méthode constructeur ( __construct() ) qui construit l'objet et le place en mémoire. Voici un exemple qui illustre 4 instances différentes de la classes Personne.

### Création d'objets de type Personne

```php
<?php
  $personne1 = new Personne();
  $personne2 = new Personne();
  $personne3 = new Personne();
  $personne4 = new Personne();
```
## Accès aux attributs
### Accès en écriture 
```php
<?php
   // Définition des attributs de la personne 1
  $personne1->nom = 'Hamon';
  $personne1->prenom = 'Hugo';
  $personne1->dateDeNaissance = '02-07-1987';
  $personne1->taille = '180';
  $personne1->sexe = 'M';
   // Définition des attributs de la personne 2
  $personne2->nom = 'Dubois';
  $personne2->prenom = 'Michelle';
  $personne2->dateDeNaissance = '18-11-1968';
  $personne2->taille = '166';
  $personne2->sexe = 'F';
   // Définition des attributs de la personne 3
  $personne3->nom = 'Durand';
  $personne3->prenom = 'Béatrice';
  $personne3->dateDeNaissance = '02-08-1975';
  $personne3->taille = '160';
  $personne3->sexe = 'F';
   // Définition des attributs de la personne 4
  $personne4->nom = 'Martin';
  $personne4->prenom = 'Pierre';
  $personne4->dateDeNaissance = '23-05-1993';
  $personne4->taille = '155';
  $personne4->sexe = 'M';
```
### Affichage du nom et du prénom de la personne 1
```php
<?php
  echo 'Personne 1 :<br/><br/>';
  echo 'Nom : ', $personne1->nom ,'<br/>';
  echo 'Prénom : ', $personne1->prenom;
```
Résultat d'exécution du code
```php
Personne 1 :
Nom : Hamon
Prénom : Hugo 
```
### Accès à une constante
```php
<?php
   echo 'Chaque personne a ', Personne::NOMBRE_DE_YEUX ,' yeux.';
 ?>
```
Résultat de l'exécution du code
```php
Chaque personne a 2 yeux. 
```
### Appel de méthode sur des objets
```php
<?php
  $personne1->boire();
  $personne2->boire();
  $personne3->manger();
  $personne4->manger();
?>
```
Après exécution, le résultat est le suivant :
```php
Résulat de l exécution du code
La personne boit
La personne boit
La personne mange
La personne mange
```

### Creation de la Class
Dans un fichier Bicycle.php
```php
<?php
     // Bicycle.php
  class Bicycle
  {
  }
```
Dans un autre fichier, au hasard index.php, d'instancier un nouvel objet de cette classe. "instancier un objet de cette classe"
```php
<?php
// index.php
require_once 'Bicycle.php';
$bike = new Bicycle();
var_dump($bike);
```

Tu as dû remarquer le mot clé public devant toutes les propriétés et méthodes.  
Il en existe 3 en tout :  
public  
private  
protected  

## Getters & Setters / Accesseurs & Mutateurs
```php
public function getCurrentSpeed(): int
{
    return $this->currentSpeed;
}


public function setCurrentSpeed(int $currentSpeed): void
{
    $this->currentSpeed = $currentSpeed;
}
```
## Constructeur
```php
public function __construct(string $color)
{
    $this->color = $color;
}
```
Un constructeur ne retourne rien son but est d'initialiser.

## Représentation
Dans les différents blocs, tu retrouves :
    le nom de ta classe,
    les propriétés, avec leur type,
    les méthodes  

Pour les différents éléments, tu retrouves les signes suivants :
    un + pour public,
    un - pour privé,
    un # pour protected.  
    