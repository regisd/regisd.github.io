---
id: 1739
title: Les incidents du réseau RATP sur votre mobile!
date: 2011-03-01T22:53:00+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=1739
permalink: /2011/03/les-incidents-du-reseau-ratp-sur-votre-mobile/
wordbooker_options:
  - 'a:8:{s:18:"wordbook_noncename";s:10:"bfbaf41648";s:18:"wordbook_page_post";s:4:"-100";s:18:"wordbook_orandpage";s:1:"2";s:23:"wordbook_default_author";s:1:"1";s:23:"wordbook_extract_length";s:3:"256";s:19:"wordbook_actionlink";s:3:"300";s:18:"wordbook_attribute";s:0:"";s:29:"wordbooker_status_update_text";s:33:"New blog post :  %title% - %link%";}'
tmac_last_id:
  - ""
dsq_thread_id:
  - "558926068"
categories:
  - Applications
  - Mobile
  - Programmation
tags:
  - Android
  - Talaria
---
Vous avez sans doute entendu parler des [menaces de la RATP](http://www.readtfb.net/2011/02/20/incidentsratp-la-lettre/) contre le site [http://incidents-ratp.com/](http://incidents-transports.com/) qui a pour but de

> Vous donner l’accès librement et gratuitement aux informations concernant vos transports en communs 

Quoi qu’il en soit, [Benoît est en train de développer une application iPhone](http://twitter.com/#!/benoitclouet/status/41998214974554112) pour accéder plus rapidement aux informations trafic des transports en commun.

Et [il m’a suggéré de faire la même chose pour Android](http://www.google.com/buzz/regis.decamps/ftg9BFBKNbG). J’ai plein de trucs importants à faire, mais une envie soudaine de coder m’a pris.

Hier, j’ai commencé. Et il me paraît intéressant pour tous les développeurs en herbe de dire combien un tel développement consomme de temps. Hier, j’ai donc passé 4 heures pour traiter les tâches suivantes.

### Découvrir le service web

J’ai d’abord regardé l’[API du service](http://incidents-transports.com/dev). C’est encore un peu sommaire. 

La liste des incidents est obtenu par un appel REST, dans le format de son choix (XML ou json).

Je me dis que Java permettra de _parser_ sans problème le XML.

(15 min)

### Préparer mon environnement

Ensuite, je perds un peu de temps à réinitialiser mon Eclipse avec le dernier plugin de développement Android.

Pas vraiment utile, vu que je vais me baser sur une ancienne version du SDK, afin de couvrir le maximum de matériels.

(15 min)

### Initier un nouveau projet

Ça s’est l’affaire d’un ou deux clics 🙂
  
J’utilise [bitbucket](https://bitbucket.org/) pour outiller ma gestion de configuration.

Je laisse l’interface vide pour le moment.

(10 min)

### Faire le client de service web

Je crée ensuite un modèle objet pour un <tt>Incident</tt>. Il est très simple. Oui, j’utilise des variables de classe publiques. Je n’ai jamais compris la convention des _getters_&_setters_. Alors, pour un développement mobile, j’évite les lourdeurs. (30 min)

[code]
  
public class Incident {
	  
int uid;

String status;
	  
String ligne;

int votePlus;
	  
int voteEnded;
	  
int voteMinus;

String reason;

Date lastModified;
  
}
  
[/code]

Il me faut évidemment un client du service web. Cela se fait très simplement avec Apache HttpClient qui fait partie du framework Android. (20 min).

[code]
  
public class IncidentProvider {
	  
private static final String TAG = « IncidentProvider »;
	  
public void refresh(URI uri) throws ClientProtocolException, IOException,
			  
SAXException {
		  
HttpClient httpClient = new DefaultHttpClient();
		  
HttpGet httpGet = new HttpGet(uri);
		  
HttpResponse response = httpClient.execute(httpGet);
		  
HttpEntity entity = response.getEntity();
		  
if (entity != null) {
			  
refresh(entity.getContent());
		  
}
	  
}
  
[/code]

Je passe ensuite au _mappage_ du résultat dans des objets <tt>Incident</tt>. Je pensais au début faire du castor/Jaxb/etc. mais c’est trucs sont trop lourds pour un mobile. De base dans le framework, on a du SAX:
  
[code]
  
public class IncidentProvider implements ContentHandler {
	  
private Incident mIncident;
	  
ArrayList@lt;incident@gt; incidents;

/\* buffers \*/
	  
private StringBuffer mBuffer;
  
[…;]
	  
public void refresh(InputStream in) throws IOException, SAXException {
			  
Xml.parse(in, Encoding.UTF_8, this);
	  
}

public void startDocument() throws SAXException {
		  
mIncidents = new ArrayList@lt;Incident@gt;();
	  
}

public void startElement(String uri, String name, String qName,
			  
Attributes atts) throws SAXException {
		  
if (« resource ».equals(name)) {
			  
mIncident = new Incident();
		  
}
		  
mBuffer = new StringBuffer();
	  
}

public void endElement(String uri, String name, String qName)
			  
throws SAXException {
		  
if (« status ».equals(name)) {
			  
mIncident.status = mBuffer.toString();
		  
} else if (« vote_plus ».equals(name)) {
			  
mIncident.setVotePlus(mBuffer.toString());
		  
} else if (« vote_minus ».equals(name)) {
			  
mIncident.setVoteMinus(mBuffer.toString());
		  
} else if (« vote_ended ».equals(name)) {
			  
mIncident.setVoteEnded(mBuffer.toString());
		  
} else if (« reason ».equals(name)) {
			  
mIncident.reason = mBuffer.toString();
		  
} else if (« line ».equals(name)) {
			  
mIncident.ligne = mBuffer.toString();
		  
} else if (« last\_modified\_time ».equals(name)) {
			  
mIncident.setLastModified(mBuffer.toString());
		  
} else if (« uid ».equals(name)) {
			  
mIncident.setUID(mBuffer.toString());
		  
} else if (« resource ».equals(name)) {
			  
mIncidents.add(mIncident);
		  
}
	  
}

public void characters(char chars[], int start, int length)
			  
throws SAXException {
		  
mBuffer.append(chars, start, length);
	  
}
  
[/code]
  
(1h avec les tests unitaires et l’écriture des _setters_ dont j’ai besoin)

### Affichage dans une liste

Je modifie ensuite l’interface pour ajouter une <tt>ListView</tt> qui présentera les résultats.

C’est là dessus que j’ai passé le plus de temps (2h). J’ai d’abord cru que je devrais écrire mon propre <tt>Adapter</tt>, alors que j’ai finalement pu utiliser le <tt>ArrayAdapter</tt>. Ensuite, j’ai mal compris comment celui-ci utilisait le <tt>TexteView</tt>.

Et c’est le « bonheur » du développement XML. Il faut exécuter dans l’émulateur (plusieurs secondes à chaque fois) pour avoir un message d’erreur pas toujours très clair…; ou bien une appli qui fonctionne mais n’affiche rien. 

### In fine

Mais [j’ai fini par faire marcher cette partie](http://www.google.com/buzz/regis.decamps/hm5mX2tu7ie).
  
[<img alt="Copie d&#039;écran" src="http://lh6.googleusercontent.com/_V9wavuJ6Kso/TWw1ApL89XI/AAAAAAAAYQ8/CTgrWzJrL-E/Capture%20d%E2%80%99e%CC%81cran%202011-03-01%20a%CC%80%2000.46.27.png" title="liste des Incidents" class="alignnone" width="336" height="494" />](http://www.google.com/buzz/regis.decamps/hm5mX2tu7ie)

Et ce soir, j’avais mieux à faire 😉
