---
id: 1596
title: Application sur carte SD
date: 2011-01-07T19:32:57+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=1596
permalink: /2011/01/application-sur-carte-sd/
tmac_last_id:
  - ""
dsq_thread_id:
  - "648949368"
categories:
  - Informatique
  - Mobile
tags:
  - Android
---
S&rsquo;il y a bien un point sur lequel l&rsquo;iPhone OS dépasse Android, c&rsquo;est la gestion de la mémoire pour les applications.

  * Sur iPhone, une application peut être installée tant qu&rsquo;il y a de l&rsquo;espace en mémoire (soit dans les 4Go ou plus de l&rsquo;appareil).
  * Sur Android, une application ne peut être installée que dans l&rsquo;espace mémoire réservé de la RAM du téléphone

Heureusement, Android 2.2 Froyo (API level 8) améliore les choses, en permettant de déplacer les applications sur carte SD. Oui mais

  * il en reste toujours un petit bout en RAM (la technique présente donc aucun intérêt pour les petites applications)
  * et surtout il faut que le développeur ait prévu le coup, c&rsquo;est-à-dire ait [ajouté une ligne dans son fichier Manifest](http://developer.android.com/guide/appendix/install-location.html)

Et c&rsquo;est ici que le bât blesse, car les développeurs de certaines grosses applications n&rsquo;ont pas placé cette option. Certes, toutes [les applications ne devraient pas l&rsquo;être](http://developer.android.com/guide/appendix/install-location.html#ShouldNot) mais, qu&rsquo;est ce qui empêche

  * Google maps
  * [RATP Lite](http://www.ratp.fr/fr/ratp/r_26687/ratp-lite-pour-android-market/) (qui n&rsquo;a de Lite que le nom: 7,91Mo)
  * [Runkeeper](http://blog.runkeeper.com/new-feature/more-fitnessclass-classes-new-android-app) (plus de 3Mo)
  * Shazam