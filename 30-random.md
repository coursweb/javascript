---
layout: page
title: Random
permalink: /js/random/
---

Un cas de figure qui exige le recours le JavaScript est le besoin de produire un résultat aléatoire.

En effet, les languages descriptifs que sont le HTML et CSS permettent de structurer et styler des documents, mais il leur est impossible de recourir à l'aléatoire, p.ex. de changer une couleur aléatoirement à chaque chargement de page. Le HTML et le CSS ne connaissent pas le hasard!

Pour produire de l'aléatoire, nous avons besoin d'un langage dynamique comme le JavaScript. Le JavaScript contient toutes sortes de fonctions mathématiques, via l'objet `Math`.

## La fonction Math.random() 

L'objet `Math` possède une fonction très utile, qui va nous permettre de "produire de l'aléatoire": c'est la méthode Math.random().

Voici ce que fait Math.random(): "La fonction Math.random() renvoie un nombre flottant pseudo-aléatoire, généré entre 0 (inclus) et 1 (exclu)".

En d'autres termes, ...

Exemple:

```
0.06658971550365189
Math.random()
0.06022587418583303
Math.random()
0.9733255967240118
Math.random()
0.47738639041701836
Math.random()
0.7644723346354934
Math.random()
0.9238101088571498
Math.random()
0.5152607963708404
Math.random()
0.14983993531041606
```

Comme on le voit, cette fonction produit une valeur aléatoire comprise entre 0 et 1. Cela semble d'une utilité très limitée, mais sachant que la valeur obtenue peut être multipliée par un autre nombre, il est possible d'obtenir au final des nombres aléatoires dans un intervalle qu'on peut spécifier librement.

À partir de là, imaginons que nous souhaitons avoir un nombre aléatoire allant de 1 à 100 (inclus).

Il nous faut faire une opération mathématique.

Le meilleure méthode est de créer une fonction qui nous permet de définir à la volée les chiffres maximum et minimum. Voici une fonction d'usage courant:

```javascript
function getRandom(min, max) {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}
```

Cela semble un peut complexe, mais tout est logique!

Avec cette fonction, si on veut obtenir un chiffre aléatoire situé entre un **minimum** et un **maximum**.  
Pour un chiffre entre 111 et 777, on écrit: ```getRandom(111, 777)```.

Pour attribuer une position aléatoire située entre 10% et 90%, voici comment procéder:

```javascript
document.getElementById("heure").style.top = getRandom(10, 90)+'%';
```

***