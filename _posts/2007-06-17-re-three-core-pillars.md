---
id: 429
disqus_id: 429 http://regis.decamps.info/blog/?p=429
title: 'Re: Three core pillars'
date: 2007-06-17T15:02:50+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/2007/06/re-three-core-pillars/
permalink: /blog/2007/06/re-three-core-pillars/
tmac_last_id:
  - ""
dsq_thread_id:
  - "3886419083"
categories:
  - English
  - Programmation
---
I do agree with [Codice Software](http://codicesoftware.blogspot.com/2007/06/three-core-pillars.html)/ Software development has three core pillars:

  * issue tracking with is a general term for defect tracking, task management, etc.
  * version control, and in particular source control management
  * test management and automation

Probably, I would also add continuous integration.

Unfortunately there are actually few tools that cover everything.

  * [Trac](http://trac.edgewall.org/) nicely integrates source control with issue management (for free). So does [JIRA](http://www.atlassian.com/software/jira/) (at a fair price). Codice Software seems more integrated, à la Microsoft Team Server. I have also seen a very innovating approach:  [is an issue tracker inside subversion.](http://www.polarion.com/) 
  * Bu they don’t manage test plans. Mercury Test Director handles this, and has a (poor) issue tracker, as well. But it is really expensive and has a very poor interface &#8212; which makes it very difficult to integrate with another issue tracker or simply with a SCM. Well it is more « user oriented »
