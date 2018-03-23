---
id: 2520
disqus_id: 2520 http://regis.decamps.info/blog/?p=2520
title: More design problems with the Android framework
date: 2012-02-07T00:05:00+00:00
layout: post
guid: http://regis.decamps.info/blog/?p=2520
permalink: /blog/2012/02/more-design-problems-with-the-android-framework/
dsq_thread_id:
  - "566867604"
categories:
  - English
  - Dev
tags:
  - Android
  - Best practice
  - Bug
  - Java
---
I already blogged about the [problems I encounter when programming for the Android plateform](http://regis.decamps.info/blog/2011/08/my-life-with-android-its-complicated/).

Well, my list gets is little bigger now!
  
<!--more-->

## Method names made by incompetents

> Ce qui se conçoit bien s’énonce clairement;
  
> et les mots pour le dire arrivent aisément. &#8212; Nicolas Boileau

And I think many programmers in the Android team don’t understand what they do when I see method or class names such as:

  * interface [<tt>OnErrorListener</tt>](http://developer.android.com/reference/android/media/MediaPlayer.OnErrorListener.html). The implenting class is a Listener for sure, but it is a listener _of errors_ not a listener _of **on**errors_. The interface should be called <tt>ErrorListener</tt> and have a method called <tt>onError(...)</tt> (the method is named correctly).
  * methods [<tt>getIsSyncable()</tt>](http://developer.android.com/reference/android/content/ContentResolver.html#getIsSyncable(android.accounts.Account, java.lang.String)) and [<tt>setIsSyncable</tt>](http://developer.android.com/reference/android/content/ContentResolver.html#setIsSyncable(android.accounts.Account, java.lang.String, int)). To Android developers: sure, automatic getter/setter generation saves time, but when you develop a public API, you should be careful about methods name. The getter/setter for boolean « is syncable » should be called <tt>isSyncable()</tt> and <tt>setSyncable(...)</tt>. 

## MediaPlayer state is inaccessible

If you use MediaPlayer, you must follow meticulously its internal state, accordingly to the documented state machine. If you don’t, you’ll get an IllegalStateException.
  
![Mediaplayer state diagramm](/blog/wp-content/uploads/2012/02/mediaplayer_state_diagram.gif)

That’s already a pain in the a$$ to pay attention to a state, but it is even worse when [there is no way to get the state of the player](http://code.google.com/p/android/issues/detail?id=800)! Your application need to maintain the MediaPlayer’s state by implementing various listeners…;
