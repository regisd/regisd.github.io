---
id: 485
disqus_id: 485 http://regis.decamps.info/blog/?p=485
title: 'Microsoft Office Sharepoint Services: Search Engine blocking bug'
date: 2008-03-06T18:05:38+00:00
author: Régis
excerpt: "SharePoint change la casse des URL, rendant l'indexation impossible. Le SP1 corrige ce bug."
layout: post
guid: http://regis.decamps.info/blog/2008/03/microsoft-office-sharepoint-services-search-engine-blocking-bug/
permalink: /blog/2008/03/microsoft-office-sharepoint-services-search-engine-blocking-bug/
tmac_last_id:
  - ""
dsq_thread_id:
  - "591983130"
categories:
  - English
  - Informatique
tags:
  - Bug
  - Microsoft
  - Moteur de recherche
  - SharePoint
---
This is hardly credible, but yet real (bug [#932619](http://support.microsoft.com/kb/932619)). When you configure a MOSS to index <tt>http://server/home<b>P</b>age</tt>, it fails with 

> http://server/home**p**age The crawler could not communicate with the server. Check that the server is available and that the firewall access is configured correctly.

And indeed, SharePoint has changed the case, making every characters lower case.

We have just applied the SP1 which is supposed to fix this ridiculous bug. However, applying SP1 is not enough, [the system admin must also change the value of the registry key CaseSensitiveUrls to 1](http://sharepointsearch.com/cs/blogs/enterprisesearch/archive/2008/01/26/crawling-case-sensitive-web-content-in-sharepoint-server-2007-and-search-server-2008.aspx).
