---
layout: page
title: Créer et dupliquer
permalink: /js/creer-dupliquer/
---

Comment faire pour créer ou dupliquer un élément HTML?

## Créer un élément

Pour créer un nouvel élément HTML dans votre page, la procédure comporte les étapes suivantes :

1. Définir l'élément avec `document.createElement` - il faut indiquer quel élément HTML on souhaite créer: un `div`, un `p`, un `button`...
2. Indiquer les attributs qu'on aimerait donner à cet élément: id, class, styles CSS...
3. Finalement, ajouter l'élément dans l'arborescence du document, avec les fonctions `insertBefore` ou `appendChild`.

Un exemple complet:

```javascript
var i;
for (i = 0; i < 60; i++) {
  var circle = document.createElement('div');
  circle.className = "circle";
  circle.id = 'circle'+i;
  document.getElementById("grid").appendChild(circle);
}
```

**Résultat:** 

* Cet exemple permet de créer 60 éléments `div`. 
* À chaque élément, on donne une classe "circle", et un identifiant qui comporte un numéro différent pour chaque élément: "circle0", "circle1", "circle2" et ainsi de suite (de 0 à 59). 
* Les éléments ainsi créés seront insérés dans un élément ayant l'ID `grid` (si cet élément n'existe pas, votre code produira une erreur).


## Dupliquer un élément

Pour dupliquer un élément (une fois ou plusieurs de fois), la méthode est très similaire. La seule différence est que nous utilisons `cloneNode`, qui permet de clôner un "node", c'est à dire un élément de la page.

Voici un exemple complet:

```javascript
// On sélectionne notre modèle:
var item = document.getElementById("batons1");

// Une boucle "for" pour le dupliquer:

var i;
for (i = 2; i < 13; i++) {

	// On commence à 2, car on veut numéroter de 2 à 12

	var clone = item.cloneNode(true);
	clone.id = 'batons'+i;
	document.querySelector("body").appendChild(clone);

}
```

### Supprimer un élément

Comment supprimer un élément du DOM?

Avec la méthode `removeChild`:

```javascript
var elem = document.querySelector('#some-element');
elem.parentNode.removeChild(elem);
```