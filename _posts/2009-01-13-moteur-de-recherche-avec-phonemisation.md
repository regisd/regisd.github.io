---
id: 784
disqus_id: 784 http://regis.decamps.info/blog/?p=784
title: Moteur de recherche avec phonémisation
date: 2009-01-13T11:42:13+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=784
permalink: /blog/2009/01/moteur-de-recherche-avec-phonemisation/
dsq_thread_id:
  - "189257699"

categories:
  - Programmation
tags:
  - Moteur de recherche
---
Au bureau, on cherche à écrire un moteur de recherche avec approximation phonétique. Pour cela, on cherche un algorithme de [phonémisation](http://fr.wikipedia.org/wiki/Phon%C3%A8me) approximatif.

Avez vous des références? j’ai déjà trouvé

  * [qdicorime](http://dev.ignu.fr/qdicorime/trunk/fabricationbase/perlmodule/Lingua-FR-Phonemise/lib/Lingua/FR/Phonemise.pm), un programme qui aide à trouver des rimes &#8212; les développeurs sont de grands poètes
  * un outil de synthèse vocale, comme [FreeTTS](http://freetts.sourceforge.net/) ou [Franfest](http://www.culte.org/projets/biglux/devel/lao/franfest.shtml/)
  * metaphoneme de Lawrence Philips publié en juin 2000 dans **C/C++ Users Journal** et [double metaphoneme](http://www.phpclasses.org/browse/package/240.html) qui est une amélioration du premier
  * une implémentation [PHP de Soundex 2](http://www.phpclasses.org/browse/package/2972.html). Celui-ci réduit les mots sur seulement 4 caractères, il a implique donc une recherche plus vague
  * une implémentation PHP de [Phonex](http://www.phpclasses.org/browse/package/2974.html) qui est une évolution de Soundex

Une implémentation java serait idéale, vu qu’on souhaitait étendre Apache [Lucene](http://lucene.apache.org).
