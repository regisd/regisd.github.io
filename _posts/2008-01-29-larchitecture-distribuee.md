---
id: 480
title: 'L’architecture distribuée'
date: 2008-01-29T19:23:30+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/2008/01/larchitecture-distribuee/
permalink: /2008/01/larchitecture-distribuee/
tmac_last_id:
  - ""
dsq_thread_id:
  - "623862822"
categories:
  - Informatique
tags:
  - Architecture
---
Pour réussir une architecture distribuée, je retiens les 3 principes de conception suivants:

  * les bibliothèques ne doivent jamais dépendre de frameworks techniques (i.e. les classes abstraites ne doivent pas dépendre de classes concrètes)
  * La conception objet doit respecter le [principe de substitution de Liskov](http://blog.emmanueldeloget.com/index.php/2006/10/12/18-le-principe-de-substitution-de-liskov)
  * Les fonctionnalités doivent respecter le principe d’ouverture et fermeture (i.e. lorsqu’une nouvelle fonctionnalité est ajouté [ouverture], le code existant ne doit pas être modifié [fermeture])
