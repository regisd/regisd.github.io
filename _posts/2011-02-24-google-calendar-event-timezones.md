---
id: 1711
disqus_id: 1711 http://regis.decamps.info/blog/?p=1711
title: Google calendar bug with timezones
date: 2011-02-24T14:35:05+00:00
layout: post
guid: http://regis.decamps.info/blog/?p=1711
permalink: /blog/2011/02/google-calendar-event-timezones/
wordbooker_options:
  - 'a:8:{s:18:"wordbook_noncename";s:10:"7472524695";s:18:"wordbook_page_post";s:4:"-100";s:18:"wordbook_orandpage";s:1:"2";s:23:"wordbook_default_author";s:1:"1";s:23:"wordbook_extract_length";s:3:"256";s:19:"wordbook_actionlink";s:3:"300";s:18:"wordbook_attribute";s:0:"";s:29:"wordbooker_status_update_text";s:33:"New blog post :  %title% - %link%";}'

dsq_thread_id:
  - "555134958"
categories:
  - English
  - Hightech
tags:
  - Bug
  - Google
---
I was ecstatic when I saw that [Google calendar supports event time zones](http://gmailblog.blogspot.com/2010/12/event-time-zones-in-google-calendar.html). This is a very nice promise for implementing travel events.

However, I have a strange behaviour: there is a one-hour offset between what I set and what is recorded.

My calendar is set for European time (GMT +1)
  
[<img src="/blog/wp-content/uploads/2011/02/greenshot_2011-02-24_14-08-48-350x35.png" alt="screenshot of my settings" title="Google calendar sets time zone at GMT +1" width="350" height="35" class="alignnone size-medium wp-image-1712" srcset="/blog/wp-content/uploads/2011/02/greenshot_2011-02-24_14-08-48-350x35.png 350w, /blog/wp-content/uploads/2011/02/greenshot_2011-02-24_14-08-48.png 734w" sizes="(max-width: 350px) 100vw, 350px" />](/blog/wp-content/uploads/2011/02/greenshot_2011-02-24_14-08-48.png)

I create a « flight » event, from Doha at 1:20 to Hong-Kong at 14:40.
  
[<img src="/blog/wp-content/uploads/2011/02/greenshot_2011-02-24_14-13-081-350x25.png" alt="screenshot of event creation" title="Creation of flight from 1:20 to 14:40" width="350" height="25" class="alignnone size-medium wp-image-1720" srcset="/blog/wp-content/uploads/2011/02/greenshot_2011-02-24_14-13-081-350x25.png 350w, /blog/wp-content/uploads/2011/02/greenshot_2011-02-24_14-13-081.png 717w" sizes="(max-width: 350px) 100vw, 350px" />](/blog/wp-content/uploads/2011/02/greenshot_2011-02-24_14-13-081.png)

So, what I just defined in GMT is a flight from 21:20 to 6:40.

But when I save this event, it appears in Google calendar (in Paris GMT+1 time) between 0:20 and 8:20. Strange…;

So, I opened the event again, and Google calendar added a one-hour offset: 2:20 (GMT+3) to 15:40 (GMT+8).

[<img src="/blog/wp-content/uploads/2011/02/greenshot_2011-02-24_14-36-321-350x26.png" alt="Details of created event" title="Flight created is from 2:20 to 15:40" width="350" height="26" class="alignnone size-medium wp-image-1721" srcset="/blog/wp-content/uploads/2011/02/greenshot_2011-02-24_14-36-321-350x26.png 350w, /blog/wp-content/uploads/2011/02/greenshot_2011-02-24_14-36-321.png 644w" sizes="(max-width: 350px) 100vw, 350px" />](/blog/wp-content/uploads/2011/02/greenshot_2011-02-24_14-36-321.png)

Can anyone explain?
