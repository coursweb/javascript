---
layout: page
title: Arrays
permalink: /js/arrays/
---

Ce chapitre donne quelques informations sur une structure de données particulière : les données tabulaires, ou "array".

Un "array", ce sont des champs de données structurés, un peu comme un tableau excel.

Voici un exemple:

```javascript
var attente = [ 15, 30, 60 ];
```

On reconnait les "array" à un détail typographique: l'utilisation de crochets carrés indique qu'on manipule des array.

L'utilité d'un array, c'est de pouvoir plus facilement manipuler ces données, accéder à un champ particulier, changer leur ordre...

Exemple d'utilisation: le projet [Stratagèmes obliques](https://oblique-strategies.github.io/). Il s'agit d'un "jeu de cartes divinatoires". La principale fonctionalité est un tirage de cartes qui puise dans un ensemble de phrases, accompagnée chacune d'une illustration.

On souhaite que le tirage soit aléatoire, mais que la phrase et l'illustration concordent.

On a donc choisi de créer un "array" à deux colonnes, suivant ce modèle:

```
var cards = [
  ["NaMi_1.jpg","Honore ton erreur comme une intention cachée"],
  ["NaMi_3.jpg","Cascades"],
  ["NaMi_5.jpg","J'aime les ordinateurs, surtout Atari"],
  ["NaMi_7.jpg","Repousse tes limites"],
  ["NaMi_9.jpg","Tape avec ta tête sur ton clavier"]
  // etc.
];
```

Au chargement du site, cet array est mis dans un ordre aléatoire.

## Ordre aléatoire

Voici une fonction pratique, qui permet de mettre un array dans un ordre aléatoire:

```javascript
function shuffle(a) {
  for (let i = a.length; i; i--) {
    let j = Math.floor(Math.random() * i);
    [a[i - 1], a[j]] = [a[j], a[i - 1]];
  }
}
```

On peut l'appliquer sur un array de cette façon:

```javascript
shuffle(array);
```

