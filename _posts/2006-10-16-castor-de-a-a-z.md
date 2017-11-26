---
id: 350
disqus_id: 350 http://regis.decamps.info/blog/?p=350
title: 'Castor: de A à Z'
date: 2006-10-16T21:18:02+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/2006/10/castor-de-a-a-z/
permalink: /2006/10/castor-de-a-a-z/
dsq_thread_id:
  - "189256698"
tmac_last_id:
  - ""
categories:
  - Informatique
---
#### Génération des beans

En suivant la convention de maven, j’ai placé mon XSD dans <tt>main/castor</tt>.

Ma fonction <tt>toXML()</tt> fait maintenant appel au Marshaller de Castor:
  
[java]
	  
public String toXML(Object obj) throws IOException, MarshalException, ValidationException {
		  
StringWriter w = new StringWriter();
		  
Marshaller marshaller = new Marshaller(w);
		  
marshaller.marshal(obj);
		  
return w.toString();
	  
}
  
[/java]

et le Unmarshaller aussi, qui pour l’occasion ne sait plus travailler qu’avec un objet &lsquo;Settings’ (d’où son changement de nom)
  
[java]
	  
public Settings loadSettings(Reader xmlSettingsReader) throws MarshalException, ValidationException {
		  
Unmarshaller um=new Unmarshaller(Settings.class);
		  
return (Settings) um.unmarshal(xmlSettingsReader);
	  
}
  
[/java]

#### Petit problème avec Castor

Je relance mes tests unitaires (<tt>mvn test</tt>). Et bam, tout est cassé. Castor n’indente pas le xml comme XStream. Ce n’est rien: je change mes constantes de test.

Je relance mes tests et rebam. Mon problème c’est que [Castor sérialise l’élément racine avec une majuscule](http://permalink.gmane.org/gmane.comp.java.castor.user/4226).
  
Par exemple, au lieu d’avoir
  
[xml]
  
<settings><localRepository/></settings>
  
[/xml]
  
Castor génère à la place
  
[xml]
  
<Settings><localRepository/></Settings>
  
[/xml]

J’ai contourné le problème de la façon suivante
  
[java]
	  
public String toXML(Object obj) throws IOException, MarshalException, ValidationException {
		  
StringWriter w = new StringWriter();
		  
Marshaller marshaller = new Marshaller(w);
		  
//FIXME Castor generates <Settings> instead of <settings>
		  
marshaller.setRootElement(« settings »);
		  
marshaller.marshal(obj);
		  
return w.toString();
	  
}
  
[/java]

Cepedant, j’aimerais bien comprendre ce qui se passe. [À suivre…;](http://comments.gmane.org/gmane.comp.java.castor.user/4226?set_lines=100000&set_cite=hide)
