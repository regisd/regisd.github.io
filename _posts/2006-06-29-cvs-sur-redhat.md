---
id: 282
disqus_id: 282 http://regis.decamps.info/blog/?p=282
title: cvs sur Fedora
date: 2006-06-29T19:52:03+00:00
author: Régis
excerpt: "J'ai mis du temps à faire fonctionner CVS pserver sur Fedora."
layout: post
guid: http://regis.decamps.info/blog/2006/06/cvs-sur-redhat/
permalink: /2006/06/cvs-sur-redhat/
tmac_last_id:
  - ""
dsq_thread_id:
  - "892547076"
categories:
  - Linux
tags:
  - SCM
---
J’ai mis du temps à faire fonctionner CVS pserver sur Fedora Core 4. Bizarrement il ne suffit pas de faire « yum install cvs » pour que ça marche. Il faut [soi-même modifier le /etc/pam.d/cvspserver](http://www.network-theory.co.uk/docs/cvsmanual/cvs_30.html "Il faut modifier la configuration de pam pour que cvs server fonctionnne")
  
Je n’aime pas <strike>Redhat</strike> Fedora.
