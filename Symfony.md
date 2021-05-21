# Symfony
## Lancement de symfony
symfony new -- full -- version: myprojet
cd myprojet
symfony server: start

symfony new --full <nom de dossier>
list des commandes => PHP ./bin/console list

Creation d'un ptrojet symfony:
dans le terminal du dossier du projet
``` 
symfony new <nom de projet> --full
```
ou par composer  
composer create-project symfony/website-skeleton <nom du projet>

Lancer le server php:  
php -S 127.0.0.1:8000 -t public/  

Lancer le server symfony:  
symfony server:start  

Lancer le server en tache de fond (attention a la fermeture):  
symfony sever:start -d

Arreter le server:  
symfony server:stop

## Webpack Encore
installation:  
```
composer require encore
```
À toi de jouer !  
A l'aide des ressources ci-dessous, configure ta machine selon tes besoins !

Installation de Node JS  
Si tu n'as pas du tout node d'installé sur ta machine, commence par là !  
https://nodejs.org/en/

Installation de Node Version Manager  
Si tu as une version de node déjà installée, mais que celle-ci n'est plus à jour, tu peux facilement remédier à ça avec nvm, avec un "V" comme "Version".  
https://github.com/nvm-sh/nvm#installing-and-updating

Installation de Yarn  
Installation de Yarn, qui va te permettre de gérer tes assets dans ton projet Symfony. Evidemment yarn fonctionne pour tout projet nécessitant du JS.  
https://classic.yarnpkg.com/en/docs/install/

Installation de Node Package Manager  
Si tu n'aime pas Yarn, avec ou sans raison, tu peux continuer, en prenant en compte les mises en gardes ci-dessus, avec outil à la place de Yarn.  
https://www.npmjs.com/get-npm

Et le tout pour windows 👇  
Si jamais tu rencontre des difficultés à installer tout ça sur windows, ici, un petit tuto récapitulatif pour nodeJS, nvm et npm. Tu peux ensuite retourner à la ressource ci-dessus pour compléter ton installation avec Yarn.  
https://docs.microsoft.com/fr-fr/windows/dev-environment/javascript/nodejs-on-windows

Installation de yarn dans le projet:
```
yarn install
```
Installation de Webpack encore.    
Si tu souhaites avoir plus de détails sur l'installation, et la configuration de Webpack encore, tu peux te rendre sur la documentation officielle de Symfony.  
https://symfony.com/doc/current/frontend/encore/installation.html

Documentation de WebPack  
Pour rappel, "Webpack Encore" n'est qu'une surcouche dédiée à Symfony d'un outil déjà existant et très utilisé dans de nombreux projets Web nécessitant du javascript : "Webpack". N'hésites pas à te renseigner sur cet outil en général si la sphère JS t'intéresse.  
https://webpack.js.org/


Pour lancer yarn en mode production (mise a jour au modification de fichier css et js)
```
yarn encore production
```