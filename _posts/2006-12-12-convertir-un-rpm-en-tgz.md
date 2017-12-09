---
id: 372
disqus_id: 372 http://regis.decamps.info/blog/?p=372
title: Convertir un RPM en tgz
date: 2006-12-12T22:37:04+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/2006/12/convertir-un-rpm-en-tgz/
permalink: /blog/2006/12/convertir-un-rpm-en-tgz/

dsq_thread_id:
  - "693537644"
categories:
  - High-tech
tags:
  - HOWTO
  - Linux
---
À mon travail, j’ai un compte Unix sur un serveur AIX sur lequel il n’y a pas tout ce que je veux…; Du coup j’ai envie d’en ajouter un peu…;

Première solution: compiler moi-même les programmes que je veux. Problème: il faut le compilateur, il faut arriver à compiler (et ce n’est pas toujours évident sous AIX &#8212; c’est un PowerPC, beaucoup de programmes systèmes ne sont pas identiques à Linux, l’assembleur d’IBM est buggé, etc.).

Deuxième solution; installer les [RPM fournis par Redhat](http://www-03.ibm.com/servers/aix/products/aixos/linux/download.html). Il faut [bidouiller son <tt>.rpmmacros</tt>](http://www.bigbold.com/snippets/posts/show/1715). Mais les RPM d’IBM sont mal conçus et ne sont pas relocalisables. Les RPM utilisent en dur <tt>/opt/freeware</tt> et ne sont pas relocalisables. Bouhhhh.

Dernière solution: extraire le contenu du RPM et l’utiliser tel quel. Je fais cela avec <tt>rpm2cpio</tt> et <tt>cpio</tt>. Mais comme le rpm2cpio d’AIX semble buggué, j’ai eu l’idée de faire ça sous Linux pour générer un tgz…; Voici mon programme:
  
[python]
  
#!/bin/sh
  
#verbose. set to &lsquo;v’ for verbose mode
  
v= »

#the original working directory (in order to restaure context)
  
pwdorig=$(pwd)
  
if [ « $v » == « v » ] ; then
    
echo pwdorig=$pwdorig
  
fi

#catch interrupt
  
trap &lsquo;echo « Cleaning up » >&2; cd « $pwdorig » ; rm -rf $tmp ; exit’ 1 2 3 15

RDS_extract() {
          
echo « Extract RPM $file »
          
cd $tmpdir
          
rpm2cpio $file | cpio -id$v
  
}

RDS_tarball() {
          
echo « Build tarball $destfile »
          
cd $tmpdir
          
tar c${v}zf $destfile *
  
}

RDS_finish(){
          
echo « Cleaning temp files »
          
cd $pwdorig
          
cp $tmpdir/$destfile .
          
rm -rf $tmpdir
  
}

echo « rpm2tgz $* »
  
for file in $*
  
do
  
tmpdir=$(mktemp -d)
  
destfile=$(dirname $1)/$(basename $file .rpm).tgz
  
#$file is the absolute path of the file
  
if [ ! « $(echo $file | cut -c 1) » = « / » ] ; then
    
file=$pwdorig/$file
  
fi
  
RDS_extract
  
RDS_tarball
  
RDS_finish
  
done
  
[/python]

Et oui, je sais: j’ai [réinventé la roue](http://gentoo-portage.com/app-arch/rpm2targz).
