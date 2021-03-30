#Transitions CSS

Le premier est le plus facile et s'appelle CSS transition.
Imaginons que tu aies une image et que tu veuilles l'animer au survol. (souris)

Prenons ce code, par example :
```css
.cat-img{
	width:200px;
}
.cat-img:hover{
	width:500px;
}
```
Pour cela, on peut utiliser la transition CSS. La transition CSS ressemble à ça :
```css
element{
	transition: <property> <duration> <curve>;
}
```
Le premier paramètre est la propriété que tu veux animer (par exemple la width, mais tu peux aussi utiliser all pour animer toutes les propriétés)
La seconde est l'animation durée.
Et le dernier est la courbe de détente (ton élément pourrait accélérer ou décélérer ou se déplacer linéairement)
