---
id: 121
title: 'LDAP pour son carnet d&rsquo;adresses?'
date: 2005-12-04T15:38:02+00:00
author: Régis
layout: post
guid: http://blog.decamps.info/?p=121
permalink: /2005/12/ldap-pour-son-carnet-dadresses/
tmac_last_id:
  - ""
dsq_thread_id:
  - "615777773"
categories:
  - Extensions
  - Informatique
  - Sites web
---
Séb vient d&rsquo;ouvrir son blog et s&rsquo;interroge sur \[la façon de gérer son carnet d&rsquo;adresse avec LDAP\](http://blog.multiseb.com/?p=2).

Nos besoins sont les mêmes: nous voulons avoir un référentiel unique contenant l&rsquo;intégralité de notre carnet d&rsquo;adresse, et avoir la possibilité de consulter et modifier ce référentiel depuis divers programmes (thunderbird, squirelmail, etc).

Techniquement, la solution qui vient la première à l&rsquo;esprit est de construire son \[carnet d&rsquo;adresses sur LDAP\](http://www.onlamp.com/pub/a/onlamp/2003/03/27/ldap_ab.html). Tous les clients de courrier peuvent consulter un annuaire LDAP, et il existe tous les langages de programmation ont des API pour y accéder. Mais les choses ne sont pas si simples:

* si toutes les grosses entreprises possèdent un LDAP en interne, il n&rsquo;existe pas d&rsquo;annuaire public dans lequel on puisse écrire. Cela oblige à héberger son propre serveur LDAP, et impose donc un minimum de disponibilité de celui-ci.
  
* si la consultation d&rsquo;un LDAP est immédiate, la modification de données est une autre paire de manches. Seb, ne te fatigue pas: Thunderbird ne peut pas écrire dans LDAP.
  
* des programmes spécifiques peuvent manipuler l&rsquo;arbre LDAP (comme \[LDAP browser\](http://www-unix.mcs.anl.gov/~gawor/ldap/)), mais ils sont trop génériques pour être agréables pour l&rsquo;édition d&rsquo;un carnet d&rsquo;adresses.

En cherchant bien, on finit par trouver des solutions:

* plusieurs groupwares s&rsquo;appuient sur un LDAP, et une interface web permet la modification des contacts: \[e-groupware\](http://www.egroupware.org/), \[kolab\](http://www.kolab.org/), \[Novell Open-exchange\](http://mirror.open-xchange.org/), etc.
  
* quelqu&rsquo;un écrit le programme qu&rsquo;on voulait: \[Directory asssitant\](http://olivier.sessink.nl/directoryassistant/) ou \[LABE\](http://www.savoirfairelinux.com/labe/index.php)

Une autre approche consiste peut-être à considérer que LDAP est trop complexe, et qu&rsquo;il vaut mieux s&rsquo;appuyer sur une etite base de données relationnelle. 

Pour ma part, j&rsquo;ai laissé tombé&#8230; J&rsquo;utilise \[Plaxo\](https://www.plaxo.com/) et j&rsquo;utilise la fonction d&rsquo;export des contacts pour mettre à jour mon carnet sous Thunderbird ou Gmail. Mise à jour: Encore mieux, plaxo propose une \[extension pour Thunderbird\](http://www.plaxo.com/downloads/tbird)