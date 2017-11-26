---
id: 3047
title: 'Jelly Beans: les applications payantes ne fonctionnent plus'
date: 2012-12-05T09:29:29+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=3047
permalink: /2012/12/jelly-beans-avec-applis-payantes/
al2fb_facebook_link_id:
  - 1065233209_4340131895891
al2fb_facebook_link_time:
  - 2012-12-05T10:02:44+00:00
al2fb_facebook_link_picture:
  - post=http://regis.decamps.info/blog/?al2fb_image=1
dsq_thread_id:
  - "959168026"
categories:
  - Brève
  - Programmation
tags:
  - Android
  - Bug
---
Sur la version Android Jelly Beans 4.1.1, [plusieurs composants sont perdus ou désactivés à chaque redémarrage du téléphone](https://code.google.com/p/android/issues/detail?id=34880 "Issue: Google Play installs app to /mnt/asec on Jelly Beans"): il s&rsquo;agit des ContentProviders, des widgets, des papiers-peints animés, des claviers alternatifs.

Cela ne concerne que les applications payantes, qui en raison d&rsquo;une mesure de sécurité, sont installées sur une partition `/mnt/asec` qui n&rsquo;est pas disponible que trop tard dans la phase de démarrage.

Ceci est très frustrant, et vient s&rsquo;ajouter à ma [liste de bugs](/blog/tag/android+bug "Bugs sur Android").
  
<!--more-->

  * C&rsquo;est très frustrant pour l&rsquo;utilisateur, car ça concerne les applications payantes. Or, quand on paye pour une application, c&rsquo;est en général qu&rsquo;on estime qu&rsquo;elle est de meilleure qualité que les autres applications gratuites. Dans ce cas, c&rsquo;est pour avoir quelque chose cassé par le système d&rsquo;exploitation
  * c&rsquo;est frustrant de voir qu&rsquo;Android reste une plateforme en perpétuelle bêta
  * c&rsquo;est très frustrant pour les développeurs, qui peut recevoir des critiques négatives sur Google play, pour lesquelles il ne peut pas répondre, et qui ne sont pas de son fait
  * c&rsquo;est frustrant pour le développeur, qui a développé une application utilisant des composants avancés et complexes, qui voit son travail ruiné par un bug dans le système d&rsquo;exploitation