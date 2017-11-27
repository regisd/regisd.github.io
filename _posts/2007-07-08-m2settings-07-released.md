---
id: 435
disqus_id: 435 http://regis.decamps.info/blog/?p=435
title: m2settings 0.7 released
date: 2007-07-08T16:58:01+00:00
author: Régis
excerpt: "J'ai apporté quelques modifications dans mon utilitaire pour éditier le fichier settings.xml de Maven et en profite pour sortir une nouvelle version."
layout: post
guid: http://regis.decamps.info/blog/2007/07/m2settings-07-released/
permalink: /blog/2007/07/m2settings-07-released/
tmac_last_id:
  - ""
dsq_thread_id:
  - "902029814"
categories:
  - Programmation
tags:
  - Java
  - M2settings
  - Maven
---
J’ai touché quelques petits trucs dans [m2settings](http://code.google.com/p/m2settings/), et j’en profite pour publier une nouvelle version ([télécharger](http://m2settings.googlecode.com/files/m2settings-0.7-one-jar.jar)). Celle-ci génère un <tt>settings.xml</tt> bien plus lisible.

Voici par exemple ce que l’on peut obtenir en quelques clic:
  
`</p>
<pre>
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns="http://maven.apache.org/POM/4.0.0">
    <interactiveMode>true</interactiveMode>
    <offline>false</offline>
    <proxies/>
    <servers/>
    <mirrors>
        <mirror>
            <mirrorOf>central</mirrorOf>
            <name>Sateh</name>
            <url>http://maven.sateh.com/repository</url>
            <id>sateh.com</id>
        </mirror>
        <mirror>
            <mirrorOf>codehaus</mirrorOf>
            <name>Codehaus MOJO</name>
            <url>http://repository.codehaus.org/</url>
            <id>codehaus-mirror</id>
        </mirror>
    </mirrors>
    <profiles>
        <profile>
            <activation>
                <activeByDefault>true</activeByDefault>
                <file/>
            </activation>
            <properties>
                <hello>world</hello>
            </properties>
            <repositories>
                <repository>
                    <snapshots>
                        <enabled>true</enabled>
                        <checksumPolicy>warn</checksumPolicy>
                    </snapshots>
                    <id>springframework.org</id>
                    <name>Springframework Maven SNAPSHOT Repository</name>
                    <url>http://static.springframework.org/maven2-snapshots/</url>
                    <layout>default</layout>
                </repository>
            </repositories>
            <pluginRepositories/>
            <id>rds</id>
        </profile>
        <profile>
            <activation>
                <activeByDefault>false</activeByDefault>
                <jdk>sun</jdk>
                <file/>
            </activation>
            <id>sun</id>
        </profile>
    </profiles>
</settings>
</pre>
<p>`
