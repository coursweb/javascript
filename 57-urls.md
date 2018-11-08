---
layout: page
title: URLs
permalink: /js/urls/
---

Interagir avec des URLs.

Recharger la page courante: 

```javascript
location.reload();
```

Rediriger vers une autre page:

```javascript
window.location.href="https://oblique-strategies.github.io/";
```

### Tester une variable URL

Il est possible d'inclure une variable dans une URL, et de la récupérer avec du JavaScript. Voici comment récupérer un élément se trouvant à la fin d'une URL, après le symbole #.

```javascript
var modeDemo = window.location.hash;

if ( modeDemo == "#demo" ) {

	// Faire quelque chose

} 
```