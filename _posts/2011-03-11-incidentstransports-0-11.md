---
id: 1811
title: IncidentsTransports-0.11
date: 2011-03-11T01:16:13+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=1811
permalink: /2011/03/incidentstransports-0-11/
wordbooker_options:
  - 'a:8:{s:18:"wordbook_noncename";s:10:"168782bf2d";s:18:"wordbook_page_post";s:4:"-100";s:18:"wordbook_orandpage";s:1:"2";s:23:"wordbook_default_author";s:1:"1";s:23:"wordbook_extract_length";s:3:"256";s:19:"wordbook_actionlink";s:3:"300";s:18:"wordbook_attribute";s:0:"";s:29:"wordbooker_status_update_text";s:33:"New blog post :  %title% - %link%";}'
tmac_last_id:
  - ""
dsq_thread_id:
  - ""
categories:
  - Mobile
  - Programmation
tags:
  - Talaria
---
J’ai apporté quelques petites modifications à IncidentsTransports pour Android.

### Crash de l’application quand l’orientation est changée

D’expérience, je sais que [les utilisateurs sont sans pitié quand une application crashe](https://market.android.com/details?id=info.decamps.droid.photoid). Et les bêta-testeurs m’ont justement remonté que ça arrivait sur mon appli, avec le message d’erreur _« Exception: Application has leaked window here »_. 

Je n’ai pas mis longtemps à comprendre d’où vient le problème. Lorsque je raffraîchis la liste des incidents, je crée une fenêtre <tt>ProgressDialog</tt> que je ferme quand le serveur a répondu. C’est d’ailleurs ce que recommande de faire le guide de développement sur [Using AsyncTask](http://developer.android.com/guide/topics/fundamentals/processes-and-threads.html#AsyncTask): 

> To update your UI, you should implement <tt>onPostExecute()</tt>, which delivers the result from <tt>doInBackground()</tt> and runs in the UI thread, so you can safely update your UI. 

Mais ces conseils ne sont pas si bons 🙁 Comme toute boîte de dialogue, celle-ci est rattachée à une vue, celle de l’activité. La boîte de dialogue est créée dans <tt>onPreExecute()</tt> (« _This step is normally used to setup the task, for instance by showing a progress bar in the user interface._) et fermée dans le <tt>onPostExecute()</tt>. Problème: si l’utilisateur modifie l’orientation de son écran, ou tout autre type de [changement de configuration](http://developer.android.com/reference/android/app/Activity.html#ConfigurationChanges), l’activité est détruite (« _This is done because any application resource, including layout files, can change based on any configuration value_« ). Du coup, la fermeture du <tt>ProgressDialog</tt> se fait dans un contexte qui n’existe plus.

Le message de l’exception ainsi levée laisse sous-entendre qu’il y a un me _memory leak_. J’ai commencé à regarder le code source de la [méthode <tt>dismiss()</tt>](http://www.google.com/codesearch/p?hl=fr#uX1GffpyOZk/core/java/android/app/Dialog.java&q=android%20dialog%20dismiss&l=264) des <tt>Dialog</tt> dans d’Android (j’aime les projets open-source), mais je ne suis pas sûr de cette implication.

Pour le moment, j’ai [changé la configuration de l’activité](https://bitbucket.org/regis/incidentstransports/issue/4/activity-has-leaked-window-phonewindow#comment-400129) pour qu’elle ne soit pas détruite sur un changement de configuration de l’appareil, mais il est sans doute possible de faire mieux.

### Messages d’erreur serveur plus détaillés

Quand le serveur ne répond pas <tt>HTTP OK</tt>, je me contentais d’afficher le code de statut, par exemple <tt>BAD REQUEST</tt>. Mais souvent, le serveur donne une explication plus détaillée dans le contenu de la réponse. Celle-ci est maintenant affichée.

### Correction bug mineur: Icône sur l’incident ajouté par l’utilisateur

Quand l’utilisateur crée un incident, j’avais affecté la ligne mais oublié l’identifiant de ligne, nécessaire pour l’affichage du pictogramme.

### Nouveau bug connnu: Impossible de voter pour l’incident créé

J’ai aussi découver [#7](https://bitbucket.org/regis/incidentstransports/issue/7/impossible-de-voter-pour-l-incident-cr) Impossible de confirmer/infirmer/indiquer terminé l’incident que l’on vient de créer.
  
Contournement: rafraîchir la liste des incidents, avant de tenter l’une de ces actions.
