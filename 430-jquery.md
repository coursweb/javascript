---
layout: page
title: jQuery
permalink: /js/jquery
---

jQuery est une librairie javascript populaire, qui facilite la manipulation d'élémenents, et offre des raccourcis pour des actions fréquentes.

Charger jQuery
==

Voici la manière de charger jQuery.

- Pour commencer, rendez-vous sur le site [jquery.com](http://jquery.com/)  pour vous procurer la dernière version.
- Cliquer sur le bouton "Download jQuery"
- Parmi les divers liens proposés, choisissez le lien qui dit *"Download the compressed, production jQuery"*
- En cliquant le lien, faites "Enregistrer sous", et enregistrez le fichier *jquery-3.1.1.min.js* à l'endroit approprié.

Une fois cela fait, il faut inclure jQuery dans votre page HTML. Voici le code pour inclure un fichier:

```
<script src="jquery.js"></script>
```

Exemple de code
==

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