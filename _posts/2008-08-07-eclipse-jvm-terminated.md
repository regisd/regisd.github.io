---
id: 546
disqus_id: 546 http://regis.decamps.info/blog/?p=546
title: Eclipse. JVM Terminated -1
date: 2008-08-07T12:45:31+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=546
permalink: /blog/2008/08/eclipse-jvm-terminated/
dsq_thread_id:
  - "189257434"
tmac_last_id:
  - ""
categories:
  - English
  - Informatique
tags:
  - Bug
  - Eclipse
  - Java
---
I installed Eclipse Europa (3.3) and Eclipse Ganymede (3.4) but could start none of them. Starting eclipse fails with

[<img src="http://regis.decamps.info/blog/wp-content/uploads/2008/08/eclipse_terminated-300x167.png" alt="Eclipse laucnher: JVM terminated, exit code -1" title="eclipse_terminated" width="300" height="167" class="aligncenter size-medium wp-image-547" srcset="http://regis.decamps.info/blog/wp-content/uploads/2008/08/eclipse_terminated-300x167.png 300w, http://regis.decamps.info/blog/wp-content/uploads/2008/08/eclipse_terminated.png 657w" sizes="(max-width: 300px) 100vw, 300px" />](http://regis.decamps.info/blog/wp-content/uploads/2008/08/eclipse_terminated.png)

I eventually found a fix, that requires to change the <tt>eclipse.ini</tt> file (I replace « new lines » with « spaces »)
  
[<img src="http://regis.decamps.info/blog/wp-content/uploads/2008/08/eclipse_ini-fixed-300x116.png" alt="eclipse.ini diff" title="eclipse_ini-fixed" width="300" height="116" class="aligncenter size-medium wp-image-548" srcset="http://regis.decamps.info/blog/wp-content/uploads/2008/08/eclipse_ini-fixed-300x116.png 300w, http://regis.decamps.info/blog/wp-content/uploads/2008/08/eclipse_ini-fixed.png 813w" sizes="(max-width: 300px) 100vw, 300px" />](http://regis.decamps.info/blog/wp-content/uploads/2008/08/eclipse_ini-fixed.png)

Hope this helps!

Othere suggestions include:

  * [changing the vmargs parameters](http://troyworks.com/blog/2008/06/08/eclipse-jvm-terminated-exit-code-1/) (also [suggested by bobobobo](http://bobobobo.wordpress.com/2008/06/29/eclipse-not-starting/)) and in particular [changing the maximum heap size](http://blogs.s60.com/creatingcarbidecpp/2008/04/stuck_at_the_starting_gate_jvm.html)<sup><a href="#footnote_0_546" id="identifier_0_546" class="footnote-link footnote-identifier-link" title="I suspect this reformats the new lines as well, depending on the editor used">1</a></sup>
  * completedly [blank out the <tt>eclipse.ini</tt> file](http://xiaoxing.wordpress.com/2007/07/25/jvm-terminated-exit-code-1/) (which obviously fixes the incorrect new line character)
  * [reinstall a 64 bit version of Java](http://www.filsa.net/2008/07/14/eclipse-34-jvm-terminated-exit-code-1/) (in case you are on a 64 bit OS)
  * [fixing the arguments after vmargs](http://capacitacionrapida.blogspot.com/2008/06/running-eclipse.html). This was obviously not the problem with my fresh installation, ubt maybe it can help other people.

<ol class="footnotes">
  <li id="footnote_0_546" class="footnote">
    I suspect this reformats the new lines as well, depending on the editor used [<a href="#identifier_0_546" class="footnote-link footnote-back-link">&#8617;</a>]
  </li>
</ol>
