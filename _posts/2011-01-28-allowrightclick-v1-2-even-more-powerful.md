---
id: 1647
disqus_id: 1647 http://regis.decamps.info/blog/?p=1647
title: 'AllowRightClick v1.2: Even more powerful'
date: 2011-01-28T00:33:33+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=1647
permalink: /2011/01/allowrightclick-v1-2-even-more-powerful/
wordbooker_options:
  - 'a:8:{s:18:"wordbook_noncename";s:10:"86b2b67aca";s:18:"wordbook_page_post";s:4:"-100";s:18:"wordbook_orandpage";s:1:"2";s:23:"wordbook_default_author";s:1:"1";s:23:"wordbook_extract_length";s:3:"256";s:19:"wordbook_actionlink";s:3:"300";s:18:"wordbook_attribute";s:0:"";s:29:"wordbooker_status_update_text";s:33:"New blog post :  %title% - %link%";}'
tmac_last_id:
  - ""
dsq_thread_id:
  - "555531497"
categories:
  - English
  - Extensions
tags:
  - AllowRightClick
  - Chrome
---
Many site try to prevent you from accessing the context menu. Well that’s a nice try; thanks to [AllowRightClick](http://regis.decamps.info/blog/projects/allow-rightclickextension-for-google-chrome/) extension for google Chrome, you will have your context menu anyway :-p

This new version works on more sites than before:

  * even if the protecting javascript was added with <tt>addEventListener()</tt>. This fixes [issue 17](http://code.google.com/p/regis/issues/detail?id=17)
  * even on <tt>div</tt> elements. The cotext menu on Youtube video will bed displayed 🙂 This fixes [issue 8](http://code.google.com/p/regis/issues/detail?id=8)
  * recursively applied on in frames. This fixes [issue 18](http://code.google.com/p/regis/issues/detail?id=18)
  * and there is now an option page to list which sites should be ignored by the extension. This is an improvement other the [previous version](http://regis.decamps.info/blog/2010/09/allowrigtclick-v1-1/), where only Yahoo mail! was left untouched. 

[Install AllowRightClick](https://chrome.google.com/extensions/detail/hompjdfbfmmmgflfjdlnkohcplmboaeo) now.

The full changelog can be found on the google code [project page](http://code.google.com/p/regis/issues/list?can=1&q=label:Milestone-AllowRightClick1.2) (bug reports usually mention the affected sites).
