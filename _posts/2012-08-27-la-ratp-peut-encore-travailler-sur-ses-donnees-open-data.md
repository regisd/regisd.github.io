---
id: 2881
disqus_id: 2881 http://regis.decamps.info/blog/?p=2881
title: La RATP peut encore travailler sur ses données Open Data
date: 2012-08-27T20:52:47+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=2881
permalink: /2012/08/la-ratp-peut-encore-travailler-sur-ses-donnees-open-data/
al2fb_facebook_link_id:
  - 1065233209_3920348121559
al2fb_facebook_link_time:
  - 2012-08-27T18:52:54+00:00
al2fb_facebook_link_picture:
  - post=/blog/wp-content/uploads/2012/08/metro_fail-350x222.png
dsq_thread_id:
  - "820689756"
categories:
  - Actualités
  - Général
  - Informatique
tags:
  - Libre
  - Métro
  - Open Data
  - Paris
---
Comme beaucoup, je me suis réjouis de voir que la [RATP rejoignait enfin le mouvement Open Data](http://www.ratp.fr/fr/ratp/r_70350/open-data/). Mais j’ai vite déchanté en voyant la faible qualité de celles-ci…;
  
<!--more-->


  
[<img src="/blog/wp-content/uploads/2012/08/metro_fail-350x222.png" alt="" title="L&#039;échec de la RATP pour libérer des données" width="350" height="222" class="alignright size-medium wp-image-2886" srcset="/blog/wp-content/uploads/2012/08/metro_fail-350x222.png 350w, /blog/wp-content/uploads/2012/08/metro_fail-471x300.png 471w, /blog/wp-content/uploads/2012/08/metro_fail.png 716w" sizes="(max-width: 350px) 100vw, 350px" />](/blog/wp-content/uploads/2012/08/metro_fail.png)
  
D’abord, parlons de ce qu’il y a:

  * la liste des [« positions géographiques des stations »](http://www.data.gouv.fr/donnees/view/Positions-g%C3%A9ographiques-des-stations-du-r%C3%A9seau-ferr%C3%A9-RATP-564122?xtmc=R%C3%A9gie%20autonome%20des%20transports%20parisiens%20%28RATP%29&xtcr=4?xtmc=R%C3%A9gie%20autonome%20des%20transports%20parisiens%20%28RATP%29&xtcr=4)
  * la liste des [« correspondances »](http://www.data.gouv.fr/donnees/view/Correspondances-stations-lignes-sur-le-r%C3%A9seau-ferr%C3%A9-RATP-564124?xtmc=R%C3%A9gie%20autonome%20des%20transports%20parisiens%20%28RATP%29&xtcr=2). Il s’agit en fait de la liste de (id_station, ligne).
  * [les plans « emblématiques » et pictogrammes](http://www.ratp.fr/fr/ratp/r_70350/open-data/)

### Les défauts

Cela semble bien parti sauf qu’il y a multitude de défauts.

La liste des stations est un référentiel simple, voire simplet 

  * La fiche sur data.gouv.fr a une documentation sommaire:
  
    > ID ; X ; Y ; nom station ; Ville/CP ; réseau. Les données de géolocalisation sont au format WGS84 (format GPS).
    
    Contrairement à son nom « ville/cp » ne contient que la ville (sauf pour Paris où il y a aussi l’arrondissement). Concernant la signification de X et Y, il s’agit en fait des longitude et latitude (et dans la notation WGS84, on écrit dans l’autre sens: d’abord latitude puis longitude) </li> 
    
      * la position est le barycentre des entrées. Or, moi je prends les escaliers, je ne creuse pas de tunnel…; Il aurait été plus intelligent de fournir la liste des entrées (et encore mieux: sont-elles accessibles aux handicapés?)
      * La plupart des stations ont une casse correcte, mais certaines stations sont incorrectement entièrement en majuscules (pour le tramway)</ul> 
    
    Le fichier « correspondances » est improprement nommé, puisqu’on y trouve tous les quais, y compris ceux qui ne constitue pas une correspondance.
    
      * Il pourrait être plus simple à _parser_ si le nom court de la ligne (ex « A » pour le RER A) était isolé des débuts et fins de ligne (actuellement  » A (Marne-la-Vallée-Chessy – Boissy-St-Leger/Cergy-St-Christophe – Poissy – St-Germain-en-Laye) « )
      * Les noms de ligne ne sont pas très cohérants, puisque un numéro parfois (ex D ((81) Melun/(81) Orry la ville Coye). J’ai réalisé que cette ligne D était en fait plus précise, car cela permet de distinguer les différentes branches. Par contre, ça semble du chinois, il faudrait que quelqu’un passe plus de 10 secondes à modéliser les données, non?
      * surtout, une information cruciale est manquante: le numéro de séquence de l’arrêt dans la ligne. Aujourd’hui, il n’est pas possible de déterminer l’ordre dans lequel les stations se suivent quand le train circule!
    
    Même les pictogrammes sont faux. En effet, les images fournies en Open Data sont entièrement transparentes.
  
    [<img src="/blog/wp-content/uploads/2012/08/Logo-T1-open-data.png" alt="Logo T1 fourni, posé sur mon bureau" title="Logo T1 open data" width="78" height="51" class="alignnone size-full wp-image-2884" />](/blog/wp-content/uploads/2012/08/Logo-T1-open-data.png){.fancybox}
  
    Cela pose un réel problème de visibilité. Or, le plan schématique montre bien que ce n’est pas ainsi que le pictogramme doit être représenté. L’intérieur du cercle devrait être un disque blanc
  
    [<img src="/blog/wp-content/uploads/2012/08/Logo-T1-réel-350x120.png" alt="Logo T1 réellement utilisé dans le plan" title="Logo T1 réel" width="350" height="120" class="alignnone size-medium wp-image-2885" srcset="/blog/wp-content/uploads/2012/08/Logo-T1-réel-350x120.png 350w, /blog/wp-content/uploads/2012/08/Logo-T1-réel.png 357w" sizes="(max-width: 350px) 100vw, 350px" />](/blog/wp-content/uploads/2012/08/Logo-T1-réel.png)
    
    ### Des informations qui auraient apporté de la valeur…;
    
    Mais je ne veux passer casser ce bon élan, car j’aimerais aussi
    
      * où se trouve la correspondance par rapport au train (première voiture, deuxième voiture, etc); cela m’aiderait à finir Zazie
      * les données pour les bus
      * [les horaires](http://www.lepoint.fr/chroniqueurs-du-point/guerric-poncet/la-ratp-ouvre-un-peu-ses-donnees-08-08-2012-1494227_506.php "La RATP oublie les horaires")
      * un peu d’union avec la SNCF pour fournir toutes les données…;
    
    ### Inexploitable aujourd’hui
    
    Certes, c’est le geste qui compte, et c’est embryonnaire. Mais pour le moment, les données « libérées » sont déjà connues de tout le monde. Et puis, elles sont à peu près inexploitables. D’ici à penser que [c’est volontaire](http://www.rudebaguette.com/2012/08/17/open-data-baby-steps-for-the-parisian-mass-transit-system/ "RATP makes a baby step towardsopen data (en)")…;
