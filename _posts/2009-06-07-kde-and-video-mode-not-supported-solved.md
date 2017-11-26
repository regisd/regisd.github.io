---
id: 900
title: 'KDE and video mode not supported [SOLVED]'
date: 2009-06-07T19:08:44+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=900
permalink: /2009/06/kde-and-video-mode-not-supported-solved/
tmac_last_id:
  - ""
dsq_thread_id:
  - "596795371"
categories:
  - Linux
tags:
  - KDE
  - Vidéo
---
Today, in KDE, I have started a windows application throuh wine. The applicaiton tried to change the video mode, and my screen turned blank with « Video mode not supported ». This means that the resolution or refresh rate are not supported by the screen. 

Alright, I restart my X11 server. I can log in, and during the initialisation of the KDE session, the screen went blank again. Usually this is configured in <tt>/etc/X11/xorg.conf</tt>, but this is obviously correct since I have the KDE login manager (kdm). Something during in KDE changes that.

My first idea was that the wine applicaiton was still in the KDE session. Being exectuted during the startup, it would push the new unsupported video mode.

Actually, it’s much more simple. There is a configuration file called <tt>~/.kde4/share/config/krandrrc</tt> which defines the resolution, à la randr ([X Resize and Rotate Extension](http://en.wikipedia.org/wiki/XRandR))
