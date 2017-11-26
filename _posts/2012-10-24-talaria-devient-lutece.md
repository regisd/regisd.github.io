---
id: 2994
title: Talaria est morte. Vive Lutece!
date: 2012-10-24T08:04:59+00:00
author: Régis
excerpt: Si vous êtes frustré par les "erreurs réseau" de Talaria, téléchargez vite Lutece qui règle définitivement ces problèmes.
layout: post
guid: http://regis.decamps.info/blog/?p=2994
permalink: /2012/10/talaria-devient-lutece/
al2fb_facebook_link_id:
  - 1065233209_4158921805752
al2fb_facebook_link_time:
  - 2012-10-24T09:30:18+00:00
al2fb_facebook_link_picture:
  - post=http://regis.decamps.info/blog/?al2fb_image=1
dsq_thread_id:
  - "897891400"
categories:
  - Applications
  - Général
  - Programmation
tags:
  - Talaria
---
Après 18 mois d’existence et plus de 13 000 téléchargements, il est temps pour Talaria de faire face aux aléas des connexions réseau. Les déconnexions sont fréquentes sur mobile, et particulièrement dans le métro!

J’ai opté pour une réécriture complète, en me basant sur le mécanisme des « Comptes et Synchro ». Et je vous invite donc à [installer Lutece](https://play.google.com/store/apps/details?id=info.decamps.droid.lutece "Lutece sur Google Play").

<!--more-->


  
Lutece reprend les principales fonctionnalités de Talaria (liste des incidents, notifications, partage), mais cette nouvelle application est basée sur `SyncAdapter` (« Comptes et Synchro »). C’est le système qui gère maintenant la synchronisation:

  * la liste des incidents n’est synchronisée que si le réseau est disponible
  * la synchronisation est suspendue quand le paramètre global « Comptes et synchronisation » est sur « OFF ».
  * en cas de déconnexion, le système réessaye plus tard
  * de plus Lutece, limite la synchronisation à certaines plages horaires
  * grace à une base de données dans le mobile, la liste des incidents est toujours accessible

Concernant Talaria, je ferai prochainement une dernière mise à jour, visant à masquer les messages d’erreur liés aux déconnexion réseau.
