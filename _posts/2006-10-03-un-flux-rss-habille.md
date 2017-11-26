---
id: 342
disqus_id: 342 http://regis.decamps.info/blog/?p=342
title: Un flux RSS habillé
date: 2006-10-03T21:21:08+00:00
author: Régis
excerpt: Mon flux RSS est décoré maintenant avec un petite CSS.
layout: post
guid: http://regis.decamps.info/blog/2006/10/un-flux-rss-habille/
permalink: /blog/2006/10/un-flux-rss-habille/
tmac_last_id:
  - ""
dsq_thread_id:
  - "564736702"
categories:
  - Informatique
tags:
  - Atom
  - Blog engine
  - Hacking
  - Wordpress
---
A l’origine, quand on visitait la page du [flux RSS de ce blog](http://regis.decamps.info/blog/feed/), on tombait sur…; le flux évidemment!

[<img id="image344" src="/blog/wp-content/uploads/2006/10/capture12_rss_nu.thumbnail.png" alt="Flux RSS nu" />](/blog/wp-content/uploads/2006/10/capture12_rss_nu.png "Flux RSS nu"){.imagelink}

Ce n’était pas très joli. Maintenant, quand on visite la page du [flux RSS de ce blog](http://regis.decamps.info/blog/feed/), on tombe sur…; le flux évidemment ; mais joliment présenté.

[<img id="image343" src="/blog/wp-content/uploads/2006/10/capture10_rss_habille.thumbnail.png" alt="Flux RSS habillÃ©" />](/blog/wp-content/uploads/2006/10/capture10_rss_habille.png "Flux RSS habillÃ©"){.imagelink}

On peut ne pas aimer, mais c’est quand même plus joli qu’avant. Je me suis même payé le luxe d’expliquer le fonctionnement du RSS…;

J’ai ajouté une petite feuille de style pour décorer un peu l’affichage. Pour cela, j’ai légèrement modifié WordPress pour qu’il ajoute la ligne
  
`<?xml-stylesheet type="text/css" href="/blog/wp-content/themes/rss.css" ?></p>
<p>Cela s'est fait dans <tt>wp-rss2.php</tt> avec<br />
` `<?php echo '<?xml-stylesheet type="text/css" href="'; echo bloginfo_rss("url"); echo'/wp-content/themes/rss.css" ?>'?>`

Bien sûr, il a aussi fallu faire [une feuille de style](/blog/wp-content/themes/rss.css).
