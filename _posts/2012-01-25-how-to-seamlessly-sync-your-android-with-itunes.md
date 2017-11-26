---
id: 2442
title: How to seamlessly sync your Android with iTunes?
date: 2012-01-25T19:08:32+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=2442
permalink: /2012/01/how-to-seamlessly-sync-your-android-with-itunes/
tmac_last_id:
  - "162978306457747456"
dsq_thread_id:
  - "555481626"
categories:
  - Applications
  - English
  - Informatique
  - Musique
tags:
  - Android
  - iTunes
  - Mac OS X
---
I want to synchronize my music library on my iMac with my Android mobile phone:

  * I want something simple.
  * I&rsquo;d rather use WiFi rather than USB. I don&rsquo;t really need a cloud service, though.
  * I want my songs to be re-encoded. Indeed, my iTunes library is Apple Lossless (when ripped from CD) or high-quality MP3 (when bought on Amazon MP3). I can&rsquo;t play m4a alac on Android. And I don&rsquo;t want to waste my phone memory on high lossless songs, since they wil be listen with earphones anyway.

<!--more-->

### Many products. None of them good.

I&rsquo;ve spent a couple of hours trying different solutions:

  * [Lifehacker recommends DoubleTwist](http://lifehacker.com/5801473/how-to-sync-android-with-your-mac-as-seamlessly-as-an-iphone). It requires you to plug the mobile with the USB cable (except if you buy DoubleTwist AirSync).
  * [Easy Phone Tunes](https://market.android.com/details?id=com.easyphonetunes.android.app&feature=search_result) is free for one playlist (well, I called that playlist « Android sync ») and works well
  * [iSyncr](https://market.android.com/details?id=com.jrtstudio.iSyncr4Mac) at €2.5 (and you have to buy an addon for Wifi). However, it looks well done, as it synchronizes play counts, too.
  * Deezer works very well. But the synchronized songs are in Deezer cache, and are inaccessible outside of Deezer. 
  * Winamp, even if still in beta can synchronize, too. Free (the pro version really brings pro features)
  * Android Sync manager
only works with Windows computers 

  * 

And **none of them offer re-encoding**.

### Solution

So, my final workflow is

  1. Use [Max](http://sbooth.org/Max/) to reencode my iTunes library to <tt>~/Music/MP3</tt>
  2. Open [Winamp for Mac](http://www.winamp.com/mac) and import this folder
  3. Open [Winamp for Android](https://market.android.com/details?id=com.nullsoft.winamp) and start sync

Max can be configured to ont regenerate files if they already exist, but I wish Winamp took care of this step.