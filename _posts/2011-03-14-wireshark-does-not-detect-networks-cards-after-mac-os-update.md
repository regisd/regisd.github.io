---
id: 1841
disqus_id: 1841 http://regis.decamps.info/blog/?p=1841
title: Wireshark does not detect networks cards after Mac OS update
date: 2011-03-14T21:16:39+00:00
author: Régis
excerpt: There are no interfaces on which a capture can be done.
layout: post
guid: http://regis.decamps.info/blog/?p=1841
permalink: /2011/03/wireshark-does-not-detect-networks-cards-after-mac-os-update/
wordbooker_options:
  - 'a:8:{s:18:"wordbook_noncename";s:10:"c6fb2e8443";s:18:"wordbook_page_post";s:4:"-100";s:18:"wordbook_orandpage";s:1:"2";s:23:"wordbook_default_author";s:1:"1";s:23:"wordbook_extract_length";s:3:"256";s:19:"wordbook_actionlink";s:3:"300";s:18:"wordbook_attribute";s:0:"";s:29:"wordbooker_status_update_text";s:33:"New blog post :  %title% - %link%";}'
tmac_last_id:
  - ""
dsq_thread_id:
  - "555818047"
categories:
  - English
  - Informatique
tags:
  - Mac OS X
---
After updating Mac OS X to the latest 10.6.6 version, Wireshark cannot detect any network card and fails with

> There are no interfaces on which a capture can be done.

Hopefully, that’s just a [permission issue](http://wiki.wireshark.org/CaptureSetup/CapturePrivileges). Here is how I solved it:
  
`admin$ sudo chgrp _developer /dev/bpf*<br />
admin$ sudo chmod g+rw /dev/bpf*<br />
` 

This will let developers run Wireshark again 🙂
