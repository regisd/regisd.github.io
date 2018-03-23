---
id: 86
disqus_id: 86 http://regis.decamps.info/blog/?p=86
title: Compte rendu du symposium DNG
date: 2005-10-29T14:30:17+00:00
excerpt: |
  Comme je l'avais annoncé ici, j'ai assisté au symposium <a href="http://www.dotnetguru.org/">DotNetGuru</a>. DNG est la première communauté française d'architectes et de développeurs sur la plateforme .net de Microsoft (qui a sponsorisé l'évènement). Les membres de l'équipe DNG ont tous un niveau technique très pointu, sont des consultants et ont donc un discours très critique vis à vis de .net, savant mélange de retours d'expérience et de veille technologique.
  
  Voilà en quelques mots ce que j'ai pensé de la journée (et encore merci à Olivier de m'avoir parlé de cet évènement).
layout: post
guid: http://regis.decamps.free.fr/wordpress/?p=86
permalink: /blog/2005/10/compte-rendu-du-symposium-dng/

dsq_thread_id:
  - "620334801"
categories:
  - Perso
tags:
  - Dotnet
  - Java
---
J’étais arrivé en avance, je n’ai donc pas manqué le début de la première conférence, malgré les petits problèmes logisitiques (vestiaire débordé et sécurité élevée due à la présence de l’homme le plus riche du monde). Pour commencer, donc, Jean-Louis Bénard ([Brainsonic](http://www.brainsonic.com/)) et Eric Groise ([Amazon](http://www.amazon.fr/)) ont parlé d’industrialisation logicielle et ont présenté [Visual-Studio-Team-quelque-chose](http://lab.msdn.microsoft.com/teamsystem/) comme un superbe outils qui répond à toutes les problématiques du développement logiciel : référentiel commun, respect de la méthode de travail (libre mais qui doit être formalisée), architecture (SOA). Cependant, j’ai des doutes sur quelques points. Par exemple, la notion de référentiel commun (qui n’est pas franchement une nouveauté) apporte-t-elle quelque chose? Certes, le manager peut voir le nombdre de bugs ouverts, mais il ne va sans doute pas s’intéresser à leur détails ; on ne gagne rien par rapport aux réunions d’équipe (à la différence des modules SAP qui s’appellent les uns les autres de façon virale).

Ensuite, Sami Jaber (qui est le fondateur de [DotNetGuru](http://www.dotnetguru.org/)) a parlé d’un sujet sur lequel on croyait tout savoir: les architectures n-tiers. Avec les technos d’aujourd’hui, il a montré comment le développeut métier pouvait écrire du « code pur cocaïne », principalement grâce à l’utilisation d’un framework technique maison. Il a aussi présenté Indigo (version moderne de COM basée sur XML et webservices) et la future version de c#.

Avant la pause déjeuner, un mec de Microsoft a présenté un peu trop longement [Windows Vista](http://www.microsoft.com/windowsvista/) et sa Windows Presentation Fondation. Pour résumer, l’écriture des GUI sera réduite à l’écriture d’une description XML et ressemblera un peu à ce que propose [Gnome](http://www.gnome.org/) depuis des lustres avec [glade](http://glade.gnome.org/). Et il faudra une machine affreusement puissante pour faire tourner une interface pleine de gadgets, dont plusieurs « inspirés » de [Mac OS X Tiger](http://www.apple.com/macosx/).

Thomas Gil (qui a quitté Valtech et est maintenant indpendant) a poursuivi avec une présentation de [Linq](http://msdn.microsoft.com/netframework/future/linq/) et XLinq, des langages de requêtes intégrés dans le langage de programmation. J’ai été très déçu par cette présentation: j’ai déjà admiré Thomas quand il expliquait des choses complexes de façon limpide, mais sur Linq, je n’ai rien compris…; Sébastien Ros a enchaîné avec Dlinq, qui parle de la même chose, mais en faisant un mapping sur une base de données relationnelle (ouf, Oracle n’est pas à jeter).

Très _hype_, Didier Girard (de [Improve](http://www.improve-technologies.com/), le « Java guy » derrière [application-servers.com](http://www.application-servers.com/)) et Julien Brunet ([Noga](http://www.noga-systemes.com/)) présentaient les clients riches. Avec tous les _buzz words_ du moment (ajax, Client riche, RIA, Eclipse RCP, etc.) ils m’ont très intéressé (étude IHM au boulot oblige). Je retiens leur vision du futur: le « bureau métier », aujourd’hui sur [Eclipse RCP](http://www.eclipse.org/rcp/) ou CAB et sur[Avalon WPF](http://msdn.microsoft.com/windowsvista/building/presentation/default.aspx) à partir de 2007…;

La dernière présentation était celle de Jean-Marc Prieur (a href= »http://www.defense.gouv.fr/sites/marine/ »>Marine nationale) qui a expliqué comment ils ont dépassé les manques d’UML avec les [Domain Specific Languages (DSL)](http://compose.labri.fr/documentation/dsl/dsl_overview.php3). Sa présentation était très vivante et pleine d’humour. J’ai beaucoup aimé.

_Last but not least_, Bill Gates est passé pour une table ronde d’une heure (le millardaire était de passage à Paris pour l’inauguration d’un labo de recherche commun avec l’INRIA, et pour parler avec Sarkozy de crimanilité sur Internet). Je ne connaissais pas trop le personnage, mais lui ai trouvé plusieurs points communs avec Woody Allen…; Cette table ronde a donné lieu a un échange très prpéparé avec l’équipe DotNetGuru. Dommage que ces derniers aient un niveau en anglais aussi faible, on comprenait à peine les questions. Et dommage que la salle n’ait pas pu participer.

Une journée très intéressante, sans doute même trop dense. Et pour ceux qui n’y étaient pas, [les photos, les présentations et la vidéo de la table ronde sont sur DotNetGuru](http://www.dotnetguru.org/modules.php?op=modload&name=News&file=article&sid=681&mode=thread).
