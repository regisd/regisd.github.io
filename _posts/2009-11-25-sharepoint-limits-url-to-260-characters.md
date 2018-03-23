---
id: 946
disqus_id: 946 http://regis.decamps.info/blog/?p=946
title: SharePoint limits URL to 260 characters
date: 2009-11-25T19:37:56+00:00
layout: post
guid: http://regis.decamps.info/blog/?p=946
permalink: /blog/2009/11/sharepoint-limits-url-to-260-characters/

dsq_thread_id:
  - "567344442"
categories:
  - Hightech
  - English
tags:
  - Bug
  - Microsoft
  - SharePoint
---
SharePoint is a Web content management system. Within SharePoint, you can create document libraries, directories, files. You end up having resources like <tt>http://my.sharepoint.site.localdomain/Public%20Documents/Director/My%20file.doc</tt>

Here comes the funny thing: the total length of this URL [cannot exceed 260 characters](http://www.sharepointjoel.com/Lists/Posts/Post.aspx?ID=111) (or read [this thread](http://social.technet.microsoft.com/Forums/en/sharepointadmin/thread/2ea9a90f-028d-425c-be8b-8455bfdf0baa)).

If a directory or file is created, and the total length exceed this, you get a very inexplicit « Unkown error » message. Of course, I think this is bad behaviour: SharePoint should at least say the URL is too long.

The RFC 2616 which defines HTTP/1.1 even says this should be an error 414:

> The HTTP protocol does not place any a priori limit on the length of
> a URI. Servers MUST be able to handle the URI of any resource they
> serve, and SHOULD be able to handle URIs of unbounded length if they
> provide GET-based forms that could generate such URIs. A server
> SHOULD return 414 (Request-URI Too Long) status if a URI is longer
> than the server can handle
