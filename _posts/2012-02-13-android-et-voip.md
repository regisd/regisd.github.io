---
id: 2556
disqus_id: 2556 http://regis.decamps.info/blog/?p=2556
title: Android et VoIP
date: 2012-02-13T23:10:48+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=2556
permalink: /blog/2012/02/android-et-voip/
dsq_thread_id:
  - "575000441"
categories:
  - High-tech
tags:
  - Application
  - Mobile
  - Android
  - VoIP
---
J’actualise un ancien article sur l’[utilisation de NeufTalk avec Fring sur un téléphone Android](http://regis.decamps.info/blog/2010/05/neuftalk-et-sip/). 

Ici, je vais essayer de refaire un panorama des logiciels disponibles.

<!--more-->

### CSipSimple

**Rating:** <i class="material-icons">star</i><i class="material-icons">star</i><i class="material-icons">star</i><i class="material-icons">star</i><i class="material-icons">star</i> 

[<img src="/blog/wp-content/uploads/2012/02/csipsimple.png" alt="Lien vers Android market" title="csipsimple" width="124" height="124" class="alignleft size-full wp-image-2575" />](https://market.android.com/details?id=com.csipsimple)

Ça démarre très bien. Dans tous les clients que j’ai testé ce soir, c’est le seul qui offre une assistance pour la configuration de NeufTalk ou Freephonie ou OVH. Il y a une indication claire pour savoir s’il faut suffixer ou non le login avec le serveur. Avec un mauvais mot de passe, on a un retour immédiat: « Forbidden » (en rouge).

Par ailleurs, l’interface est réussie, et l’intégration au téléphone est très bien faite.

<strike>Malheureusement, tout s’écroule quand je passe un appel: l’autre téléphone ne sonne même pas, alors que CSipSimple affiche une durée de communication croissante…;</strike> Edit: après un nouveau test, tout fonctionne très bien

En plus, le projet est open-source [sur Google code](http://code.google.com/p/csipsimple/ "CSipSimple sur Google code").

### Fring

**Rating:** <i class="material-icons">star</i><i class="material-icons">star</i><i class="material-icons">star</i><i class="material-icons">star</i><i class="material-icons">star_border</i> 


  
[<img src="/blog/wp-content/uploads/2012/02/fring.png" alt="Lien vers Android market" title="fring" width="124" height="124" class="alignleft size-full wp-image-2557" />](https://market.android.com/details?id=com.fring)
  
Il faut créer un énième compte pour Fring, et ils ont ajouté un bandeau publicitaire qui n’existait pas il y a 2 ans. Comme avant, fring essaye de vendre son propre service de VoIP, mais ça ne me choque pas.

L’interface est belle, il y a une bonne intégration avec le téléphone et ça fonctionne 🙂

En plus de faire de la VoIP, Fring fait de la messagerie instantanée via Microsoft™ Messenger®, Google Talk™ et AIM®. La vidéo fonctionne aussi avec d’autres utilisateurs de Fring (mais je n’ai pas testé).

<br style="clear: both;" />

### Nimbuzz

**Rating:** <i class="material-icons">star</i><i class="material-icons">star</i><i class="material-icons">star</i><i class="material-icons">star_border</i><i class="material-icons">star_border</i> 


  
[<img src="/blog/wp-content/uploads/2012/02/nimbuzz.png" alt="Lien vers Android market" title="nimbuzz" width="78" height="78" class="alignleft size-full wp-image-2574" />](https://market.android.com/details?id=com.nimbuzz)
  
Nimbuzz demande également la création d’un compte interne. Ils mettent en avance son propre service de VoIP. Pour en utiliser un autre (tel que Neuftalk ou Freemobile ou autre), il faut aller dans Préférences > Paramètres de l’Appel > Autre compte.

Pour la configuration, on n’a pas le droit à l’erreur, sinon, il faut supprimer le compte et tout recommencer…;

L’intégration des contacts n’a pas l’air de fonctionner chez moi.

Et le service de test présente un net écho. Bref, je ne suis pas convaincu.

Nimbuzz fait également de la messagerie instantanée, mais je n’ai pas re-testé cette partie. Je me souviens que l’an dernier, il était impossible de fusionner un contact présent sur plusieurs réseaux.

<br style="clear: both;" />

### Linphone

**Rating:** <i class="material-icons">star</i><i class="material-icons">star</i><i class="material-icons">star_border</i><i class="material-icons">star_border</i><i class="material-icons">star_border</i> 


  
[<img src="/blog/wp-content/uploads/2012/02/linphone.png" alt="Lien vers Android market" title="linphone" width="124" height="124" class="alignleft size-full wp-image-2564" />](https://market.android.com/details?id=org.linphone)

La qualité sonore est vraiment mauvaise avec Neuf.

Dans les astuces, pensez à configurer « +33 » comme préfixe, sinon vous allez immanquablement tombé sur « vous ne pouvez pas appeler ce numéro ».

Il y a une bonne intégration avec le carnet d’adresses.

<br style="clear: both;" />

### Mizudroid

**Rating:** <i class="material-icons">star</i><i class="material-icons">star_border</i><i class="material-icons">star_border</i><i class="material-icons">star_border</i><i class="material-icons">star_border</i> 


  
[<img src="/blog/wp-content/uploads/2012/02/mizudroid.png" alt="Lien vers Android market" title="mizudroid" width="124" height="124" class="alignleft size-full wp-image-2558" />](https://market.android.com/details?id=com.mizuvoip.mizudroid.GUI)
  
Le panneau de configuration fait peur, mais en réalité seuls les 3 premiers champs sont utiles.

La subtilité, c’est qu’il faut aller tout en bas pour appuyer sur « Save settings ». Dans une application Android bien faite, il aurait suffit d’appuyer sur le bouton « retour »…;

Avec un mauvais mot de passe, le logiciel bloque sur « registering », et ensuite impossible de quitter l’activité. J’ai été obligé de forcer la fermeture de l’application.

L’intégration avec les contacts est assez mal faite: j’ai le dernier contact appelé en multiples exemplaires en haut, il n’y a pas les photos de mes contacts.

Enfin, et surtout la qualité sonore ne me paraît pas des meilleures.

<br style="clear: both;" />

### SIPDroid

**Rating:** <i class="material-icons">star</i><i class="material-icons">star_border</i><i class="material-icons">star_border</i><i class="material-icons">star_border</i><i class="material-icons">star_border</i> 


  
[<img src="/blog/wp-content/uploads/2012/02/sipdroid.jpg" alt="Lien vers Android market" title="sipdroid" width="124" height="124" class="alignleft size-full wp-image-2570" />](https://market.android.com/details?id=org.sipdroid.sipua)
  
De gros problèmes dans l’enchaînement des activités: Après avoir configuré un compte et passé un appel, la seule activité qui voulait bien s’afficher est celle de paramétrage des comptes.

C’est aussi une des rares applications qui ne présente pas de bouton « Raccroché » lors d’un appel!

<br style="clear: both;" />

### Tiviphone

**Rating:** <i class="material-icons">star_border</i><i class="material-icons">star_border</i><i class="material-icons">star_border</i><i class="material-icons">star_border</i><i class="material-icons">star_border</i> 


  
[<img src="/blog/wp-content/uploads/2012/02/tivi.png" alt="Lien vers Android market" title="tivi" width="124" height="124" class="alignleft size-full wp-image-2572" />](https://market.android.com/details?id=com.tivi.tiviphone)
  
Cette application utilise plusieurs Toast pour indique la progression de la connexion. Ça fait un peu bidouille, mais au moins, on voit ce qui se passe. Sauf que dans tous les cas, j’ai une erreur « Not found »…;

Les développeurs ont apparemment oublié de placer un clavier pour numéroter les numéros. On peut le saisir dans une _textbox_ qui ouvre le clavier azerty standard…;

<br style="clear: both;" />

### 3CXPhone

**Rating:** <i class="material-icons">star_border</i><i class="material-icons">star_border</i><i class="material-icons">star_border</i><i class="material-icons">star_border</i><i class="material-icons">star_border</i> 


  
[<img src="/blog/wp-content/uploads/2012/02/3cx.jpg" alt="Lien vers Android market" title="3cx" width="124" height="124" class="alignleft size-full wp-image-2566" />](https://market.android.com/details?id=com.tcx.sip.ui)

La configuration est complexe, on s’y perd entre « name », « display name », « user » et « id » (oui, tout ça pour le même compte). Au final, je n’ai pas réussi à me connecter…; L’erreur est un vague « Not registered ».

<br style="clear: both;" />

### AGEphone

**Rating:** <i class="material-icons">star_border</i><i class="material-icons">star_border</i><i class="material-icons">star_border</i><i class="material-icons">star_border</i><i class="material-icons">star_border</i> 


  
[<img src="/blog/wp-content/uploads/2012/02/agephone.png" alt="Lien vers Android market" title="agephone" width="124" height="124" class="alignleft size-full wp-image-2565" />](https://market.android.com/details?id=com.ageet.AGEphone)
  
L’interface ne suit pas les recommandations Android. 

En cas de mauvais mot de passe, l’erreur est un vague « Not ready ». Avec un bon mot de passe, je compose un numéro et n’entend rien.

<br style="clear: both;" />

### ecocaller

**Rating:** <i class="material-icons">star_border</i><i class="material-icons">star_border</i><i class="material-icons">star_border</i><i class="material-icons">star_border</i><i class="material-icons">star_border</i> 


  
[<img src="/blog/wp-content/uploads/2012/02/ecocaller.png" alt="Lien vers Android market" title="ecocaller" width="124" height="124" class="alignleft size-full wp-image-2569" />](https://market.android.com/details?id=cz.acrobits.softphone.ecocaller)
  
À la différence de leur copie d’écran, je n’ai pas de bouton « call » sur le clavier…; Je ne peux donc qu’appeler des contacts, et ça ne fonctionne pas.
  
Il y a un « SIP log » qui aurait pu être utile, mais qui reste vide, alors que j’ai entré les paramètres de mon compte…;

<br style="clear: both;" />

### Ne sont même pas des clients SIP

Inutile de les installer, ce ne sont même pas des clients SIP. Ils foncitonnent sur leur propre réseau, propriétaire.

  * Skype, qui est tout de même le leader de la VoIP.
  * Google talk, qui est en très forte progression, avec Google+ hangout et l’explosition du nombre de terminaux sous Android
  * Tango
  * Viber

<br style="clear: both;" />

### Autres clients

Je pense avoir testé les principaux logiciels disponibles pour Android. Si jamais j’en ai oublié un, n’hésitez pas à laisser un commentaire. De même si vous avez obtenu un résultat positif avec ceux sur lesquels je me suis cassé les dents.
