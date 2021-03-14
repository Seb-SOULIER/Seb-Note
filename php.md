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
