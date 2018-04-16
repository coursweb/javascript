---
layout: page
title: JavaScript
permalink: /js/
---

**JavaScript** est un langage de programmation...
* **scripté** (interprété) - pas de compilateur à proprement parler.* **côté client** - s’exécute dans un navigateur en général(il existe des environnements côté serveur : NodeJS).* **asynchrone** - plusieurs « morceaux » peuvent s’exécuter en parallèle.

Il a été créé en 1995, pour Netscape Navigator, par Brendan Eich (en 10 jours, selon la légende, pour coïncider avec la sortie de Netscape 2). En fin 1996, Netscape entreprend des démarches pour faire de JavaScript un standard (qui s'appelle ECMAScript). 

JavaScript n'a rien à voir avec **Java**, un autre language de programmation. 

Que permet le JavaScript?
===

Le JavaScript, s'il a été utilisé initialement pour ajouter de "petites fonctionalités" aux navigateurs, comme p.ex. ouvrir des fenêtres pop-up, est néanmoins un langage de programmation à part entière. 

Dans un navigateur JavaScript, permet :
* de spécifier des changements sur le document :* sur le contenu, la structure, le style* en interceptant des événements (souris, clavier, doigts...)

Mais également (API HTML5) :
* d’échanger avec un serveur (AJAX)* de dessiner (canvas - bitmap - ou svg - vectoriel)* de se géolocaliser* d’enregistrer localement du contenu (cache ou bdd)
* de jouer des fichiers audio ou video

<h3>Des applications en JavaScript</h3>

JavaScript est utilisé par des applications comme [Figma](https://www.figma.com/) (éditeur graphique, dont le code est [écrit en C++](https://medium.com/figma-design/building-a-professional-design-tool-on-the-web-6332ed4f1fcc#.8egblptg3) puis converti en JavaScript), ou pour simuler dans le navigateur des ordinateurs historiques (cf. [Internet Arcade](https://archive.org/details/internetarcade)).

Entre ces deux extrêmes, le JavaScript peut être utilisé pour développer des extensions de navigateur - par exemple l'extension Firefox [Add-Art](https://github.com/slambert/Add-Art) qui remplace les bannières publicitaires par des travaux d'artistes - ou pour étendre les fonctionalités de logiciels comme [Adobe InDesign](https://forums.adobe.com/community/indesign/indesign_scripting), [Max](https://docs.cycling74.com/max7/tutorials/javascriptchapter01) ou [Sketch](http://developer.sketchapp.com/introduction/plugin-scripts/). 

![La galaxie javascript, par Olivier Le Goaër](/cours-javascript/img/galaxie-javascript.jpg)

Le standard JavaScript est révisé régulièrement. La 6ème version (ES6 ou ES2015) a été finalisée en juin 2015 et la 7ème (ES7 ou ES2016) en juin 2016. Juriy Zaytev propose un [tableau récapitulatif](http://kangax.github.io/compat-table/) des fonctionnalités supportées par les différentes implémentations et navigateurs.

État du JavaScript en 2017
==

De nombreux utilitaires ont été construits sur la base du JavaScript:

- **jQuery** est une *bibliothèque* JavaScript (library) - une boîte à outils pour faciliter les usages les plus communs.
- **Node.js** est une *plateforme serveur* JavaScript (runtime) - comme Apache, mais exécutant du code JavaScript plutôt que du PHP.
- **AngularJS** est un *framework* de programmation JavaScript front-end, créé par Google.
- **Ember** est un autre *framework* front-end JavaScript.
- **React** est encore un *framework* JavaScript front-end, créé par les développeurs de Facebook.

![Frameworks JavaScript](/cours-javascript/img/js-frameworks.jpg)

Une application web contemporaine, au lieu d'utiliser **LAMP** (**L**inux, **A**pache, **M**ySQL, **P**HP), pourrait tourner sur **MEAN**, acronyme pour l'utilisation de **M**ongoDB (base de données), **E**xpress.js, **A**ngular.js, et **N**ode.js - une base logicielle entièrement codée en JavaScript.

La bibliothèque jQuery
==

Lancée en janvier 2006 par John Resig, **jQuery** est une bibliothèque JavaScript libre et multi-plateforme créée pour faciliter l'écriture de scripts côté client dans le code HTML des pages web.

Dans son article, *[Thank you, jQuery](https://adactio.com/journal/10806)*, publié en juin 2016, Jeremy Keith indique qu'au cours des 10 années depuis la sortie de jQuery, de nombreuses améliorations proposées par jQuery ont été intégrées nativement par les navigateurs (```querySelector```, ```querySelectorAll``` - voir [Selectors API](https://developer.mozilla.org/en-US/docs/Web/API/Document_object_model/Locating_DOM_elements_using_selectors)), tandis que d'autres (comme l'animation) ont font désormais partie du CSS3.

> La plus grosse amélioration que JavaScript a connue dans les navigateurs modernes est peut-être le support de la méthode *querySelectorAll*, qui nous permet d’accéder aux éléments du DOM à l’aide de sélecteurs CSS, comme nous le faisons avec jQuery ! - *Scott Jehl, 2014*  

Il est désormais nettement plus facile de se passer de jQuery, et d'écrire du "Plain Vanilla JavaScript". L'objectif ultime d'un outil comme jQuery serait de ne plus être nécessaire.

Le site [Vanilla JS](http://vanilla-js.com/) expose sous un mode parodique (en se présentant comme une énième bibliothèque JavaScript) les avantages (en termes de vitesse) à utiliser du JavaScript pur, plutôt que de se reposer sur une bibliothèque telle que jQuery, Prototype, Dojo, MooTools.

![](/cours-html/img/Strip-Prendre-le-train-en-marche-650-final1.jpg){:id: .large-image}

Préprocesseurs:
===

On a vu l'apparition de préprocesseurs (comme SASS ou LESS) pour faciliter l'écriture du CSS. Cela existe aussi pour le JavaScript, ces langages sont convertis en JavaScript normal pouvant être compris par le navigateur.

- [**CoffeeScript**](http://coffeescript.org/) est un langage de programmation plus épuré que le JavaScript.
- [**TypeScript**](https://www.typescriptlang.org/) est un langage de programmation plus stricte que le JavaSript, permettant de gérer des types comme en Java. TypeScript est notamment utilisé par AngularJS 2 et sponsorisé par Microsoft.
- [**Dart**](https://www.dartlang.org/) est un langage de programmation proche de Java pouvant être compilé vers JavaScript. Il est utilisé par Google.

