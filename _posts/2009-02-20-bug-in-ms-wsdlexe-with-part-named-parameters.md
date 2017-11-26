---
id: 830
title: 'bug in MS wsdl.exe with part named &lsquo;parameters&rsquo;'
date: 2009-02-20T15:22:45+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=830
permalink: /2009/02/bug-in-ms-wsdlexe-with-part-named-parameters/
tmac_last_id:
  - ""
dsq_thread_id:
  - "628751401"
categories:
  - English
  - Programmation
tags:
  - .net
  - Bug
  - Microsoft
---
There is a bug in MS [wsdl.exe](http://msdn.microsoft.com/en-us/library/7h3ystb6(vs.71).aspx) utility used to [create a proxy class](http://soumadri.net/wpblog/?p=7). If the WSDL has a [message part named « parameters », the web service client will not be generated](http://developers.de/blogs/andreas_erben/archive/2007/02/02/svcutil.exe_2F00_wsdl.exe_3A00_-issue-with-message-part-name-_2200_parameters_2200_.aspx).

This is might be the case with any message part whose name is a reserved word in C#.