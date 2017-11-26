---
id: 1602
title: iChat blocks Jabber when parental controls are enabled
date: 2011-01-10T21:54:04+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=1602
permalink: /2011/01/ichat-blocks-jabber-when-parental-controls-are-enabled/
tmac_last_id:
  - ""
dsq_thread_id:
  - "555407078"
categories:
  - English
  - Informatique
tags:
  - Bug
  - Mac OS X
---
Mac OS Snow Leopard has added Jabber support in iChat, which enables Facebook chat, Google talk, etc. However, if you enable parental controls, leaving the « Limit iChat » checkbox unchecked, [iChat disables Jabber all together](http://tech.kateva.org/2009/05/cant-select-jabber-or-google-talk-for.html). [This has been reported several times on the Apple forums](http://discussions.apple.com/search.jspa?threadID=&q=Parental+Controls&objID=f902&dateRange=all&userID=&numResults=15&rankBy=10001) too.

But [there is a workaround](http://www.lensovet.net/~sysadmin/w/Enable_Jabber_accounts_in_iChat_with_Parental_Controlled_accounts). As administrator, run
  
`<br />
sudo dscl . -mcxset /users/<em>username</em> com.apple.iChatAgent Setting.parentalControls always -bool false<br />
`