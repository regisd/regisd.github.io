---
id: 311
title: Weighted categories
date: 2006-08-15T21:48:59+00:00
author: Régis
excerpt: I have installed the weighted categories plugin for wordpress.
layout: post
guid: http://regis.decamps.info/blog/2006/08/weighted-categories/
permalink: /2006/08/weighted-categories/
tmac_last_id:
  - ""
dsq_thread_id:
  - "564529875"
categories:
  - English
  - Informatique
---
Thanks to the [weighted categories plugin for wordpress](http://www.hitormiss.org/projects/weighted-categories) by [Matt Kingston](http://www.hitormiss.org/), now, the categories in my sidebar are nicely displayed à la [flickr](http://www.flickr.com/photos/tags/).

However, I noticed a strange bug after installation. My last category had its link broken&#8230; And this category was _Vacances_ (holidays). So, this was a no-go.

I had a quick look in the code and found out that Matt was using the <tt>list_cats</tt> function, parsed the result, and reformated it. And probably there is a problem with the last entrey because we miss a newline or something like that. 

Anyway, to tell the truth, I didn&rsquo;t like that much. I think Worpress should return an array with <tt>list_cats</tt>, so that we can display it as we want. It seems [MVC](http://en.wikipedia.org/wiki/Model-view-controller) is not always used by PHP developers&#8230; I don&rsquo;t know much of Worpress internals, but could not find such a function, so I wrote a simple one.

[Get my modified version of the weighted categories plugin for wordpress](/blog/data/weighted_categories.phps)