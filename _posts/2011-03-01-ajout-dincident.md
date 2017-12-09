---
id: 1744
disqus_id: 1744 http://regis.decamps.info/blog/?p=1744
title: 'Ajout d’incident'
date: 2011-03-01T23:26:09+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=1744
permalink: /blog/2011/03/ajout-dincident/
wordbooker_options:
  - 'a:9:{s:18:"wordbook_noncename";s:10:"bfbaf41648";s:18:"wordbook_page_post";s:4:"-100";s:18:"wordbook_orandpage";s:1:"2";s:23:"wordbook_default_author";s:1:"1";s:23:"wordbook_extract_length";s:3:"256";s:19:"wordbook_actionlink";s:3:"300";s:26:"wordbooker_publish_default";s:2:"on";s:18:"wordbook_attribute";s:36:"En train de développer une appli...";s:29:"wordbooker_status_update_text";s:33:"New blog post :  %title% - %link%";}'

dsq_thread_id:
  - "555134963"
categories:
  - Projet
tags:
  - Mobile
---
J’ai passé 2h30 à compléter mon application Android pour <http://incidents-transports.com> (qui [a changé de nom aujourd’hui](http://twitter.com/#!/ogirardot/status/42668466376933376))

J’ai ajouté une nouvelle activité pour rapporter un nouvel incident.

Il me fallait donc un référentiel des lignes existantes. Je n’ai pas fait compliqué, et ai codé ce référentiel en dur. Grosso-modo c’et une Hashmap qui fait:
  
`<br />
"Metro" : {"1", "2", "3", "3bis", etc.},<br />
"RER": {"A", "B", "C", "D", "E"}<br />
` 

Puis j’ai défini l’interface utilisateur. Un peu comme Benoît sur iPhone, j’ai mis un premier <tt>Spinner</tt> qui permet de choisir le type de ligne (« Métro », « RER », etc.) et un second qui permet de choisir la ligne exacte.

[code]
			  
Spinner spinnerLineName = (Spinner) findViewById(R.id.SpinnerLineName);

public void onItemSelected(AdapterView< ?> parentAdapter,
					  
View selectedItemView, int position, long id) {
				  
lineType= parentAdapter.getItemAtPosition(position).toString();
				  
String[] linenames = TransportationProvider.getLines(lineType);
				  
ArrayAdapter<string> adapter = new ArrayAdapter</string><string>(
						  
parentAdapter.getContext(), R.layout.spinnerlinename, linenames);
				  
spinnerLineName.setAdapter(adapter);
			  
}
  
[/code]

Et pour finir, j’ai ajouté une méthode <tt>post(Incident incident)</tt> sur mon <tt>IncidentProvider</tt>. 

Dans la journée, Olivier Girardot, m’a donné l’API pour poster. Il m’a fait peur parce que l’ajout d’un incident ne peut se faire qu’en JSON. Mais miracle, Android gère très simplement le JSON. 

```
	  
public static void post(Incident newIncident) throws JSONException {
		  
JSONObject json=new JSONObject();
		  
json.put(« line_name »,newIncident.ligne);
		  
json.put(« reason », newIncident.reason);
		  
json.put(« source », « rds »);//TODO
		  
String req=json.toString();

URI uri= new URI(DEFAULT\_ADD\_SERVICE_URL);

HttpClient httpClient = new DefaultHttpClient();
		  
HttpPost httpPost = new HttpPost(uri);
		  
StringEntity body;
		  
try {
			  
body = new StringEntity(req);
			  
httpPost.setEntity(body);
			  
HttpResponse response = httpClient.execute(httpPost);
		  
} catch (Exception e) {
			  
// TODO Auto-generated catch block
			  
e.printStackTrace();
		  
}
	  
}
  
```
