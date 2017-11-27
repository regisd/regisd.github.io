---
id: 2269
disqus_id: 2269 http://regis.decamps.info/blog/?p=2269
title: The output stream is obtained with getInputStream()
date: 2011-12-06T10:54:04+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=2269
permalink: /2011/12/the-output-stream-is-obtained-with-getinputstream/
tmac_last_id:
  - "162978325667651584"
dsq_thread_id:
  - "614301797"
categories:
  - Brève
  - English
  - Programmation
tags:
  - Java
---
I have never used the Process class before and I’m baffled by the getters of the <tt><a href="http://docs.oracle.com/javase/6/docs/api/java/lang/Process.html">Process</a></tt> class:

  * <tt><a href="http://docs.oracle.com/javase/6/docs/api/java/lang/Process.html#getErrorStream()">getErrorStream()</a></tt> returns the process error output stream. That makes sense.
  * <tt><a href="http://docs.oracle.com/javase/6/docs/api/java/lang/Process.html#getInputStream()">getInputStream()</a></tt> returns the process standard _output_ stream

How [confusing](http://stackoverflow.com/questions/4228853/java-process-getinputstream-vs-getoutputstream) is that?
