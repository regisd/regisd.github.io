---
id: 349
disqus_id: 349 http://regis.decamps.info/blog/?p=349
title: Maven est formidable
date: 2006-10-15T23:46:04+00:00
author: Régis
excerpt: "Post technique pour dire que j'aime fichetrement Maven, ce system qui est à Java ce que les gestionnaires de packages sont au distributions linux."
layout: post
guid: http://regis.decamps.info/blog/2006/10/castor-lelement-root-a-une-majuscule/
permalink: /blog/2006/10/maven-est-formidable/

dsq_thread_id:
  - "653614970"
categories:
  - Programmation
tags:
  - HOWTO
  - Build
  - Java
---
#### Maven, le gentoo-portage pour Java

J’ai découvert [Maven](http://www.maven.org/) il y a (trop) peu longtemps.

C’est assez génial, ça offre des archetypes de projet pour aller plus vite, un peu comme les [scaffolds de Ruby on rails](http://wiki.rubyonrails.org/rails/pages/Scaffold). Et ensuite ça gère la dépendence des jars, un peu comme [une bonne distribution linux](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=2&chap=1). 

#### m2settings

Maven stocke les paramètres d’un utilisateur dans un fichier de configuration XML. Aujourd’hui, j’ai décidé de m’amuser à écrire une petite interface graphique pour modifier ce fichier…; Mon projet va s’appeler **m2settings**

#### Quel outil de mapping Java<->XML ?

Je ne me pose pas trop de questions, je vais faire ça en Java. Je commence par le lien JavaBean<->XML. Comme toujours en Java, il y a une pléthore de possibilité:

  * [Apache Xerces](http://xerces.apache.org/xerces2-j/) ne répond pas vraiment, il fait le parsing de XML. Mais moi, j’aurais aussi besoin d’écrire la configuration modifiée
  * Justement [Apache betwixt](http://jakarta.apache.org/commons/betwixt/index.html) fait le contraire: il transforme un Bean en XML.
  * Jato semble répondre, mais manque de documentation et le projet est visiblement <strike>mort</strike> en hibernation
  * [castor](http://www.castor.org/) répond parfaitement à mon besoin (et en plus je l’ai déjà un peu utilisé au boulot)
  * [Xstream](http://xstream.codehaus.org/) fait aussi tout à fait ce que je veux faire, et semble [vraiment très simple à utiliser](http://xstream.codehaus.org/tutorial.html).

Je décide donc de commencer avec Xstream.

#### On démarre avec XStream

Je crée donc un projet Java, compatible avec eclipse
  
`<br />
mvn create<br />
mvn eclipse:eclipse<br />
` 

En pratique, voilà ce que je veux faire:
  
[java]
  
package org.sourceforge.m2settings.beans;

import org.sourceforge.m2settings.XMLBinder;

import junit.framework.TestCase;

public class XMLBinderTest extends TestCase {
	  
private XMLBinder xmlbind;

private static final String XML_PROXY =
		   
« <proxy>\n <active>true</active>\n <protocol>http</protocol>\n <username>user</username>\n <password>secretpwd</password>\n <port>8080</port>\n <host>proxy.intra</host>\n <nonProxyHosts>*.intra</nonProxyHosts>\n <id>myproxy-id</id>\n</proxy>« ;

private static final Proxy proxy =
			  
new Proxy(true, « http », « user »,
			  
« secretpwd », « 8080 », « proxy.intra », « *.intra », « myproxy-id »);;

@Override
	  
protected void setUp() throws Exception {
		  
xmlbind = new XMLBinder();
	  
}

/**
	   
* Test transformation of Proxy bean into XML:
	   
*/
	  
public void testMarshallProxy() {
		  
assertEquals(XML_PROXY, xmlbind.toXML(proxy));
	  
}

/**
	   
* Test transform XML section of <proxy> into Proxy bean
	   
*
	   
*/
	  
public void testUnmarshallProxy() {
		  
Proxy p=(Proxy) xmlbind.fromXML(XML_MIRROR);
		  
assertEquals(proxy, p);
	  
}
  
}
  
[/java]

Pour résoudre mes erreurs de compilation, il me fau vite écrire mon xmlbind qui étant Xstream:
  
[java]
  
package org.sourceforge.m2settings;

import org.sourceforge.m2settings.beans.Mirror;

public class XMLBinder extends XStream {
	  
public XMLBinder() {
		  
// does not require XPP3 library
		  
// uses standard DOM library instead
		  
super(new DomDriver());
		  
this.alias(« proxy », Proxy.class);
	  
}
  
}
  
[/java]

Ce qui m’oblige enfin à écrire le bean en question:
  
[java]
  
package org.sourceforge.m2settings.beans;

/**
   
* <proxy> <active/> <protocol/> <username/> <password/> <port/> <host/>
   
* <nonProxyHosts/> <id/> </proxy> *
   
* @author regis
   
*
   
*/
  
public class Proxy {
	  
/**
	   
* Whether this proxy configuration is the active one.
	   
*/
	  
private boolean active;

private String protocol; // TODO enumeration

private String username;

private String password;

private String port;

private String host;

/**
	   
* The list of non-proxied hosts (usually comma-delimited).
	   
*/
	  
private String nonProxyHosts;

private String id;

public Proxy(Boolean active, String protocol, String username,
			  
String password, String port, String host, String nonProxyHosts,
			  
String id) {
		  
setActive(active);
		  
setProtocol(protocol);
		  
setUsername(username);
		  
setPassword(password);
		  
setPort(port);
		  
setHost(host);
		  
setNonProxyHosts(nonProxyHosts);
		  
setId(id);
	  
}

@Override
	  
public boolean equals(Object obj) {
		  
if (obj.getClass() != Proxy.class)
			  
return false;

Proxy p = (Proxy) obj;
		  
return (active == p.isActive() && protocol == p.getProtocol()
				  
&& username == p.getUsername() && password == p.getPassword()
				  
&& port == p.getPort() && host == p.getHost()
				  
&& nonProxyHosts == p.getNonProxyHosts() && id == p.getId());
	  
}
  
}
  
[/java]

#### Il faut écrite tous ses beans à la main?

Tout cela marche très bien, mais il faut écrire tous les beans…;

Alors je passe à Castor, qui sait faire cela à partir de schéma XML. Et justement, j’ai le [XSD de settings](http://http://maven.apache.org/xsd/settings-1.0.0.xsd).

La suite au prochain épisode!
