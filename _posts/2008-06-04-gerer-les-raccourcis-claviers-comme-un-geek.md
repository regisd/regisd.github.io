---
id: 527
title: Gérer les raccourcis claviers (comme un geek)
date: 2008-06-04T19:17:41+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=527
permalink: /2008/06/gerer-les-raccourcis-claviers-comme-un-geek/
tmac_last_id:
  - ""
dsq_thread_id:
  - "585381800"
categories:
  - Linux
tags:
  - Astuce
  - KDE
---
Hier, j&rsquo;expliquais [comment modifier les raccourcis clavier de KDE les plus courants](http://regis.decamps.info/blog/2008/06/afficher-ou-masquer-le-bureau/).

On peut faire la même chose de façon un peu plus geek, ou disons le franchement un peu moins simple.

Dans KDE 3, les programmes peuvent recevoir des messages via [DCOP](http://developer.kde.org/documentation/other/dcop.html)<sup><a href="#footnote_0_527" id="identifier_0_527" class="footnote-link footnote-identifier-link" title="Desktop communication protocol">1</a></sup>. 

Par exemple, pour afficher/masquer le bureau, on peut exécuter la commande:
  
`dcop kicker kicker toggleShowDesktop`
  
Traduction (de droite à gauche) <!--more-->cela exécute la méthode 

<tt>toggleShowDesktop()</tt>, sur l&rsquo;objet kicker, sur le programme kicker<sup><a href="#footnote_1_527" id="identifier_1_527" class="footnote-link footnote-identifier-link" title="kicker, c&rsquo;est le tableau de bord, il faut savoir que c&rsquo;est lui qui est responsable de la minimisation/maximisation des fen&ecirc;tres">2</a></sup>, par un message DCOP.

Et si tu n&rsquo;est pas si geek que ça jeune droïde, tu peux utiliser kdcop, qui est une interface graphique à dcop. kdcop fait une introspection des programmes en cours de fonctionnement dans KDE, et permet donc de parcourir leurs interfaces DCOP (ce qui aide à trouver la commande <tt>dcop kicker kicker toggleShowDesktop</tt> si on ne la connait pas à l&rsquo;avance)

Ensuite, il ne reste plus qu&rsquo;à enregistrer cette action DCOP pour le raccourci clavier de son choix, toujours dans le centre de contrôle KDE, mais cette fois-ci dans « Actions d&rsquo;entrées »<sup><a href="#footnote_2_527" id="identifier_2_527" class="footnote-link footnote-identifier-link" title="et non, on ne peut pas d&eacute;marrer khotkeys directement">3</a></sup>.

<ol class="footnotes">
  <li id="footnote_0_527" class="footnote">
    Desktop communication protocol [<a href="#identifier_0_527" class="footnote-link footnote-back-link">&#8617;</a>]
  </li>
  <li id="footnote_1_527" class="footnote">
    kicker, c&rsquo;est le tableau de bord, il faut savoir que c&rsquo;est lui qui est responsable de la minimisation/maximisation des fenêtres [<a href="#identifier_1_527" class="footnote-link footnote-back-link">&#8617;</a>]
  </li>
  <li id="footnote_2_527" class="footnote">
    et non, on ne peut pas démarrer <tt>khotkeys</tt> directement [<a href="#identifier_2_527" class="footnote-link footnote-back-link">&#8617;</a>]
  </li>
</ol>