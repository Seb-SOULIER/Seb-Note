# Les variables en PHP

Tous les langages informatiques utilisent des variables.  
Cela permet d'enregistrer de manière temporaire (c'est-à-dire le temps de l'exécution du programme) des informations dans la mémoire de l'ordinateur.  

Les noms des variables sont choisis par le développeur (en suivant certaines normes pouvant varier d'un langage à l'autre) qui peut y enregistrer des valeurs de différents types (nombres, texte, ...).  
Ainsi stockées dans des variables, les données sont faciles à retrouver et à manipuler.  
Il existe aussi des variables prédéfinies, accessibles dès le départ sans que l'on ait besoin de les créer.

Pour te donner un exemple parlant, les variables sont un peu comme des boîtes, dans lesquelles tu peux mettre différentes choses, et qui ont une étiquette dessus avec un nom, suffisamment parlant pour que tu saches ce que tu y as mis.
🤓

## Les règles associées au nom des variables

    Une variable commence toujours par le caractère '$' (dollar).
    Ne doit pas commencer par un chiffre.
    Ne peut contenir que des chiffres, des lettres et le caractère '_' (souligné).

✅ Exemples de noms de variables valides :
```php
    $str
    $my_value
    $_old
    $theBestValue
```

Attention, les noms des variables sont sensibles à la casse. $Black et $black sont deux variables différentes.

❌ Exemples de noms de variables invalides :
```php
    $4days            // commence par un chiffre
    day4              // pas de symbole $
    $my-bad           // contient un caractère interdit (-)
    $                 // pas de nom
    $name@domain      // caractère interdit (@)
    $first name       // caractère interdit ( )
```

    Il est recommandé, en PHP, de nommer ses variables en camelCase.

### C'est dans la boîte

Une petite explication courte et claire du concept de variable informatique.  
https://sulfureetcontreculture.blogspot.fr/2008/07/programmation-quest-ce-quune-variable.html  
Les bases des variables

Quelques principes de base sur la documentation officielle.  
http://php.net/manual/fr/language.variables.basics.php  

## Les types

Il existe deux grandes familles de types de données :
- scalaire
- composé

### Les variables scalaires sont des variables ne contenant qu'une seule valeur à la fois. Elles sont composées des types suivants :
- Entier (nombre sans virgule) : c'est le type integer.
- Réel (nombre à virgule. En php, le séparateur décimal est en fait un point) : c'est le type float.
- Booléen (2 valeurs, vrai ou faux) : c'est le type boolean.
- Chaîne de caractères (valeurs encadrées par des simples quotes ou des doubles quotes) : c'est le type string

### Les variables composées sont des variables comportant plusieurs éléments.
- Tableaux : c'est le type array
- Objets : c'est le type object

### Il existe également 2 types spéciaux :
- Les ressources : variable spéciale faisant référence à une ressource externe (fichier, connexion à une base de données...). On ne va pas s'étendre sur le sujet pour le moment.
- NULL : représente une variable qui n'a pas de valeur.

Lorsque l'on souhaite créer une variable, on parle de déclaration.  
Lorsque l'on souhaite lui attribuer (ou modifier) une valeur, il faut utiliser l'opérateur d'affectation =. On parle donc d'affectation.  
À la première déclaration de la variable, on parle d'initialisation et on affecte une valeur à cette variable.  
Dans certains langages, il est possible de déclarer une fonction sans l'initialiser tout de suite, mais en PHP l'initialisation et la déclaration se font en même temps.  
Le nom de la variable est toujours écrit en premier, suivi de l'opérateur d'affectation, suivi de la valeur.  
```php
$i = 1; // on affecte la valeur 1 à la variable $i;
1 = $i; // renvoie une erreur car 1 n'est pas une variable, on ne peut donc pas lui affecter de valeur.
```
Exemples de déclaration de variables :
```php
    Entiers : $size = 200; $start = 0;
    Réels $pi = 3.141592654; $half = 0.5;
    Booléens $isSaved = true; $hasField = false;
    Chaînes $firstName = "Indiana"; $lastName = 'Jones';
```
Tu noteras qu'il est également possible d'affecter une même valeur à plusieurs variables d'un coup :
```php
    $a = $b = $c = 2; // les trois variables $a, $b et $c sont initialisées en même temps à 2
```

Les bonnes pratiques :

Pour des raisons de lisibilité du code, dès l'instant que l'on va "typer" une variable en assignant une valeur, on fera en sorte de toujours utiliser le même type pour cette variable.  

Les types des variables  
http://php.net/manual/fr/language.types.intro.php  
L'affectation  
https://secure.php.net/manual/fr/language.operators.assignment.php  

## La portée (ou scope) des variables

La zone dans le code où est déclarée une variable est importante. Une variable peut ne pas être visible par l'ensemble de ton code.  

Dans la plupart des cas, quand tu déclares une variable, celle-ci est dans tout le script en- dessous de l'endroit où tu l'affectes. On parle de variable à portée globale.

```php 
    <?php
    echo﻿ $film; // erreur car $film n'existe pas;

    $film = 'Indiana Jones et le Royaume du crâne de cristal';
    echo $film; // affiche bien le contenu de $film car la variable a été définie au-dessus.
```

Si au contraire, tu déclares une variable à l'intérieur d'une fonction (tu verras en détail les fonctions dans une future quête), cette variable ne sera visible et donc accessible que dans ce bloc. On parle cette fois de variable à portée locale. De plus, les variables à portée globale ne sont pas non plus accessibles à l'intérieur de la fonction.  
En d'autres termes : ce qui se passe dans une fonction, reste dans la fonction !
Exemple :
```php
<?php

$total = 0;
// $total est accessible ici

function add() {       
    $note1 = 15;     // $total n'est pas accessible ici
    $note2 = 20;
}
// $total est accessible ici aussi
// $notes1 et $notes2 ne sont pas accessibles ici
```

La portée des variables  
http://php.net/manual/fr/language.variables.scope.php  

# Les chaînes de caractères en PHP
Une chaîne de caractères (ou string en anglais) est, comme son nom l'indique, une suite de caractères (lettres, chiffres, ponctuation...), placés dans un ordre défini.
Pour faire plus simple, un mot ou une phrase sont des chaînes de caractères. Au même titre que les integer ou les array, les string sont un type de données en PHP (mais également dans la plupart des langages informatiques).  

```php
echo 'Je suis professeur'; // affiche : Je suis professeur

echo 'J\'aime porter un chapeau'; // affiche : J'aime porter un chapeau
echo "J'aime porter un chapeau"; // affiche la même chose, pas besoin d'échapper une simple quote dans des doubles quotes et vice versa

$firstname = 'Indiana';
$presentation = 'Indiana Jones est un célèbre archéologue';
echo $firstname; // affiche : Indiana
echo '$firstname'; // affiche : $firstname
echo "$firstname"; // affiche : Indiana

$firstname = 'Indiana';
$lastname = 'Jones';
echo $firstname . $lastname;  // affiche : IndianaJones
$fullname = $firstname . ' ' . $lastname; // le résultat d'une concaténation peut aussi être enregistré dans une variable.  
echo $fullname; // affiche : Indiana Jones

$presentation = "$firstname $lastname est un célèbre archéologue"; // les variables sont interprétées 
echo $presentation; // affiche : Indiana Jones est un célèbre archéologue

$film = $fullname . ' et le temple maudit';
echo $film; // affiche : Indiana Jones et le temple maudit;

$avis = 'Jaime bien regarder ' . $film;
echo $avis;  // affiche : J'aime bien regarder Indiana Jones et le temple maudit;

$name = 'Indiana';
$name .= ' Jones'; // équivalent à $name = $name . ' Jones';
echo $name; // affiche : Indiana Jones
```

```php
$actor = 'Harrison Ford';
echo $actor[0]; // affiche 'H' car c'est le premier caractère de la chaîne $actor;
echo $actor[1]; // affiche 'a', le second caractère.
echo $actor[9]; // affiche 'F'
echo $actor[25]; // affiche une erreur car ce caractère n'existe pas dans la chaîne !

$actor = 'Sean Connery';
echo $actor[-1]; // affiche 'y' car c'est le dernier caractère de la chaîne
echo $actor[-7]; // affiche 'C' car c'est le septième caractère de la chaîne en partant de la fin
echo $actor[-25]; // affiche une erreur car ce caractère n'existe pas dans la chaîne !
```

strlen : permet de connaître la taille d'une chaîne, c'est-à-dire le nombre de caractères qui la composent.
```php
$weapon = 'fouet';
$length = strlen($weapon); // vaut 5, car fouet contient 5 caractères;
```

trim : permet de tronquer les caractères blancs (espaces, tabulation...) en début et fin d'une chaîne. Il existe les variantes ltrim (left) et rtrim (right) qui font la même chose, mais seulement à gauche et à droite de la chaîne.

Note également qu'il est possible (optionnellement) d'indiquer à trim un autre type de caractère à tronquer à la place des blancs.
```php
$temple = ' maudit  ';
echo $temple; // affiche " maudit  "
echo trim($temple); //  affiche "maudit"
echo ltrim($temple); // affiche "maudit  ";
echo rtrim($temple); // affiche " maudit";
```
Manipulation de la casse : PHP est sensible à la casse. C'est-à-dire qu'un caractère minuscule est différent du même caractère en majuscule.

Autrement dit, 'a' != 'A'. Il existe cependant plusieurs fonctions pour modifier la casse.  
Ainsi, strtoupper, renvoie une chaîne en majuscule, tandis que strtolower renvoie une chaîne en minuscule.  
Des variantes existent, comme ucfirst qui convertit le premier caractère d'une chaîne en majuscule, ou encore ucwords qui convertit chaque première lettre des mots d'une phrase en majuscule.  

```php
$name = 'indiana jones';
echo strtoupper($name); // affiche 'INDIANA JONES'
echo ucfirst($name); // affiche 'Indiana jones'
echo ucwords($name); // affiche 'Indiana Jones'
```
str_replace : cette fonction permet de remplacer tout ou partie d'une chaîne par une autre chaîne.
```php
$text = 'Indiana Jones est un professeur';
echo str_replace('professeur', 'aventurier', $text); // affiche : "Indiana Jones est un aventurier"
echo str_replace('archéologue', 'aventurier', $text); // affiche : "Indiana Jones est un professeur" car le terme "archéologue" n'est pas présent dans $text
```
Bien entendu, cela fonctionne uniquement si le motif recherché est trouvé dans la chaîne, sinon la chaîne d'origine non modifiée est renvoyée.  
Par défaut, str_replace est sensible à la casse, mais il existe str_ireplace qui lui, y est insensible.

Conversion : il existe également des fonctions qui vont aider à échapper certains caractères automatiquement. Par exemple, htmlentities convertit automatiquement les balises HTML contenues dans la chaîne, pour qu'elles ne soient pas interprétées à l'affichage.

Cela évite des problèmes d'affichage ou d'injection de code malveillant dans une page. Il existe d'autres fonctions utiles comme addslashes, url_encode, nl2br...

explode et implode : Ces deux fonctions, souvent indissociables l'une de l'autre, sont très utilisées.

Elles permettent pour explode de convertir une chaîne de caractères en un tableau (en fonction d'un délimiteur) et pour implode, de faire l'opération inverse.
```php
$team = 'Harrison Steven George';
$persons = explode(' ', $team); 
// la chaîne $team a été explosée en fonction du délimiteur 'espace', en un tableau contenant ['Harrison', 'Steven', 'George']. 
// le caractère délimiteur 'espace' n'est plus présent dans le tableau obtenu.
// Pour utiliser explode(), le délimiteur est un paramètre obligatoire.
echo implode (',', $persons); 
// implode prend en paramètres un délimiteur et un tableau. 
// affiche "Harrison,Steven,George". Une chaîne est créée à partir des chaînes contenues dans le tableau, et le délimiteur (ici la virgule) est placé entre chaque élément du tableau.
// pour utiliser implode(), le délimiteur est un paramètre optionnel
echo implode($persons); // affiche "HarrisonStevenGeorge".
```

# Les tableaux et boucles en PHP
```php
$weapons = ['whip', 'gun', 'saber'];
$weapons[] = 'nuclear';
var_dump($weapons);
/*
  var_dump affichera :
  array(4) {
    [0] => string(4) "whip"
    [1] => string(3) "gun"
    [2] => string(5) "saber"
    [3] => string(7) "nuclear"
  }
*/
```
count()  
Permet de compter le nombre d'éléments d'un tableau.
```php
$weapons = ['whip', 'gun', 'saber'];
  echo count($weapons); // affiche 3
```
sort()  
Permet de trier un tableau par ordre croissant de valeur.
```php
  $array = [2, 4, 1, 0, 8, 5];
  sort($array);
  var_dump($array); 
  /*
    affiche:
    array(6) {
      [0] => int(0)
      [1] => int(1)
      [2] => int(2)
      [3] => int(4)
      [4] => int(5)
      [5] => int(8)
    }
  */
```

Cela marche aussi si tu as un tableau ayant pour valeur des chaînes de caractères. Le tableau sera trié par ordre alphabétique.
```php
  $weapons = ['whip', 'gun', 'saber'];
  sort($weapons);
  var_dump($weapons);
  /*
    affiche:
    array(3) {
      [0] => string(3) "gun"
      [1] => string(5) "saber"
      [2] => string(4) "whip"
    }
  */
```

La fonction sort() ne sert qu'à trier des tableaux numériques.   Si tu l'utilises sur un tableau associatif tu perds l'association clé => valeur.  
Note: Cette fonction assigne de nouvelles clés pour les éléments du paramètre array. Elle effacera toutes les clés existantes que vous aviez pu assigner, plutôt que de les trier.

Il existe d'autres fonctions pour un tableau associatif :

asort()  
Permet d'effectuer un tri sur les valeurs en gardant les clés intactes  
ksort()  
Permet d'effectuer un tri sur les clés en gardant les valeurs intactes  

Dans chacune de ces fonctions, tu vas pouvoir définir si tu souhaites un tri ascendant ou descendant. N'hésite pas à consulter la documentation pour savoir comment procéder....  

Contrairement à la plupart des fonctions php, tu ne peux pas faire :  
$sortedWeapons = sort($weapons);  
En effet, l'utilisation de sort() (comme toute autre fonction de tri) modifie directement le tableau passé en paramètre et retourne TRUE ou FALSE selon si le tri a fonctionné ou non.  

Toutes ces fonctions de tri travaillent sur le tableau lui-même, contrairement à la pratique normale qui serait de retourner le tableau trié.  

in_array()  
Permet de vérifier la présence d'une valeur dans un tableau.  
```php
$weapons = ['whip', 'gun', 'saber'];
var_dump(in_array('whip', $weapons)); // affiche true
var_dump(in_array('shield', $weapons)); // affiche false
```
Cette fonction est très utile lorsque tu l'utilises dans une structure conditionnelle :
```php
if (in_array('shield', $weapons)) { 
    echo "La valeur 'shield' est déjà présente dans le tableau";
  } else {
    $weapons[] = 'shield';
    echo "La valeur 'shield' a été ajoutée au tableau weapons. Tu peux donc l'afficher de cette façon: $weapons[3]";
  }
```
array_sum()  
Permet de calculer la somme des valeurs d'un tableau.  
```php
  $values = [1, 2, 3, 4, 5];
  echo array_sum($values); // affiche 15
```
## Fonctions principales en PHP
Il existe des dizaines d'autres fonctions sur les array. N'hésite donc pas à aller jeter un oeil par ici.  
http://www.progmatique.fr/article-33-Php-fonctions-manipuler-tableaux.html  

## Les boucles 
La boucle for  
La boucle for est la plus simple à mettre en place. Tu vas indiquer à PHP de boucler un certain nombre de fois. C'est toi qui définis ce nombre. La boucle for intègre un compteur.  

Sa notation est la suivante :

for (debut; fin; pas) {  
    // Do something  
}  

Dans l'exemple ci-dessus, ce qui est très important ce sont les expressions et leurs emplacements :

    debut : Dans cette première expression, tu vas initialiser une variable (souvent nommée $i mais ça n'est pas obligatoire) qui va te servir de compteur. Tu indiques donc ici à quelle valeur ta boucle va débuter.

    fin : Dans cette deuxième expression, tu vas définir la limite de ce compteur (sa valeur maxi ou mini en fonction du "pas"). La boucle s'arrête quand cette valeur est atteinte.

    pas : Dans cette troisième expression, tu vas définir l'action sur ton compteur à chaque tour de boucle, c'est à dire de combien (de quel "pas") la valeur de $i doit augmenter ou diminuer à chaque tour. Attention ici, il ne suffit pas d'indiquer une valeur de pas, mais bien de modifier la valeur actuelle du compteur en effectuant une affectation.
```php
// Exemple concret d'une boucle allant de 0 à 9 avec un pas de 1
for ($i = 0; $i < 10; $i = $i+1) {
    // Do something
}
// Mais j'aurais pu l'écrire comme cela
for ($counter = 0; $counter < 10; $counter++) {
    // Do something
}
// Et si j'avais voulu aller de 9 à 0
for ($i = 9; $i >= 0; $i--) {
    // Do something
}
// Parcourir un tableau indexé numériquement :
$weapons = ['whip', 'gun', 'saber'];
for ($i = 0; $i < count($weapons); $i++) {
  echo $weapons[$i];  // affiche chaque valeur du tableau tour après tour
}
```
PHP Manual - La boucle for  
http://php.net/manual/fr/control-structures.for.php  

## La boucle while
```php
// Exemple de boucle while
$i = 0;
while ($i < 10) {
    // Do something
    $i++;
}

// Exemple de boucle infinie (À NE PAS FAIRE !!!)
$firstname = 'Henry';
while ($firstname != 'Indy') {
    $firstname = 'Indiana';
    // Do something...
}
```
Le premier exemple est simple, on boucle tant que $i est strictement inférieur à 10.  
Le second est une boucle infinie. Étant donné que le while boucle tant que la condition est true, il faut bien veiller à ce que l'expression du while devienne false.  

PHP Manual - La boucle while  
http://php.net/manual/fr/control-structures.while.php  

## La boucle foreach
Le foreach permet de boucler sur les tableaux.  
Il existe 2 façons de mettre en place un foreach :  
```php
$movies = [
  "Les Aventuriers de l'arche perdue",
  "Indiana Jones et le Temple maudit",
  "Indiana Jones et la Dernière Croisade",
  "Indiana Jones et le Royaume du crâne de cristal",
  "Indiana Jones 5"
];

// Si tu n'as pas besoin des clés du tableau
foreach ($movies as $movie){
    // Do something...
    echo $movie;
    // Affiche "Les Aventuriers de l'arche perdue"
    // (au 1er tour, puis les autres valeurs aux tours suivants)
}

// Si tu as besoin des clés du tableau
foreach ($movies as $key => $movie){
    // Do something...
    echo $key;      // Affiche 0 (au 1er tour)
    echo $movie;    // Affiche "Les Aventuriers de l'arche perdue" (au 1er tour)
}
```
C'est à toi de choisir le nom des variables dans ton foreach (ici $key et $movie).  

Comme pour tout nommage de variable, essaie d'avoir des noms ayant un sens. Par exemple ici, le tableau contenant des films s'appelle $movies.  Quand tu boucles avec foreach, tu vas alors récupérer un film à chaque fois, d'où la variable s'appelant $movie (cette fois au singulier).  

Cette approche pluriel/singulier est souvent utilisée car elle permet de facilement comprendre ce que contient la variable (le tableau dans son ensemble, ou un élément du tableau).  

On dit que le foreach va itérer sur chaque élément du tableau (ou de la collection).  
Cela signifie que chaque élément va être lu séquentiellement à chaque tour de boucle.  

L'élément en cours de lecture, ainsi que sa clé selon la notation du foreach (avec ou sans le =>), vont être affectés à des variables temporaires ($key, $movie). Récupérer la clé est surtout utile en présence d'un tableau associatif.  

PHP Manual - La boucle foreach  
http://php.net/manual/fr/control-structures.foreach.php

## Boucles infinies
Attention: Si la condition d'arrêt d'une boucle est mal définie, cela peut être critique. En effet, la boucle sera infinie et plantera ton programme.  
En PHP, si tu n'as pas modifié la configuration de base, les scripts ont une durée de vie de 30 secondes, donc ton navigateur (voire tout ton poste) peut ne pas répondre pendant maximum 30 secondes (il s'agit du paramètre max_execution_time dans ton fichier php.ini). Mais sur des langages de plus bas niveau, cela peut avoir des conséquences plus graves.  
