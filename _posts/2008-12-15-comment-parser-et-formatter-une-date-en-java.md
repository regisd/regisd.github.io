---
id: 762
title: Comment parser et formater une date en Java
date: 2008-12-15T22:16:48+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=762
permalink: /2008/12/comment-parser-et-formatter-une-date-en-java/
dsq_thread_id:
  - "189257672"
tmac_last_id:
  - ""
categories:
  - Programmation
tags:
  - Java
---
Petite solution rapide à une problématique simple.

On reçoit une date sous la forme « 2008_1 » (c&rsquo;est issu d&rsquo;un nom de fichier), et on souhaite la formater dans un format plus agréable à lire, « janv. 2008 ».

Pour cela, je propose d&rsquo;utiliser un DateFormat, et le SimpleDateFormat fait parfaitement l&rsquo;affaire, et ça ne fait que quelques lignes de code:
  
[code]
  
DateFormat parseDate=new SimpleDateFormat(« y_M »);
  
Date date=parseDate.parse(string);
  
DateFormat printDate=new SimpleDateFormat(« MMM yyyy »);
  
return printDate.format(date);
  
[/code]
  
<!--more-->


  
Et j&rsquo;ajoute le test unitaire qui correspond
  
[code]
	  
@Test
	  
public void testReformat() throws ParseException {
		  
assertEquals(« janv. 2008 », JourMois.reformat(« 2008_1 »));
		  
assertEquals(« janv. 2008 », JourMois.reformat(« 08_1 »));
		  
assertEquals(« janv. 2008 », JourMois.reformat(« 2008_01 »));
	  
}
  
[/code]