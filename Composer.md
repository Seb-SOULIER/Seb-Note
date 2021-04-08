Installation de composer => https://getcomposer.org/Composer-Setup.exe

## initialisation d'un projet Composer
Vérifier si la version est a jour
```terminal
composer self-update
composer --version   //donne la version
```
Initialiser un projet qui va utiliser Composer  
a la racine du projet
```terminal
composer init
```
Creation du fichier composer.json
  
  
  Creation dossier vendor/
```terminal
composer install
```
require lae fichier autoload.php dans index.php.

## Installer une librairie
Dans le terminal
```terminal
composer require <vendor>/<package_name>
```
<vendor> representant le nom de l'éditeur du package et <âckage_name> le nom du package  
    
Si tu ne connais pas la librairie:
```terminal
composer require
```
affiche une liste des librairies
  
