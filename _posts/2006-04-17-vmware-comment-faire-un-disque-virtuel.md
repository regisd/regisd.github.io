---
id: 256
disqus_id: 256 http://regis.decamps.info/blog/?p=256
title: 'VMware: comment faire un disque virtuel'
date: 2006-04-17T15:47:53+00:00
author: Régis
layout: post
guid: http://blog.decamps.info/?p=256
permalink: /blog/2006/04/vmware-comment-faire-un-disque-virtuel/

dsq_thread_id:
  - "768688911"
categories:
  - Hightech
---
En fait, c’est très simple: il suffit d’utiliser [Qemu](http://fabrice.bellard.free.fr/qemu/ "QEMU is a generic and open source processor emulator which achieves a good emulation speed by using dynamic translation.").

```
qemu-img create -f vmdk NewDisk.vmdk 2G
```

Ceci crée un nouveau disuqe virtuel de taille maximale de 2Go. La taille réelle du fichier `.vmdk` est sensiblement égale aux données qui sont stockées sur le disque.
