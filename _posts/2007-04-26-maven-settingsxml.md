---
id: 409
title: Maven settings.xml
date: 2007-04-26T18:19:59+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/2007/04/maven-settingsxml/
permalink: /2007/04/maven-settingsxml/
tmac_last_id:
  - ""
dsq_thread_id:
  - "558802718"
categories:
  - Informatique
tags:
  - M2settings
  - Maven
---
J&rsquo;avais [déjà parlé](http://regis.decamps.info/blog/2006/10/maven-est-formidable/) de [m2settings](http://code.google.com/p/m2settings/) quand j&rsquo;en avais eu l&rsquo;idée, mais du prosélytisme occasionnel ne fait pas de mal&#8230; J&rsquo;ai avancé mon petit [utilitaire qui permet de configurer le fichier de configuration (settings.xml) de Maven 2](http://code.google.com/p/m2settings/).

Alors pourquoi cette simple interface graphique pour manipuler un fichier XML n&rsquo;est-elle pas déjà finie?

  * Eh bien déjà parce que j&rsquo;ai manqué de temps, et ce n&rsquo;est pas en passant 4h tous les 4 mois qu&rsquo;on avance.
  * s&rsquo;ajoute à cela un manque de motivation, visiblement m2settings ne suscite pas un grand intérêt
  * ensuite parce que le Visual Editor d&rsquo;Eclipse manquait de stabilité chez moi. Et l&rsquo;idée que l&rsquo;éditeur fasse de l&rsquo;introspection trouve ses limites quand on commence à faire de l&rsquo;héritage de classes graphiques. Très rapidement, le Visual Editor s&rsquo;est mis à afficher des fenêtres entièrement grises et je devais faire du Swing à la main &#8212; non je ne suis pas fan. Bref, j&rsquo;ai changé du tout au tout au profit de Netbeans (et forcément il faut refaire toute l&rsquo;interface, et prendre en main NetBeans, aussi)
  * et puis, le modèle objet de projet (le POM) n&rsquo;est pas non plus si simple
  * enfin, je me rends compte que mon AMD 64 n&rsquo;est pas non plus un foudre de guerre &#8212; j&rsquo;ose à peine imaginer ce que ça donne sur une machine moins performante