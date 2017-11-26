---
id: 389
disqus_id: 389 http://regis.decamps.info/blog/?p=389
title: All-in-one jar
date: 2007-02-03T19:54:56+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/2007/02/all-in-one-jar/
permalink: /blog/2007/02/all-in-one-jar/
dsq_thread_id:
  - "189256786"
tmac_last_id:
  - ""
categories:
  - English
  - Programmation
tags:
  - Java
---
The more I use Maven, the more I think it simplifies the developer’s life and the packaging task.

The packaging task? Not so much, in fact. If you write a mavenized Java application, you can easily build the jar with « mvn package ». But the application probably won’t run as such. To run the jar, the end user needs to have the libraries the application depends upon, and sets his CLASSPATH correctly. You cannot expect that from end-users.

That’s why I think the jar packaging is incomplete. You still need to provide more jars, and something to run the whole thing. Well that’s not Maven’s fault but the way Java is designed.

There are two elegant solutions to this. The first one is to provide a webstart descriptor, and use maven to deploy all required jars on the same server.

The other solution is to flattern the jar, to make a all-in-one jar. [Minijar](http://mojo.codehaus.org/minijar-maven-plugin/ueberjar-mojo.html) can do this for you, and there is even a maven plugin. 

I have only added a dependency on my pom:
  
[xml]
  
<dependency>
	  
<groupid>org.codehaus.mojo</groupid>
	  
<artifactid>minijar-maven-plugin</artifactid>
	  
<version>1.0-alpha-1</version>
  
</dependency>
  
[/xml]

And now
  
`<br />
mvn minijar:ueberjar<br />
` 
  
produces an artifact which contains all my code+librairies.

That’s great but it does not work well. Running
  
`<br />
java -jar myapp-ueberjar.jar<br />
` 

gives me an « Invalid or corrupt jarfile ».

[Vafer](http://vafer.org/blog/20070124132358/trackback/), minijar:ueberjar is great but I think documentation is terribly lacking. I could not get more than a [page which shows the usage](https://svn.codehaus.org/mojo/trunk/mojo/minijar-maven-plugin//src/site/apt/usage.apt). 

What should I put in my POM to define the MANIFEST, and in particular to set the Main-Class?
