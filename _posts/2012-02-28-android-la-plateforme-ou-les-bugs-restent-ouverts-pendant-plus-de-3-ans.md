---
id: 2608
title: Android, la plateforme où les bugs restent ouverts pendant plus de 3 ans
date: 2012-02-28T21:42:45+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=2608
permalink: /2012/02/android-la-plateforme-ou-les-bugs-restent-ouverts-pendant-plus-de-3-ans/
dsq_thread_id:
  - "592687832"
categories:
  - Programmation
tags:
  - Android
  - Bug
---
Je continue ma série sur les [bugs d’Android](http://regis.decamps.info/blog/tag/android+bug/), cette fois pour dire que ça m’agace de voir un bug trivial non corrigé pendant plus de 3 ans.
  
<!--more-->


  
Le problème, c’est que si l’on a une WebView, et que l’on fait
  
[code]
  
webView.loadData(« Régis », »utf-8&Prime;);
  
[/code]

Voilà ce qui apparaît:
  
<img src="http://regis.decamps.info/blog/wp-content/uploads/2012/02/Capture-d’écran-2012-02-28-à-21.38.37-150x93.png" alt="webView avec du contenu chargé par loadData" width="150" height="93" />

Pourquoi dis-je que la correction est triviale? Parce que ça fonctionne:
  
[code]
  
webView.loadDataWithBaseURL(null, « Régis », « text/html », « utf-8 », null);
  
[/code]

Et ça m’énerve, parce que [ça fait plus de 3 ans que ça traîne](http://code.google.com/p/android/issues/detail?id=1958 "Android issue 1958")!
