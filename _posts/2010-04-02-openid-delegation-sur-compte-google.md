---
id: 1172
disqus_id: 1172 http://regis.decamps.info/blog/?p=1172
title: OpenID delegation sur compte Google
date: 2010-04-02T11:26:39+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=1172
permalink: /blog/2010/04/openid-delegation-sur-compte-google/
dsq_thread_id:
  - "189257879"

categories:
  - High-tech
---
De plus en plus de [sites acceptent une authentification par OpenID](https://www.myopenid.com/directory).

## Sites qui acceptent OpenID

Moi, j’utilise souvent

  * [Dailymotion](http://www.dailymotion.com/login/openid)
  * [Stackoverflow](http://stackoverflow.com/users/login)
  * [Slashdot](http://slashdot.org/my/login)
  * [mon blog](http://regis.decamps.info/blog/wp-login.php?redirect_to=http%3A%2F%2Fregis.decamps.info%2Fblog%2F2010%2F04%2Fopenid-delegation-sur-compte-google%2F) 😉

## Utiliser Google

En même temps, je suis presque toujours connecté avec mon compte Google.

Et ça tombe bien, car Google profiles est un Open ID Provider.

Vous pouvez donc saisir <tt>http://www.google.com/profiles/<em>votre.nom</em></tt> dans l’URL OpenID.

### Délégation

Mais, si on a un site personnel, on peut aussi mettre en place une _délégation_ de son site vers un fournisseur OpenID. Pour les comptes Google, cette combinaison marche plutôt bien pour moi (à ajouter dans la balise <tt>head</tt> de la page HTML)
  
`<br />
<link rel="openid2.provider" href="https://www.google.com/accounts/o8/ud" /><br />
<link rel="openid2.local_id" href="https://www.google.com/profiles/regis.decamps" /><br />
<meta http-equiv="X-XRDS-Location" content="https://www.google.com/accounts/o8/id" /><br />
<link rel="openid.server" href="https://www.google.com/accounts/o8/ud?source=profiles"/><br />
<link rel="openid.delegate" href="https://www.google.com/profiles/regis.decamps"/><br />
` 

J’ai mis cela dans la page index.php de mon site, et grâce à cela, je peux me connecter en un clic avec l’OpenID <tt>http://regis.decamps.info/</tt>

Pretty cool 🙂

### Associer son OpenID à un compte existant

Évidemment, dans de nombreux cas, j’avais un compte avant qu’OpenID ne soit supporté (voire même qu’il n’existe). Dans ce cas, il faut commencer par une étape d’association. On se connecte avec son ancien login/mot de passe, puis on indique qu’on a un (ou plusieurs) OpenID.<figure id="attachment_1180" style="width: 350px" class="wp-caption alignnone">

<img src="/blog/wp-content/uploads/2010/04/Capture-d’écran-2010-04-02-à-12.43.18-350x117.png" alt="Screenshot sur Sourceforge" title="Association d&#039;OpenID sur un compte Sourceforge" width="350" height="117" class="size-medium wp-image-1180" srcset="/blog/wp-content/uploads/2010/04/Capture-d’écran-2010-04-02-à-12.43.18-350x117.png 350w, /blog/wp-content/uploads/2010/04/Capture-d’écran-2010-04-02-à-12.43.18.png 992w" sizes="(max-width: 350px) 100vw, 350px" /><figcaption class="wp-caption-text">Avant de pouvoir utiliser son OpenID avec un compte existant, il faut l'associer (ici sur Sourceforge)</figcaption></figure> 

## Et les sites qui ne l’utilisent pas

Il y a encore de trop nombreux sites qui ne supportent pas OpenID: twitter, wikipedia, last.fm, flickr, digg, etc.

On peut leur faire savoir sur <http://demand.openid.net/>
