---
id: 837
title: Disposing objects in Sharepoint
date: 2009-02-27T08:41:32+00:00
author: Régis
excerpt: Sharepoint is a good development platform. Like in the good old days of C, you need to free objects from memory :-p
layout: post
guid: http://regis.decamps.info/blog/?p=837
permalink: /2009/02/disposing-objects-in-sharepoint/
dsq_thread_id:
  - "189257741"
tmac_last_id:
  - ""
categories:
  - English
  - Programmation
tags:
  - SharePoint
---
[ironic mode]Sharepoint is a good development platform. Like in the good old days of C, you need to free objects from memory :-p[/ironic mode]
  
<!--more-->


  
Stephan Großner [explains](http://blogs.technet.com/stefan_gossner/archive/2008/12/05/disposing-spweb-and-spsite-objects.aspx)

> Each <tt>SPWeb</tt> and <tt>SPSite</tt> object holds a reference to an <tt>SPRequest</tt> object which holds a reference to a SharePoint COM object that is responsible to communicate with the backend SQL server.
> 
> Disposing a <tt>SPWeb</tt> object will not actually remove the <tt>SPWeb</tt> object from memory<sup><a href="#footnote_0_837" id="identifier_0_837" class="footnote-link footnote-identifier-link" title="this is done by the .net garbage collector and actually the .NET framework does not allow to remove any object from memory in a deterministic way">1</a></sup> but it will call a method of the <tt>SPWeb</tt> object which causes the COM object to close the connection to the SQL server and to release its allocated memory. 
> 
> After the dispose only the small managed <tt>SPWeb</tt> and <tt>SPRequest</tt> objects remain in memory which do not create a big memory overhead. They are removed by the dot net framework through garbage collection later as with any other managed object as soon as no references to the object exist any more. 

If the <tt>SPWeb</tt> object is not disposed, it will eventually be freed from memory by the garbage collector, but not the COM objected created to make the connection with SQL ; hence the connection to the SQL server will stay open and there will be a memory leak <sup><a href="#footnote_1_837" id="identifier_1_837" class="footnote-link footnote-identifier-link" title="that’s about 2MB for the COM object created by a SPWeb">2</a></sup>. Microsoft has even invented a term for this kind of thing: _unmanaged objects_.

That’s where [SPDisposeCheck tool](http://blogs.msdn.com/sharepoint/archive/2008/11/12/announcing-spdisposecheck-tool-for-sharepoint-developers.aspx) may become handy. On a broader scope, [identifying memory problems](http://blog.dynatrace.com/2009/02/12/sharepoint-identifying-memory-problems-introduced-by-custom-code/) is a great article.

<ol class="footnotes">
  <li id="footnote_0_837" class="footnote">
    this is done by the .net garbage collector and actually the .NET framework does not allow to remove any object from memory in a deterministic way [<a href="#identifier_0_837" class="footnote-link footnote-back-link">&#8617;</a>]
  </li>
  <li id="footnote_1_837" class="footnote">
    that’s about 2MB for the COM object created by a <tt>SPWeb</tt> [<a href="#identifier_1_837" class="footnote-link footnote-back-link">&#8617;</a>]
  </li>
</ol>
