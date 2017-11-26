---
id: 1476
title: Utiliser firefox en intranet
date: 2010-11-02T13:40:05+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=1476
permalink: /2010/11/utiliser-firefox-en-intranet/
tmac_last_id:
  - ""
dsq_thread_id:
  - "561311837"
categories:
  - Informatique
tags:
  - Firefox
  - Microsoft
---
La plupart des intranets « tout Microsoft » utilisent [NTLM](http://fr.wikipedia.org/wiki/NT_Lan_Manager) pour authentifier les utilisateurs sur les sites.

Si Firefox supporte bien le NTLM, par défaut, il faut saisir son mot de passe à chaque visite. C’est parce que Firefox ne fait pas confiance au site qui demande le jeton NTLM. Pour que Firefox ait confiance, il suffit d’ajouter le site dans [network.automatic-ntlm-auth.trusted-uris](http://kb.mozillazine.org/Network.automatic-ntlm-auth.trusted-uris)

Pour cela, visiter la page « about:config », accepter l’avertissement.

Chercher « ntlm » pour trouver le paramètre **network.automatic-ntlm-auth.trusted-uris**. Indiquer ici les sites visités, séparés par des virgules.
