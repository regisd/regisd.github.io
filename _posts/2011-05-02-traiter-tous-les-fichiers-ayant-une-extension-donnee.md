---
id: 1927
disqus_id: 1927 http://regis.decamps.info/blog/?p=1927
title: Traiter tous les fichiers ayant une extension donnée
date: 2011-05-02T10:54:04+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=1927
permalink: /2011/05/traiter-tous-les-fichiers-ayant-une-extension-donnee/
wordbooker_options:
  - 'a:8:{s:18:"wordbook_noncename";s:10:"1dc942dda8";s:18:"wordbook_page_post";s:4:"-100";s:18:"wordbook_orandpage";s:1:"2";s:23:"wordbook_default_author";s:1:"1";s:23:"wordbook_extract_length";s:3:"256";s:19:"wordbook_actionlink";s:3:"300";s:18:"wordbook_attribute";s:0:"";s:29:"wordbooker_status_update_text";s:33:"New blog post :  %title% - %link%";}'
tmac_last_id:
  - ""
dsq_thread_id:
  - "555134870"
categories:
  - Informatique
  - Linux
tags:
  - Shell
---
Sous Unix, mon besoin est de faire un traitement (disons un <tt>ls</tt>) sur tous les fichiers donné (disons tous les <tt>*.xml</tt>) d’un répertoire.

Naturellement, j’écris
  
[code]
  
for f in*.xml
  
do
  
    ls « $f »
  
done
  
[/code]

Les guillemets sont obligatoire pour gérer les noms de fichiers contenant des espaces.

Le problème, c’est que je ne gère pas la casse…;

Après avoir [perdu du temps en essayant de modifier IFS](http://www.cyberciti.biz/tips/handling-filenames-with-spaces-in-bash.html), la [solution toute simple](http://www.macgeekery.com/tips/cli/handling_filenames_with_spaces_in_bash) est d’utiliser <tt>read</tt>:
  
[code]
  
ls -1 * | grep -i « .xml$ » | while read f
  
do
      
ls « $f »
  
done
  
[/code]
