# Base de donnée relationnel
Données stockées dans les tables
Chaque tables contient des champs
chaques lignes (Tuple) posséde un id unique (Clé primaire)
SGBD => Systéme de gestion de Base de Données

```sql
mysql -u Seb -p /* lancement de MySql */
mysql -u Seb -D Kaamelott; /* lancement MySql avec ouverture Bdd */
CREATE DATABASE Kaamelott; /* Creation d'une base de donnée */
USE kaamelott; /* Entre ds la bdd */
CREATE TABLE knight ('id' INT PRIMARY KEY AUTO_INCREMENT NOT NULL,name VARCHAR(80) NOT NULL,'age' INT NOT NULL, 'birthday' DATE, 'adresse' TEXT);
/* Creation d'une table avec les colonnes suivantes */
DESCRIBE knight; /* Affiche la composition de la table */
INSERT INTO knight (`name`,`age`) VALUES ('Arthur','40');
/* Insert les valeurs aux colonnes */
SELECT * FROM knight; /* Affiche tout le tableau */
SHOW knight; /* Affiche le tableau */
UPDATE knight SET age = 36 WHERE id = 2;
/* Mets l'age a 36 sur la ligne ou ID = 2 */
SELECT * FROM knight WHERE age > 37;
/* Affiche toutes les lignes ou l'age est sup a 37 */
ALTER TABLE knight ADD is_dubbed BOOL NULL;
/* Ajoute une colonne a la table */
UPDATE knight SET is_dubbed = 1;
/* met la colonne is_dubbed a 1 pour tout le tableau */
DELETE FROM knight WHERE id = 3; /* Efface la ligne 3 */
TRUNCATE TABLE knight; /* Vide le tableau */ 
DROP TABLE knight; /* Supprime le tableau */
SELECT firstname FROM knight; 
/* Affiche les firstname du tableau */ 
```

## Lancement depuis un PHP
```php
<?php
$pdo = new \PDO('mysql:host=localhost;dbname=database_name', 'wilder_username', 'wilder_password');
```

## Connection entre les tables  
Pour définir une contrainte de clé étrangère, une fois le champ school_id créé, il faut taper la commande SQL suivante :

```Terminal
ALTER TABLE wizard
ADD CONSTRAINT fk_wizard_school 
FOREIGN KEY (school_id) 
REFERENCES school(id);
```

Il est également possible de définir une contrainte de clé étrangère directement à la création d’une table, par ex :
```terminal
CREATE TABLE wizard (
    id INT PRIMARY KEY AUTO_INCREMENT,
    firstname VARCHAR(100) NOT NULL,
    lastname VARCHAR(100) NOT NULL,
    CONSTRAINT fk_wizard_school      
        FOREIGN KEY (school_id)             
        REFERENCES school(id)    
);
```
Dans les deux cas, les mots-clés à retenir sont :  

    CONSTRAINT : tu indiques ici le nom que tu souhaites, qui te permet d’identifier ta contrainte.  
    FOREIGN KEY() : indique que tu souhaites créer une contrainte de type “clé étrangère” sur le champ indiqué entre les parenthèses, ici school_id, de la table wizard.  
    REFERENCES () : et ce dernier mot-clé indique que la clé étrangère fait référence ici au champ id de la table school.  
