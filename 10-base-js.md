---
layout: page
title: Bases JavaScript
permalink: /js/bases/
---

Quelques bases JavaScript...

Navigateurs et JavaScript
==

Chaque navigateur intègre un interpréteur de JS, plus ou moins performant: 
SpiderMonkey (Firefox), V8 (Google Chrome), Chakra (Internet Explorer), SquirrelFish (Safari)

Le JavaScript permet un niveau d'interactivité plus riche qu'avec de l'HTML simple:
* Certains traitements simples (ex: contrôle des saisies utilisateur) peuvent être réalisés par le navigateur plutôt que par le serveur.
* Un document HTML/CSS chargé dans le navigateur peut être "remanié" dynamiquement.

Placer du JavaScript dans un document HTML
==

Comme pour les feuilles de style CSS, vous avez plusieurs options:

**1) Dans un fichier séparé:** 

Vous pouvez enregistrer votre code JavaScript dans un fichier dont le nom se terminera par `.js`. 

Vous devrez les charger ainsi:

```html
<script src="script.js"></script>
```

C'est la méthode recommandée : déplacer le code JavaScript dans un fichier externe et utiliser le moins possible du code inline dans un fichier HTML pour favoriser la maintenabilité et séparer clairement les responsabilités.

On placera ce code soit dans la partie ```<head>``` du document (si on souhaite que le JavaScript s'exécute *avant* le chargement du contenu), ou tout en bas, juste avant la balise fermante ```</body>``` (si on souhaite que le contenu soit chargé en premier, ce qui est souvent le cas).

Il est possible d'influer sur le chargement du JavaScript avec deux attributs, **"async"** et **"defer"**.

```html
<script async src="script.js">
```

Normalement, lorsque le navigateur charge un fichier JavaScript, le rendu visuel de la page est ***bloqué*** pendant ce laps de temps. En effet, le chargement d’une ressource JavaScript est bloquante. Avec l'attribut **"async"**, on peut indiquer au navigateur que le rendu de la page peut se poursuivre **en parallèle** (de manière **asynchrone**).

```html
<script defer src="script.js">
```

L'attribut **"defer"** indique au navigateur que le rendu de la page peut se poursuivre pendant le chargement du fichier JavaScript, et que l'exécution de celui-ci doit attendre que le rendu intégral de la page soit fini. Cela garantit que le JavaScript ne ralentit pas le chargement. Voir [cet article](https://bitsofco.de/async-vs-defer/) d'Ire Aderinokun pour plus de détails.

**2) Dans le code de la page HTML (inline):**

```html
<script>
//ici vos définitions de fonctions/procédures JS //...
</script>
```


**3) Directement dans un élément HTML:**

```html
<a href="#" onclick="alert('Vous avez cliqué !'); return false;">Cliquez-moi !</a>
```

**4) Dans la console développeur:**

La console est un outil intégré à votre navigateur. Voici comment l'afficher:

* Dans Chrome: Alt+Cmd+J
* Dans Firefox: Alt+Cmd+K
* Dans Safari: Alt+Cmd+C

Si vous effectuez cela sur Facebook, vous constaterez que cette plateforme n'apprécie pas que ses utilisateurs ouvrent la console développeur:

![Message d’avertissement de Facebook apparaissant dans la console](/cours-javascript/img/fb-console.jpg)

L'artiste James Bridle a [écrit un article](http://booktwo.org/notebook/welcome-js/) et développé un script  - [welcome.js](https://github.com/stml/welcomejs/) - en résponse à cette pratique.

### Trois instructions pour démarrer

Afficher une boîte avec un message:

```javascript
alert("Bonjour !");
```

Écrire du texte dans la console (pour débugguer):

```javascript
console.log("Texte d'essai");
```

Écrire quelque chose dans le document, dans une balise HTML qui a un certain id:

```javascript
document.getElementById('item').innerHTML = "<p>Mon contenu</p>";
```

Quelques explications sur cette ligne de code très puissante:

- **"document"** est un objet JavaScript qui correspond à l'ensemble de la page HTML actuelle.
- **"getElementById()"** est une fonction permettant de sélectionner un élément HTML précis, en fonction de son attribut "id". Ici, on sélectionne l'élément dont l'identifiant est "item".
- **"innerHTML"** est une méthode permettant de redéfinir (de remplacer complètement) le contenu d'un objet HTML.
- Ces commandes sont "accollées" par l'utilisation du point. En JavaScript, le point sert à créer un enchaînement d'opérations, qui se lisent de gauche à droite: "dans ce document, on effectue une sélection par identifiant, dans laquelle on effectue un remplacement de contenu".
- Le signe "=" introduit le contenu qui sera inséré par la foncion innerHTML. Le contenu doit être encadré par des guillemets (simples ou doubles). Comme on le voit, il peut se composer de texte et de HTML.

## Syntaxe JavaScript

Chaque instruction est séparée par un point-virgule (;).

Syntax des commentaires:  
Par ligne : 

```javascript
// Ceci est un commentaire sur une ligne
```

Par bloc : 

```javascript
/* Ceci est un
commentaire 
sur plusieurs lignes
*/
```

Conventions

* Noms de variables et fonctions écrits en CamelCase
* Noms de constantes écrits en majuscule

### Déclaration et typage

* Variables avec le mot clé "var" 
* Constantes avec le mot clé "const"
* Une variable peut être déclarée après avoir été utilisée (hoisting)

### Types primitifs

```javascript

// Entier
var annee = 2014;

// Réel
var prix_ttc = 45.789;

// Chaîne de caractère
var message="Gangnam style";
var message='Gangnam style';

// Booléen
var estSympa=true;
```

Notion de fonction
===

Une fonction, c'est un ensemble d’instructions prêt à être utilisé après sa déclaration.

Dans cette exemple, on déclare une fonction "afficher()". Elle va effectuer deux actions: afficher un message dans la console, et dans un élément HTML.

Cette fonction va recevoir deux paramètres, "id" et "message".

```javascript
// déclaration de la fonction
function afficher(id, message) {
  console.log("Message: " + message);
  document.getElementById(id).innerHTML = message;
};
// deux exemples d'appel
afficher("id1", "<p>Du contenu bien frais !</p>");
afficher("id2", "Un autre contenu.");
```

Particularités des fonctions:

* Permet la ré-utilisabilité du code
* Deux temps : la déclaration, puis l’appel
* Peut avoir des paramètres (ici id et message)

### Structures de contrôle

Condition

```javascript
if (expr) { ... } else { ... }
```

Boucle

```javascript
while (expr) { ... }
do { ... } while (expr);
```

Sélection

```javascript
switch(expr) { case n:...}
```

Itération

```javascript
for (expr1; expr2; expr3) { ... }
for (value in object) { ... } for each (key in object) { ... }
```

Enchaînement

```javascript
with(object) { key1...}
```

Opérateurs arithmétiques
===

Opérateurs binaires

Opérateurs unaires

Opérateurs logiques

