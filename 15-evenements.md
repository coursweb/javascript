---
layout: page
title: Événements
permalink: /js/evenements/
---

Evènements HTML
==

**Évènement** | **Élément(s) HTML concerné(s)**
`onLoad` | BODY, FRAMESET, OBJECT
`onUnload` | BODY et FRAMESET
`onError` | IMG, OBJECT, BODY et FRAMESET
`onAbort` | BODY et FRAMESET
`onSelect` | INPUT et TEXTAREA
`onChange` | INPUT, SELECT et TEXTAREA
`onSubmit` | FORM
`onReset` | FORM
`onFocus` | LABEL, INPUT, SELECT, TEXTAREA et BUTTON
`onBlur` | LABEL, INPUT, SELECT, TEXTAREA et BUTTON
`onResize` | BODY
`onScroll` | BODY
`onClick` | Quasiment tout
`onMouseOver` | Quasiment tout
`onContextMenu` | Quasiment tout

Il existe un grand nombre d'événements, voici quelques références:

* Wikipedia: [DOM Events](https://en.wikipedia.org/wiki/DOM_events)
* w3schools: [Liste des DOM Events](https://www.w3schools.com/jsref/dom_obj_event.asp)
* Mozilla: [Référence des événements DOM](https://developer.mozilla.org/fr/docs/Web/Events).
* W3C: [Spécification UI Events](https://w3c.github.io/uievents/) du .


Deux stratégies possibles:

Directement à l'aide d'attributs dédiés (inline):

```html<input type="text" id="userName" onBlur="doSomething();" onFocus="doSomethingElse();"/>
```

Ou mise en place d'écouteurs d'évènement:

```html
<head>
  <script>
    var inputTag = document.getElementById('userName'); 
    inputTag.addEventListener('blur', doSomething(), false);    inputTag.addEventListener('focus', doSomethingElse(), false);  </script>
</head><body>  <input type="text" id="userName"/></body>
```

Evènements et standards
==

Le navigateur implèmente des comportements par défaut pour les évènements

* Le clic gauche sur un lien hypertexte charge un nouveau document,* Un clic gauche sur un bouton soumet le formulaire,
* Un clic droit affiche un menu contextuel,* ...

Il est possible d'inhiber ce comportement par défaut, et le remplacer si besoin:

```html
<a href="#" onclick="return false">Continuer</a>
```
