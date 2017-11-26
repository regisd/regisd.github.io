---
id: 1106
title: SharePoint is not designed for performance
date: 2009-12-13T13:24:38+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=1106
permalink: /2009/12/sharepoint-is-not-designed-for-performance/
tmac_last_id:
  - ""
dsq_thread_id:
  - "616589226"
categories:
  - English
  - Informatique
tags:
  - SharePoint
---
I hate SharePoint when it’s running slow, which is almost all the time. Last day, a Microsoft consultant told be SharePoint was designed for best performance.

In a couple of quick point, I’ll argue the opposite: SharePoint is slow, and many best practices to provide good performances have been ignored.

This are things that are not done by default, but which can be changed with blood, tears and sweat:

  * Pages are provided uncompressed, but it is possible to add [gzip compression](http://www.bluedoglimited.com/SharePointThoughts/ViewPost.aspx?ID=63)
  * Javascript and CSS have not been [mignified](http://developer.yahoo.com/performance/rules.html#minify)
  * Static content does not come with a [far-future expiration date](http://developer.yahoo.com/performance/rules.html#expires), hence the browser cache policy is inefficient. This can be changed with [blob caching](http://www.pointsharepoint.com/2009/03/blob-caching.html), known to be [the source of 404 errors](http://sharepointinterface.com/2009/10/30/manually-clearing-the-moss-2007-blob-cache/).

You want more? These things cannot be improved:

  * The HTML pages produces are huge. A typical publishing page is about 100kB.
  * The HTML has inline CSS
  * This also comes with several huge CSS files. <tt>core.css</tt> is 82KB. As a result, « 67.4% of CSS (estimated 120.5kB of 178.7kB) is not used by the current page ». In term of maintenance: Webdesigners, get ready to master 5,000 lines of CSS
  * SharePoint does not support [Etags](http://developer.yahoo.com/performance/rules.html#etags), hence the browser cache policy is inefficient
  * Storage of documents is done in database. How do you think SQL servers behaves when the database is larger than 100GB (and a large project can easily reach such an amout with many files and their different revisions)
