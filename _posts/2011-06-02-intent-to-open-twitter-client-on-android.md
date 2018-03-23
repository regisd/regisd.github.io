---
id: 1949
disqus_id: 1949 http://regis.decamps.info/blog/?p=1949
title: Intent to open twitter client on Android
date: 2011-06-02T11:59:49+00:00
excerpt: There is no standard and straightforward way to open a twitter client on Android from your application. Here is how I do.
layout: post
guid: http://regis.decamps.info/blog/?p=1949
permalink: /blog/2011/06/intent-to-open-twitter-client-on-android/
wordbooker_options:
  - 'a:8:{s:18:"wordbook_noncename";s:10:"dd621ae41b";s:18:"wordbook_page_post";s:4:"-100";s:18:"wordbook_orandpage";s:1:"2";s:23:"wordbook_default_author";s:1:"1";s:23:"wordbook_extract_length";s:3:"256";s:19:"wordbook_actionlink";s:3:"300";s:18:"wordbook_attribute";s:0:"";s:29:"wordbooker_status_update_text";s:33:"New blog post :  %title% - %link%";}'

dsq_thread_id:
  - "555844115"
categories:
  - English
  - Dev
tags:
  - Android
---
Many Android developers [ask](http://stackoverflow.com/questions/2077008/android-intent-for-twitter-application) how to start the default twitter client from their application. Which Intent should you use?

It is often advised to [send an Intent with <tt>ACTION_SEND</tt>](http://stackoverflow.com/questions/2077008/android-intent-for-twitter-application/2077361#2077361). However, many programs will fire up: Gmail, SMS send, dropbox, twitter clients, MMS Send, flickr send, etc. This is too broad.

On the other hand, some people advise to [filter on the MIME type <tt>application/twitter</tt>](http://stackoverflow.com/questions/2077008/android-intent-for-twitter-application/2147163#2147163). But this is too restrictive: very few clients will recognize this unofficial/non-standardized MIME type (twidroid is among them, but HTC default client is not).

Eventually, I came up with the following solution: list all applications that reply to <tt>ACTION_SEND</tt> and filter on known package names.



Hope this helps!
