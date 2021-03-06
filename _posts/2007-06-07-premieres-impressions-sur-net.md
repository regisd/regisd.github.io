---
id: 424
disqus_id: 424 http://regis.decamps.info/blog/?p=424
title: Premières impressions sur .net
date: 2007-06-07T17:40:31+00:00
layout: post
guid: http://regis.decamps.info/blog/2007/06/premieres-impressions-sur-net/
permalink: /blog/2007/06/premieres-impressions-sur-net/

dsq_thread_id:
  - "695356755"
categories:
  - Dev
tags:
  - Dotnet
  - Java
  - Microsoft
---
Je suis en train de découvrir le monde .net.

## Le langage C#

Mes premières impressions sont assez neutres sur le langage C#. Il n’y a rien de révolutionnaire (par rapport à Java 5 en tout cas). 

La notion de _delegates_ est assez sympathique, même si j’ai l’impression que les Design patterns _Observer_ et _Strategy_ permettent de répondre aux mêmes besoins en Java.

La gestion des _threads_ à l’air plus simple en C# également.

C# permet aussi de gérer les pointeurs, comme en C++. Toujours proche du C++, C# permet de surcharger les opérateurs. Cela permet d’écrire des choses comme
  
`<br />
Personne.Nom = "Haba";<br />
Personne.Prenom = "Bart";<br />
` 
  
tout en faisant en réalité appel à des méthodes. C’est strictement équivalent en Java à
  
`Personne.setNom("Haba");<br />
Personne.setPrenom("Bart");<br />
` .
  
On peut apprécier (le code est écrit de façon plus « élégante »), mais je préfère les conventions de Java qui reflètent mieux ce qui se passent (on ne modifie pas directement l’attribue de classe).

La gestion des bibliothèques a l’air assez bien conçue (mais Microsoft ne pouvait pas vraiment faire pire que l’actuel DLL hell) et le mécanisme de signature a l’air plus homogène que celui des jar. ClickOnce est une copie de JavaWS, mieux intégrée à Windows.

## L’IDE Visual Studio 2005

Concernant l’IDE en revanche, je suis assez déçu. Certes l’interface est jolie, mais ce n’est pas pour cela qu’elle est ergonomique. 

Et surtout ça ressemble plus à un éditeur de texte qu’à un environnement de développement. Il n’y a pas de détection d’erreur à la volée, la complétion automatique est beaucoup moins puissante que dans Eclipse, sans parler des quickfixes…;

Bon, je compléterai sans doute bientôt!
