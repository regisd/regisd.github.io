---
id: 1482
disqus_id: 1482 http://regis.decamps.info/blog/?p=1482
title: Life streaming sur son wordpress
date: 2010-11-03T22:18:05+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=1482
permalink: /2010/11/life-streaming-sur-son-wordpress/
tmac_last_id:
  - ""
dsq_thread_id:
  - "567041807"
categories:
  - Extensions
  - Général
tags:
  - Wordpress
---
Il existe des dizaines de services qui permettent d’agrèger son activé sur le net en un seul endroit: [Friendfeed](http://www.friendfeed.com/); [Lifestreams](http://lifestrea.ms/) ; [Plaxo](http://www.plaxo.com/) Pulse ; [profilactic](http://www.profilactic.com/) ; [AOL Lifestream](http://lifestream.aol.com/) ; (Yahoo!) [mybloglog](http://www.mybloglog.com/) ; Google [Buzz](http://www.google.com/buzz).

Mais à bien y réfléchir, est-ce vraiment prudent de confier ainsi ses données à des entreprises, qui peuvent, du jour au lendemain fermer (mugshot.org), être racheté (jaiku par Google ; Friendfeed par Facebook). Ils peuvent aussi ne pas évoluer comme on le souhaite.

Il n’y a, je pense, qu’une solution: héberger soi-même toute cette activité. Et pout cela, plusieurs logiciels disponibles:

  * Récupérer le [code source de Jaiku](http://code.google.com/p/jaikuengine/) (rendu open-source par Google) et l’héberger sur [Google app engine](code.google.com/appengine/) 
  * Installer [wordpress](http://wordpress.org/) et un plugin de syndication de contenu.

### Feed WordPress

J’ai retenu [Feedwordpress](http://feedwordpress.radgeek.com/). C’est lui qui fait ainsi remonter mes avis de Cityvox vers mon blog.

Evidemment, c’est possible parce que Cityvox offre un flux Atom ou RSS. _A contrario_, j’ai arrêté d’écrire des avis sur Allociné par exemple, parce qu’ils sont alors inexploitables…;
