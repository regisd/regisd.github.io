---
id: 2843
disqus_id: 2843 http://regis.decamps.info/blog/?p=2843
title: Neuftalk est devenu SFR Libertalk
date: 2012-07-26T22:11:50+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=2843
permalink: /2012/07/neuftalk-est-devenu-sfr-libertalk/
al2fb_facebook_link_id:
  - 1065233209_3800060394441
al2fb_facebook_link_time:
  - 2012-07-26T20:11:55+00:00
al2fb_facebook_link_picture:
  - post=http://regis.decamps.info/blog/wp-content/uploads/2012/07/img.png
dsq_thread_id:
  - "781192048"
categories:
  - Applications
  - Mobile
tags:
  - Android
  - VoIP
---
Assez discrètement, SFR a fermé Neuf talk pour le remplacer par [SFR Libertalk](http://www.sfr.fr/adsl-fibre/services-options/appels-repondeurs-fixes/sfr-libertalk/).

Mais, pour une fois, il ne s’agit pas que d’une changement marketing ne concernant que le nom. L’infrastructure technique change: [ma recommandation d’utiliser Fring](http://regis.decamps.info/blog/2010/05/neuftalk-et-sip/) n’est plus d’actualité…;

À la place, vous pouvez utiliser [un autre client SIP](http://regis.decamps.info/blog/2012/02/android-et-voip/ "Liste des clients SIP").
  
Et aujourd’hui, je recommande CSipSimple. Voici un tutoriel pour mettre en œuvre SFR Libertalk sur CSipSimple.

<!--more-->

### Configuration avec l’assistant

C’est un [autre Régis qui développe CSipSimple](https://play.google.com/store/apps/developer?id=Regis+Montoya "Régis Montoya développe CSipSimple"), et il est très réactif. La version « trunk » de son application a déjà un assistant pour Libertalk (voir le [ticket 1837](https://code.google.com/p/csipsimple/issues/detail?id=1837 "issue 1837 CSipSimple") du projet)

Si ce n’est pas déjà fait, [autorisez votre téléphone à installer des « sources inconnues »](http://droidsp.blogspot.fr/2012/04/comment-autoriser-les-sources-inconnues.html) (c’est à dire, en dehors de Google play).

Téléchargez et installez la version beta 4.0 r1736.
  
[<img src="http://regis.decamps.info/blog/wp-content/uploads/2012/07/img.png" alt="Aller à http://nightlies.csipsimple.com/trunk/CSipSimple-r1736-trunk.apk" title="CsipSimple-4.0-1736.apk" width="344" height="344" class="alignnone size-full wp-image-2844" srcset="http://regis.decamps.info/blog/wp-content/uploads/2012/07/img.png 344w, http://regis.decamps.info/blog/wp-content/uploads/2012/07/img-150x150.png 150w, http://regis.decamps.info/blog/wp-content/uploads/2012/07/img-100x100.png 100w" sizes="(max-width: 344px) 100vw, 344px" />](http://nightlies.csipsimple.com/trunk/CSipSimple-r1736-trunk.apk)

Il suffit ensuite de faire « Ajouter un compte », type Libertalk et saisir vos numéro de téléphone (fixe) et mot de passe.

### Configuration avancée de CSipSimple

Si vous préférez rester avec la version « production » actuellement sur <strike>l’Android market</strike> [Google play](https://play.google.com/store/apps/details?id=com.csipsimple "CSipSimple sur Google play"), vous pouvez obtenir le même résultat avec un compte « expert ».

À partir des commentaires laissés [sur l’atelier SFR](http://atelier.sfr.fr/beta-tests/sfr-libertalk-emportez-avec-vous-votre-ligne-fixe), j’ai fini par trouver une configuration fonctionnelle. Les champs en vert sont ceux à modifier (plus détails en cliquant sur chaque écran).<figure id="attachment_2847" style="width: 210px" class="wp-caption alignnone">

<a href="http://regis.decamps.info/blog/2012/07/neuftalk-est-devenu-sfr-libertalk/device-2012-07-26-214013/" rel="attachment wp-att-2847"><img src="http://regis.decamps.info/blog/wp-content/uploads/2012/07/device-2012-07-26-214013-210x350.png" alt="Capture d&#039;écran" title="device-2012-07-26-214013" width="210" height="350" class="size-medium wp-image-2847" srcset="http://regis.decamps.info/blog/wp-content/uploads/2012/07/device-2012-07-26-214013-210x350.png 210w, http://regis.decamps.info/blog/wp-content/uploads/2012/07/device-2012-07-26-214013.png 480w" sizes="(max-width: 210px) 100vw, 210px" /></a><figcaption class="wp-caption-text">Compte expert</figcaption></figure> <figure id="attachment_2851" style="width: 210px" class="wp-caption alignnone"><a href="http://regis.decamps.info/blog/2012/07/neuftalk-est-devenu-sfr-libertalk/device-2012-07-26-214042-2/" rel="attachment wp-att-2851"><img src="http://regis.decamps.info/blog/wp-content/uploads/2012/07/device-2012-07-26-2140421-210x350.png" alt="Capture d&#039;écran" title="device-2012-07-26-214042" width="210" height="350" class="size-medium wp-image-2851" srcset="http://regis.decamps.info/blog/wp-content/uploads/2012/07/device-2012-07-26-2140421-210x350.png 210w, http://regis.decamps.info/blog/wp-content/uploads/2012/07/device-2012-07-26-2140421.png 480w" sizes="(max-width: 210px) 100vw, 210px" /></a><figcaption class="wp-caption-text">Identifiant du compte</figcaption></figure> <figure id="attachment_2852" style="width: 210px" class="wp-caption alignnone"><a href="http://regis.decamps.info/blog/2012/07/neuftalk-est-devenu-sfr-libertalk/device-2012-07-26-214106-2/" rel="attachment wp-att-2852"><img src="http://regis.decamps.info/blog/wp-content/uploads/2012/07/device-2012-07-26-2141061-210x350.png" alt="" title="device-2012-07-26-214106" width="210" height="350" class="size-medium wp-image-2852" srcset="http://regis.decamps.info/blog/wp-content/uploads/2012/07/device-2012-07-26-2141061-210x350.png 210w, http://regis.decamps.info/blog/wp-content/uploads/2012/07/device-2012-07-26-2141061.png 480w" sizes="(max-width: 210px) 100vw, 210px" /></a><figcaption class="wp-caption-text">Transport et timeout</figcaption></figure> <figure id="attachment_2854" style="width: 210px" class="wp-caption alignnone"><a href="http://regis.decamps.info/blog/2012/07/neuftalk-est-devenu-sfr-libertalk/device-2012-07-26-220617/" rel="attachment wp-att-2854"><img src="http://regis.decamps.info/blog/wp-content/uploads/2012/07/device-2012-07-26-220617-210x350.png" alt="Capture d&#039;écran" title="device-2012-07-26-220617" width="210" height="350" class="size-medium wp-image-2854" srcset="http://regis.decamps.info/blog/wp-content/uploads/2012/07/device-2012-07-26-220617-210x350.png 210w, http://regis.decamps.info/blog/wp-content/uploads/2012/07/device-2012-07-26-220617.png 480w" sizes="(max-width: 210px) 100vw, 210px" /></a><figcaption class="wp-caption-text">Proxy</figcaption></figure>
