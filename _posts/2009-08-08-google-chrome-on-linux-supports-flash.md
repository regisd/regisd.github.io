---
id: 924
disqus_id: 924 http://regis.decamps.info/blog/?p=924
title: Google chrome on linux supports Flash
date: 2009-08-08T14:13:10+00:00
author: Régis
excerpt: |
  The latest builds of Chrome has an experimental support of mozilla plugins. I now have flash :-)
  
  Google chrome is a very fast web browser, is lightweight, quick to start and innovating. However the linux version didn't support plugins. As such, Flash player was not support, and I had to choice but to stick on firefox/opera for browsing dailymotion, facebook games and so on.
layout: post
guid: http://regis.decamps.info/blog/?p=924
permalink: /2009/08/google-chrome-on-linux-supports-flash/
tmac_last_id:
  - ""
dsq_thread_id:
  - "674913303"
categories:
  - Extensions
  - Linux
tags:
  - Chrome
  - Google
---
Google chrome has been a major news in the web browser space. I couldn’t help but to test it. It’s incredibly lightweight and fast, and brings a fair amount of innovations. I have been using it more and more since the latest version of firefox 3.5, which has disappointed me a lot &#8212; firefox is slow to start, and I’m pretty sure there are many holes for memory leaks. 

Google chrome is a very fast web browser, is lightweight, quick to start and innovating. However the linux version didn’t support plugins. As such, Flash player was not support, and I had to choice but to stick on firefox/opera for browsing dailymotion, facebook games and so on.

The latest builds of Chrome has an experimental support of mozilla plugins. I now have flash 🙂<figure id="attachment_925" style="width: 350px" class="wp-caption alignnone">

[<img src="http://regis.decamps.info/blog/wp-content/uploads/2009/08/screenshot-chrome+plugins-350x285.png" alt="Google chrome with plugins in Linux" title="screenshot-chrome+plugins" width="350" height="285" class="size-medium wp-image-925" srcset="http://regis.decamps.info/blog/wp-content/uploads/2009/08/screenshot-chrome+plugins-350x285.png 350w, http://regis.decamps.info/blog/wp-content/uploads/2009/08/screenshot-chrome+plugins-1024x833.png 1024w, http://regis.decamps.info/blog/wp-content/uploads/2009/08/screenshot-chrome+plugins.png 1050w" sizes="(max-width: 350px) 100vw, 350px" />](http://regis.decamps.info/blog/wp-content/uploads/2009/08/screenshot-chrome+plugins.png)<figcaption class="wp-caption-text">Google chrome with plugins in Linux</figcaption></figure> 

  1. Install the latest build of chrome.
  2. Start chrome with the appropriate option
  
    `chrome --enable-plugins`

Oh by the way, I’ve made a quick script to easily install or upgrade chrome on linux

    #!/bin/sh
    DEST=/usr/local/google/chrome
    URL=http://dl.google.com/linux/direct/google-chrome-unstable_current_i386.deb
    tmp=$(mktemp -p /tmp -d)
    cd $tmp
    wget $URL
    ark -ba $(basename $URL)
    cd google-chrome-unstable_current_i386
    tar -xvf data.tar.lzma
    rm -rf $DEST
    mkdir -p $DEST
    mv opt/google/chrome/* $DEST
    cd
    rm -rf $tmp
    #Symlinks to required libraries
    ln -s /lib/libnspr4.so libnspr4.so.0d
    ln -s /lib/libnss3.so libnss3.so.1d
    ln -s /lib/libnssutil3.so libnssutil3.so.1d
    ln -s /usr/lib/libplc4.so libplc4.so.0d
    ln -s /lib/libplds4.so libplds4.so.0d
    ln -s /lib/libsmime3.so libsmime3.so.1d
    ln -s /lib/libssl3.so libssl3.so.1d
    
    

This script installs chromes in DEST=/usr/local/chrome

To start chrome: <tt>/usr/local/chrome/chrome --enable-plugins</tt>
