---
id: 442
title: Envoi de fichiers sur mobile
date: 2007-07-21T14:55:00+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/2007/07/envoie-de-fichiers-sur-mobile/
permalink: /2007/07/envoi-de-fichiers-sur-mobile/
tmac_last_id:
  - ""
categories:
  - Brève
  - Linux
  - Mobile
---
Avant pour envoyer un fichier sur mon téléphone par mobile, je passais par le client obex de KDE. C&rsquo;était pas très bien intégré, mais ça marchait.

Maintenant, ils ont tout réécrit pour l&rsquo;incorporer dans kioslave. C&rsquo;est probablement une solution plus élégante, mais ça ne marche plus.

Du coup, je suis obligé d&rsquo;envoyer mes fichiers avec le client obexftp en ligne de commande&#8230; (d&rsquo;ailleurs je me suis fait [un petit wrapper](http://shellutils.googlecode.com/svn/trunk/send2bt.sh) pour ça).