# Installer PHP 🐘

## Installer PHP sur Ubuntu

Installer PHP, en exécutant :
``` Terminal
sudo apt install php
```

## Installer PHP sur Windows

Pour Windows, suis ce tutoriel :
How to Install PHP on Windows https://www.sitepoint.com/how-to-install-php-on-windows


# Premières lignes de script 📜

Tu vas écrire tes premières lignes de code PHP dans un fichier dont l’extension sera obligatoirement .php. Les fichiers PHP commencent avec une balise <?php sur la 1ère ligne, pour définir que le fichier contient du code PHP. De plus, chaque ligne d’instructions au sein du fichier doit se terminer par un point virgule ;.

Crée un fichier hello.php qui contient les lignes suivantes :
```php
<?php
echo 'Hello Wilders';
```

Il existe 2 manières d’exécuter du code PHP :  
Dans un terminal, avec la Command Line Interface (CLI) de PHP et le nom du fichier à exécuter : php hello.php  
Dans un navigateur web, en utilisant un serveur HTTP  

Avec le CLI, seul le fichier demandé sera exécuté. Le résultat s'affiche directement dans le terminal.

Tu peux tester avec ce que tu viens de faire. Dans ton terminal, déplace-toi à côté du fichier hello.php si ce n’est pas déjà le cas. Pour en être sûr, exécute ls dans ton terminal, tu devrais y voir le fichier désiré. Exécute ensuite php hello.php. Ton Hello wilder! devrait apparaître dans ton terminal.
Executer du PHP avec un serveur

Pour ton développement au quotidien, tu as besoin d'un serveur HTTP le plus simple d'utilisation et de configuration. Et ça tombe bien, car PHP intègre en interne son propre serveur HTTP !

Attention, ce serveur interne à PHP n'est à utiliser que durant la phase de développement. En production, tu utiliseras un serveur plus robuste comme Apache ou Nginx.

Pour lancer le serveur interne de PHP, il suffit d'ouvrir un terminal, de se placer dans le dossier dans lequel tu veux exécuter ton code PHP et de taper la commande :

```php
php -S localhost:8000
```

ensuite, tu n'auras plus qu'à ouvrir la page http://localhost:8000/hello.php dans ton navigateur pour afficher ton fichier PHP.

Par convention, le port 8000 est utilisé, mais tu pourrais lancer plusieurs serveurs PHP en même temps. Dans ces cas-là, tu devrais choisir des ports différents (8001, 8002...) si 8000 est déjà occupé.

Lors de tes prochains développements, les fichiers accessibles via un navigateur Web depuis internet vont se trouver dans un dossier que, par convention, l'on nomme public. On y trouve, entre autres, le point d'entrée de ton site. Le reste de ton code sera dans un dossier appelé, encore par convention, src.

Pour éviter d'avoir à saisir localhost:8000/public/hello.php pour accéder à ton site, tu peux à la place saisir la commande

```php
php -S localhost:8000 -t public/
// l'option -t (target) demande en paramètre le dossier dans lequel se situent les fichiers PHP que tu veux lancer via ton navigateur.
```

Ces scripts feront eux-mêmes appel aux fichiers PHP dans les autres dossiers comme src, mais toi, tu n'auras jamais à les appeler directement via ton navigateur.

    Remarque : le serveur PHP n'est fonctionnel que le temps durant lequel il est lancé. Si tu le stoppes (avec ctrl+C, même sur Mac) ou si tu fermes le terminal à partir duquel il est lancé, le serveur s'arrêtera et tes pages PHP ne seront plus accessibles.

Le serveur HTTP interne de PHP

Une petite vidéo pour apprendre les différentes options de ce serveur
https://www.grafikart.fr/tutoriels/php/serveur-web-interne-778
Configuration de PHP ⚙️

Bravo, tu as installé PHP. Nous allons maintenant le configurer. Cette configuration se fait dans un fichier appelé php.ini. Tu peux localiser le fichier en exécutant la commande locate php.ini. Tu devrais avoir au moins ce résultat :

/etc/php/7.X/cli/php.ini

Il se peut que tu ne trouve pas de fichier php.ini, mais un php.ini.default. Tu dois copier ce fichier et le renommer en supprimant l'extension .default.

Par défaut, PHP n'affiche pas les erreurs (ce qui est très bien quand tu es en production).

Par contre, quand tu es en développement, ça peut t'intéresser ! Tu vas donc configurer le fichier php.ini pour que ces erreurs s'affichent.

Ouvre le fichier en mode administrateur avec l'éditeur de ton choix.

Comme par exemple Gedit sur Ubuntu :
sudo gedit /etc/php/7.X/cli/php.ini

Le fichier contient beaucoup de lignes appelées directives.

Il y a également beaucoup de commentaires qui permettent de comprendre à quoi sert chacune de ces directives.

Trouve la ligne qui indique
```php
display_errors = Off
// et change-la en
display_errors = On
```

De même, juste au-dessus, trouve la ligne
```php
error_reporting = E_ALL & ~E_DEPRECATED & ~E_STRICT
//et modifie-la en
error_reporting = E_ALL
```
Tu viens de dire à PHP d'afficher les erreurs en général (et tous les types d'erreurs).

Nous n'allons pas modifier d'autres directives pour le moment, mais tu seras sans doute amené à le faire de temps à autre.

Si le serveur PHP de développement tourne déjà, pense à le relancer pour que les modifications soient bien prises en compte. Dans la fenêtre de ton terminal où tourne ton serveur PHP, appuie sur les touches Ctrl + C pour couper le serveur, et relance la commande php -S localhost:8000 comme précédemment.
Comprendre le fonctionnement d'un serveur Web

En une courte vidéo.
https://www.youtube.com/watch?v=UEteb-otzFM