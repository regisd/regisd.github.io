---
id: 2283
title: Simple framework for python plugins
date: 2012-05-24T13:08:57+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=2283
permalink: /2012/05/simple-framework-for-python-plugins/
al2fb_facebook_link_id:
  - 1065233209_3536292440407
al2fb_facebook_link_time:
  - 2012-05-24T11:09:02+00:00
al2fb_facebook_link_picture:
  - post=http://regis.decamps.info/blog/?al2fb_image=1
al2fb_facebook_error:
  - |
    Refresh token: cURL communication error 28 SSL connection timeout:  Array
    (
    [url] => https://graph.facebook.com/oauth/access_token...
    [content_type] =>
    [http_code] => 0
    [header_size] => 0
    [request_size] => 0
    [filetime] => -1
    [ssl_verify_result] => 0
    [redirect_count] => 0
    [total_time] => 0
    [namelookup_time] => 4.0E-5
    [connect_time] => 0.874112
    [pretransfer_time] => 0
    [size_upload] => 0
    [size_download] => 0
    [speed_download] => 0
    [speed_upload] => 0
    [download_content_length] => 0
    [upload_content_length] => 0
    [starttransfer_time] => 0
    [redirect_time] => 0
    )
    
al2fb_facebook_error_time:
  - 2012-05-24T11:09:27+00:00
dsq_thread_id:
  - "702047041"
categories:
  - English
  - Programmation
tags:
  - Python
---
Plugins are often good to build a loosely coupled, modular software architecture. They also foster third-party contributions.

This article describes how I did it very simply in python, this framework is called [spf](https://github.com/regisd/simple_plugin_framework "Single plugin framework on github") (Simple plugin framework) and is available on github.

<!--more-->

After reading [a review on existing framworks](http://wehart.blogspot.com/2009/01/python-plugin-frameworks.html), I tried [yapsy](http://yapsy.sourceforge.net/). Unfortunately it&rsquo;s python&nbsp;2, and despite doing a couple of obvious changes in the code, I couldn&rsquo;t make a working plugin, failing with error
  
`module.__init__() takes at most 2 arguments (3 given)`

After that, I decided to understand better how <tt>exec()</tt> works on <tt>__init__.py</tt> and what such a framework should do. I read the brilliant article [A Simple Plugin Framework](http://martyalchin.com/2008/jan/10/simple-plugin-framework/) by Marty Alchin (who, I think, was a django contributor, and don&rsquo;t know if he still is).

His design is so KISS, I love it. This article is just a up-to-date (there was python 2 to python 3 update to do) and simplified (without references to django) version of his « framework ».

The first thing is to define the notion of plugin.

  * a _mount point_ is a place where extra features can be added
  * a _plugin_ _is a specific implementation that is added to a specific place_

Let&rsquo;s first define a mount point, as a metaclass that simply contains the list of plugins to apply there.

[code]
  
class MountPoint(type):
      
 »&rsquo;
      
* A way to declare a mount point for plugins. Since plugins are an example of loose coupling, there needs to be a neutral location, somewhere between the plugins and the code that uses them, that each side of the system can look at, without having to know the details of the other side.
      
* A way to register a plugin at a particular mount point. Since internal code don&rsquo;t want to look around to find plugins that might work for it, there needs to be a way for plugins to announce their presence. This allows the guts of the system to be blissfully ignorant of where the plugins come from; again, it only needs to care about the mount point.
      
* A way to retrieve the plugins that have been registered. Once the plugins have done their thing at the mount point, the rest of the system needs to be able to iterate over the installed plugins and use them according to its need.

Add the parameter \`metaclass = MountPoint\` in any class to make it a mont point.

 »&rsquo;

def \_\_init\_\_(cls, name, bases, attrs):
          
if not hasattr(cls, &lsquo;plugins&rsquo;):
              
\# This branch only executes when processing the mount point itself.
              
\# So, since this is a new plugin type, not an implementation, this
              
\# class shouldn&rsquo;t be registered as a plugin. Instead, it sets up a
              
\# list where plugins can be registered later.
              
cls.plugins = []
          
else:
              
\# This must be a plugin implementation, which should be registered.
              
\# Simply appending it to the list is all that&rsquo;s needed to keep
              
\# track of it later.
              
cls.plugins.append(cls)
  
[/code]

Now, let&rsquo;s write a mount point. To have a very simple example, my mount point is to print text.
  
[code]
  
class TextTransformer(object, metaclass=MountPoint):
      
 »&rsquo; Plugins can inherit this mount point in order to modify text.

A plugin that registers this mount point must implement the method
      
* transform_text(self, string):
      
 »&rsquo;

def \_\_init\_\_(self, program):
          
pass
  
[/code]

As you can see, this is very simple. Because python doesn&rsquo;t have interfaces, it is very important to write documentation.

For instance, I can have 3 transformers for HTML text
  
[code]
  
class HtmlTransformer(TextTransformer):
      
def \_\_init\_\_(self, program):
          
self.tag = None

#As documented in the Mount point, this must be implemented

def transform_text(self, string):
          
if self.tag:
              
return « < {tag}>{original} ».format(tag=self.tag, original=string)
          
else:
              
return string

class HtmlEmTransformer(HtmlTransformer):
      
 »&rsquo; Plugin to wrap text in a html tag
      
 »&rsquo;

def \_\_init\_\_(self, program):
          
 »&rsquo; This TextTransformer will transform « string«  into « _string_« 
          
 »&rsquo;
          
self.tag = « em »

class HtmlBoldTransformer(HtmlTransformer):
      
 »&rsquo; Plugin to wrap text in a html tag
      
 »&rsquo;

def \_\_init\_\_(self, program):
          
 »&rsquo; This TextTransformer will transform « string«  into « **string**« 
          
 »&rsquo;
          
self.tag = « b »

[/code]

A <tt>main</tt> method that has a TextTransformer mount point
  
[code]
  
class MyProgram:
      
plugins = ExtensionsAt(TextTransformer)

def main(self):
          
\# Here I declare a mount point TextTransformer
          
\# « hello world » will be printed by each plugin

for plugin in self.plugins:
              
retval=plugin.transform_text(« hello world »)
              
print(« Plugin {plugin} produces {retval} ».format(plugin=plugin, retval=retval))

if \_\_name\_\_ == &lsquo;\_\_main\_\_&rsquo;:
      
prog = MyProgram()
      
prog.main()
  
[/code]

As you can see, I have used a utility method to retrieve plugins at a given mount point
  
[code]
  
class ExtensionsAt(object):
      
 »&rsquo; Descriptor to get plugins on a given mount point.
      
 »&rsquo;

def \_\_init\_\_(self, mount_point):
          
 »&rsquo; Initialize the descriptor with the mount point wanted.
          
Eg: ExtensionsAt(apf.GUIMenu) to get extensions that change the GUI Menu.
          
 »&rsquo;
          
self.mount = mount_point

def \_\_get\_\_(self, instance, owner=None):
          
 »&rsquo; Plugin are instanciated with the object that is calling them.
          
 »&rsquo;
          
return [p(instance) for p in self.mount.plugins]
  
[/code]

And that&rsquo;s it! Provided the plugin classes are loaded in memory, they will be <strike>magically</strike> executed.

<pre>/Library/Frameworks/Python.framework/Versions/3.2/bin/python3.2 /Users/regis/workspace/plugin/apf.py
Plugin HtmlTransformer produces hello world
Plugin HtmlEmTransformer produces <em>hello world</em>
Plugin HtmlBoldTransformer produces <b>hello world</b>

Process finished with exit code 0
</pre>