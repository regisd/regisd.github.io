---
id: 460
title: Kopete startup slow
date: 2007-10-11T18:51:42+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/2007/10/kopete-startup-slow/
permalink: /2007/10/kopete-startup-slow/
dsq_thread_id:
  - "189257059"
tmac_last_id:
  - ""
categories:
  - Brève
  - English
  - Informatique
  - Linux
  - Logiciel
tags:
  - Bug
---
[Kopete](http://kopete.kde.org/) is a great multi-protocol instant messenger. Some modules can also be plugged, which allows additional functionalities such as splel cheking, message history, statistics, etc.

However, for some times, Kopete startup was very slow (and taking 100% cpu). The solution was simple: [turn off the stat module](http://bugs.kde.org/show_bug.cgi?id=139347)!
