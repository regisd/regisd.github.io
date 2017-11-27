---
id: 1772
disqus_id: 1772 http://regis.decamps.info/blog/?p=1772
title: 'WordPress: changer le message de maintenance'
date: 2011-03-03T08:52:45+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=1772
permalink: /blog/2011/03/wordpress-changer-le-message-de-maintenance/
wordbooker_options:
  - 'a:9:{s:18:"wordbook_noncename";s:10:"66be5ea225";s:18:"wordbook_page_post";s:4:"-100";s:18:"wordbook_orandpage";s:1:"2";s:23:"wordbook_default_author";s:1:"1";s:23:"wordbook_extract_length";s:3:"256";s:19:"wordbook_actionlink";s:3:"300";s:26:"wordbooker_publish_default";s:2:"on";s:18:"wordbook_attribute";s:0:"";s:29:"wordbooker_status_update_text";s:33:"New blog post :  %title% - %link%";}'
wordbooker_thumb:
  - /blog/wp-content/uploads/2011/03/greenshot_2011-03-03_10-44-38.png
wordbooker_extract:
  - |
    Quand on fait une mise à jour sur wordpress, celui-ci affiche un message utile mais disgracieux:
    Indisponibilité temporaire pour cause de maintenance. Veuillez revenir dans un instant
    
    En fait, il est possible de mettre ce que l'on souhaite. Il suff ...
tmac_last_id:
  - ""
dsq_thread_id:
  - "560162129"
categories:
  - Général
  - Informatique
tags:
  - Wordpress
---
Quand on fait une mise à jour sur wordpress, celui-ci affiche un message utile mais disgracieux:

> Indisponibilité temporaire pour cause de maintenance. Veuillez revenir dans un instant

En fait, il est possible de mettre ce que l’on souhaite. Il suffit d’ajouter la page <tt>wp-content/maintenance.php</tt><figure id="attachment_1773" style="width: 351px" class="wp-caption alignnone">

<img src="/blog/wp-content/uploads/2011/03/greenshot_2011-03-03_10-44-38.png" alt="Capture d&#039;écran page maintenance" title="Page de maintenance" width="351" height="392" class="size-full wp-image-1773" srcset="/blog/wp-content/uploads/2011/03/greenshot_2011-03-03_10-44-38.png 351w, /blog/wp-content/uploads/2011/03/greenshot_2011-03-03_10-44-38-313x350.png 313w" sizes="(max-width: 351px) 100vw, 351px" /><figcaption class="wp-caption-text">Et voilà. Ma page de maintenance affiche un message plus sympathique.</figcaption></figure>
