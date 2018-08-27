---
layout: page
title: Classes
permalink: /js/classes/
---

Accéder aux classes CSS
==

Voici quelques besoins courants: 

- Accéder aux classes CSS d'un élément - p.ex. pour déterminer si un menu est fermé ou ouvert.
- Attribuer une classe CSS à un élément - pour lui appliquer un style, voir une animation CSS.

### Ajouter et supprimer des classes

Voici comment cela se fait avec jQuery:

```javascript
if ($(".icon .bar").hasClass("active")) {
  $(".icon .bar").removeClass("active");
  $(".icon .bar").addClass("notActive");
} else {
  $(".icon .bar").removeClass("notActive");
  $(".icon .bar").addClass("active");
}
```

En JavaScript classique, on utilisait une méthode un peu rudimentaire pour ajouter une classe:

```javascript
el.className += ' ' + className;
```

Il existe désormais une méthode plus pratique, qui est [supportée dans la majorité des navigateurs](https://caniuse.com/#feat=classlist) depuis 2013.

Elle permet de tester si une classe existe:

```javascript
var element = document.querySelector("#box");

element.classList.contains("class-name");
```

Et permet d'ajouter ou supprimer une classe:


```javascript

// ajouter une classe
ELEMENT.classList.add("CLASS_NAME");

// supprimer une classe
ELEMENT.classList.remove("CLASS_NAME");
```

