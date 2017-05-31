---
layout: page
title: MediaQueries
permalink: /js/mediaqueries/
---

Comment faire pour appliquer un code JavaScript à une certaine résolution d'écran ?

Les Media Queries que nous utilisons en CSS, existent-elles en JavaScript ?

Oui, il existe différentes méthodes pour obtenir le même effet en JavaScript. Voici différentes méthodes pour obtenir la largeur actuelle de la fenêtre:

* document.documentElement.clientWidth
* document.body.clientWidth
* window.innerWidth

Ces trois méthodes devraient retourner le même nombre de pixels.

Un exemple d'utilisation:

```javascript

if (document.documentElement.clientWidth < 900) {
	// scripts
}

if (document.documentElement.clientWidth > 680 && document.documentElement.clientWidth < 1260) {
	// scripts
}
```

* screen.width = donne la largeur totale de l'écran, pas toujours égale à la fenêtre du navigateur.

Voici un exemple utilisant cette méthode:

```javascript
if (screen.width >= 600) {
	// complicated script
}
```

## méthode: matchMedia

Une autre méthode consiste à utiliser window.matchMedia() :

```javascript
if (window.matchMedia("(min-width: 400px)").matches) {
  // the view port is at least 400 pixels wide
} else {
  // the view port is less than 400 pixels wide
}
```

On peut aussi tester l'orientation:

```javascript
var mql = window.matchMedia("(orientation: portrait)");
if (mql.matches) {
  /* La zone d'affichage/viewport est en portrait */
} else {
  /* La zone d'affichage/viewport est en paysage */
}
```

[Voir documentation MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Testing_media_queries)

## Méthode subtile

On peut souhaiter suivre les breakpoints du CSS, sans redéfinir les mêmes unités dans le JavaScript. Voici une technique utilisée par Jeremy Keith:

[Conditional CSS](https://adactio.com/journal/5429/)