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

