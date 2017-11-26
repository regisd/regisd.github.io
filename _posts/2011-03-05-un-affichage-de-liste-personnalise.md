---
id: 1787
disqus_id: 1787 http://regis.decamps.info/blog/?p=1787
title: Un affichage de liste personnalisé
date: 2011-03-05T20:00:24+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=1787
permalink: /blog/2011/03/un-affichage-de-liste-personnalise/
wordbooker_options:
  - 'a:9:{s:18:"wordbook_noncename";s:10:"838182c9df";s:18:"wordbook_page_post";s:4:"-100";s:18:"wordbook_orandpage";s:1:"2";s:23:"wordbook_default_author";s:1:"1";s:23:"wordbook_extract_length";s:3:"256";s:19:"wordbook_actionlink";s:3:"300";s:26:"wordbooker_publish_default";s:2:"on";s:18:"wordbook_attribute";s:0:"";s:29:"wordbooker_status_update_text";s:33:"New blog post :  %title% - %link%";}'
wordbooker_thumb:
  - http://regis.decamps.info/blog/wp-content/uploads/2011/03/device-233x350.png
wordbooker_extract:
  - |
    L'API de incidents-transports a évolué est indique maintenant l'identifiant de la ligne sur lequel l'incident a eu lieu. Je tire parti de cette nouvelle information, en affichant le pictogramme de la ligne concernée dans la liste.
    
    
    
    Pour cela, il ...
tmac_last_id:
  - ""
dsq_thread_id:
  - "568012203"
categories:
  - Programmation
tags:
  - Android
  - Talaria
---
[L’API de incidents-transports](http://www.incidents-transports.com/dev/) a évolué et indique maintenant l’identifiant de la ligne sur lequel l’incident a eu lieu. Je tire parti de cette nouvelle information, en affichant le pictogramme de la ligne concernée dans la liste. <figure id="attachment_1789" style="width: 233px" class="wp-caption alignnone">

[<img src="http://regis.decamps.info/blog/wp-content/uploads/2011/03/device-233x350.png" alt="Capture d&#039;écran montrant l&#039;Adapter au travail" title="Liste des incidents avec Custom Adapter" width="233" height="350" class="size-medium wp-image-1789" srcset="http://regis.decamps.info/blog/wp-content/uploads/2011/03/device-233x350.png 233w, http://regis.decamps.info/blog/wp-content/uploads/2011/03/device.png 320w" sizes="(max-width: 233px) 100vw, 233px" />](http://regis.decamps.info/blog/wp-content/uploads/2011/03/device.png)<figcaption class="wp-caption-text">L'Adapter surchargé permet de construire un affichage plus avancé</figcaption></figure> 

Pour cela, il faut écrire un <tt>ListAdapter</tt>. Evidement, le mien étend le <tt>ArrayAdapter</tt>, et surcharge la méthode <tt>getView(...)</tt>.

[code]
	  
@Override
	  
public View getView(int position, View convertView, ViewGroup parent) {
		  
Incident incident = getItem(position);

View view = super.getView(position, convertView, parent);
		  
TextView textViewName = (TextView) view
				  
.findViewById(R.id.TextViewIncidentListItemLine);
		  
TextView textViewStatus = (TextView) view
				  
.findViewById(R.id.TextViewIncidentListItemStatus);
		  
textViewName.setText(incident.ligne);
		  
textViewStatus.setText(incident.status +  » @  »
				  
+ Incident.DATEFORMAT_HHMM.format(incident.lastModified));

ImageView imageViewStatus = (ImageView) view
				  
.findViewById(R.id.ImageViewIncidentListItemStatus);
		  
if (Incident.STATUS_CURRENT.equals(incident.status)) {
			  
Drawable drawable = getContext().getResources().getDrawable(
					  
android.R.drawable.ic\_dialog\_alert);
			  
imageViewStatus.setImageDrawable(drawable);
		  
} else if (Incident.STATUS_ENDED.equals(incident.status)) {
			  
Drawable drawable = getContext().getResources().getDrawable(
					  
R.drawable.check\_ok\_green);
			  
imageViewStatus.setImageDrawable(drawable);
		  
}

ImageView imageViewPicto = (ImageView) view
				  
.findViewById(R.id.ImageViewIncidentListItemPicto);
		  
// sinon reprend l’image de la ligne précédente
		  
imageViewPicto.setImageBitmap(null);
		  
if (incident.lineId > 0) {
			  
Transportation transport = TransportationProvider.TRANSPORTS
					  
.get(incident.lineId);
			  
if (transport != null && StringUtil.isNotEmpty(transport.picto)) {
				  
try {
					  
FileInputStream inputStream = getContext().openFileInput(
							  
transport.picto);
					  
Bitmap bm = BitmapFactory.decodeStream(inputStream);
					  
imageViewPicto.setImageBitmap(bm);
					  
//imageViewPicto.setBackgroundColor(android.R.color.darker_gray);
				  
} catch (FileNotFoundException e) {
					  
Log.w(TAG, « File not found: » + transport.picto);
				  
}
			  
}
		  
}
		  
return view;
	  
}
  
[/code]
