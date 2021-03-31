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

