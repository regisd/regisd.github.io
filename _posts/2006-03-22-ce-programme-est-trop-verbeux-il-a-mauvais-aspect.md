---
id: 230
disqus_id: 230 http://regis.decamps.info/blog/?p=230
title: Ce programme est trop verbeux, il a mauvais aspect
date: 2006-03-22T00:10:44+00:00
author: Régis
excerpt: "Aujourd'hui j'aurais pû être sauvé par l'AOP."
layout: post
guid: http://blog.decamps.info/?p=230
permalink: /blog/2006/03/ce-programme-est-trop-verbeux-il-a-mauvais-aspect/

dsq_thread_id:
  - "578842514"
categories:
  - Programmation
tags:
  - Java
---
Je ne veux pas entrer dans les détails ici, mais j’avais besoin de comparer les performances de 2 applications:

* une application historique écrite en C
  
* un prototype de portage écrit en Java

L’idée était d’exécuter ces 2 applications sur le même environnement, avec des données significatives (disons celles de production), sur une machine disponible exclusivement sur ces tests (donc pas sur les environnements de développement <strike>super lents</strike> mutualisés à l’extrême), sachant qu’on n’a pas d’environnement de test…; On a donc retenu l’environnement de pré-production. Mes tests de performance ont eu lieu ce matin. J’avais testé le programme java en développement, il fonctionnait très bien. Ce matin, je prends donc le RER en direction du centre d’exploitation, pour aider à lancer le programme java, et faire face aux prévisibles imprévus. 

Mon exploitant me prépare l’environnement, et on lance le batch, il tourne bien. Mais je me rends soudain compte d’une horreur. Il est excessivement verbeux: chaque traitement engendre plusieurs lignes sur stdout! 

Il n’y a pas de log4j. Impossible de reporter ces tests. Il faut trouver une solution rapidement.

Heureusement j’ai le code source (et me souviens parfaitement avoir pensé « c’est moche tous ces println, mais pour un prototype, ce n’est pas grave »). Alors, _a posteriori_, voici la solution que j’aurais due adopter: l’AOP, bien sûr.

Pour cela, il faut avoir installé \[aspectJ\]( http://www.eclipse.org/aspectj/), et je suppose qu’on a pris le plugin pour Eclipse dans la foulée. La première chose à faire, c’est de convertir son projet en projet de type AspectJ. Un coup de bouton droit sur le projet et « Convert to AspectJ project » suffit.

Je commence donc par définir un point de coupure sur les print*():

```
pointcut printLn(): call(* PrintStream.print*(..));

```

Et j’ajoute un _advice_ _autour_ de ce printLn()

```
void around() : printLn() {
		//don't 
		//proceed();
}
```

Ici, donc, j&#8217;empaquette mon PrinterStream.print\*(…;) dans une fonction qui ne fait rien. Comme ça, j’ai supprimé tous mes System.out.print\*(…;) (qui font appel à PrinterStream.print()). 

Finalement, voici mon aspect:

```
import java.io.PrintStream;
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
```

Eclipse tisse l’aspect automatiquement: il n’y a plus qu’à exécuter le programme initial; tous ses print\*(\*) ont été remplacés par…; rien 😉 Je vais pouvoir faire mes tests de performance sans désavantager le java!
