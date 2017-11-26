---
id: 1366
title: Neuftalk et SIP
date: 2010-05-24T21:16:19+00:00
author: Régis
excerpt: ou comment téléphoner (presque) gratuitement depuis son mobile
layout: post
guid: http://regis.decamps.info/blog/?p=1366
permalink: /2010/05/neuftalk-et-sip/
dsq_thread_id:
  - "189257906"
tmac_last_id:
  - ""
categories:
  - Mobile
  - Shopping
tags:
  - Adsl
  - Android
---
À quoi ça sert: à téléphoner depuis son mobile au même prix que depuis sa ligne fixe 🙂

## Prérequis

  * posséder un téléphone qui contient un client SIP; 
  * avoir une ligne ADSl dégroupée, chez Neuf, SFR ou d&rsquo;autres;
  * activer le SIP sur son compte ADSL;
  * être connecté à l&rsquo;internet au moment de l&rsquo;appel. 

## Explications du pourquoi du comment

Vous pouvez passer au paragraphe suivant si vous êtes pressé ou pas curieux&#8230;
  
<!--more-->


  
Avec les technologies de VoIP (_Voice over Internet Protocol_), quand on parle, la voix est transformée en paquets de données compressées (en quelque sorte, des MP3 d&rsquo;une seconde) qu&rsquo;une sont transférés sur l&rsquo;Internet (par IP, l&rsquo;_Internet Protocol_). L&rsquo;intérêt majeur le prix: une connexion Internet est économique, alors qu&rsquo;une ligne téléphonique coûte cher. Évidemment, quand c&rsquo;est moins cher, c&rsquo;est moins bien et la VoIP a des inconvénients: la qualité de la voix est souvent moins bonne, hachée ou saccadée, il peut y avoir des latences aussi. 

C&rsquo;est exactement ce que font aussi Skype ou Microsoft windows live messenger. C&rsquo;est aussi comme cela que fonctionne ma ligne « fixe » &#8212; c&rsquo;est d&rsquo;ailleurs pour cela que mon téléphone est raccordé au boitier ADSL, et non plus à la prise téléphonique, comme d&rsquo;antan avec France Télécom. Mais à la différence de Skype ou WLM, qui sont des protocoles propriétaires, mon boîtier utilise SIP (_Session Initiation Protocol_) qui et un protocol de VoIP ouvert.

L&rsquo;idée ici, c&rsquo;est d&rsquo;utiliser mon téléphone mobile, connecté à l&rsquo;Internet, pour établir une communication SIP, en utilisant mon opérateur ADSL. Résultat: cette communication est facturée par mon fournisseur d&rsquo;accès ADSL au prix d&rsquo;une communication depuis mon « fixe », plutôt que par mon opérateur mobile décomptée du forfait. Adieu les minutes à 30 centimes!

## Activer SIP chez son opérateur ADSL

Chez SFR/neuf, il faut d&rsquo;abord [s&rsquo;inscrire au service Neuftalk](http://neuftalk.sfr.fr/inscrire.html).
  
On reçoit alors un courrier contentant son identifiant SIP et son mot de passe.

Chez Free, c&rsquo;est informations sont directement accessibles dans son interface d&rsquo;administration.

Une fois le sésame reçu, on a accès à un fournisseur SIP.

## Avoir un téléphone SIP

Il faut maintenant un client SIP. Comme le protocole SIP est ouvert, il en existe plusieurs. Par exemple, on peut installer [Fring sur Android](http://www.fring.com/android/) et [Fring sur iPhone](http://itunes.apple.com/app/fring/id290948830). Certains téléphones intègrent directement cette capacité d&rsquo;appel SIP, comme le Nokia N95. 

Assez clairement, il faut un téléphone récent&#8230;

## Configurer son client SIP

Il suffit alors d&rsquo;entrer les identifiants SIP dans son client SIP. Voici comment faire avec Fring:
  
<img src="http://regis.decamps.info/blog/wp-content/uploads/2010/05/device0-233x350.png" alt="Menu > Addon" title="Fring" width="233" height="350" class="size-medium wp-image-1367" srcset="http://regis.decamps.info/blog/wp-content/uploads/2010/05/device0-233x350.png 233w, http://regis.decamps.info/blog/wp-content/uploads/2010/05/device0.png 320w" sizes="(max-width: 233px) 100vw, 233px" />
  
<figure id="attachment_1368" style="width: 233px" class="wp-caption alignnone"><img src="http://regis.decamps.info/blog/wp-content/uploads/2010/05/device1-233x350.png" alt="Selectionner SIP" title="Fring add-ons" width="233" height="350" class="size-medium wp-image-1368" srcset="http://regis.decamps.info/blog/wp-content/uploads/2010/05/device1-233x350.png 233w, http://regis.decamps.info/blog/wp-content/uploads/2010/05/device1.png 320w" sizes="(max-width: 233px) 100vw, 233px" /><figcaption class="wp-caption-text">Selectionner SIP</figcaption></figure>

Quelques subtilités:

  * avec Fring, il faut ajouter **@voip.wengo.fr** à l&rsquo;identifiant fourni
  * Avec NeufTalk (de SFR), le proxy SIP est inutile. Laisser vide ou indiquer **voip.wengo.fr**<figure id="attachment_1370" style="width: 233px" class="wp-caption alignnone">

<img src="http://regis.decamps.info/blog/wp-content/uploads/2010/05/device2-233x350.png" alt="Paramétrage du compte SIP" title="Fring SIP" width="233" height="350" class="size-medium wp-image-1370" srcset="http://regis.decamps.info/blog/wp-content/uploads/2010/05/device2-233x350.png 233w, http://regis.decamps.info/blog/wp-content/uploads/2010/05/device2.png 320w" sizes="(max-width: 233px) 100vw, 233px" /><figcaption class="wp-caption-text">Paramétrage du compte SIP avec @voip.wengo.fr</figcaption></figure> 

Maintenant, dans Fring, on peut appeler n&rsquo;importe quel numéro, sans consommer une seconde de forfait/hors-forfait:
  
<figure id="attachment_1369" style="width: 233px" class="wp-caption alignnone"><img src="http://regis.decamps.info/blog/wp-content/uploads/2010/05/device3-233x350.png" alt="Appel d&#039;un correspondant par SIP" title="Fring call" width="233" height="350" class="size-medium wp-image-1369" srcset="http://regis.decamps.info/blog/wp-content/uploads/2010/05/device3-233x350.png 233w, http://regis.decamps.info/blog/wp-content/uploads/2010/05/device3.png 320w" sizes="(max-width: 233px) 100vw, 233px" /><figcaption class="wp-caption-text">Appel d'un correspondant par SIP</figcaption></figure>