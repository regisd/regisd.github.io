---
id: 412
title: Logitech MX900 on Linux
date: 2007-05-14T21:22:56+00:00
author: Régis
excerpt: |
  My mouse has stopped to work. After a short diagnostic, I came to the conclusion that the wire cut. Unfortunately, you can't buy a simple wire. My new mouse will be wireless!
  How to make it work on Gentoo linux?
layout: post
guid: http://regis.decamps.info/blog/2007/05/logitech-mx900-on-linux/
permalink: /2007/05/logitech-mx900-on-linux/
dsq_thread_id:
  - "189256840"
tmac_last_id:
  - ""
categories:
  - Linux
---
I just bought a new mouse. It is a nice Logitech MX900: very comfortable, and wireless (since the wire was the point of failure from my previous mouse). I was wondering whether it would work fine under Linux. Actually, it works better than expected.
  
[<img id="image413" src="http://regis.decamps.info/blog/wp-content/uploads/2007/05/00036266.thumbnail.jpg" alt="Logitech MX900" />](http://regis.decamps.info/blog/wp-content/uploads/2007/05/00036266.jpg "Logitech MX900"){.imagelink}

When I plugged the mouse (actually, the base), it was automatically discovered and working fine. Even the wheel was behaving like expected. All this thanks to evdev: In the past, we had to use `xmodmap` or the `ButtonMapping` option in `/etc/X11/xorg.conf`.

However, my thumb buttons were not working. I like when thumb1 acts as a « backward » button in firefox and thumb2 as a « forward » button &#8212; that really ease navigation, I think. Once again, a [nice documentation came from Gentoo](http://planet.gentoo.org/developers/betelgeuse/2006/11/26/getting_mx_revolution_setup_in_gentoo).

But to make a long story short, the only thing I had to do was configure `/etc/X11/imwheel/imwheelrc` as follow
  
`".*"<br />
None, Thumb1, Alt_L|Left<br />
None, Thumb2, Alt_L|Right<br />
` 
  
And run `imwheel` &#8212; and not forget to publish this post before pressing thumb1 😉
