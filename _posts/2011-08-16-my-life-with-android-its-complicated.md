---
id: 2160
disqus_id: 2160 http://regis.decamps.info/blog/?p=2160
title: 'My life with Android: « it’s complicated »'
date: 2011-08-16T07:25:53+00:00
author: Régis
excerpt: Mobile development on Android is one of the most callenging thing I have done so far. This is a limited compilation of the problems I have encountered on a simple application...
layout: post
guid: http://regis.decamps.info/blog/?p=2160
permalink: /blog/2011/08/my-life-with-android-its-complicated/
wordbooker_options:
  - 'a:10:{s:18:"wordbook_noncename";s:10:"f4afb31bd7";s:18:"wordbook_page_post";s:4:"-100";s:18:"wordbook_orandpage";s:1:"2";s:23:"wordbook_default_author";s:1:"1";s:23:"wordbook_extract_length";s:3:"256";s:19:"wordbook_actionlink";s:3:"300";s:18:"wordbook_attribute";s:0:"";s:29:"wordbooker_status_update_text";s:33:"New blog post :  %title% - %link%";s:23:"wordbook_scheduled_post";s:1:"1";s:17:"wordbook_new_post";s:1:"1";}'
tmac_last_id:
  - "162978336623165440"
dsq_thread_id:
  - "556925262"
categories:
  - English
  - Programmation
tags:
  - Android
  - Best practice
  - Bug
---
[<img class="alignright size-thumbnail wp-image-2162" title="it-s-complicated-facebook-status" src="/blog/wp-content/uploads/2011/07/it-s-complicated-when-facebook-status-can-t-describe-you-part-1-25473565-150x150.jpg" alt="Facebook screenshot: relationship status: it's complicated" width="150" height="150" />](/blog/wp-content/uploads/2011/07/it-s-complicated-when-facebook-status-can-t-describe-you-part-1-25473565.jpg)

Mobile development is difficult: there is not much memory, the CPU is low, network connection is limited, there are different screen sizes and hardware capabilities to take care of, etc. Android aims at helping on these topics, but the life of an Android developer is still not a paradise…;

### Some classes pretend to help, but just don’t

The framework encourages you to use classes that supposely simplify complex development.

For instance, [AsyncTask](http://developer.android.com/reference/android/os/AsyncTask.html) « allows to perform background operations and publish results on the UI thread without having to manipulate threads and/or handlers. »

However, there are limitations or other problems virtually impossible to solve. For instance with AsyncTask, [the application crash when the orientation is changed](http://stackoverflow.com/questions/1111980/how-to-handle-screen-orientation-change-when-progress-dialog-and-background-threa).

<pre>Activity has leaked window PhoneWindow$DecorView that was originally added here 
E/WindowManager(  244):</pre>

Eventually, I have found that only [services](http://developer.android.com/reference/android/app/Service.html) can correctly handle long running operations. But they are more complicated to code.

### The XML nightmare

With XML, you can build a software that perfectly compiles, and crash at runtime. Sometime not entering in your own code at all. 

In the worse situation, it can crash the OS without letting a second to run a debugger. For instance, when I was going to Settings > Account and Sync > Add account, the phone crashed and rebooted. Why? Because I forgot the `smallIcon` attribute in the `authentificator.xml` (similar to this [Resources$NotFoundException: String resource ID #0x0](http://stackoverflow.com/questions/5240866/getting-an-exception-when-trying-to-add-an-account-in-android/5286416)).

### The recycling in adapters

A <tt>ListAdapter</tt> connects data to rows representing this data in a <tt>ListView</tt>. As I already mentioned, resources are limited, so it is a good practice to recycle a former view rather than creating a new one. As such, when the user scrolls down the list, instead of creating new views for the new rows, the views are recycled from rows that are not visible anymore. This is usually performed with this nippet of code:
  
```
if (convertView == null) {
			  
view = mInflater.inflate(R.layout.mylayout, parent, false);
		  
} else {
			  
view = convertView;
		  
}
```

But this can lead to strange beahaviours or things difficult to debug. For instance, if a list view has a checkbox, this code is incorrect
  
```
checkBox.setChecked(myDataItem.isActve);
  
checkBox.setOnCheckedChangeListener(new CompoundButton.OnCheckedChangeListener() {
  
@Override
  
public void onCheckedChanged(CompoundButton buttonView,
  
boolean isChecked) {
  
myDataItem.isActive = isChecked)
  
}
  
});
```

With this code, the checkboxes are checking and unchecking themselves randomly when the user scrolls the list. Whereas this code is correct. Can you spot the difference and explain what happens?

```
checkBox.setOnCheckedChangeListener(new CompoundButton.OnCheckedChangeListener() {
  
@Override
  
public void onCheckedChanged(CompoundButton buttonView,
  
boolean isChecked) {
  
myDataItem.isActive = isChecked)
  
}
  
});
  
checkBox.setChecked(myDataItem.isActve);
```

In the first case [setChecked() triggers the onClickListener defined in a a data element which is now hidden](http://stackoverflow.com/questions/5444355/android-listview-with-checkbox-problem/5446929#5446929).

### <tt>SyncAdapter</tt> requires <tt>AccountAuthentificator</tt> and <tt>ContentProvider</tt>

A <tt>SyncAdapter</tt> is used to synchronize Internet data with a <tt>ContentProvider</tt>. This is what gives you a synchronized address book, a synchronized list of emails, synchronized tweets, etc.

In all this examples, it is require to provide an <tt>AccountAuthentificator</tt>. However, I think this account authentificator is irrelevant for synchronizing public data, like weather forecast. 

Well, the android framework thinks differently. It is mandatory to have these 3 pieces: <tt>SyncAdapter</tt>, <tt>AccountAuthentificator</tt>, <tt>ContentProvider</tt>. If one is missing, the _android system_ might crash when you go in the Settings screen, and the phone will reboot without little to no debug message:

<pre>EXCEPTION IN SYSTEM PROCESS.  System will crash.
E AndroidRuntime: java.lang.NullPointerException</pre>

If you think this one sucks too, please star [issue 5009](http://code.google.com/p/android/issues/detail?id=5009 "Added account causes system crash and reboot of 'Accounts & Settings'").
