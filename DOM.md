### Qu'est-ce que le DOM?

DOM signifie Document Object Model. C'est une interface utilisée pour manipuler le contenu d'une page HTML.
console.log(document);    =>  voir le document

## Sélectionner et modifier des éléments HTML
const someDivClass = document.querySelector('.my-div');
const someImg = document.querySelector('.my-img');
const someDivId = document.querySelector('#another-div');
const someH1 = document.querySelector('.my-div h1');

changer une image:
// We create a variable catImage set to our first DOM node that have the class .img-cat
const catImage = document.querySelector('.img-cat');
// We set the source of the image to a new url
catImage.src = "https://placekitten.com/200/286";

# InnerHTML :
const title = document.querySelector('.title');
title.innerHTML = "Hello, Bob!";

// We create a variable userName set to the result of prompt
const userName = prompt("What's your name");
// We create a variable set to the first element that match .title
const title = document.querySelector('.title');
// We replaced what's between the two tag by a template string with userName
title.innerHTML = `Hello, ${userName}`;

# getElementBy
const title = document.getElementById('title');
const heading = document.getElementsByTagName('h1');

// We create a variable catImage, set to the DOM node that have the id dog-img
const dogImg = document.getElementById("dog-img");
// We change the width and the alt of the image
dogImg.width = "500";
dogImg.alt = "A sleeping dog";

# Sélectionner plusieurs éléments qui ont la même classe/la même balise
document.querySelectorAll('h1');

const dogsPicture = [
  "https://random.dog/0c021634-cc90-443e-bedb-6f754fcfb7bc.png",
  "https://placedog.net/500/280",
  "https://placedog.net/500/300",
  "https://placedog.net/500/302",
  "https://placedog.net/500/305"
];
// We create a variable set to the array with all element that match the selector img
const images = document.querySelectorAll('img');
// We loop as many time as we have img elements
for(let i = 0; i < images.length; i++){
  // For each loop turn we change the current image for the corresponding image in the array
  images[i].src = dogsPicture[i];
}

## Créer un nouvel élément HTML
const newCatImage = document.createElement('img');
newCatImage.src = "https://placekitten.com/408/287";

# La méthode appendChild va ajouter l'élément passé à la fin de l'élément sur lequel tu utilises la méthode.
Dans cet exemple, ceci ajoutera newCatImage à la fin de document.body:
document.body.appendChild(newCatImage);

# Cette méthode est également disponible sur d'autres noeuds HTML, par exemple, tu peux l'utiliser pour ajouter un élément à une <div>.
const myDiv = document.querySelector('.myDiv');
myDiv.appendChild(myElement);


# Changer la position d'un Élément du DOM
newDiv.appendChild(newCatImage);

const secondCat = document.querySelector('#second-cat-img');  => defini la second image
const firstDiv = document.querySelector('#first-div');        => defini la premiere div
firstDiv.appendChild(secondCat);                              => affecte SecondCat dans la premiere Div

# Supprimer un Élément du DOM
myElement.remove();

const ListImg = document.querySelectorAll(".img-cat");    =>  defini toutes les images cat
for (let i=0; i < ListImg.length; i++){                   =>  fait une boucle sur les images
     ListImg[i].remove();                                 =>  Efface chaque ligne
  };
 
# changer le style d'un élément HTML
someDiv.style.backgroundColor = "light-blue";
someText.style.fontSize = "20px";

