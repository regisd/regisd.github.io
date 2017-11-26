---
id: 941
title: Synchroniser les contacts de son mobile avec son compte Gmail
date: 2009-11-13T15:56:33+00:00
author: Régis
excerpt: "Synchroniser les contacts de son mobile avec ceux de Gmail peut s'avérer très précieux quand on perd son mobile..."
layout: post
guid: http://regis.decamps.info/blog/?p=941
permalink: /2009/11/synchroniser-les-contacts-de-son-mobile-avec-son-compte-gmail/
dsq_thread_id:
  - "189257821"
tmac_last_id:
  - ""
categories:
  - Mobile
tags:
  - Gmail
  - Google
---
J&rsquo;ai perdu mon Nokia xpress music à l&rsquo;Oktoberfest,. Cela se comprend, les pintes sont des Maß&#8230; J&rsquo;ai fini par en récupérer un neuf auprès de Bouygues (un petit truc, forcément 🙁 ). mais je ne voulais absolument pas re-saisir tous mes contacts. 

J&rsquo;écris cet article pour 2 raisons:

  * parce que je suis surpris que si peu de monde connaisse le protocole [Sync ML](http://fr.wikipedia.org/wiki/SyncML). Plus sérieusement: personne ne semble synchroniser ses contacts avec Google mail, alors que c&rsquo;est très pratique: 
  * si on perd son téléphone
  * mais aussi pour ne pas gérer deux carnets d&rsquo;adresse. La synchronisation de gmail et du mobile résout l&rsquo;éternel problème des carnets d&rsquo;adresses qui contiennent des informations contradictoires
  * la deuxième raison est qu&rsquo;il m&rsquo;a fallu 2 jours pour retrouver les bons paramètres&#8230;.

## Les avantages

Le site [Google sync](http://www.google.com/mobile/products/sync.html) vend très bien les choses.
  


## Comment faire

Le mécanisme fonctionne très bien avec:

  * iPhone (toujours lui)
  * Blackberry (forcément, aussi)
  * La plupart des télephones récents, qui supportent le syncML.

Moi, je suis donc dans le dernier cas.

Normalement, il suffit d&rsquo;utiliser le navigateur wap de son téléphone pour butiner sur http://m.google.com/sync pour configurer automatiquement son téléphone.

J&rsquo;y suis allé, et est été renvoyé par un « votre téléphone n&rsquo;est aps pris en charge actuellement ». **Arg!**

### Configurer manuellement son Nokia

Mais en fait ce n&rsquo;est pas vrai, en configurant manuellement son mobile, ça marche!

Les explications sont un peu cachées dans la page [Device setup instructions](http://www.google.com/support/mobile/bin/topic.py?topic=22181). En fait, on peut prendre un téléphone _proche_. Par exemple, pour un Nokia 3600 ou 5300, les [instructions du Nokia 6300](http://www.google.com/support/mobile/bin/answer.py?hl=en&answer=98265) font l&rsquo;affaire 🙂

A retenir donc:

  * L&rsquo;adresse de synchronisation est <tt>http<strong>s</strong>://m.google.com/syncml</tt> et il ne faut pas s&rsquo;inquiéter si une requête http répond « Error 404 &#8211; not found »
  * Le compte est l&rsquo;adresse gmail complète (y compris @gmail.com)

Hope this helps!