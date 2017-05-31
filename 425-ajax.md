---
layout: page
title: Ajax
permalink: /js/ajax/
---

La technologie Ajax

Asynchronous JavaScript and XML (Ajax)

Un objet spécial sert à effectuer des requêtes/réponses HTTP en arrière plan d'un document déjà chargé

Bouscule les habitudes de navigation par page

Une seule URL (une seule page) semble désormais rendre toute les fonctionnalités possibles

Requête/réponse HTTP

Fonctionnement asynchrone (ou pas)

```javascript
/* VERSION SYNCHRONE */var xmlhttp = new XMLHttpRequest();
xmlhttp.open("GET", "http://ailleurs.com", false);
xmlhttp.send();
// bloqué ici en attente de la réponse...
window.alert(xmlhttp.responseText);
```

```javascript
/* VERSION ASYNCHRONE */
var xmlhttp = new XMLHttpRequest();
xmlhttp.onreadystatechange = function() {
  if (xmlhttp.readyState == 4 && xmlhttp.status == 200) {
    window.alert(xmlhttp.responseText); 
  }
};
xmlhttp.open("GET", "http://ailleurs.com", true);
xmlhttp.send();
```

Choix du format de la réponse:

* Textuel (responseText) : chaînes ou alors innerHtml
* XML (responseXml) : accès au DOM !