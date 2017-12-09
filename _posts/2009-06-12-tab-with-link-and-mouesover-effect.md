---
id: 902
disqus_id: 902 http://regis.decamps.info/blog/?p=902
title: Tab with link and mouesover effect
date: 2009-06-12T20:09:49+00:00
author: Régis
excerpt: How to design a Tab where content change on mouseover and where titles are links.
layout: post
guid: http://regis.decamps.info/blog/?p=902
permalink: /blog/2009/06/tab-with-link-and-mouesover-effect/

dsq_thread_id:
  - "559495551"
categories:
  - English
  - Programmation
tags:
  - HTML
  - JavaScript
---
I like the user experience offered by [01net](http://www.01net.com/). There is a contextual text which changes when the mouse goes over titles positionned in tabs, and the tabs titles are links to a more detailed page.

I’ve done the [tab widget with clickable links with jQuery](http://regis.decamps.info/demo/idtab.html) (live demo). I have slightly extended the [original jQuery UI tabs by BKlaus Hartl](http://www.stilbuero.de/2007/10/23/jquery-ui-tabs-aka-tabs-3/).

First you need to [include the jQuery library](http://docs.jquery.com/Tutorials:Getting_Started_with_jQuery).

Then set up a the [tabs widget](http://docs.jquery.com/UI/Tabs).

By default, the content of the tab panel is changed when you click on the tab. I want to change this behaviour, and select a tab with the mouseover event instead. Jquery provides an [option](http://docs.jquery.com/UI/Tabs#option-event "option to change the event in jquery tab") for this:
  
[javascript]
  
$(&lsquo;#tabs’).tabs( {
    
event: &lsquo;mouseover’
  
});
  
[/javascript]

Now comes the hard part. I want to change the event handler triggered when clicking a tab. As the documentation might suggest, I tried to set the [select event handler](http://docs.jquery.com/UI/Tabs#event-select).

However, it turns out that a tab is now « clicked » when the mouse rolls hover, because of the <tt>event</tt> I have changed before. The jQuery documentation should say that <tt>select</tt> is « The event which is triggered, as defined by the event option (or, by default, when the link in the tab title is clicked) »

So I have decided to overide the click event on the link. To do this, I have added a class attribute to my links. Instead of
  
[html]

  * <a href="#fragment-1" id="tab-one" rel="ahah_1.html"><span>One</span></a>
[/html]
  
I have now
  
[html]

  * <a href="#fragment-1" id="tab-one" class="clickable-tab" rel="ahah_1.html"><span>One</span></a>
[/html]
  
As you can see, I have decided to rely on the « rel » attribute to define the real link, and this looks rather [appropriate](http://http://www.w3.org/TR/html4/struct/links.html#adef-rel).

And of course, I have defined some Javascript to handle the click:
  
[javascript]
	  
$(&lsquo;.clickable-tab’).click(function(){
	  
document.location=this.rel;
	  
return false; });
  
[/javascript]

Edit: to improve the user experience, [discret-incognito](http://http://discret-incognito.com/ "Arnaud") advised me to set the pointer to <tt>cursor</tt> for the links on tab titles. This is done in one line of CSS
  
[css]
    
.clickable-tab {
      
cursor: pointer;
      
/\* cursor: hand; &#8212; add this for IE 5. I don’t care \*/
    
}
  
[/css]
  
But because, this is overridden by jQuery-UI, it doesn’t work &lsquo;or just a fraction of second). I actually have to overload jQuery:
  
[javascript]
  
$(« .clickable-tab »).css(« cursor », »pointer »);
  
[/javascript]

Thanks for reading, enjoy the [live demo of tabs widget](http://regis.decamps.info/demo/idtab.html). Hope this helps!
