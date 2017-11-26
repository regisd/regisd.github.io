---
id: 2597
title: Envie de faire un peu de développement Android?
date: 2012-02-21T14:33:56+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=2597
permalink: /2012/02/envie-de-developpement-android/
dsq_thread_id:
  - "584083524"
categories:
  - Mobile
  - Programmation
tags:
  - Android
  - REST
  - web-service
---
Un ami me demande

> J’ai subitement envie de me remettre un peu à faire du dev. Je commencerais bien par un application Android qui se connecte à un service REST. Tu me conseilles quoi?

<!--more-->

### Gestion de source

Avant de démarrer le projet, ce n&rsquo;est pas parce que tu fais un truc dans ton coin, qu&rsquo;il ne faut pas gérer sérieusement les sources. Je te recommande [bitbucket](https://bitbucket.org/ "Source code hosting"), qui offre un dépôt git (à la mode) ou Mercurial (que je trouvais meilleur) [avec intégration sur le bug tracker](http://confluence.atlassian.com/display/BITBUCKET/Setting+Up+the+Bitbucket+Issues+Service "Bitbucket integrates source code and bug tracker"). L&rsquo;hébergement peut être privé, même dans l&rsquo;offre gratuite.

### Client-Serveur

#### Encapsulation, &#8230; ou pas

Pour les échanges de données entre le client mobile et le serveur, REST me semble une évidence. 

Il n&rsquo;y a pas de support SOAP dans Android, si tu veux absolument en faire tu es bon pour du <tt>out.print("<soap:envelope...>")</tt>. 

Et [SOAP n&rsquo;est plus pérenne](http://reinout.vanrees.org/weblog/2010/11/11/soap-is-dead-long-live-rest.html), de toute façon&#8230;

#### Format d&rsquo;échange

Ensuite, tu peux faire du XML ou du Json. Les 2 fonctionnent bien.

  * Le JSon est sans aucun doute moins verbeux. Il est peut-être un chouia plus simple à produire côté serveur (par exemple en [python](http://docs.python.org/library/json.html "Python Json package")). Sur Android, [la bibliotthèque Json](http://developer.android.com/reference/org/json/package-summary.html "org.json package on Android") rend sa consommation très simple.
  * Le XML est verbeux, ce qui n&rsquo;est pas un atout lors d&rsquo;une connexion GPS/3G. Il favorise le typage des éléments, ce qui est un atout pour communiquer avec des services tiers. Pour les échanges plus volumineux, l&rsquo;implémentation SAX d&rsquo;un <tt><a href="http://developer.android.com/reference/org/xml/sax/ContentHandler.html" title="SAX ContentHandler for Android">ContentHandler</a></tt> est sans doute la façon la moins consommatrice en termes de mémoire pour traiter le flux de données.

### Serveur

Soit tu utiliser un service tiers existant, soit tu développes le tien.

#### Un service existant

Dans ce cas, rien à développer, évidemment 🙂 L&rsquo;avantage, est que tu te concentres sur ton client, avec des web-services qui fonctionnent déjà, et qui répondent à un certain besoin.

Mon expérience est qu&rsquo;en étant pas maître du service, tu peux être confronté à des limitations fonctionnelles.

  * Par exemple, [incidents-transports.com n&rsquo;indique pas le type d&rsquo;une ligne](http://incidents-transports.com/api/ligne.json) (est-ce un métro, un tramway, un RER?)
  * par exemple, [Google+ ne permet pas de poster](https://developers.google.com/+/api/ "Gogole+ API")
  * De plus, les grosses API (Facebook, Google) demandent de plus en plus de s&rsquo;authentifier, ce qui oblige à implémenter OAuth, et c&rsquo;est loin d&rsquo;être trivial

#### Ton propre service

Tu as le choix de la technologie, évidemment&#8230;

  * Avec un budget nul, tu peux partir sur du PHP, parce que les [hébergements gratuits](http://php.developpez.com/comparatifs/hebergeurs/ "Hébergements PHP gratuits") ou économiques sont légion
  * Si tu n&rsquo;a pas trop de sous mais du temps, tu peux faire du Google App Engine (GAE), en python ou en Java. Le code n&rsquo;est plus portable, puisqu&rsquo;il utilise le modèle MapReduce de la plateforme. Cependant, cela reste un bon choix pour héberger un service REST de type CRUD.
  * Si tu as des sous, tu pars évidemment sur un environnement hébergé de ton choix.

Mon expérience récente, c&rsquo;est que [Python est un super langage](http://regis.decamps.info/blog/2011/08/un-vrai-plaisir-de-developper-en-python/) côté serveur: Concis, efficace, simple.

Pour GAE, il faut bien comprendre que le [DataStore](http://code.google.com/appengine/docs/python/datastore/ "Google app engine datastore") n&rsquo;est _pas_ une base de données relationnelle, avec toutes les conséquences que cela entraîne<sup><a href="#footnote_0_2597" id="identifier_0_2597" class="footnote-link footnote-identifier-link" title="Je viens de d&eacute;couvrir l&rsquo;existence d&rsquo;un Google Cloud SQL">1</a></sup>. De plus, [les restrictions et limitations](http://stackoverflow.com/a/3068371/94363 "Hidden limitations of Google App Engine?") imposées par Google font que la plupart des frameworks ne marchent pas ou marchent mal, ce qui se traduit souvent par une belle perte de temps &#8212; ça va mieux depuis que certains frameworks sont _forkés_ pour GAE.

### Client Android

#### Environnement de développement

Pour Android, dans tous les cas, il faut [le <strike>DSK</strike> SDK](http://developer.android.com/sdk/index.html "Download Android SDK").

Concernant l&rsquo;environnement de développement, le choix est assez restreint, et la seule plateforme outillée est [Eclipse](http://www.eclipse.org/downloads/packages/eclipse-ide-java-developers/indigosr1 "Download Eclipse IDE Indigo for Java") + [Google ADT (Android development tools)](http://developer.android.com/sdk/eclipse-adt.html) que l&rsquo;on trouve sur le « plugin site » <tt><a href="https://dl-ssl.google.com/android/eclipse/">https://dl-ssl.google.com/android/eclipse/</a></tt>

Tu peux jouer l&rsquo;aventurier fortuné, et tenter [IntelliJ for Android](http://www.jetbrains.com/idea/features/google_android.html)

Sur Netbeans, il n&rsquo;y a pas d&rsquo;outil de conception d&rsquo;interface graphique. Donc, à moins de ne pas supporter les autres IDE, je ne vois pas d&rsquo;intérêt à Netbeans. 

Si tu penses toujours que [Maven](http://maven.apache.org/ "Apache Maven - Java developement framework") ne fait pas perdre de temps, il y a [un plugin](http://code.google.com/p/maven-android-plugin/ "maven-android-plugin pour Android sur Maven"). Mais je ne te recommande pas cette option &#8212; on n&rsquo;est pas sensé avoir 36 dépendances non plus dans une appli mobile.

#### Viser l&rsquo;API Level 7

Tu sais que les systèmes Android sont fragmentés, et [je conseille de te prendre <tt>minVersion=7</tt>](http://regis.decamps.info/blog/2012/01/fragmentation-des-systemes-android-2/). Sur la javadoc d&rsquo;Android, il est possible de masquer les éléments qui ne fonctionnent que sur des niveaux plus élevés.

#### La complexité du développement Android

Côté Android, le framework s&rsquo;est complexifié à chaque version (API Level 15 pour l&rsquo;état de l&rsquo;art), mais les composants de bases n&rsquo;ont pas changé: et tu commenceras par [les fondamentaux](http://developer.android.com/guide/topics/fundamentals.html "Android application fundamentals"): l&rsquo;[<tt>Activity</tt>, qui correspond à un écran](http://developer.android.com/reference/android/app/Activity.html) et l&rsquo;[<tt>Intent</tt> qui permet de démarrer un autre composant](http://developer.android.com/reference/android/content/Intent.html). 

Dans ton exemple, pour synchroniser des données serveurs, tu vas devoir faire une connexion réseau longue:

  * impossible à faire dans l&rsquo;activité courante, car cela bloquerait le processus courant, et donc figerait l&rsquo;application au point d&rsquo;entraîner une erreur de type « Application Non Responsive » (pour éviter cette erreur de programmation, cela génère carrément une exception à partir de l&rsquo;API 10)
  * Tu peux créer un processus comme au bon vieux temps, mais le [Thread](http://developer.android.com/reference/java/lang/Thread.html) est un peu pénible à gérer.
  * Plus simplement, [la documentation t&rsquo;encourage à utiliser une <tt>AsyncTask</tt>](http://developer.android.com/resources/articles/painless-threading.html "(supposely) painless threading in Android"), ce qui te permet de livrer un logiciel fonctionnel rapidement. Mais à terme, cette [<tt>AsyncTask</tt> est une erreur](http://regis.decamps.info/blog/2011/08/my-life-with-android-its-complicated/ "Don't use AsyncTask"), car elle est trop liée à l&rsquo;activité qui l&rsquo;a créée
  * Pour faire proprement les choses, tu peux alors te pencher sur l&rsquo;[<tt>IntentService</tt> qui est un service fonctionnant dans un thread distinct et avec lequel on communique via Intent](http://developer.android.com/reference/android/app/IntentService.html). C&rsquo;est à mon avis la solution la plus élégante pour bien faire les choses.
  * Si tu veux fournir la solution la plus robuste, y compris dans les scénarios déconnectés, tu vas créer un [<tt>ContentProvider</tt> qui stocke les données localement](http://developer.android.com/guide/topics/providers/content-provider-creating.html) à l&rsquo;aide d&rsquo;une [base SQLite](http://developer.android.com/reference/android/database/sqlite/SQLiteDatabase.html), un [<tt>SyncAdapter</tt> qui effectue la connexion réseau et met à jour le <tt>ContentProvider</tt>](http://developer.android.com/reference/android/content/AbstractThreadedSyncAdapter.html) en conséquence, et un [<tt>Account</tt> parce que le framework l&rsquo;exige](http://stackoverflow.com/questions/2720315/should-i-use-android-accountmanager/8614699#8614699 "stackoverflow: Should I use android AccountManager?") pour afficher l&rsquo;ensemble dans « Comptes et synchronisation ».

Je ne t&rsquo;ai mis que quelques pointeurs, mais tu constates déjà qu&rsquo;il y a un certain nombre de choses à ingurgiter&#8230;

### Gloablement

Tout ceci n&rsquo;est pas fait pour te décourager, mais tout ça n&rsquo;a rien de _simple_, surtout si tu veux faire les choses correctement.

Les commentaires sont bienvenus!

<ol class="footnotes">
  <li id="footnote_0_2597" class="footnote">
    Je viens de découvrir l&rsquo;existence d&rsquo;un <a href="https://developers.google.com/cloud-sql/">Google Cloud SQL</a> [<a href="#identifier_0_2597" class="footnote-link footnote-back-link">&#8617;</a>]
  </li>
</ol>