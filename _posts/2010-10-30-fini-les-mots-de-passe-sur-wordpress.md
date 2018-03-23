---
id: 1466
disqus_id: 1466 http://regis.decamps.info/blog/?p=1466
title: La fin des mots de passe sur WordPress
date: 2010-10-30T10:37:49+00:00
excerpt: "Avec JanRain, la connexion sur un blog worpress ne nécessite pas de se souvenir d'un énième mot de passe."
layout: post
guid: http://regis.decamps.info/blog/?p=1466
permalink: /blog/2010/10/fini-les-mots-de-passe-sur-wordpress/

dsq_thread_id:
  - "555134877"
categories:
  - Misc
tags:
  - Extension
  - Wordpress
---
Souvent dans les forums ou les blogs, je suis prêt à poster une réponse ou un commentaire, mais quand vient le moment de le faire.
  
[<img src="/blog/wp-content/uploads/2010/10/screenshot2-connected-350x171.png" alt="Vous devez être connecté pour laisser un commentaire" title="Capture d&#039;écrant d&#039;un site exigeant la connexion" width="350" height="171" class="alignnone size-medium wp-image-1467" srcset="/blog/wp-content/uploads/2010/10/screenshot2-connected-350x171.png 350w, /blog/wp-content/uploads/2010/10/screenshot2-connected.png 524w" sizes="(max-width: 350px) 100vw, 350px" />](/blog/wp-content/uploads/2010/10/screenshot2-connected.png)

Certes, je comprends qu’on ne laisse pas les commentaires ouverts aux spammeurs ni aux trolls. Mais dans ce cas, il faut que la connexion soit facile. Je n’ai pas envie de créer un énième compte avec son énième mot de passe.

Heureusement, des solutions technologiques existent: elles s’appellent [OpenID](http://openid.net/) ou [Facebook connect](http://www.facebook.com/help/?page=730).

Et [Janrain Engage](http://www.janrain.com/products/engage) est un plugin pour WordPress qui permet d’utiliser ces technologies sur un blog wordpress. La fenêtre de connexion est modifié par ce plugin:

[<img src="/blog/wp-content/uploads/2010/10/screenshot-engage-303x350.png" alt="Capture d&#039;écran - login.php" title="Engage proprose &quot;or log in with...&quot;" width="303" height="350" class="alignnone size-medium wp-image-1468" srcset="/blog/wp-content/uploads/2010/10/screenshot-engage-303x350.png 303w, /blog/wp-content/uploads/2010/10/screenshot-engage.png 370w" sizes="(max-width: 303px) 100vw, 303px" />](/blog/wp-content/uploads/2010/10/screenshot-engage.png)

En cliquant sur « log in with…; » les visiteurs du site peuvent se connecter avec leurs comptes existants. J’ai retenu [OpenID](http://openid.net/), [Google](http://code.google.com/intl/fr-FR/apis/accounts/docs/OpenID.html), [Yahoo!](http://openid.yahoo.com/), [Facebook](http://www.facebook.com/help/?page=730), [Windows Live](http://winliveid.spaces.live.com/Blog/cns!AEE1BB0D86E23AAC!1745.entry), [AOL](http://dev.aol.com/aol-and-63-million-openids) (tous sont OpenID sauf Facebook).

[<img src="/blog/wp-content/uploads/2010/10/screenshot-engage2-317x350.png" alt="Capture d&#039;écran choix du compte" title="Choix du fournisseur d&#039;identité" width="317" height="350" class="alignnone size-medium wp-image-1472" srcset="/blog/wp-content/uploads/2010/10/screenshot-engage2-317x350.png 317w, /blog/wp-content/uploads/2010/10/screenshot-engage2.png 411w" sizes="(max-width: 317px) 100vw, 317px" />](/blog/wp-content/uploads/2010/10/screenshot-engage2.png)
