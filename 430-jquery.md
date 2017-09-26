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

