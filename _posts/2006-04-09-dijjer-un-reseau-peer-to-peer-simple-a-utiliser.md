---
id: 245
disqus_id: 245 http://regis.decamps.info/blog/?p=245
title: 'Dijjer : un réseau peer-to-peer simple à utiliser'
date: 2006-04-09T13:57:06+00:00
author: Régis
layout: post
guid: http://blog.decamps.info/2006/04/dijjer-un-reseau-peer-to-peer-simple-a-utiliser/
permalink: /2006/04/dijjer-un-reseau-peer-to-peer-simple-a-utiliser/
tmac_last_id:
  - ""
dsq_thread_id:
  - "571374970"
categories:
  - Extensions
tags:
  - Peer-to-peer
---
Il existe beaucoup de réseaux peer-to-peer. Le plus populaire et efficace aujourd’hui est à mon avis \[bittorrent\](http://www.bittorrent.com/).

Mais bittorrent a un défaut: la resource peut devenir indisponible si plus personne n’alimente le torrent. Ce serait bien si le torrent pouvait être couplé à une url http: on utilise le peer-to-peer pour économiser de la bande passante quand c’est possible, et on utilise le serveur http quand on n’a pas le choix. Et bien, c’est un peu ce que fait \[dijjer\](http://dijjer.org/).

Par ailleurs, la publication avec bittorrent n’est pas triviale. Il faut mettre en place un tracker, créer un petit fichier torrent (qui décrit le fichier sur ce tracker) et diffuser ce torrent. Là encore dijjer résoud ce problème. Si je veux distribuer http://blog.decamps.info/monfichier.ext en peer-to-peer, je n’ai qu’à faire un lien vers http://localhost:9115/http://blog.decamps.info/monfichier.ext

Pour l’utilisateur de bittorrent maintenant, il faut télécharger le .torrent et l’ouvrir dans le programme bittorrent préalablement installé (par exemple \[Azureus\](http://azureus.sourceforge.net/) ou \[ktorrent\](http://ktorrent.pwsp.net/)). L’utilisateur de dijjer n’a qu’à utiliser le lien http://localhost:9115/http://blog.decamps.info/monfichier.ext qui correspond à un téléchargement http ordinaire. Mais qu’est-ce que ce port 9115 sur ma machine? Et bien c’est le programme dijjer qui a ouvert un service, un proxy http distribué pour résumé.
  
Et comme http://localhost:9115/http://blog.decamps.info/monfichier.ext n’est pas très joli, on peut passer par http://dijjer.org/get/http://blog.decamps.info/monfichier.ext qui fournit en plus des explications sur l’installation du client dijjer (écrit en java).

Tout cela semble très bien, surtout quand on sait qu’il existe une \[extension firefox\](https://addons.mozilla.org/addon.php?id=753) qui ajoute un « sauvegarder avec dijjer » qui ajoute simplement http://localhost:9115/ devant l’url.

Maintenant, les choses ne sont pas si idéales. D’abord parce que ajouter http://dijjer.org/get/blabla devant l’url crée un « single point of failure » vis à vis du site dijjer.org. Mais d’un autre côté, l’url http://localhost:9115/blabla fournira un résultat peut compréhensible si dijjer n’est pas démarré sur l’ordinateur de l’utilisateur &#8212; ce qui n’est pas peu acceptable dans la philosophie du « dijjer est plus simple que bittorrent ».

Et finalement, la popularité de bittorrent lui fournit un gros atout. Si je suis le seul à utiliser \[Dijjer\](http://dijjer.org/), il est certain que je profiterai assez peu du peer-to-peer. Bon je teste un peu plus et je vous tiens au courant.

En attendant, sur Gentoo il existe un \[ebuild de Dijjer\](http://bugs.gentoo.org/show_bug.cgi?id=101245) non officiel. Et l’extension firefox citée précédemment ne s’intalle pas sur firefox 1.5. J’ai donc fait une nouvelle extension qui porte le joli nom de [Dijjer this!](http://dijjer.org/get/http://blog.decamps.info/data/dijjerthis0.1.xpi "Extension firefox pour t&Atilde;&copy;l&Atilde;&copy;charger sur dijjer. Version 0.1") (à télécharger par dijjer, bien sûr avant qu’on ne la trouve sur \[Mozilla addons\](https://addons.mozilla.org/firefox/2357/)).

(tags: <a rel="tag" href="http://blogmarks.net/tag/p2p">p2p</a>)
