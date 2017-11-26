---
id: 121
disqus_id: 121 http://regis.decamps.info/blog/?p=121
title: 'LDAP pour son carnet d’adresses?'
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
Séb vient d’ouvrir son blog et s’interroge sur \[la façon de gérer son carnet d’adresse avec LDAP\](http://blog.multiseb.com/?p=2).

Nos besoins sont les mêmes: nous voulons avoir un référentiel unique contenant l’intégralité de notre carnet d’adresse, et avoir la possibilité de consulter et modifier ce référentiel depuis divers programmes (thunderbird, squirelmail, etc).

Techniquement, la solution qui vient la première à l’esprit est de construire son \[carnet d’adresses sur LDAP\](http://www.onlamp.com/pub/a/onlamp/2003/03/27/ldap_ab.html). Tous les clients de courrier peuvent consulter un annuaire LDAP, et il existe tous les langages de programmation ont des API pour y accéder. Mais les choses ne sont pas si simples:

* si toutes les grosses entreprises possèdent un LDAP en interne, il n’existe pas d’annuaire public dans lequel on puisse écrire. Cela oblige à héberger son propre serveur LDAP, et impose donc un minimum de disponibilité de celui-ci.
  
* si la consultation d’un LDAP est immédiate, la modification de données est une autre paire de manches. Seb, ne te fatigue pas: Thunderbird ne peut pas écrire dans LDAP.
  
* des programmes spécifiques peuvent manipuler l’arbre LDAP (comme \[LDAP browser\](http://www-unix.mcs.anl.gov/~gawor/ldap/)), mais ils sont trop génériques pour être agréables pour l’édition d’un carnet d’adresses.

En cherchant bien, on finit par trouver des solutions:

* plusieurs groupwares s’appuient sur un LDAP, et une interface web permet la modification des contacts: \[e-groupware\](http://www.egroupware.org/), \[kolab\](http://www.kolab.org/), \[Novell Open-exchange\](http://mirror.open-xchange.org/), etc.
  
* quelqu’un écrit le programme qu’on voulait: \[Directory asssitant\](http://olivier.sessink.nl/directoryassistant/) ou \[LABE\](http://www.savoirfairelinux.com/labe/index.php)

Une autre approche consiste peut-être à considérer que LDAP est trop complexe, et qu’il vaut mieux s’appuyer sur une etite base de données relationnelle. 

Pour ma part, j’ai laissé tombé…; J’utilise \[Plaxo\](https://www.plaxo.com/) et j’utilise la fonction d’export des contacts pour mettre à jour mon carnet sous Thunderbird ou Gmail. Mise à jour: Encore mieux, plaxo propose une \[extension pour Thunderbird\](http://www.plaxo.com/downloads/tbird)
