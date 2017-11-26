---
id: 364
disqus_id: 364 http://regis.decamps.info/blog/?p=364
title: 'Shell programming: echo a variable'
date: 2006-11-10T21:49:21+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/2006/11/shell-programming-echo-a-variable/
permalink: /2006/11/shell-programming-echo-a-variable/
dsq_thread_id:
  - "189256718"
tmac_last_id:
  - ""
categories:
  - English
  - Informatique
tags:
  - Shell
---
Quite often when I write shell scripts, I need to echo a variable for debugging. 

If _a_ is &lsquo;toto’, I’d like to print:
  
a=toto

Of course, you can do
  
[code]
  
echo a=$a
  
[/code]

But since I’m <strike>a programmer</strike> lazy, I’d like to:
  
[code]
  
echo_var a
  
[/code]

How might you would write the echo_var function? (my solution in the comments)
