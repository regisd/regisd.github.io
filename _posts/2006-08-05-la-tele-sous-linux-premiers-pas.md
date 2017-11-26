---
id: 302
title: 'La télé sous Linux, premiers pas&#8230;'
date: 2006-08-05T16:47:10+00:00
author: Régis
excerpt: "Ca fait plusieurs années que je n'ai pas de télé, mais vu les prix des cartes tuner TNT, j'ai décidé de me lancer dans l'aventure de la TNT. Sous linux, c'est plus fun..."
layout: post
guid: http://regis.decamps.info/blog/2006/08/la-tele-sous-linux-cest-de-la-bombe/
permalink: /2006/08/la-tele-sous-linux-premiers-pas/
tmac_last_id:
  - ""
dsq_thread_id:
  - "189256654"
categories:
  - Linux
---
Ca fait plusieurs années que je n&rsquo;ai pas de télé, mais vu les prix des cartes tuner TNT, j&rsquo;ai décidé de me lancer dans l&rsquo;aventure de la TNT.

#### Recompilation du noyau

Je suis sous Gentoo linux, et me suis aidé du [guide carte TNT de Desintegr](http://desintegr.eu.org/wordpress/2006/01/27/hauppauge-wintv-hvr-1100-et-linux-partie-1/).

Personnellement, j&rsquo;ai préféré tout mettre en module plutôt que de compiler « en dur » dans le noyau.

Il ne reste plus qu&rsquo;à choisir son lecteur&#8230;

#### tvtime

[TVtime](http://tvtime.sourceforge.net/) est spécialisé dans l&rsquo;affichage de la télévision. 

Je commence la configuration avec:
  
`<br />
tvtime-configure --norm=pal --frequencies=europe<br />
` 

Ensuite, en lançant l&rsquo;application, il suffit de rentrer dans le menu (touche TAB) et de lancer un scan des chaînes, comme on ferait avec une vraie télé.

J&rsquo;ai assez rapidement trouvé quelques chaînes.
  
[<img id="image303" src="http://regis.decamps.info/blog/wp-content/uploads/2006/08/capture6.thumbnail.png" alt="TVtime screenshot" />](http://regis.decamps.info/blog/wp-content/uploads/2006/08/capture6.png "TVtime screenshot"){.imagelink}
  
Le problème, c&rsquo;est que la qualité n&rsquo;est pas terrible, et que je n&rsquo;ai pas de son pour le moment&#8230;