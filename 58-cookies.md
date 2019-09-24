---
layout: page
title: Cookies
permalink: /js/cookies/
---

Les cookies sont un moyen d'enregistrer une information propre à l'utilisateur, dans la session utilisateur du navigateur.

Ce procédé sera utile p.ex. pour un site offrant une fonctionalité de "login", ou pour enregistrer des préférences comme p.ex. le choix de langue dans un site multilingue.

## Méthodes JavaScript

Voici des méthodes JavaScript pour créer et lire les cookies.

Le code suivant va enregistrer un cookie avec jQuery, lorsque l'utilisateur clique sur un lien contenant un paramètre de langue.

```javascript

$(".lang-nav").on("click", "a", function(){
 		 // définir un attribut de langue via un paramètre d'URL:
 		 // example = ?lang=fr
 		 var lang = $(this).attr('href');
 		 // un "replace" pour ne garder que l'identifiant de langue
 		 var lang = lang.replace("?lang=", "");
 	
 		 // Set a language Cookie!
 		 
 		 var date = new Date();
 		 date.setTime(date.getTime() + (15 * 24 * 60 * 60 * 1000)); // 15 days
 		 expires = "; expires=" + date.toGMTString(); 
 		 document.cookie = "coursweblang=" + lang + expires + "; path=/"; 
 		 
 		 return false;
  });
  
 ```
 
## Méthodes PHP

## Lire un Cookie en PHP
 
Voici une méthode pour lire un Cookie avec le language PHP, donc côté serveur. On vérifie d'abord si le Cookie existe, si ce n'est pas le cas, on définit une valeur par défaut.
 
Si le cookie existe, notre variable PHP $lang prendra la valeur du Cookie, et nous pourrons p.ex. afficher le contenu dans la langue correcte.
 
 ```php
 
 if ( !isset($_COOKIE["coursweblang"]) ) {
			  
    $lang = "fr";
			  
  } else {
			  			  
    $lang = $_COOKIE["coursweblang"];
			
}
```

## Ecrire un cookie en PHP

Pour écrire (enregistrer) un cookie pour l'utilisateur actuel, on utilisera la fonction `setcookie()`.

On enregistre les informations suivantes:

- nom (identifiant) du cookie.
- valeur du cookie.
- durée de vie du cookie, en secondes.
- URL concernée.

Voici un exemple: 

```php
$cookie_name = "user";
$cookie_value = "John Doe";
setcookie($cookie_name, $cookie_value, time() + (86400 * 30), "/"); // 86400 = 1 day
```