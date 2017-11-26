---
id: 424
title: Premières impressions sur .net
date: 2007-06-07T17:40:31+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/2007/06/premieres-impressions-sur-net/
permalink: /2007/06/premieres-impressions-sur-net/
tmac_last_id:
  - ""
dsq_thread_id:
  - "695356755"
categories:
  - Programmation
tags:
  - .net
  - 'C#'
  - Java
  - Microsoft
---
Je suis en train de découvrir le monde .net.

##### Le langage C#

Mes premières impressions sont assez neutres sur le langage C#. Il n&rsquo;y a rien de révolutionnaire (par rapport à Java 5 en tout cas). 

La notion de _delegates_ est assez sympathique, même si j&rsquo;ai l&rsquo;impression que les Design patterns _Observer_ et _Strategy_ permettent de répondre aux mêmes besoins en Java.

La gestion des _threads_ à l&rsquo;air plus simple en C# également.

C# permet aussi de gérer les pointeurs, comme en C++. Toujours proche du C++, C# permet de surcharger les opérateurs. Cela permet d&rsquo;écrire des choses comme
  
`<br />
Personne.Nom = "Haba";<br />
Personne.Prenom = "Bart";<br />
` 
  
tout en faisant en réalité appel à des méthodes. C&rsquo;est strictement équivalent en Java à
  
`Personne.setNom("Haba");<br />
Personne.setPrenom("Bart");<br />
` .
  
On peut apprécier (le code est écrit de façon plus « élégante »), mais je préfère les conventions de Java qui reflètent mieux ce qui se passent (on ne modifie pas directement l&rsquo;attribue de classe).

La gestion des bibliothèques a l&rsquo;air assez bien conçue (mais Microsoft ne pouvait pas vraiment faire pire que l&rsquo;actuel DLL hell) et le mécanisme de signature a l&rsquo;air plus homogène que celui des jar. ClickOnce est une copie de JavaWS, mieux intégrée à Windows.

##### L&rsquo;IDE Visual Studio 2005

Concernant l&rsquo;IDE en revanche, je suis assez déçu. Certes l&rsquo;interface est jolie, mais ce n&rsquo;est pas pour cela qu&rsquo;elle est ergonomique. 

Et surtout ça ressemble plus à un éditeur de texte qu&rsquo;à un environnement de développement. Il n&rsquo;y a pas de détection d&rsquo;erreur à la volée, la complétion automatique est beaucoup moins puissante que dans Eclipse, sans parler des quickfixes&#8230;

Bon, je compléterai sans doute bientôt!