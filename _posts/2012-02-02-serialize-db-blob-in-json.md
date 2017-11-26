---
id: 2478
disqus_id: 2478 http://regis.decamps.info/blog/?p=2478
title: Serialize db.Blob in JSON
date: 2012-02-02T01:22:14+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=2478
permalink: /blog/2012/02/serialize-db-blob-in-json/
dsq_thread_id:
  - "560947842"
categories:
  - English
  - Programmation
tags:
  - google-app-engine
  - JavaScript
  - JSON
  - Python
---
For a couple of days, I’ve been playing with google-app-engine. In order to build a JSON-based RESTful service, Google suggests a [utility method to transform an object into JSON](http://code.google.com/p/google-app-engine-samples/source/browse/trunk/geochat/json.py?r=55).

Unfortunately, this does not handle <tt>db/Blob</tt> entries, and fails with
  
`<br />
UnicodeDecodeError: 'utf8' codec can't decode byte 0x89 in position 0: invalid start byte<br />
` 

(I have a png image in my blob).

After struggling with it, I eventually found the fix (also posted on [stackoverflow](http://stackoverflow.com/a/9105898/94363))
  
<!--more-->


  
[code]
  
class GqlEncoder(json.JSONEncoder):
      
«  » »Extends JSONEncoder to add support for GQL results and properties.

Adds support to simplejson JSONEncoders for GQL results and properties by
      
overriding JSONEncoder’s default method.
      
«  » »
      
def default(self, obj):
          
if hasattr(obj, &lsquo;\_\_json\_\_’):
              
return getattr(obj, &lsquo;\_\_json\_\_’)()

if isinstance(obj, db.GqlQuery):
              
return list(obj)

elif isinstance(obj, db.Model):
              
properties = obj.properties().items()
              
output = {}
              
for field, value in properties:
                  
data = getattr(obj, field)
                  
if isinstance(data, str):
                      
\# db.Blob inherits from str
                      
data = data.encode(&lsquo;string-escape’)
                  
output[field] = data
              
output[&lsquo;id’] = obj.key().id()
              
return output
  
[/code]
