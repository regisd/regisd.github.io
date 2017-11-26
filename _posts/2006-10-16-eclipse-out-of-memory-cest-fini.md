---
id: 352
disqus_id: 352 http://regis.decamps.info/blog/?p=352
title: 'Eclipse Out of memory : c’est fini'
date: 2006-10-16T19:32:11+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/2006/10/eclipse-out-of-memory-cest-fini/
permalink: /2006/10/eclipse-out-of-memory-cest-fini/
dsq_thread_id:
  - "189256708"
tmac_last_id:
  - ""
categories:
  - Informatique
tags:
  - Bug
  - Eclipse
  - Java
---
**Edit**: updated in [JVM Terminated -1](http://regis.decamps.info/blog/2008/08/eclipse-jvm-terminated/).

Mon eclipse 3.2.1 était particulièrement instable. Je n’avais pas besoin de faire grand chose pour planter avec un lamentable « Out of memory » <tt>java.lang.OutOfMemoryError: PermGen space</tt>.

Pourtant j’avais modifié mon eclipse.ini :
  
`<br />
-vmargs<br />
-Xms512m<br />
-Xmx1024m<br />
` 

En fait, c’est un autre paramètre qu’il fallait ajouter dans ce fichier de configuration
  
`<br />
-XX:MaxPermSize=256m<br />
` 

Et maintenant ça semble aller mieux 😉
