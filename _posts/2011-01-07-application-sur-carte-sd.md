---
id: 1596
disqus_id: 1596 http://regis.decamps.info/blog/?p=1596
title: Application sur carte SD
date: 2011-01-07T19:32:57+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=1596
permalink: /blog/2011/01/application-sur-carte-sd/

dsq_thread_id:
  - "648949368"
categories:
  - Hightech
tags:
  - Mobile
  - Android
---
S’il y a bien un point sur lequel l’iPhone OS dépasse Android, c’est la gestion de la mémoire pour les applications.

  * Sur iPhone, une application peut être installée tant qu’il y a de l’espace en mémoire (soit dans les 4Go ou plus de l’appareil).
  * Sur Android, une application ne peut être installée que dans l’espace mémoire réservé de la RAM du téléphone

Heureusement, Android 2.2 Froyo (API level 8) améliore les choses, en permettant de déplacer les applications sur carte SD. Oui mais

  * il en reste toujours un petit bout en RAM (la technique présente donc aucun intérêt pour les petites applications)
  * et surtout il faut que le développeur ait prévu le coup, c’est-à-dire ait [ajouté une ligne dans son fichier Manifest](http://developer.android.com/guide/appendix/install-location.html)

Et c’est ici que le bât blesse, car les développeurs de certaines grosses applications n’ont pas placé cette option. Certes, toutes [les applications ne devraient pas l’être](http://developer.android.com/guide/appendix/install-location.html#ShouldNot) mais, qu’est ce qui empêche

  * Google maps
  * [RATP Lite](http://www.ratp.fr/fr/ratp/r_26687/ratp-lite-pour-android-market/) (qui n’a de Lite que le nom: 7,91Mo)
  * [Runkeeper](http://blog.runkeeper.com/new-feature/more-fitnessclass-classes-new-android-app) (plus de 3Mo)
  * Shazam
