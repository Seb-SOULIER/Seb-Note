### Qu'est-ce que le DOM?

DOM signifie Document Object Model. C'est une interface utilisée pour manipuler le contenu d'une page HTML. *
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

const boxSty = document.querySelector(".box");    => Variable pour les elements box
boxSty.style.backgroundColor = "yellow";          => Defini la couleur de fond Jaune
boxSty.style.height = "300px";                    => Defini la hauteur de 300 px
boxSty.style.width = "400px";                     => Defini la largeur de 400 px

const textChang = document.querySelector(".title");   => Variable pour les elements titre 
textChang.style.fontSize = "60px";                    => Defini la taille du text
textChang.style.textAlign = "center";                 => Defini la position du text
textChang.style.color = 'lightBlue';                  => Defini la couleur du text

# Ajouter/Supprimer une classe à un élément
element.classList.add('myClass');
element.classList.remove('myClass');

const newBox = document.createElement("div");                     => creer un element dans la box div
newBox.classList.add('box');                                      => ajout la class box
const containerBox = document.querySelector(".container-boxes");  => creer un variable pour contenaire
containerBox.appendChild(newBox);                                 => ajout la box au contenaire

## Gestionnaires d'événements
someDiv.onclick = function(){
	someDiv.style.backgroundColor = "red";
}

# AddEventListener
someDiv.addEventListener('click', function(){
someDiv.style.backgroundColor = "red";
})

//exemple//
const imageChien = document.querySelector(".img-dogs");		=>	Variable pour l'image du chien
imageChien.addEventListener("click", function () {		=>	Si click sur la photo
  imageChien.src = "https://placekitten.com/200/286";		=>	attribution de la nouvelle photo
  imageChien.alt = "Chat!!";					=>	changement du text de la photo
});
const survtitle = document.querySelector(".title");		=>	Variable pour le titre
survtitle.addEventListener("mouseover", function () {		=>	si souris passe dessus
  survtitle.style.color = "red";				=>	Couleur du texte devient rouge
});
survtitle.addEventListener("mouseleave", function () {		=>	si souris s'en va
  survtitle.style.color = "black";				=>	couleur du texte devient noir
});

## Travailler avec un formulaire form
const form = document.querySelector("#form");
const firstName = document.querySelector("#firstname");
const lastName = document.querySelector("#lastname");
form.onsubmit = function(event) {
  event.preventDefault();
  console.log(`Hello, ${firstName.value} ${lastName.value}`);
};

const form = document.querySelector("#form");			=> creation des variables avec les DOM
const inputTodo = document.querySelector("#todoInput");
const todolist = document.querySelector("#todolist");
form.onsubmit = function(event) {				=> fonction onsubmit
  event.preventDefault();					=> Nous voulons empêcher la page de se relooker.
  const newTodo = document.createElement("li");			=> Nous créons une variable que nous fixons à un nouveau noeud li
  newTodo.innerHTML = inputTodo.value;				=> Nous ajoutons le texte à "li"
  todolist.appendChild(newTodo);				=> On ajoute "li" à l'ul
  inputTodo.value = "";						=> Nous effaçons la valeur de inputTodo
};

# Changer une classe
element.classList.toggle("mystyle");

const button = document.querySelector(".dropdown-btn");
const listIcon = document.querySelector(".dropdown-menu-content");
button.addEventListener('click', function(){
  listIcon.classList.toggle("visible");
});

# Obtenir des informations sur l'événement event
const positionMouse = document.querySelector("#title-cursor-position");		=> Variable du texte de la position de la mouse
document.body.addEventListener("mousemove", function (event) {			=> Si la souris bouge
  positionMouse.innerHTML = `x:${event.clientX}, y:${event.clientY}`;		=> le texte position de souris deviens
});

