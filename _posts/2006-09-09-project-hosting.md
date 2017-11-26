---
id: 334
title: Project hosting
date: 2006-09-09T15:10:07+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/2006/09/project-hosting/
permalink: /2006/09/project-hosting/
tmac_last_id:
  - ""
dsq_thread_id:
  - "559444214"
categories:
  - Informatique
  - Programmation
tags:
  - Google
---
Il y a un certain nombre de services pour l&rsquo;hébergement de développements informatiques.

Le plus gros et connu d&rsquo;entre-eux est [Sourceforge](http://sf.net) qui offre la panoplie complète, de l&rsquo;hébergement du code (en CVS ou svn), à la documentation, en passant par un gestionnaire de bug ou même un système très performant de distribution de fichiers. Malheureusement, Sourceforge hérite un peu de son passé, l&rsquo;interface est touffue, la création d&rsquo;un projet un peu complexe, et il y a eu beaucoup de problèmes de performance ses derniers mois.

Récemment, Google est entré dans la danse avec [google code hosting](http://code.google.com/hosting/). Interface simpliste: gestionnaire de bugs moyen, pas de gestion de la documentation ou des actualités, hébergement svn uniquement avec une petite interface web. Ca répond à des besoins basiques, mais c&rsquo;est tout.

En s&rsquo;hébergeant soi-même, on peut s&rsquo;orienter vers [Trac](http://trac.edgewall.org/). Trac d&rsquo;ailleurs a introduit une idée très intéressante: celle de l&rsquo;intégration étroite des anomalies/tâches avec les modifications du code source. Lorsque l&rsquo;on commit son code dans subversion, on peut indiquer un numéro de bug (et le lien qui-va-bien est alors créé dans l&rsquo;interface de Trac) ou réciproquement on peut indiquer dans un commentaire de bug un changeset. Bref, voilà quelque chose qui ressemble à de la gestion de configuration. Et trac est livré avec un wiki. Seule son interface est un peu décevante. Si on veut dépenser des sous et être en J2EE, il y a [JIRA](http://www.jira.com/) qui fait à peu près la même chose (et ajoute la gestion des workflows entre autres).

Mais sinon, je viens de découvrir [unfuddle](http://unfuddle.com) qui ressemble fortement à Trac (je parierai qu&rsquo;il est basé sur Trac). Il ne s&rsquo;agit pas d&rsquo;un logiciel mais d&rsquo;un service hébergé. Il y a la formule basique (un développeur) gratuite. Par rapport à Trac, l&rsquo;interface est très sympa, et l&rsquo;administration se fait sur le web plutôt qu&rsquo;en ligne de commande.