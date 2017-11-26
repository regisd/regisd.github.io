---
id: 3091
title: Utiliser Lutece malgré le bug 34880
date: 2013-01-21T21:40:03+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=3091
permalink: /2013/01/utiliser-lutece-malgre-le-bug-34880/
al2fb_facebook_exclude:
  - "1"
dsq_thread_id:
  - "1039014812"
categories:
  - Général
---
Lutece utilise un composant technique avancé, qui vient s&rsquo;insérer dans « Comptes et Synchro ».
  
Malheureusement, Android Jelly Beans 4.1.1 (et aussi 4.1.2 semble-t-il) présente [le bug 34880](https://code.google.com/p/android/issues/detail?id=34880 "Android issue 34880")&nbsp;: les composants de synchronisation disparaissent à chaque redémarrage pour les applications payantes installées depuis Google Play.
  
<!--more-->


  
Le contournement que je propose est le suivant.

### Activer l&rsquo;option _Sources inconnues_

Si ce n&rsquo;est pas déjà fait, cette option se trouve dans `Paramètres système > Sécurité > Sources inconnues`.
  


<div id='gallery-16' class='gallery galleryid-3091 gallery-columns-1 gallery-size-thumbnail'>
  <figure class='gallery-item'> 
  
  <div class='gallery-icon portrait'>
    <a href='http://regis.decamps.info/blog/2013/01/utiliser-lutece-malgre-le-bug-34880/device-2013-01-21-213457/'><img width="150" height="150" src="http://regis.decamps.info/blog/wp-content/uploads/2013/01/device-2013-01-21-213457-150x150.png" class="attachment-thumbnail size-thumbnail" alt="" /></a>
  </div></figure><figure class='gallery-item'> 
  
  <div class='gallery-icon portrait'>
    <a href='http://regis.decamps.info/blog/2013/01/utiliser-lutece-malgre-le-bug-34880/device-2013-01-21-213533/'><img width="150" height="150" src="http://regis.decamps.info/blog/wp-content/uploads/2013/01/device-2013-01-21-213533-150x150.png" class="attachment-thumbnail size-thumbnail" alt="" /></a>
  </div></figure><figure class='gallery-item'> 
  
  <div class='gallery-icon portrait'>
    <a href='http://regis.decamps.info/blog/2013/01/utiliser-lutece-malgre-le-bug-34880/device-2013-01-21-213608/'><img width="150" height="150" src="http://regis.decamps.info/blog/wp-content/uploads/2013/01/device-2013-01-21-213608-150x150.png" class="attachment-thumbnail size-thumbnail" alt="" /></a>
  </div></figure><figure class='gallery-item'> 
  
  <div class='gallery-icon portrait'>
    <a href='http://regis.decamps.info/blog/2013/01/utiliser-lutece-malgre-le-bug-34880/device-2013-01-21-213623/'><img width="150" height="150" src="http://regis.decamps.info/blog/wp-content/uploads/2013/01/device-2013-01-21-213623-150x150.png" class="attachment-thumbnail size-thumbnail" alt="" /></a>
  </div></figure>
</div>

### Télécharger Lutece

[Télécharger Lutece](https://www.dropbox.com/s/7m5r8atq70158bh/Lutece.apk "Télécharger Lutece depuis Dropbox") **en dehors de Google Play**.
  
**NB** Lutece reste une application payante; la présence d&rsquo;une license sera vérifiée.
  


<div id='gallery-17' class='gallery galleryid-3091 gallery-columns-3 gallery-size-thumbnail'>
  <figure class='gallery-item'> 
  
  <div class='gallery-icon portrait'>
    <a href='http://regis.decamps.info/blog/2013/01/utiliser-lutece-malgre-le-bug-34880/device-2013-01-21-220050/'><img width="150" height="150" src="http://regis.decamps.info/blog/wp-content/uploads/2013/01/device-2013-01-21-220050-150x150.png" class="attachment-thumbnail size-thumbnail" alt="" /></a>
  </div></figure>
</div>

### Installer

Une notification apparaît pour indiquer que le téléchargement est en cours.
  
Quand le télécharement est terminé, ouvrir la notification et accepter de **Mettre à jour**.
  


<div id='gallery-18' class='gallery galleryid-3091 gallery-columns-1 gallery-size-thumbnail'>
  <figure class='gallery-item'> 
  
  <div class='gallery-icon portrait'>
    <a href='http://regis.decamps.info/blog/2013/01/utiliser-lutece-malgre-le-bug-34880/device-2013-01-21-220628/'><img width="150" height="150" src="http://regis.decamps.info/blog/wp-content/uploads/2013/01/device-2013-01-21-220628-150x150.png" class="attachment-thumbnail size-thumbnail" alt="" /></a>
  </div></figure><figure class='gallery-item'> 
  
  <div class='gallery-icon portrait'>
    <a href='http://regis.decamps.info/blog/2013/01/utiliser-lutece-malgre-le-bug-34880/device-2013-01-21-220712/'><img width="150" height="150" src="http://regis.decamps.info/blog/wp-content/uploads/2013/01/device-2013-01-21-220712-150x150.png" class="attachment-thumbnail size-thumbnail" alt="" /></a>
  </div></figure>
</div>