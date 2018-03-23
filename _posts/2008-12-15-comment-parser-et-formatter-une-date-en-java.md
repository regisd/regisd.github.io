---
id: 762
disqus_id: 762 http://regis.decamps.info/blog/?p=762
title: Comment parser et formater une date en Java
date: 2008-12-15T22:16:48+00:00
layout: post
guid: http://regis.decamps.info/blog/?p=762
permalink: /blog/2008/12/comment-parser-et-formatter-une-date-en-java/
dsq_thread_id:
  - "189257672"

categories:
  - Dev
tags:
  - Java
---
Petite solution rapide à une problématique simple.

On reçoit une date sous la forme « 2008_1 » (c’est issu d’un nom de fichier), et on souhaite la formater dans un format plus agréable à lire, « janv. 2008 ».

Pour cela, je propose d’utiliser un DateFormat, et le SimpleDateFormat fait parfaitement l’affaire, et ça ne fait que quelques lignes de code:
  
```
DateFormat parseDate=new SimpleDateFormat(« y_M »);
  
Date date=parseDate.parse(string);
  
DateFormat printDate=new SimpleDateFormat(« MMM yyyy »);
  
return printDate.format(date);
```

  
Et j’ajoute le test unitaire qui correspond
  
```	  
@Test
	  
public void testReformat() throws ParseException {
		  
assertEquals(« janv. 2008 », JourMois.reformat(« 2008_1 »));
		  
assertEquals(« janv. 2008 », JourMois.reformat(« 08_1 »));
		  
assertEquals(« janv. 2008 », JourMois.reformat(« 2008_01 »));
	  
}
  
```