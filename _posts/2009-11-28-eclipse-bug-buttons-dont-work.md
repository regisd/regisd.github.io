---
id: 968
title: 'Eclipse bug: buttons don’t work'
date: 2009-11-28T19:01:20+00:00
author: Régis
excerpt: |
  New Project, Next. Hey! Next!
  What? Some buttons don't work any more!
layout: post
guid: http://regis.decamps.info/blog/?p=968
permalink: /2009/11/eclipse-bug-buttons-dont-work/
tmac_last_id:
  - ""
dsq_thread_id:
  - "608328680"
categories:
  - English
  - Informatique
tags:
  - Bug
  - Eclipse
  - Linux
---
My Eclipse Galileo has been behaving very strangely, as some buttons have stopped to work after an update of libgtk: I was unable to click on some buttons (it was as if I was never releasing the click, the button was pushed, but not clicked)

I discovered this when I tried to create a New Project, type Java, Next. Hey! Next!
  
What? I couldn’t click on « next ». However the Enter key still working…;

This is actually a [SWT bug with GTK in Eclipse](https://bugs.eclipse.org/bugs/show_bug.cgi?id=287307).

Workaround is to <tt>export GDK_NATIVE_WINDOWS=1</tt>

I have Java 1.6 Java HotSpot(TM), Mandriva 2010, desktop on KDE4, GTK 2.2.18 (recently updated my Mandriva).

Thank you [norio](http://www.norio.be/blog/2009/10/problems-eclipse-buttons-ubuntu-910) for the tip!
