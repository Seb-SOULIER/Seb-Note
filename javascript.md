# Javascript

Ecriture en camelCase => minuscule au début puis majuscule a l'interieur.  
ECMa Script => Standards JavaScript.  
Variable let et const apparition ES12 => 2021  

### Ajout d'un JS dans une page HTML (dans le body)
```html
	<script>
		console.log ("Bonjour");
	</script>
```

### Ajout avc un fichier externe script.js
```html
	<script src="script.js"></script>
```

### Insertion de commentaire
```html
	1	// Commentaire 

	1	/* Commentaire
	2	   Ici		*/

	1	/**
	2	*  Ici
	3	*  le
	4	*  commentaire
	5	*/
 ```

```js 
console.log ("Bonjour");	// => Affiche "Bonjour" sur la console.
const  
//=> Variable dont le type ne change pas (tableau, ligne de texte) ou la variable ne change pas. Non ré-assignable
	const name = "Bob";
	name = "John";
let  
//=> Variable qui peut reasigner et bouger,changer. Ré-assignable
type of 1;	//=> reponse 'Number'
type of True; 	//=> reponse 'bolean'
```

## Variable de condition:
	==	même valeur
	=== 	même valeur et même type
	!=	pas égal (valeur)
	!==	pas égal (valeur ou type)
	if texte === falses	=>	if !texte
	&& = and , et
	|| = or, ou


| Données primitifs  | Données Complexes |
| :--------------- | -----:|
| Boolean (vrai ou faux)  |  Function (Fonction) |
| string ("chaine de caractére")  |   Object (Plusieurs boites) |
| message entre " " ou ' '  |   Array (Cas particulier d'object |
| Number (Nombre)  |   tableau avec plusieurs valeurs) |
| Null (Pas de valeur => 'objet')  |    |
| Undefined (pas déclaré)  |    |
| [immutables] | [mutables] |
  
    
``` js
If /*(condition)*/ { /*ce qu'il faut faire*/ }
else if (/*si autre condition*/) { }
else { /*sinon on fait*/ }	

If // :  vérifie une condition (précisée entre les parenthèses). si vraie = executable.
Else if //: ajoute des "embranchements" pour traiter plus de cas
Else //: Ajoute une autre instruction  si la condition est fausse.
```

### les ternaires => if => ? et Else => :

```js
const userName = prompt ("What's your name?");  
// => ecrire du texte et enregistrer la reponse sur userName
// ! = inversement de boolean  (ex : !false = true)

let userCountry = prompt ("Where are you from?");
switch (userCountry){
	Case "France":
	Console.log ("Bonjour");
	breack;
	Case "England":
	Console.log ("Hello");
	breack;
	// ...
}	
// /!\ break : pour marquer la fin d'une comparaison  /!\
```

#### LA CONCATENATION :  
Le fait d'accoler plusieurs chaînes les unes à la suite des autres  (ex: "hello" + "I'm" + "Bob" ).

#### L'INTERPOLATION DE CHAINES :  
Il suffit d'écrire la chaîne avec des "backticks" (``) à la place des guillemets simples ou doubles.  
Inserer une valeur ds une chaine => `Hello, ${name}`;  

#### Tableau
Créer Tableau : crochets  [] et écris à l'intérieur les éléments que tu veux.  
Pour changer  une valeur dans le tableur :  nom de la valeur [ position de l'élement ] = nouveau nom de valeur 

| extentions  | Actions |
| :--------------- | :-----|
| concat: ƒ concat() | Fusionne deux tableaux en un. |
| copyWithin: ƒ copyWithin() |  |
| entries: ƒ entries() |  |
| every: ƒ every() |  |
| fill: ƒ fill() |  |
| filter: ƒ filter() |  |
| find: ƒ find() |  |
| findIndex: ƒ findIndex() |  |
| flat: ƒ flat() |  |
| flatMap: ƒ flatMap() |  |
| forEach: ƒ forEach() |  |
| includes: ƒ includes() | Verifie la présence dans un tableau. |
|  | (ex: nom-tableau.includes("banane")  // true 	// false |
| indexOf: ƒ indexOf() | retournera la première position obtenue lorsque l 'élément a été vu. |
| join: ƒ join() | transforme le tabeau en chaine de caractères OU change le séparateur (ex: * , - ) |
| keys: ƒ keys() |  |
| lastIndexOf: ƒ lastIndexOf() | renverra le dernier index (position dans le tableau) où un élément spécifique a été vu. |
| length:0 | Longeur du tableau : faire console.log(nom-tableau.length). |	
| map: ƒ map() |  |
| pop: ƒ pop() | SUPPRIME un éléments a la FIN du tableau. |
| push: ƒ push() | AJOUTE un élément a la FIN du tableau (ex: nomTableau.push|("nom-ajout"); ). |	
| reduce: ƒ reduce() |  |
| reduceRight: ƒ reduceRight() |  |
| reverse: ƒ reverse() |  |
| shift: ƒ shift() | SUPPRIME le premier élément du tableau. |
| slice: ƒ slice() |  |
| some: ƒ some() |  |
| sort: ƒ sort() | Triera le tableau par ordre alphabétique. |
| splice: ƒ splice() | tableau.splice(1,0,'ajout')	1=position ds le tableau, 0=supression ds le tableau |	
| toLocaleString: ƒ toLocaleString() |  |
| toString: ƒ toString() |  |
| unshift: ƒ unshift() | Ajoute un élément DEBUT |	
| values: ƒ values() |  |
| Split: | sépare un text en tableau |

### Parcourir un tableau
```js
	for (let i = 0; i< tableau.length; i++){
	console.log (Tableau [i]);
	}		//=> consultation d'un tableau
```

## D.R.Y - Don't repeat Yourself
Créer une fonction ou une boucle

## Fonction
```js
Function sum (a,b){
	return a+b;
}
console.log(sum(1,2));
```

## Boucle
```js
let i=0;
while (i<5){
	console.log(`turn number ${i}`);
	i++;
}		//=> Boucle
```

```js
let i=0;
do {
	console.log(`turn number ${i}`);
	i++;
} while (i<5);		//=> boucle avec condition a la fin
```

```ks
for (let i=0; i < nomTableau.length; i++){
console.log ("turn number" + i );
}		//=> boucle juqu'a la fin d'un tableau
```