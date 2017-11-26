---
id: 1777
title: Appel de service web asynchrone
date: 2011-03-04T00:13:00+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=1777
permalink: /2011/03/appel-de-service-web-asynchrone/
wordbooker_options:
  - 'a:8:{s:18:"wordbook_noncename";s:10:"ead24a67f0";s:18:"wordbook_page_post";s:4:"-100";s:18:"wordbook_orandpage";s:1:"2";s:23:"wordbook_default_author";s:1:"1";s:23:"wordbook_extract_length";s:3:"256";s:19:"wordbook_actionlink";s:3:"300";s:18:"wordbook_attribute";s:0:"";s:29:"wordbooker_status_update_text";s:33:"New blog post :  %title% - %link%";}'
tmac_last_id:
  - ""
dsq_thread_id:
  - "575080099"
categories:
  - Mobile
  - Programmation
tags:
  - Android
  - Talaria
---
Lorsque l&rsquo;on fait un appel web, la méthode <tt>execute()</tt> prend un certain temps. Elle fige l&rsquo;interface graphique.

Pour éviter cela, il faut exécuter cette tâche longue dans un autre thread, et le framework Android offre la clase [AsyncTask](http://developer.android.com/reference/android/os/AsyncTask.html) pour cela.<figure id="attachment_1779" style="width: 348px" class="wp-caption alignnone">

[<img src="http://regis.decamps.info/blog/wp-content/uploads/2011/03/Capture-d’écran-2011-03-04-à-00.05.37.png" alt="Screencast" title="Tâche asynchrone dans Android" width="348" height="508" class="size-full wp-image-1779" srcset="http://regis.decamps.info/blog/wp-content/uploads/2011/03/Capture-d’écran-2011-03-04-à-00.05.37.png 348w, http://regis.decamps.info/blog/wp-content/uploads/2011/03/Capture-d’écran-2011-03-04-à-00.05.37-239x350.png 239w" sizes="(max-width: 348px) 100vw, 348px" />](http://screencast.com/t/FXfjzUyMW)<figcaption class="wp-caption-text">La liste des incidents est maintenant rafraichie de façon asynchrone.</figcaption></figure> 

Le code m&rsquo;a pris une heure:
  
[code]
	  
private class RefreshListTask extends AsyncTask<string , Integer, Boolean> {
		  
private ProgressDialog progressDlg;
		  
private Toast toast;

@Override
		  
protected Boolean doInBackground(String&#8230; params) {
			  
String scope = params[0];
			  
boolean success = false;
			  
try {
				  
success = mProvider.refresh(scope);
			  
} catch (ClientProtocolException e) {
				  
Log.getStackTraceString(e);
				  
String s = getString(R.string.msg\_error\_clientprotocolexception);
				  
toast.setText(s);
				  
success = false;
			  
} catch (IOException e) {
				  
Log.getStackTraceString(e);
				  
String s = e.getLocalizedMessage();
				  
toast.setText(s);
				  
success = false;
			  
} catch (SAXException e) {
				  
Log.getStackTraceString(e);
				  
String s = getString(R.string.msg\_error\_saxparse);
				  
toast.setText(s);
				  
success = false;
			  
} catch (URISyntaxException e) {
				  
// should not happen
				  
Log.e(TAG, e.getMessage());
				  
Log.getStackTraceString(e);
			  
}
			  
return new Boolean(success);
		  
}

@Override
		  
protected void onPreExecute() {
			  
super.onPreExecute();
			  
progressDlg = new ProgressDialog(ListIncidentsActivity.this);
			  
progressDlg.show();
			  
toast = Toast.makeText(ListIncidentsActivity.this, « undefined »,
					  
Toast.LENGTH_LONG);
		  
}

@Override
		  
protected void onPostExecute(Boolean result) {
			  
super.onPostExecute(result);
			  
progressDlg.dismiss();

if (Boolean.TRUE.equals(result)) {
				  
// ListAdapter adapter=new IncidentListAdapter(provider);
				  
mAdapter.notifyDataSetChanged();
				  
if (mProvider.isEmpty()) {
					  
toast.setText(« Aucun incident connu actuellement »);
					  
toast.show();
				  
}
			  
} else {
				  
toast.show();
			  
}
		  
}
	  
}
  
[/code]

Et même chose pour le poste d&rsquo;un nouvel incident.

Le refactoring est obligatoire: le <tt>doInBackground()</tt> n&rsquo;a pas accès aux éléments d&rsquo;interface du thread principal &#8212; Il n&rsquo;y a pas d&rsquo;erreur à la compilation, mais un crash à l&rsquo;exécution.</string>