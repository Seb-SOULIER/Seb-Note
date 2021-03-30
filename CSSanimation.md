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

```css
// Rotation
// Pour appliquer une rotation sur un élément nous pouvons utiliser la propriété rotate :
transform: rotate(10deg);

// Mise à l'échelle
// Tu peux changer l'échelle en utilisant la propriété scale avec la transformation css :
transform: scale(1.5);

// Déplacer
// Tu peux déplacer un élément horizontalement et verticalement en utilisant transform. Celle-ci est utile quand tu veux faire bouger tes éléments :
transform : translate(200px,200px) ;

// Incliner
// Skewing permet d'incliner l'élément :
transform: skew(20deg,10deg);

// Combiner plusieurs propriétés
// Tu peux combiner plusieurs propriétés en une seule fois dans ta transformation :
transform: rotate(10deg) scale(1.5);

// Pour une utilisation plus avancée, les transformations 3D existent aussi et peuvent permettre des animations plus complexes et esthétiques.
```
# 🐇 Animations CSS
Les animations que nous avons créées en utilisant des transitions CSS sont assez simples, n'est-ce pas ?
Et si nous voulons créer des animations plus complexes ? Ou une animation qui peut être lancée sans interaction avec l'utilisateur.
Et bien bonne nouvelle, c'est possible avec les animations CSS !

Pour créer une animation avec CSS, tu dois utiliser des @keyframes.
Un exemple vaut des milliers d'explications :
```css
@keyframes slideIn {
  from {
    transform: translate(0px, 0px);
  }
  to {
    transform: translate(200px, 0px);
  }
}
```
From est l'état de départ de l'élément et to est l'état de l'élément souhaité à la fin de l'animation.
Ensuite, pour appliquer l'animation à un élément, il suffit d'appliquer la propriétés animation-name et `animation-duration
```css
.my-div{
	animation-name:slideIn;
	animation-duration:1s;
}
```
Tu peux aussi ajouter une propriété animation-iteration-count pour definir le nombre d'itération souhaité.
```css
animation-iteration-count: infinite;
animation-iteration-count: 3;
```

/!\ On pourrait aussi utiliser l'animation-direction:alternate
```css
@keyframes slideIn {
  0% {
    transform: translate(0px, 0px);
  }
  50% {
    transform: translate(200px, 0px);
  }
  100% {
    transform: translate(0px, 0px);
  }
}
```
Ici, nous utilisons des pourcentages, les pourcentages représentent le % de l'animation.
Dans cet exemple, l'image commencera à la position 0, se déplacera ensuite à la position 200px et reviendra à la position 0 à la fin de l'animation.
