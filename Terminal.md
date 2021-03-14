# Configurer Git
Une fois que GitHub Desktop (et donc Git) est installé, ouvrez votre terminal . Vous pouvez vérifier que Git existe vraiment en tapant:

## Définissez votre nom:
```Terminal
git config --global user.name "Your Name"  
Maintenant configurez votre courrier électronique:  
git config --global user.email "youremail@example.com"
```
## Créer un Dépôt
Vous allez créer un nouveau dossier de projet puis l'initialiser en tant que dépôt Git.  
Ouvrez votre terminal!  
Dans la fenêtre de votre terminal, tapez ces commandes, une à la fois, en appuyant sur la touche "Entrée" pour valider votre saisie  

### Tout d'abord, créez un nouveau dossier:  
Astuce: mkdir signifie make directory  
```Terminal
mkdir hello-world  
```  
### entrez dans ce dossier:
Astuce: cd signifie change directory  
```Terminal
cd hello-world  
```
### Enfin, dites à Git d'initialiser(démarrer le suivi) du dossier dans lequel vous êtes:  
```Terminal
git init  
```
La dernière commande devrait renvoyer quelque chose commençant par "Initialized empty Git repository".  

## Vérifier l'état + ajouter et soumettre les modifications

Ensuite, vérifiez le statut de votre dépôt pour savoir s'il y a eu des changements. Vous savez que vous avez changé quelque chose , mais Git le sait-il aussi ?

Assurez-vous que vous êtes toujours dans votre répertoire «hello-world» lorsque vous exécutez ces commandes. Utilisez maintenant Git pour voir ce qui a changé dans votre dépôt:

Tout d'abord, vérifiez le statut:
```js
git status
// Git devrait vous dire qu'un fichier a été ajouté.
// Puis ajouter le fichier que vous venez de créer afin qu'il devienne une partie des modifications que vous soumettez avec Git:
git add readme.txt
// Enfin, soumettez (commit) ces modifications à l'historique du dépôt avec un court (m) message décrivant les mises à jour.
git commit -m "Création du fichier readme"
```

Dans le terminal, vous pouvez afficher les différences entre le fichier actuel et la dernière version soumise.

Dites à Git de vous afficher le diff:
```js
git diff
```

## Ajouter le nom d'utilisateur GitHub à Git

Ajoutez votre nom d'utilisateur GitHub à votre configuration Git. Enregistrez-le exactement comme vous l'avez créé sur GitHub avec les mêmes majuscules et minuscules.

Ajoutez votre nom d'utilisateur GitHub à votre configuration Git:

```js
git config --global user.username <USerNamE>
// Vous pouvez vérifier ce que vous avez configuré dans Git en tapant: :
git config --global user.username
```
Pour changer votre nom d'utilisateur Git, il suffit de faire la même commande que précédemment, mais avec la bonne capitalisation:

```JS
git config --global user.username <USerNamE>
```
Lorsque vous avez effectué la mises à jour de votre configuration, vérifiez à nouveau!

## Créer un dépôt distant

Vous voulez synchroniser votre version local avec celle enregistrée sur GitHub.com. Créez d'abord un dépôt distant (remote) sur GitHub.com.

Aller à github.com , connectez-vous, puis cliquez sur '+' dans le haut À droite, puis cliquez sur 'New repository'.
Donnez-lui un nom qui correspond au nom de votre dépôt local, 'hello-world', et une brève description.
Rendez-le public. Cela signifie qu'il sera répertorié sur votre profil public.
Cliquer enfin sur "create repository"!

## Connectez votre dépôt local à votre remote
Maintenant, vous avez créé un dépôt vide sur GitHub.com. En haut, vous verrez 'Configuration rapide', assurez-vous que le bouton "HTTPS" soit sélectionné et copiez l'adresse: c'est l'adresse de votre dépôt Git sur les serveurs de GitHub.

Retour dans votre terminal, et à l'intérieur du dossier 'hello-world' que vous avez initialisé en tant que dépôt Git dans les défis précédents. Vous voulez que Git retienne l'adresse de la version à distance présente sur les serveurs de GitHub. Vous pouvez avoir plusieurs remotes, pour les différencier, chacun a un nom. Le remote principal est généralement appelé origin.

### Pour ajouter une télécommande nommée 'origine' à votre dépôt:
```JS
git remote add origin <URLFROMGITHUB>
// Votre dépôt local sait maintenant où votre référentiel distant, nommé 'origin', se trouve sur les serveurs de GitHub. Pensez-y comme ajout d'un nom et d'une adresse sur la numérotation rapide, maintenant lorsque vous devez envoyer quelque chose là-bas, vous le pouvez.

//Si vous avez GitHub Desktop sur votre ordinateur, une remote nommée 'origin' est automatiquement créé dans votre dépôt local. Dans ce cas, vous devrez préciser l'URL à associer à 'origin'. Utilisez cette commande au lieu du 'add' ci-dessus:
git remote set-url origin <URLFROMGITHUB>
```

## Poussez votre travail dans votre remote
Ensuite, poussez (envoyer) tout ce que vous avez effectué localement dans votre dépôt distant sur GitHub. C'est quelque chose que vous ferez souvent pour que votre version à distance soit à jour et synchronisée avec l'état de votre version locale.

Git dispose d'un système de branche afin que vous puissiez travailler sur différentes parties d'un projet à différents moments. Nous allons apprendre plus à ce propos par la suite, mais par défaut, la première branche est nommée «master». Lorsque vous poussez (et tirez plus tard) d'un projet, vous dites à Git le nom de branche que vous voulez ainsi que le nom du remote avec lequel vous voulez travailler.

Dans ce cas, nous enverrons notre branche nommée 'master' à notre remote sur GitHub nommée 'origin'.

```JS
git push origin master
```

Maintenant, accédez à la page de votre dépôt sur GitHub.com et actualisez la page. Wow! votre dépôt distant est à jour avec le local. Félicitation!



Commandes du terminal
```js
// Créer un nouveau dossier (aka make directory)  
mkdir <FOLDERNAME>  

// Naviguer dans un dossier existant (aka change directory)
cd <FOLDERNAME>

// Lister les éléments dans un dossier
ls

// Activez Git pour un repertoire
git init

// Vérifiez l'état des modifications dans un dépôt
git status

// Afficher les modifications apportés aux fichiers
git diff

// Ajouter les modifications d'un fichier à soumettre
git add <FILENAME>
// Pour ajouter toutes les modifications d'un seul coup
git add .

// Pour soumettre les modifications que vous avez ajoutées avec un court message décrivant les modifications
git commit -m "your commit message"

// Ajouter un remote
git remote add <REMOTENAME> <URL>
// Modifier l'URL d'un remote
git remote set-url <REMOTENAME> <URL>
// Afficher l'adresse d'un remote
git remote -v

// Tirer des changement à partir d'un remote
git pull <REMOTENAME> <BRANCHNAME>

Pousser des modifications
git push <REMOTENAME> <BRANCH>


Ajouter un remote
git remote add <REMOTENAME> <URL>
Changer l'URL d'un remote
git remote set-url <REMOTENAME> <URL>
Afficher l'adresse des remotes
git remote -v

Vous pouvez créer et passer sur une branche en une seule commande
git checkout -b <BRANCHNAME>
Créer une nouvelle branche
git branch <BRANCHNAME>
Se déplacer sur une branche
git checkout <BRANCHNAME>
Lister les branches
git branch
Renommer la branche courante
git branch -m <NEWBRANCHNAME>
Vérifiez la branche sur laquelle vous travaillez
git status

Fusionner une branche dans la branche courante
git merge <BRANCHNAME>
Changer la branche sur laquelle vous travaillez
git checkout <BRANCHNAME>
Supprimer une branche locale
git branch -d <BRANCHNAME>
Supprimer une branche distante
git push <REMOTENAME> --delete <BRANCHNAME>
Tirer depuis une branche distante
git pull <REMOTENAME> <BRANCHNAME>

.gitignore => fichier nommé dedans ignoré dans le git  
:WQ   => enregistrer et quitter  
:QA   => Sortir sans quitter  
git pull  => tirer le projet  
git push  => envoyer le projet  
git checkout-b "nom de la branch"  
girt branch -d  
git commit -m origin master => valider les modifications  
git init => initialise une branch  
echo => ecrire dans un fichier  
cat => lecture d'un fichier  
cd/  
ls => dir cd qu'il y a  
ls -a avec les fichiers cachés  
/root  
~utilisateur  
mkdir.dossier => creation d'un dossier  
../ =>Dossier parent  






