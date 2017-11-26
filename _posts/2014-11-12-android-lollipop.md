---
id: 3230
disqus_id: 3230 http://regis.decamps.info/blog/?p=3230
title: Quoi de neuf dans Android Lollipop?
date: 2014-11-12T23:33:50+00:00
author: Régis
excerpt: |
  Ce qui distingue <a href="http://www.android.com/versions/lollipop-5-0/">Lollipop</a>, c'est d'abord sa nouvelle interface graphique. Avec des animations discrètes, l'interface paraît très fluide. Les notifications et le gestionnaire de tâche ont aussi été repensés. Et sous le capot, il y a des changements. Mais je ne pense pas que cette version soit la plus marquante.
layout: post
guid: http://regis.decamps.info/blog/?p=3230
permalink: /blog/2014/11/android-lollipop/
dsq_thread_id:
  - "3150546482"
categories:
  - Informatique
tags:
  - Android
  - Lollipop
  - WebView
---
Ce qui distingue [Lollipop](http://www.android.com/versions/lollipop-5-0/), c’est d’abord sa nouvelle interface graphique. Avec des animations discrètes, l’interface paraît très naturelle et fluide.

<!--more-->

## Notifications

La première chose que vous allez sans doute découvrir sont les notifications sur l’écran de verrouillage. Comme sur iOS, cela permet de jeter un œil sans avoir à déverrouiller l’écran.

Les notifications sont bien bien sûr protégées par différents niveaux de confidentialité.

En attendant que toutes les [applications implémentent ces niveaux de sécurité](https://developer.android.com/reference/android/app/Notification.Builder.html#setVisibility(int)), les notifications sont affichées sans leur contenu sur l’écran de vérouillage. C’est pourquoi je vous recommande de les afficher par défaut, sauf pour les applications choisies manuellement:

  * **Paramètres** > **Sons et notifications**<li 
**>Si l’appareil est verrouillé : **Afficher l’intégralité du contenu des notifications**</li> 

  * **Notifications de l’application** : « **Sensible** » pour les applications qui pourraient afficher des informations sensibles — par exemple Gmail.</ul> 

À l’usage, c’est une très nette amélioration de l’écran de verrouillage de KitKat, en particulier vis-à-vis de la musique, que je peux maintenant mettre en pause et reprendre en toute fluidité.

## Le gestionnaire de tâches peut plusieurs fois la même application

Le gestionnaire de tâches vient avec un modèle dit « document ». Cela signifie qu’une application peut apparaître plusieurs fois dans le gestionnaire de tâches  une fois pour chaque document ouvert.<figure id="attachment_3232" style="width: 196px" class="wp-caption alignright">

[<img src="http://regis.decamps.info/blog/wp-content/uploads/2014/10/screenshot-task_manager-196x350.png" alt="Gmail apparaît deux fois: une fois pour la boîte de réception; une fois pour la fenêtre de composition." width="196" height="350" class="size-medium wp-image-3232" srcset="http://regis.decamps.info/blog/wp-content/uploads/2014/10/screenshot-task_manager-196x350.png 196w, http://regis.decamps.info/blog/wp-content/uploads/2014/10/screenshot-task_manager-168x300.png 168w" sizes="(max-width: 196px) 100vw, 196px" />](http://regis.decamps.info/blog/wp-content/uploads/2014/10/screenshot-task_manager.png)<figcaption class="wp-caption-text">Gmail appraît deux fois: une fois pour la boîte de réception; une fois pour la fenêtre de composition.</figcaption></figure> 

Je n’aime pas du tout ce changement. Chrome pollue ma liste de tâches, car chaque onglet ouvre dans Chrome y est listé. Edit: dans ce cas spécifique, un paramétrage permet de revenir à une seule tâche pour Chrome.

## Des changements plus techniques

### Un peu plus rapide par défaut

Depuis ses débuts, Android utilisait Dalvik comme machine virtuelle. KitKat a introduit un nouveau moteur d’exécution, ART (Android Runtime) qui était une option à activer explicitement. Sous Lollipop, ART est le seul moteur disponible.

### Une meilleure expérience web

À partir de maintenant, la <tt>WebView</tt> est fournie par Chrome et non plus par le framework. Cela signifie que les mises à jour seront plus fréquentes.

### Nouveau lecteur multimédia

Le lecteur <tt>NuPlayer</tt> qui propulse autant les vidéos dans Chrome que dans Youtube, ou n’importe quelle autre application a été ré-écrit.

## Conclusion

Je ne pense pas que cette version soit aussi importante que les précédentes Cupcake (2009) apportait le support des widgets et claviers alternatifs ; Eclair (2009) a facilité la synchronisation avec « comptes et synchronisation » ; Ice-Cream Sandwich (2011) unifiait les applications pour tablettes et téléphones ; Jelly bean (2012) promettait d’être plus rapide et gérait les langues droite-à-gauche. Ceci dit, maintenant que j’ai goûté à Lollipop, j’aime son goût, et je ne reviendrai pas à Kitkat.
