---
layout: page
title: Manipulation d’objets
permalink: manipulation.html
---

Extensions au noyau JS
==

Objets de type BOM:

Window, Navigator, Screen, History, Location

Objets de type DOM:

DOM Document, DOM Elements, DOM Attributes, DOM Events, ...

Objets de type HTML:

```html
<a>, <area>, <canvas>, <button>, <form>, <iframe>, <image>,
<input>, <link>, <meta>, <object>, <option>, <select>, 
<table>, <td>, <th>, <tr>, <textarea>, ...
```

Permet de manipuler le navigateur
 
Tous les navigateurs (IE, Firefox, Chrome, ...) sont des logiciels qui offrent les mêmes fonctionnalités de base
 
Ouvrir/fermer des onglets, aller à une URL, mémoriser la liste des URL précédemment consultées, etc
 
Arborescence d'objets
 
((image))

Méthodes d'interaction avec l'utilisateur par le biais de la fenêtre du navigateur

Utilisation de l'objet window

```javascript
window.alert("Bienvenue sur ce site !");
```

Divers exemples BOM

```javascript
//affiche dans la console le nom de code du navigateur utilisé
console.log(window.navigator.appCodeName);

//redirige le navigateur vers une adresse quelconque
window.location = "http://www.univ-pau.fr";

//ouvre un nouvel onglet dans le navigateur
var onglet = window.open('http://www.youtube.com');

//Fais revenir une page en arrière (similaire au boutton 'Back')
window.history.back();

//Affiche dans une boite de dialogue la résolution de l'écran utilisé
window.alert(window.screen.availWidth + "x" + window.screen.availHeight);

//Ecrit de l'html directement dans le document (et supprime l'existant)
window.document.write("<b>Bienvenue à l'université de Pau</b>");
```

DOM: Document Object Model

Représentation d'un document x(ht)ml sous sa
forme 100% objet

* Les balises sont des noeuds et leurs imbrications forment une arborescence
* Cette structure d'arbre est ensuite facile à manipuler

L'arbre DOM est chargé dans le navigateur

* L'arbre est parcouru par le moteur de rendu du navigateur afin de produire l'affichage graphique
* Chaque modification ultérieure de cet arbre force le rafraîchissement de l'affichage graphique

Document XHTML : exemple

```html
<!DOCTYPE html>
<html>
<head>
  <title>Bienvenue</title>
  <script src="essai.js"></script>
</head>
<body>
  <p id="intro">
    Pour me contacter : <a href="mailto:moi@example.org">cliquez ici</a>
    <ul>(img
      <li>Uniquement en semaine</li>
    </ul>
  </p>
  <h1 class="joli1">S'inscrire à la Newsletter</h1>
  <form>
    <input type="text" name="news_email"/>
  </form>
</body>
</html>
```(img

Arbre du document XHTML:

![Arbre du document XHTML](/cours-javascript/img/arbre-DOM.jpg)

**Propriétés d'un nœud:**

**Popriétés** | **Commentaires**
childNodes | nœuds enfants (Array)
firstChild | premier nœud enfant
lastChild | dernier nœud enfant
nextSibling | prochain nœud d'un type (nœud de même niveau)
parentNode | nœud parent
previousSibling | nœud précédent d'un type (nœud de même niveau)
nodeName | nom du nœud
nodeValue | valeur / contenu du nœud
nodeType | type du nœud
innerHTML | contenu littéral html du noeud

Navigation dans l'arbre DOM

![Navigation DOM](/cours-javascript/img/DOM-navigation.jpg)

**Méthodes d'un nœud:**

**Méthodes** | **Commentaires**
```createElement()``` | Méthode pour créer un nouvel élément HTML dans le document (div, p, span, a, form, input, etc...).
```createTextNode()``` | Méthode pour créer un nœud texte.
```appendChild()``` | Pour ajouter l'élément créé dans le document. L'élément sera ajouté comme étant le dernier nœud enfant d'un élément parent.
```insertBefore()``` | Pour ajouter l'élément créé avant un autre nœud.
```removeChild()``` | Pour supprimer un nœud.

Accès direct aux nœuds

Par la valeur de **l'attribut id** (si il existe)

```javascript
var result = document.getElementById("intro") ;
// Renverra 0 ou 1 résultat
```  

Par la valeur de **l'attribut class** (si il existe)

```javascript
var result = document.getElementsByClassName("joli1") ;
// Renverra 0 ou n résultats
```      


Par le **nom de la balise** (Tag en anglais)

```javascript
var result = document.getElementsByTagName("input") ;
// Renverra 0 ou n résultats
```   


Par la valeur de **l'attribut name** (si il existe)

```javascript
var result = document.getElementsByName("news_email") ;
// Renverra 0 ou n résultats
```  

Par **les sélecteurs CSS**  

```javascript
var result = document.querySelector("p#intro") ;
// Renverra 0 ou 1 résultat, le premier trouvé
```  


```javascript
var result = document.querySelectorAll("ul.joli > li") ;
// Renverra 0 ou n résultats
```

Exemple qui change les couleurs de fond de tout élément ayant la classe ```.example``` :

```javascript
var x = document.querySelectorAll(".example");
var i;
for (i = 0; i < x.length; i++) {
    x[i].style.backgroundColor = "red";
}
```

> La plus grosse amélioration que JavaScript a connue dans les navigateurs modernes est peut-être le support de la méthode `querySelectorAll`, qui nous permet d’accéder aux éléments du DOM à l’aide de sélecteurs CSS, comme nous le faisons avec jQuery ! - *Scott Jehl, dans: Design web responsive et responsable, 2014*        

Mode d'accès : comparaison
===

Accès par navigation dans l'arbre DOM:

```html
<html>
  <head>
    <title>Bienvenue</title>
    <script>
      function changeColor() {
        var htmlTag = document.childNodes[0];
        var bodyTag = htmlTag.lastChild;
        var pTag = bodyTag.firstChild;
        pTag.style.color="#0000FF";
      }
    </script>
  </head>
  <body onload="changeColor();">
    <p>Lorem Ipsum</p>
  </body>
</html>
```

Accès direct, par l'attribut ID('foo'): 

```html
<html>
  <head>
    <title>Bienvenue</title>
    <script>
      function changeColor() {
        var pTag = document.getElementById('foo');
        pTag.style.color="#0000FF";
      }
    </script>
  </head>
  <body onload="changeColor();">
    <p id="foo">Lorem Ipsum</p>
  </body>
</html>
```

Objets HTML
===

Après avoir navigué et atteint le nœud de son choix, il faut agir dessus

Pour cela, il est nécessaire de connaître sa véritable nature (son type)

nœud ```<body>``` ? nœud ```<h1>``` ?, nœud ```<img>``` ? Etc.

Principe : les attributs Html correspondent aux propriétés de l'objet (en notation CamelCase)

```html
<img src="tux.gif" alt="Linux" id="foo"/>
```

```javascript
var imgTag = document.getElementById('foo'); //navigation
imgTag.src = "tux2.gif"; //action !
```

```html
<input type="text" value="" size="5" id="bar"/>
```

```javascript
var inputTag = document.getElementById('bar'); //navigation
inputTag.value = "coucou"; //action !
inputTag.size = inputTag.size * 2; //action !
```
