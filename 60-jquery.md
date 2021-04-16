---
layout: page
title: jQuery
permalink: /js/jquery
---

jQuery est une bibliothèque javascript populaire, qui facilite la manipulation d'élémenents, et offre des raccourcis pour des actions fréquentes.

## À propos de jQuery

Lancée en janvier 2006 par John Resig, **jQuery** est une bibliothèque JavaScript libre et multi-plateforme créée pour faciliter l'écriture de scripts côté client dans le code HTML des pages web.

Dans son article, *[Thank you, jQuery](https://adactio.com/journal/10806)*, publié en juin 2016, Jeremy Keith indique qu'au cours des 10 années depuis la sortie de cette bibliothèque, de nombreuses améliorations proposées par jQuery ont été intégrées nativement par les navigateurs (```querySelector```, ```querySelectorAll``` - voir [Selectors API](https://developer.mozilla.org/en-US/docs/Web/API/Document_object_model/Locating_DOM_elements_using_selectors)), tandis que d'autres (comme l'animation) font désormais partie du CSS3.

> La plus grosse amélioration que JavaScript a connue dans les navigateurs modernes est peut-être le support de la méthode *querySelectorAll*, qui nous permet d’accéder aux éléments du DOM à l’aide de sélecteurs CSS, comme nous le faisons avec jQuery ! - *Scott Jehl, 2014*  

Il est désormais nettement plus facile de se passer de jQuery, et d'écrire du "Plain Vanilla JavaScript". L'objectif ultime d'un outil comme jQuery serait de ne plus être nécessaire.

Le site [Vanilla JS](http://vanilla-js.com/) expose sous un mode parodique (en se présentant comme une énième bibliothèque JavaScript) les avantages (en termes de vitesse) à utiliser du JavaScript pur, plutôt que de se reposer sur une bibliothèque telle que jQuery, Prototype, Dojo, MooTools.

![](/cours-html/img/Strip-Prendre-le-train-en-marche-650-final1.jpg){:id: .large-image}


## Charger jQuery

Voici la manière de charger jQuery.

- Rendez-vous sur le site [jquery.com](http://jquery.com/)  pour vous procurer la dernière version.
- Cliquer sur le bouton "Download jQuery"
- Parmi les divers liens proposés, choisissez le lien qui dit *"Download the compressed, production jQuery"*
- En cliquant le lien, faites "Enregistrer sous", et enregistrez le fichier *jquery-3.1.1.min.js* à l'endroit approprié.

Une fois cela fait, il faut inclure jQuery dans votre page HTML. Voici le code pour inclure un fichier:

```
<script src="jquery.js"></script>
```

## Exemple de code

Voici un exemple de code jQuery:

```
<script>
 $("body").append("<h1>Salut les jeunes</h1>");
</script>
```

Avec la méthode "append", jQuery créé un nouvel élément (balise h1 avec le texte "Salut les jeunes"), à l'intérieur de l'élément "body".

### Protection antispam des adresses email

Voilà un problème épineux: comment faire figurer un email de contact sur un site web sans se faire spammer?

D'une part, nous souhaitons que les visiteurs puissent facilement envoyer un email. Le mieux serait d'intégrer l'adresse avec une balise HTML, qui permet de simplement cliquer l'adresse: 

```html
<a href="mailto:contact@example.com">contact@example.com</a>
```

Le problème est que ce code est facilement lisible par des robots analysant des millions de pages web, pour récolter les adresses email, et les intégrer dans des listes d'adresses revendues à des spammeurs.

Une méthode de se protéger est de remplacer le texte par une image, ou d'écrire l'adresse en utilisant un subterfuge comme : "écrivez à contact arobase suivi du domaine de ce site". Cela n'est pas idéal, car cela exige un effort supplémentaire de la part de nos visiteurs humains.

Le JavaScript peut résoudre ce problème: nous pouvons ecrire l'adresse d'une manière que les robots ne comprendrons pas, mais la convertir en adresse cliquable pour les visiteurs. Voici un exemple de script jQuery:

```javascript
$.fn.emailSpamProtection = function(className) {
  return $(this).find("." + className).each(function() {
    var $this = $(this);
    var s = $this.text().replace(" [at] ", "&#64;");
    $this.html("<a href=\"mailto:" + s + "\">" + s + "</a>");
  });
};
$("body").emailSpamProtection("email");
```

À noter que cela exige d'écrire nos adresses mail avec une syntaxe particulière: 

```html
<span class="email">contact [at] example.com</span>
```

### Liens externes dans nouveau tab

Une fonctionalité souvent utilisée, dans un site, consiste à ouvrir les liens sortants dans un nouvel onglet. Voici une méthode permettant d'appliquer ce comportement avec jQuery:

```javascript
$("a[href^=http]").each(
  function(){ 
    if(this.href.indexOf(location.hostname) == -1) {
      $(this).attr('target', '_blank');
    }
  }
);
```

Voici un code faisant la même chose, en "pur JavaScript", sans recourir à jQuery:

```javascript
for (var links = document.links, i = 0, a; a = links[i]; i++) {
  if (a.host !== location.host) {
    a.target = '_blank';
  }
}
```

### Afficher et masquer un menu

Voici un code jQuery faisant usage de "toggle":

```javascript
$( ".mobile-menu"  ).click(function() {
  $("#menu").toggle();
});
```

Dans certaines situations, il est utile de vérifier l'état du menu avant de procéder à l'action afficher / masquer:

```javascript
/* 
 * 2.
 * Mobile Menu
 ****************************************************
 * Show/hide the menu when clicking on .mobile-menu
 */

$( ".mobile-menu"  ).on("click", function(){
  var state = $("#menu").data( "toggle" );
  if ( state == "open") {
    $("#menu").hide().data( "toggle", "closed" );
  } else {
    $("#menu").show().data( "toggle", "open" );
  }
});

```

Ce script utilise les méthodes suivantes:

* `$( ".mobile-menu"  )` : C'est le sélecteur qui définit l'objet cliquable, qui va déclencher L'action afficher / masquer.
* `.on("click", function()` : la méthode `on()` est l'une des plus importantes dans jQuery. Elle permet de déclencher une suite d'opérations après un événement. Ici nous avons choisi "click".
*  `var state = $("#menu").data( "toggle" )`: On définit une variable nommée "state", pour détecter l'état actuel de notre menu – est-il ouvert ou fermé? Le sélecteur `$("#menu")` correspond à notre menu. La méthode `data()` permet de lire un attribut "data" (un attribut HTML, qui peut être appliqué sur tout élément comme une classe CSS, mais sert uniquement à stoquer une donnée utilisable en JavaScript).
* `if ( state == "open") {` : Nous vérifions si l'état (c.à.d. la valeur de notre attribut data-toggle) est "open", ou non.
* `$("#menu").hide()` : Le menu étant ouvert, notre action consiste à le masquer, avec la méthode jQuery `hide()`...
* `.data( "toggle", "closed" )` : En plus de le fermer, nous redéfinissons l'attribut "data-toggle" et lui donnons la valeur "closed".
* `} else {` : Si le menu n'est pas ouvert.
* `$("#menu").show()`: Avec la méthode `show()` on affiche le menu.
* `.data( "toggle", "open" )` : ...et on redéfinit l'attribut "data-toggle", sa valeur est désormais "open".
