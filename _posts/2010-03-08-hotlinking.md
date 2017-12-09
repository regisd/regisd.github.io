---
id: 1156
disqus_id: 1156 http://regis.decamps.info/blog/?p=1156
title: hotlinking
date: 2010-03-08T00:30:40+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=1156
permalink: /blog/2010/03/hotlinking/

dsq_thread_id:
  - "189257871"
categories:
  - Programmation
tags:
  - HTML
---
Depuis quelques jours, mon site est vicitime d’_image hotlinking_. Résultat: depuis le début du mois, j’ai consommé plus de 35Go de bande passante, et OVH, mon hébergeur, m’envoie des emails pour me prévenir que mon blog risque d’être suspendu :-/

En effet, pour illustrer ma critique sur les [homos préfèrent les blondes](http://regis.decamps.info/blog/2008/04/les-homos-preferent-les-blondes/), j’ai placé en image l’affiche de la pièce.

Sauf que <a href="http://www.wawacity.eu/96624-Les-homos-preferent-les-blondes-Megaupload.html" rel="nofollow" >www.wawacity.eu</a> a réutilisé cette même image, en faisant un lien direct sur mon domaine:

    
    <img src="/blog/wp-content/uploads/2008/04/les-homos-preferent-les-blondes.jpg" />
    

Résultat: chaque visiteur de ce site charge l’image sur mon site. J’ai en moyenne 50 visites par jour sur l’ensemble du site ; mais le site qui « pompe » l’image est un site de piratage qui a engendré 120 000 requêtes par jour pour cette image!

Première parade rapide: j’ai renommé mon image pour _casser_ le lien.

Mais j’écris cet article pour parler de ma solution: je viens d’ajouter une règle Apache pour interdire la lecture de ressources si le navigateur indique une provenance extérieure.

J’ai donc déposé dans mon répertoire contenant les médias la configuration <tt>.htaccess</tt> suivante:

    
    # Prevent Files image hotlinking and bandwidth stealing
    RewriteEngine On
    RewriteBase /blog/wp-content/uploads/
    #RewriteCond %{HTTP_REFERER} !^$
    RewriteCond %{HTTP_REFERER} !^http://regis.decamps.info/.*$ [NC]
    RewriteRule \.(gif|jpg|jpeg|swf|flv|png)$ / [F,L]
