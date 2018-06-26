---
layout: page
title: URLs
permalink: /js/urls/
---

Interagir avec des URLs.

Recharger la page courante: `location.reload();`

Redireger vers une page:

window.location.href="https://oblique-strategies.github.io/";

### Tester une variable URL

```javascript
var modeDemo = window.location.hash;

if ( modeDemo == "#demo" ) {

	// Faire quelque chose

} 
```