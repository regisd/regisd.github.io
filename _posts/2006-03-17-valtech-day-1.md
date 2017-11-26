---
id: 224
title: Valtech day 1
date: 2006-03-17T00:17:40+00:00
author: Régis
excerpt: Mon petit compte-rendu de cette première journée des Valtech Days, séminaires de veille technologique.
layout: post
guid: http://blog.decamps.info/?p=224
permalink: /2006/03/valtech-day-1/
tmac_last_id:
  - ""
dsq_thread_id:
  - "189256542"
categories:
  - Boulot
  - Informatique
---
Ce matin, je n&rsquo;ai eu aucun mal à me lever tôt. Probablement parce que le soleil se lève plus tôt. Sans doute parce que j&rsquo;étais particulièrement motivé pour aller aux [Valtech Days](http://blog.decamps.info/2006/03/valtech-days-1617-mars/ "Valtech Days 2006").

## EJB 3, pragmatisme, mais ambitions perdues

J&rsquo;ai commencé par un retour d&rsquo;expérience sur la mise en œuvre d&rsquo;EJB 3. Ce séminaire était technique, et a abordé des problèmes assez complexes de politique de chargement d&rsquo;EJB détaché. Bizarrement, je dois être le seul à trouver les EJB 2 simple à développer (il faut dire que je suis outillé de la \[Rolls\](http://www-306.ibm.com/software/awdtools/developer/application/) au bureau). J&rsquo;ai donc du mal à trouver l&rsquo;intérêt de déplacer de la complexité dans des fichiers de paramétrage ou dans de l&rsquo;EJBQL. Je trouve cependant l&rsquo;héritage d&rsquo;EJB très sympathique.

## Automatisation des recettes fonctionnelles

L&rsquo;idée intéressante présentée lors de ce séminaire est la suivante: il faut automatiser les tests, sauf ceux qui portent sur les nouveautés.

En effet, la MOA voit la recette comme une activité consommatrice de ressource. De plus, si elle est confrontée à des régressions, elle se forgera un mauvaise image du nouveau logiciel. Il est donc souvent rentable d&rsquo;investir dans une automatisation des tests (que ce soit l&rsquo;achat de [WinRunner](http://blog.decamps.info/www.mercury.com/us/products/quality-center/functional-testing/winrunner/) ou l&rsquo;écriture des scripts de test proprement dite).

Par contre, il vaut mieux laisser les utilisateurs tester manuellement les nouvelles fonctionnalités. Cela donne une image positive (en tout cas innovante) de la nouvelle version du logiciel.

## Stratégie de JBoss

Le CTO de JBoss a ensuite expliqué pour sa société était forcée de s&rsquo;appuyer sur ces 2 piliers

  * better suppor
  * better software quality.

Le meilleur support se comprend bien. Tout le monde peut proposer du support pour ce serveur J2EE open-source (HP ou Novell, par exemple). JBoss doit donc avoir le meilleur support s&rsquo;ils veulent le vendre. Et ils sont obligés de le vendre, puisqu&rsquo;il ne tirent pas de bénéfice de leur licence LGPL&#8230;

D&rsquo;un autre côté, ils sont obligés d&rsquo;avoir un bon logiciel, car s&rsquo;il fonctionne mal, ça leur coûterait cher d&rsquo;assurer le support. Une offre logicielle attirante avoir des utilisateurs, et est le seul moyen d&rsquo;avoir l&rsquo;opportunité de vendre du support derrière.

## The History and Evidence for Iterative Development, and the Historical Accident of the Waterfall

À elle seule, cette présentation justifie cette journée. [Craig Larman](http://www.craiglarman.com/) est connu pour son best-seller [UML 2 et les design patterns](http://www.amazon.fr/exec/obidos/ASIN/2744070904/wwwdeveloppec-21/403-0947517-3034828). Il est également évangéliste des méthodes agiles.

Sa présentation a été tout simplement brillante. Il a commencé par un petit cours d&rsquo;épistémologie: dans l&rsquo;Histoire, on constate que la pensée dominante au début de toute science est fausse, et que proposer une autre idée est vue considéré par tous comme une profanation. Par exemple, sur les saignées, qui ont « soignées » pendant des siècles toutes sorte de maladies. C&rsquo;était la pensée dominante, trouvée dans les livres, pratiquée par les experts.

L&rsquo;informatique est une science nouvelle et le [développement en V](http://fr.wikipedia.org/wiki/Cycle_en_V) est la méthode de développement dominante.

Pourtant, avec cette méthode 50% des projets informatiques se passent mal, et ce malgré tous les investissements réalisés dans la qualité logicielle au cours des dernières années. En fait, les projets durent en moyenne 2 fois plus longtemps que ce qui était initialement prévu. Et pour avoir une certitude de 90%, il faut multiplier l&rsquo;estimation initiale par 3,5.

Mais d&rsquo;où vient cette affreuse méthode en cascade, ou cycle en V? De recommandations du département de la défense américain [DoD 2167](http://www.software.org/quagmire/descriptions/dod-std-2167a.asp), qui se sont propagées dans les armées de l&rsquo;OTAN, puis dans les entreprises. Ces recommandations proposent le modèle en cascade en s&rsquo;inspirant d&rsquo;un papier de Royce de 1970. Or ce papier commence par « I&rsquo;m going to describe my personal views about managing a large software development ». L&rsquo;ingénierie logicielle repose donc uniquement sur le point de vue d&rsquo;une personne&#8230;

Plus ironique encore, ce que l&rsquo;on décrit comme le modèle en cascade, avec le classique schéma « besoins -> conception -> implémentation -> test -> intégration -> maintenance » est sous titré par Royce « A more _grandiose_ approach ». En anglais, _grandiose_ est péjoratif, cela signifie « illusoire », c&rsquo;est un mirage. Le modèle que l&rsquo;on attribue aujourd&rsquo;hui à Royce est décrit par son propre auteur comme « risky and invites failure ».

Des études statistiques existent et montrent que le Waterfall est mauvais. D&rsquo;autres montrent que les méthodes agiles fonctionnent bien. Elles reposent sur des évidences:

* l&rsquo;architecte code comme un « super développeur » dans l&rsquo;équipe. Il n&rsquo;est pas dans sa tour d&rsquo;ivoire et ne fait pas des diagrammes UML qui vont directement dans les archives (ou la corbeille selon les entreprises)

  * les développements sont itératifs
  * n accepte les changements des besoins
  * l&rsquo;intégration continue est pratiquée
  * l&rsquo;organisation est simple, il y a peu de rôles
  * etc.

Et pourtant [people still believe in waterfall](http://tarmo.fi/blog/2005/09/09/dont-draw-diagrams-of-wrong-practices-or-why-people-still-believe-in-the-waterfall-model/)

Pour plus de détails, je recommande la lecture de [Iterative and Incremental Development: A Brief History](http://www2.umassd.edu/SWPI/xp/articles/r6047.pdf) (pdf)
  
Moi, en tout cas, je ne veux pas envoyer Craig Larman, [Don Wells](http://www.extremeprogramming.org/) ou [Ronald E Jeffries](http://www.xprogramming.com/) au bûcher. Par contre, je me pose la question: comment fait-on de l&rsquo;agile dans un développement au forfait?

## UML 1 vers UML 2

Désolé, il commence à se faire tard, je n&rsquo;ai pas grand chose d&rsquo;exceptionnel à dire de la présentation de Pascal Roques.

## SCRUM

Un ScrumMaster français nous a présenté les différentes phases d&rsquo;une des deux principales méthodes agiles (l&rsquo;autre étant XP). Sa présentation était un peu plus « pratique » (et beaucoup moins évangéliste) que celle de Craig. Soyons honnête, elle n&rsquo;était pas aussi vivante non plus (ou est-ce la fin de la journée qui se faisait sentir).

En tout cas, je n&rsquo;ai toujours pas de réponse à ma question: mais comment on fait dans une relation contractuelle avec un prestataire externe?