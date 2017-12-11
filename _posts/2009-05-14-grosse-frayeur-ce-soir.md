---
id: 885
disqus_id: 885 http://regis.decamps.info/blog/?p=885
title: Grosse frayeur ce soir
date: 2009-05-14T21:35:48+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=885
permalink: /blog/2009/05/grosse-frayeur-ce-soir/
dsq_thread_id:
  - "189257797"

categories:
  - Hightech
tags:
  - Linux
---
Ce soir, mon ordinateur ne démarre pas. Un système de fichiers n’a pas pu être monté à cause d’incohérences. Manque de bol, il s’agit de `/home`. Mais je suis encore confiant.

Le `fsck` échoue. Je suis un peu moins confiant. Je décide de l’appliquer directement sur le disque, et non sur le périphérique RAID. Je veux donc démonter mon RAID, mais il refuse car il y a un volume actif sur le RAID. 

Hé oui, car j’utilise LVM…; En fait, j’ai deux disques `/dev/sda9` et `/dev/sdb2` agrégés en RAID 1 (mirroring) sur `/dev/md0`.
  
J’ai placé ce `/dev/md0` dans un groupe physique LVM `/dev/raidvg`.
  
Et sur ce groupe physique, j’ai créé un volume logique `/dev/raidvg/home` sur lequel est monté mon répertoire `/home`

A ce stade, je me dis donc qu’il me suffit de stopper mon LVM. Et je lance (un peu à l’improviste) la commande `vgremove` sur `/dev/raidvg`. Il me demande la confirmation du retrait de /dev/raidvg/home dans la foulée.

Et là, je me rends compte qu’il est absurde de lancer `fsck` sur `/dev/sda9` car ce volume sert uniquement de support à LVM et n’est pas la partition de données en tant que telles.

Et c’est à ce moment que j’entre en mode panique: je n’ai pas moyen de récupérer ma configuration LVM car je l’ai détruite!

Il y a bien sur un `vgcfgrestore`, mais il nécessite un fichier de backup dans `/etc/lvm/backup` et je n’avais pas vu la commande `vgcfgbackup`! 

Avant de recréer un nouveau système de fichiers sur ce nouveau volume LVM, je me dis que LVM doit bien pouvoir redétecter l’ancienne configuration. Je cherche désespérément avec `lvscan` mais non…;

Et là je découvre qu’il y a un répertoire `/etc/lvm/archive`. Avec pleins de fichiers; LVM est génial. Il a créé un backup à chacune des opérations que j’ai faites avec lui depuis la création des volumes physiques. Je retrouve la configuration d’avant catastrophe, et fais une copie dans `/etc/lvm/backup`.

Je retrouve mon volume logique sans problème, et je finis par reconstruire mon système de fichiers à coups de `fsck.reiserfs` 

Et j’ai retenu la leçon: la panne disque n’est pas la seule façon de perdre ses données. Je fais une copie de tout mon `/home` sur un autre système de fichiers. Il faudrait que je grave tout ça.

Et LVM est génial.
