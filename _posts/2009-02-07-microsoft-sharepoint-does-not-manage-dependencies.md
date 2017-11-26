---
id: 808
disqus_id: 808 http://regis.decamps.info/blog/?p=808
title: Microsoft Sharepoint does not manage dependencies
date: 2009-02-07T14:28:47+00:00
author: Régis
excerpt: Sharepoint does not manage dependencies of DLL.
layout: post
guid: http://regis.decamps.info/blog/?p=808
permalink: /blog/2009/02/microsoft-sharepoint-does-not-manage-dependencies/
tmac_last_id:
  - ""
dsq_thread_id:
  - "881201379"
categories:
  - English
  - Informatique
  - Programmation
tags:
  - .net
  - SharePoint
---
Sharepoint does not mangage library dependencies depsite the GAC and the stack of recent technologies it relies on.
  
<!--more-->


  
Imagine you build an assembly <tt>common.dll</tt> used by a feature for Sharepoint<sup><a href="#footnote_0_808" id="identifier_0_808" class="footnote-link footnote-identifier-link" title="on the Sharepoint platform, features are packages that are deployed on a webapp, and activated on a or several sites in this webapp. For instance you could have a &laquo; tagcloud feature &raquo; ; when activated, you can add a column in your list with a new content type called &laquo; tag &raquo; in which it is possible to insert text used to label the items of the list ; and then you can insert in your pages a webpart that draws the tag cloud of all tags used in your lists">1</a></sup>, and deploy this feature on Sharepoint. Everything works like a charm (well, taking out the pain of developing on sharepoint, of course). You deploy a second feature using the same <tt>common.dll</tt> assembly. Everything is good at this point.

Now, retract the second feature. Sharepoint thinks it should clean the place and removes the DLL. The other feature does not work in Sharepoint any more.

Shame on MS! This kind of problems is addressed for ages by the [RPM](http://fr.wikipedia.org/wiki/RPM_Package_Manager), just to name one.

<ol class="footnotes">
  <li id="footnote_0_808" class="footnote">
    on the Sharepoint platform, features are packages that are deployed on a webapp, and activated on a or several sites in this webapp. For instance you could have a « <a href="http://http://www.codeplex.com/nuage">tagcloud feature</a> » ; when activated, you can add a column in your list with a new content type called « tag » in which it is possible to insert text used to label the items of the list ; and then you can insert in your pages a webpart that draws the tag cloud of all tags used in your lists [<a href="#identifier_0_808" class="footnote-link footnote-back-link">&#8617;</a>]
  </li>
</ol>
