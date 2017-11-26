---
id: 2881
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
  - post=http://regis.decamps.info/blog/wp-content/uploads/2012/08/metro_fail-350x222.png
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
Comme beaucoup, je me suis réjouis de voir que la [RATP rejoignait enfin le mouvement Open Data](http://www.ratp.fr/fr/ratp/r_70350/open-data/). Mais j&rsquo;ai vite déchanté en voyant la faible qualité de celles-ci&#8230;
  
<!--more-->


  
[<img src="http://regis.decamps.info/blog/wp-content/uploads/2012/08/metro_fail-350x222.png" alt="" title="L&#039;échec de la RATP pour libérer des données" width="350" height="222" class="alignright size-medium wp-image-2886" srcset="http://regis.decamps.info/blog/wp-content/uploads/2012/08/metro_fail-350x222.png 350w, http://regis.decamps.info/blog/wp-content/uploads/2012/08/metro_fail-471x300.png 471w, http://regis.decamps.info/blog/wp-content/uploads/2012/08/metro_fail.png 716w" sizes="(max-width: 350px) 100vw, 350px" />](http://regis.decamps.info/blog/wp-content/uploads/2012/08/metro_fail.png)
  
D&rsquo;abord, parlons de ce qu&rsquo;il y a:

  * la liste des [« positions géographiques des stations »](http://www.data.gouv.fr/donnees/view/Positions-g%C3%A9ographiques-des-stations-du-r%C3%A9seau-ferr%C3%A9-RATP-564122?xtmc=R%C3%A9gie%20autonome%20des%20transports%20parisiens%20%28RATP%29&xtcr=4?xtmc=R%C3%A9gie%20autonome%20des%20transports%20parisiens%20%28RATP%29&xtcr=4)
  * la liste des [« correspondances »](http://www.data.gouv.fr/donnees/view/Correspondances-stations-lignes-sur-le-r%C3%A9seau-ferr%C3%A9-RATP-564124?xtmc=R%C3%A9gie%20autonome%20des%20transports%20parisiens%20%28RATP%29&xtcr=2). Il s&rsquo;agit en fait de la liste de (id_station, ligne).
  * [les plans « emblématiques » et pictogrammes](http://www.ratp.fr/fr/ratp/r_70350/open-data/)

### Les défauts

Cela semble bien parti sauf qu&rsquo;il y a multitude de défauts.

La liste des stations est un référentiel simple, voire simplet 

  * La fiche sur data.gouv.fr a une documentation sommaire:
  
    > ID ; X ; Y ; nom station ; Ville/CP ; réseau. Les données de géolocalisation sont au format WGS84 (format GPS).
    
    Contrairement à son nom « ville/cp » ne contient que la ville (sauf pour Paris où il y a aussi l&rsquo;arrondissement). Concernant la signification de X et Y, il s&rsquo;agit en fait des longitude et latitude (et dans la notation WGS84, on écrit dans l&rsquo;autre sens: d&rsquo;abord latitude puis longitude) </li> 
    
      * la position est le barycentre des entrées. Or, moi je prends les escaliers, je ne creuse pas de tunnel&#8230; Il aurait été plus intelligent de fournir la liste des entrées (et encore mieux: sont-elles accessibles aux handicapés?)
      * La plupart des stations ont une casse correcte, mais certaines stations sont incorrectement entièrement en majuscules (pour le tramway)</ul> 
    
    Le fichier « correspondances » est improprement nommé, puisqu&rsquo;on y trouve tous les quais, y compris ceux qui ne constitue pas une correspondance.
    
      * Il pourrait être plus simple à _parser_ si le nom court de la ligne (ex « A » pour le RER A) était isolé des débuts et fins de ligne (actuellement  » A (Marne-la-Vallée-Chessy &#8211; Boissy-St-Leger/Cergy-St-Christophe &#8211; Poissy &#8211; St-Germain-en-Laye) « )
      * Les noms de ligne ne sont pas très cohérants, puisque un numéro parfois (ex D ((81) Melun/(81) Orry la ville Coye). J&rsquo;ai réalisé que cette ligne D était en fait plus précise, car cela permet de distinguer les différentes branches. Par contre, ça semble du chinois, il faudrait que quelqu&rsquo;un passe plus de 10&nbsp;secondes à modéliser les données, non?
      * surtout, une information cruciale est manquante: le numéro de séquence de l&rsquo;arrêt dans la ligne. Aujourd&rsquo;hui, il n&rsquo;est pas possible de déterminer l&rsquo;ordre dans lequel les stations se suivent quand le train circule!
    
    Même les pictogrammes sont faux. En effet, les images fournies en Open Data sont entièrement transparentes.
  
    [<img src="http://regis.decamps.info/blog/wp-content/uploads/2012/08/Logo-T1-open-data.png" alt="Logo T1 fourni, posé sur mon bureau" title="Logo T1 open data" width="78" height="51" class="alignnone size-full wp-image-2884" />](http://regis.decamps.info/blog/wp-content/uploads/2012/08/Logo-T1-open-data.png){.fancybox}
  
    Cela pose un réel problème de visibilité. Or, le plan schématique montre bien que ce n&rsquo;est pas ainsi que le pictogramme doit être représenté. L&rsquo;intérieur du cercle devrait être un disque blanc
  
    [<img src="http://regis.decamps.info/blog/wp-content/uploads/2012/08/Logo-T1-réel-350x120.png" alt="Logo T1 réellement utilisé dans le plan" title="Logo T1 réel" width="350" height="120" class="alignnone size-medium wp-image-2885" srcset="http://regis.decamps.info/blog/wp-content/uploads/2012/08/Logo-T1-réel-350x120.png 350w, http://regis.decamps.info/blog/wp-content/uploads/2012/08/Logo-T1-réel.png 357w" sizes="(max-width: 350px) 100vw, 350px" />](http://regis.decamps.info/blog/wp-content/uploads/2012/08/Logo-T1-réel.png)
    
    ### Des informations qui auraient apporté de la valeur&#8230;
    
    Mais je ne veux passer casser ce bon élan, car j&rsquo;aimerais aussi
    
      * où se trouve la correspondance par rapport au train (première voiture, deuxième voiture, etc); cela m&rsquo;aiderait à finir Zazie
      * les données pour les bus
      * [les horaires](http://www.lepoint.fr/chroniqueurs-du-point/guerric-poncet/la-ratp-ouvre-un-peu-ses-donnees-08-08-2012-1494227_506.php "La RATP oublie les horaires")
      * un peu d&rsquo;union avec la SNCF pour fournir toutes les données&#8230;
    
    ### Inexploitable aujourd&rsquo;hui
    
    Certes, c&rsquo;est le geste qui compte, et c&rsquo;est embryonnaire. Mais pour le moment, les données « libérées » sont déjà connues de tout le monde. Et puis, elles sont à peu près inexploitables. D&rsquo;ici à penser que [c&rsquo;est volontaire](http://www.rudebaguette.com/2012/08/17/open-data-baby-steps-for-the-parisian-mass-transit-system/ "RATP makes a baby step towardsopen data (en)")&#8230;