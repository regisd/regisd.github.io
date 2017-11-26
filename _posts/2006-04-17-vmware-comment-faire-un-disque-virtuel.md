---
id: 256
title: 'VMware: comment faire un disque virtuel'
date: 2006-04-17T15:47:53+00:00
author: Régis
layout: post
guid: http://blog.decamps.info/?p=256
permalink: /2006/04/vmware-comment-faire-un-disque-virtuel/
tmac_last_id:
  - ""
dsq_thread_id:
  - "768688911"
categories:
  - Général
---
En fait, c’est très simple: il suffit d’utiliser [Qemu](http://fabrice.bellard.free.fr/qemu/ "QEMU is a generic and open source processor emulator which achieves a good emulation speed by using dynamic translation.").

<pre>qemu-img create -f vmdk NewDisk.vmdk 2G
</pre>

Ceci crée un nouveau disuqe virtuel de taille maximale de 2Go. La taille réelle du fichier `.vmdk` est sensiblement égale aux données qui sont stockées sur le disque.
