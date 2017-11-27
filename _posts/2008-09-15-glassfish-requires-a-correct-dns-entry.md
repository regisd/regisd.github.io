---
id: 587
disqus_id: 587 http://regis.decamps.info/blog/?p=587
title: Glassfish requires a correct DNS entry
date: 2008-09-15T18:48:31+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=587
permalink: /2008/09/glassfish-requires-a-correct-dns-entry/
dsq_thread_id:
  - "189257570"
tmac_last_id:
  - ""
categories:
  - English
  - Informatique
tags:
  - Java
---
In order to start correctly, Glassfish requires that the server has a recorded entry in the DNS.
  
<!--more-->


  
Otherwise, you end up with the following error
  
`<br />
[#|2008-09-15T16:25:30.135+0000|WARNING|sun-appserver9.1|javax.enterprise.system.util|_ThreadID=10;_ThreadName=main;_RequestID=ddeffeec-f4a1-4853-81b1-16717c6c9317;|Unknown host exception - Setting host to localhost|#]</p>
<p>[#|2008-09-15T16:25:52.191+0000|WARNING|sun-appserver9.1|javax.enterprise.resource.corba.ee._INITIALIZING_.rpc.presentation|_ThreadID=10;_ThreadName=main;_RequestID=ddeffeec-f4a1-4853-81b1-16717c6c9317;|"IOP00710208: (INTERNAL) Unable to determine local hostname from InetAddress.getLocalHost().getHostName()"<br />
org.omg.CORBA.INTERNAL:   vmcid: SUN  minor code: 208  completed: No<br />
        at com.sun.corba.ee.impl.logging.ORBUtilSystemException.getLocalHostFailed(ORBUtilSystemException.java:4921)<br />
        at com.sun.corba.ee.impl.logging.ORBUtilSystemException.getLocalHostFailed(ORBUtilSystemException.java:4939)<br />
        at com.sun.corba.ee.impl.orb.ORBImpl.getLocalHostName(ORBImpl.java:1785)<br />
        at com.sun.corba.ee.impl.orb.ORBImpl.set_parameters(ORBImpl.java:699)<br />
        at org.omg.CORBA.ORB.init(ORB.java:337)<br />
        at com.sun.enterprise.util.ORBManager.initORB(ORBManager.java:546)<br />
        at com.sun.enterprise.util.ORBManager.getORB(ORBManager.java:278)<br />
        at com.sun.enterprise.util.ORBManager.getORB(ORBManager.java:289)<br />
        at com.sun.enterprise.server.ondemand.EjbServiceGroup.createORB(EjbServiceGroup.java:506)<br />
        at com.sun.enterprise.server.ondemand.EjbServiceGroup.startORB(EjbServiceGroup.java:432)<br />
        at com.sun.enterprise.server.ondemand.EjbServiceGroup._start(EjbServiceGroup.java:152)<br />
        at com.sun.enterprise.server.ondemand.EjbServiceGroup.start(EjbServiceGroup.java:139)<br />
        at com.sun.enterprise.server.ondemand.ServiceGroup$1.run(ServiceGroup.java:193)<br />
        at java.security.AccessController.doPrivileged(Native Method)<br />
        at com.sun.enterprise.server.ondemand.ServiceGroup.startChildren(ServiceGroup.java:190)<br />
        at com.sun.enterprise.server.ondemand.MainServiceGroup.start(MainServiceGroup.java:58)<br />
        at com.sun.enterprise.server.ondemand.ServerEntryListenerImpl.notifyEntry(ServerEntryListenerImpl.java:85)<br />
        at com.sun.enterprise.server.ondemand.entry.ServerEntryHelper.sendEvent(ServerEntryHelper.java:75)<br />
        at com.sun.enterprise.server.ondemand.entry.ServerEntryHelper.generateStartUpEntryContext(ServerEntryHelper.java:64)<br />
        at com.sun.enterprise.server.ondemand.OnDemandServer.generateEntryContext(OnDemandServer.java:140)<br />
        at com.sun.enterprise.server.ondemand.OnDemandServer.onStartup(OnDemandServer.java:119)<br />
        at com.sun.enterprise.server.PEMain.run(PEMain.java:411)<br />
        at com.sun.enterprise.server.PEMain.main(PEMain.java:338)<br />
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)<br />
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)<br />
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)<br />
        at java.lang.reflect.Method.invoke(Method.java:597)<br />
        at com.sun.enterprise.server.PELaunch.main(PELaunch.java:412)<br />
Caused by: java.net.UnknownHostException: pc2118bb: pc2118bb<br />
        at java.net.InetAddress.getLocalHost(InetAddress.java:1353)<br />
        at com.sun.corba.ee.impl.orb.ORBImpl.getLocalHostName(ORBImpl.java:1783)<br />
        ... 25 more<br />
|#]<br />
[#|2008-09-15T16:25:52.199+0000|SEVERE|sun-appserver9.1|javax.enterprise.system.core|_ThreadID=10;_ThreadName=main;java.lang.RuntimeException: org.omg.CORBA.INTERNAL:   vmcid: SUN  minor code: 208  completed: No;_RequestID=ddeffeec-f4a1-4853-81b1-16717c6c9317;|CORE5081: Exception while creating ORB: [java.lang.RuntimeException: org.omg.CORBA.INTERNAL:   vmcid: SUN  minor code: 208  completed: No]|#]</p>
<p>[#|2008-09-15T16:25:52.200+0000|SEVERE|sun-appserver9.1|javax.enterprise.system.core|_ThreadID=10;_ThreadName=main;java.lang.RuntimeException: Unable to create ORB;_RequestID=ddeffeec-f4a1-4853-81b1-16717c6c9317;|CORE5082: Exception running j2ee services: [java.lang.RuntimeException: Unable to create ORB]|#]<br />
[#|2008-09-15T16:25:52.210+0000|SEVERE|sun-appserver9.1|javax.enterprise.system.core|_ThreadID=10;_ThreadName=main;_RequestID=ddeffeec-f4a1-4853-81b1-16717c6c9317;|Server Startup failed. Exiting...|#]</p>
<p>[#|2008-09-15T16:25:52.211+0000|INFO|sun-appserver9.1|javax.enterprise.system.core|_ThreadID=10;_ThreadName=main;|Server shutdown in progress...|#]</p>
<p>[#|2008-09-15T16:25:52.211+0000|INFO|sun-appserver9.1|javax.enterprise.system.container.web|_ThreadID=10;_ThreadName=main;|WEB0303: Stopping Sun-Java-System/Application-Server.|#]</p>
<p>`
