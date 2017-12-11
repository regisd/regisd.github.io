---
id: 2978
disqus_id: 2978 http://regis.decamps.info/blog/?p=2978
title: 'Android SQLLiteOpenHelper n’aide pas vraiment'
date: 2012-10-11T21:37:11+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=2978
permalink: /blog/2012/10/android-databasehelper-naide-pas-vraiment/
al2fb_facebook_link_id:
  - 1065233209_4106220368249
al2fb_facebook_link_time:
  - 2012-10-11T19:37:18+00:00
al2fb_facebook_link_picture:
  - post=http://regis.decamps.info/blog/?al2fb_image=1
dsq_thread_id:
  - "881453464"
categories:
  - Dev
tags:
  - Android
---
Arg! Je viens de découvrir avec horreur que `<a href="http://developer.android.com/reference/android/database/sqlite/SQLiteOpenHelper.html">SQLLiteOpenHelper</a>` n’était pas _thread-safe_.

Plus précisément, lorsque l’on fait un `<a href="http://developer.android.com/reference/android/content/ContentProvider.html">ContentProvider</a>`, on a envie d’écrire quelque chose comme:
  
```
@Override
	  
public Cursor query(Uri uri, String[] projection, String selection,
			  
String[] selectionArgs, String sortOrder) {
		  
SQLiteDatabase db = mDatabaseHelper.getReadableDatabase();
		  
final String groupBy = null;
		  
final String having = null;
		  
switch (sUriMatcher.match(uri)) {
		  
case URI\_MATCH\_1:
			  
return db.query(TABLE1, projection,
					  
selection, selectionArgs, groupBy, having, sortOrder);
		  
default:
			  
throw new IllegalArgumentException(« Unknown URI  » + uri);
		  
}
	  
}
	  
}
``` 

Hé bien, cela peut lever une exception 

```
10-11 21:17:24.624: E/AndroidRuntime(29832): Caused by: java.lang.IllegalStateException: Cannot perform this operation because the connection pool has been closed.
```

En fait, la base qu’on manipule est fermée d’office lorsque

  * un autre thread appelle `getWritableDatabase()`. 
  * un autre thread appelle `close()` sur une autre instance de database, obtenue par un autre `SQLLiteOpenHelper`

Conclusion:

  * Réutiliser le même `SQLLiteOpenHelper`
  * N’utiliser que `getWritableDatabase()`

Plus de détails dans un article en anglais [Database pitfalls](http://www.ragtag.info/2011/feb/1/database-pitfalls/).
