---
id: 846
title: Best practice for changing the value of a column in SharePoint
date: 2009-03-31T22:56:09+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=846
permalink: /2009/03/best-practice-for-changing-the-value-of-a-column-in-sharepoint/
dsq_thread_id:
  - "189257748"
tmac_last_id:
  - ""
categories:
  - English
  - Programmation
tags:
  - Best practice
  - SharePoint
---
In SharePoint development, it is pretty common to change the value of an element.

For instance, let&rsquo;s consider the column named « Title » defined in many lists. Suppose we want to change the « Title » of an item. What&rsquo;s sound straightforward is to write this

<pre>SPListItem item // get the needed item</pre>

<pre>item["Title"] = "New value";</pre>

Now to deply this solution on a French platform, and _c&rsquo;est le drame_: [Value does not fall withinh the expected range](http://nuage.codeplex.com/WorkItem/View.aspx?WorkItemId=3267). That&rsquo;s because the column is referenced here by its _display name_. So, for the French platform it should be

<pre>item["Titre"] = "New value";</pre>

Even worse. The display name is editable by end users (or more precisely by site administrators). Everyone get the point: this is code snippet is a _worse practice_.

The best practice is to use the internal name (which is « Title » for any language and will never change)

<pre>item[item.Fields.GetFieldByInternalName("Title").Id] = "New value";</pre>

And now, I can confidently say that SharePoint happy is developper unfriendly.

Note also, this sugguests another best practice: when you create a custom column: [don&rsquo;t use spaces in the internal name](http://blogs.syrinx.com/blogs/sharepoint/archive/2008/02/06/best-practices-for-working-with-column-names-in-sharepoint.aspx).