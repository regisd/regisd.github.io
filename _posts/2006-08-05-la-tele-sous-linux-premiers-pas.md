---
id: 302
disqus_id: 302 http://regis.decamps.info/blog/?p=302
title: 'La télé sous Linux, premiers pas…;'
date: 2006-08-05T16:47:10+00:00
author: Régis
excerpt: "Ca fait plusieurs années que je n'ai pas de télé, mais vu les prix des cartes tuner TNT, j'ai décidé de me lancer dans l'aventure de la TNT. Sous linux, c'est plus fun..."
layout: post
guid: http://regis.decamps.info/blog/2006/08/la-tele-sous-linux-cest-de-la-bombe/
permalink: /blog/2006/08/la-tele-sous-linux-premiers-pas/

dsq_thread_id:
  - "189256654"
categories:
  - High-tech
tags:
  - Linux
  - TV
  - HOWTO
---
Ca fait plusieurs années que je n’ai pas de télé, mais vu les prix des cartes tuner TNT, j’ai décidé de me lancer dans l’aventure de la TNT.

#### Recompilation du noyau

Je suis sous Gentoo linux, et me suis aidé du [guide carte TNT de Desintegr](http://desintegr.eu.org/wordpress/2006/01/27/hauppauge-wintv-hvr-1100-et-linux-partie-1/).

Personnellement, j’ai préféré tout mettre en module plutôt que de compiler « en dur » dans le noyau.

Il ne reste plus qu’à choisir son lecteur…;

#### tvtime

[TVtime](http://tvtime.sourceforge.net/) est spécialisé dans l’affichage de la télévision. 

Je commence la configuration avec:
  
`<br />
tvtime-configure --norm=pal --frequencies=europe<br />
` 

Ensuite, en lançant l’application, il suffit de rentrer dans le menu (touche TAB) et de lancer un scan des chaînes, comme on ferait avec une vraie télé.

J’ai assez rapidement trouvé quelques chaînes.
  
[<img id="image303" src="/blog/wp-content/uploads/2006/08/capture6.thumbnail.png" alt="TVtime screenshot" />](/blog/wp-content/uploads/2006/08/capture6.png "TVtime screenshot"){.imagelink}
  
Le problème, c’est que la qualité n’est pas terrible, et que je n’ai pas de son pour le moment…;
