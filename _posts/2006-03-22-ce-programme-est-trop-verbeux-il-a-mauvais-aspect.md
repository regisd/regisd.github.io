---
id: 230
title: Ce programme est trop verbeux, il a mauvais aspect
date: 2006-03-22T00:10:44+00:00
author: Régis
excerpt: "Aujourd'hui j'aurais pû être sauvé par l'AOP."
layout: post
guid: http://blog.decamps.info/?p=230
permalink: /2006/03/ce-programme-est-trop-verbeux-il-a-mauvais-aspect/
tmac_last_id:
  - ""
dsq_thread_id:
  - "578842514"
categories:
  - Boulot
  - Informatique
tags:
  - Java
---
Je ne veux pas entrer dans les détails ici, mais j&rsquo;avais besoin de comparer les performances de 2 applications:

* une application historique écrite en C
  
* un prototype de portage écrit en Java

L&rsquo;idée était d&rsquo;exécuter ces 2 applications sur le même environnement, avec des données significatives (disons celles de production), sur une machine disponible exclusivement sur ces tests (donc pas sur les environnements de développement <strike>super lents</strike> mutualisés à l&rsquo;extrême), sachant qu&rsquo;on n&rsquo;a pas d&rsquo;environnement de test&#8230; On a donc retenu l&rsquo;environnement de pré-production. Mes tests de performance ont eu lieu ce matin. J&rsquo;avais testé le programme java en développement, il fonctionnait très bien. Ce matin, je prends donc le RER en direction du centre d&rsquo;exploitation, pour aider à lancer le programme java, et faire face aux prévisibles imprévus. 

Mon exploitant me prépare l&rsquo;environnement, et on lance le batch, il tourne bien. Mais je me rends soudain compte d&rsquo;une horreur. Il est excessivement verbeux: chaque traitement engendre plusieurs lignes sur stdout! 

Il n&rsquo;y a pas de log4j. Impossible de reporter ces tests. Il faut trouver une solution rapidement.

Heureusement j&rsquo;ai le code source (et me souviens parfaitement avoir pensé « c&rsquo;est moche tous ces println, mais pour un prototype, ce n&rsquo;est pas grave »). Alors, _a posteriori_, voici la solution que j&rsquo;aurais due adopter: l&rsquo;AOP, bien sûr.

Pour cela, il faut avoir installé \[aspectJ\]( http://www.eclipse.org/aspectj/), et je suppose qu&rsquo;on a pris le plugin pour Eclipse dans la foulée. La première chose à faire, c&rsquo;est de convertir son projet en projet de type AspectJ. Un coup de bouton droit sur le projet et « Convert to AspectJ project » suffit.

Je commence donc par définir un point de coupure sur les print*():

<pre>pointcut printLn(): call(* PrintStream.print*(..));
</pre>

Et j&rsquo;ajoute un _advice_ _autour_ de ce printLn()

<pre>void around() : printLn() {
		//don't 
		//proceed();
	}
</pre>

Ici, donc, j&#8217;empaquette mon PrinterStream.print\*(&#8230;) dans une fonction qui ne fait rien. Comme ça, j&rsquo;ai supprimé tous mes System.out.print\*(&#8230;) (qui font appel à PrinterStream.print()). 

Finalement, voici mon aspect:

<pre>import java.io.PrintStream;
/**
 * Cet aspect inhibe les System.out.print*() entre autres
 */
public aspect StopPrintingAspect {
	// je définis les points de coupure printLn comme les appels à un print*()
	// sur des PrintStream (ne pas oublier l'import
	pointcut printLn(): call(* PrintStream.print*(..));
	
	// je remplace les points printLn par... rien.
	void around() : printLn() {}
}
</pre>

Eclipse tisse l&rsquo;aspect automatiquement: il n&rsquo;y a plus qu&rsquo;à exécuter le programme initial; tous ses print\*(\*) ont été remplacés par&#8230; rien 😉 Je vais pouvoir faire mes tests de performance sans désavantager le java!