---
id: 1585
disqus_id: 1585 http://regis.decamps.info/blog/?p=1585
title: 'C# Bug in WebRequest'
date: 2010-12-28T11:14:11+00:00
author: Régis
excerpt: Sometimes, HttpWebRequest hangs on a http 100 "Continue" request
layout: post
guid: http://regis.decamps.info/blog/?p=1585
permalink: /blog/2010/12/c-bug-in-webrequest/

dsq_thread_id:
  - "555134887"
categories:
  - English
  - Dev
tags:
  - Bug
  - Microsoft
---
I have discovered what I believe is a bug in the C# framework.

I have a simple code that sends a Http webdav request
  
```
req = (HttpWebRequest)WebRequest.Create(url);
  
req.Method = « PROPFIND »;
  
req.Headers = new WebHeaderCollection();
  
// I dunno what’s for, but Sharepoint throws error 404 if it is not set
  
req.Headers.Set(« translate », « f »);
  
req.Headers.Set(« Depth », depth.ToString());

// encode en UTF8 le corp de message à transmettre
  
byte[] bytes = Encoding.UTF8.GetBytes((string)query);

req.ContentType = « text/xml »;
  
req.ContentLength = bytes.LongLength;

RequestStream = req.GetRequestStream();
  
RequestStream.Write(bytes, 0, bytes.Length);
  
RequestStream.Close();
  
HttpWebResponse webResp = (HttpWebResponse)req.GetResponse();
  
// Note : C# has no constant for http status code WEBDAV_MULTI
  
if (((int)webResp.StatusCode) == 207)
      
{
   
// handle web response
       
}
```

Everything works fine most of the time.

This is a typical http dump
  
`<br />
PROPFIND /path/to/foo.bar HTTP/1.1<br />
translate: f<br />
Depth: 0<br />
Content-Type: text/xml<br />
Host: httpserver<br />
Content-Length: 90<br />
Expect: 100-continue<br />
HTTP/1.1 100 Continue<br />
< ?xml version="1.0" encoding="UTF-8"?><d:propfind xmlns:d='DAV:'><d:allprop /></d:propfind>HTTP/1.1 207 Multi-Status<br />
Date: Mon, 27 Dec 2010 09:42:27 GMT<br />
Server: IBM_HTTP_Server/2.0.47.1 Apache/2.0.47 (Unix) DAV/2<br />
Transfer-Encoding: chunked<br />
Content-Type: text/xml; charset="utf-8"</p>
<p>37b<br />
< ?xml version="1.0" encoding="utf-8"?><br /><d:multistatus xmlns: D="DAV:" xmlns:ns0="DAV:"><br /><d:response xmlns:lp1="DAV:" xmlns:lp2="http://apache.org/dav/props/"><br /><d:href>/path/to/foo.bar</d:href><br /><d:propstat><br /><d:prop><br /><lp1:resourcetype /><br /><lp1:creationdate>2010-12-21T15:07:41Z</lp1:creationdate><br /><lp1:getcontentlength>2269</lp1:getcontentlength><br /><lp1:getlastmodified>Tue, 21 Dec 2010 15:07:41 GMT</lp1:getlastmodified><br /><lp1:getetag>"4cc6-8dd-ff786940"</lp1:getetag><br /><lp2:executable>F</lp2:executable><br /><d:supportedlock><br /><d:lockentry><br /><d:lockscope><d:exclusive /></d:lockscope><br /><d:locktype><d:write /></d:locktype><br /></d:lockentry><br /><d:lockentry><br /><d:lockscope><d:shared /></d:lockscope><br /><d:locktype><d:write /></d:locktype><br /></d:lockentry><br /></d:supportedlock><br /><d:lockdiscovery /><br /></d:prop><br /><d:status>HTTP/1.1 200 OK</d:status><br /></d:propstat><br /></d:response><br /></d:multistatus><br />
` 

Now, sometimes, C# hangs on
  
`<br />
PROPFIND /path/to/foo.bar HTTP/1.1<br />
translate: f<br />
Depth: 0<br />
Content-Type: text/xml<br />
Host: httpserver<br />
Content-Length: 90<br />
Expect: 100-continue<br />
HTTP/1.1 100 Continue<br />
` 

It is only 100 seconds afterwards that the IBM http server sends a timeout.

Why is the request never send? [Mironelli gives a workaround](http://haacked.com/archive/2004/05/15/http-web-request-expect-100-continue.aspx#1908)
  
```
req.ServicePoint.Expect100Continue = false;
```

That way, the request contains the full body from the beginning, instead of [a check for the server capabilities](http://www.w3.org/Protocols/rfc2616/rfc2616-sec8.html#sec8.2.3).
