---
id: 930
disqus_id: 930 http://regis.decamps.info/blog/?p=930
title: Questions and critics on SharePoint
date: 2009-08-29T18:19:32+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=930
permalink: /blog/2009/08/questions-and-critics-on-sharepoint/
tmac_last_id:
  - ""
dsq_thread_id:
  - "919259575"
categories:
  - Informatique
tags:
  - Bug
  - Microsoft
  - SharePoint
---
I have rised a number of [questions on friendfeed](http://friendfeed.com/search?q=from:rds+group:sharepointtalk), but many of them remain unanswered. 

  * In Sharepoint WCM, I can create folders in the « Pages » library with SharePoint designer but not with the web interface. Why? Are there side effects?
  * After an incremental crawl in Sharepoint 2007 search engine, are deleted documents supposed to be removed from the index? Any official reference?
  * Why is the HTML code so invalid/ugly

Also, I have encountered bugs…; What’s the problem with:

  * I try to import an Excel spreadsheet in SharePoint, as described in [http://www.sharepointcustomization.com/wss…;.](http://www.sharepointcustomization.com/wss/articles/lists-excel.htm) When I click the « Import » button, Excel does NOT open, I am redirected to /_layouts/ and thereby receive an « Access denied »
  * When starting the standard approbation workflow, user sometimes gets « critical error » and Shapepoint logs refer to an « invalid canary ».
  * Deployed a solution. Some time later, deployed an upgrade containg a updated DLL and updated master pages. Ended with stsadm -o execadmsvcjobs and stsadm -o copyappbincontent. But the webpart behaves like it used to with the 1st version. Any idea why? Why was iisreset required?
  * Firefox is not supported in many scenarios

Also, what do you think about this SharePoint oddness:

  * « starting date » is a Date and « end date » is a Date+Time
