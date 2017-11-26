---
id: 2529
disqus_id: 2529 http://regis.decamps.info/blog/?p=2529
title: NullPointerException in PendingIntent.java:195
date: 2012-02-08T00:24:13+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=2529
permalink: /blog/2012/02/nullpointerexception-in-pendingintent-java-195/
dsq_thread_id:
  - "568158891"
categories:
  - Programmation
tags:
  - Android
  - Bug
---
Mobile development is difficult for a number of reasons. But Android framework does not help…; This is my complaint of today (read more in the series [Android bugs](http://regis.decamps.info/blog/tag/android+bug))
  
<!--more-->

If you want to display a notification in the Android status bar, the [the javadoc for NotificationManager](http://developer.android.com/reference/android/app/NotificationManager.html) makes you believe that something like this will work
  
[code]
  
int icon = android.R.drawable.stat\_notify\_chat;
  
CharSequence tickerText = « Bonjour! Tu veux qu’on déjeune ensemble ce midi? »;
  
long when = System.currentTimeMillis();
  
Notification notification = new Notification(icon, tickerText, when);

int id = (int) (Math.random() * 100);
  
notificationManager.notify(id, notification);
  
[/code]

Well, it doesn’t. My text is only the _ticker_, but the notification bar can also be expanded. Hence a title and a message must be defined. Actually, you must add a <tt>LastestEventInfo</tt>
  
[code]
  
NotifActivity context = this;
  
String contentTitle = « You have a new messsage »;
  
String contentText = « regis@example.com (42) »;
  
PendingIntent contentIntent = null
  
notification.setLatestEventInfo(context, contentTitle, contentText, contentIntent);
  
[/code]

So far, so good

[<img src="http://regis.decamps.info/blog/wp-content/uploads/2012/02/device-2012-02-07-233404-150x150.png" alt="" title="Notification ticker" width="150" height="150" class="alignnone size-thumbnail wp-image-2532" />](http://regis.decamps.info/blog/wp-content/uploads/2012/02/device-2012-02-07-233404.png)

Because, I have used a random <tt>id</tt>, the notification will not be updated, and each time this code is executed, it will add a new notification.

[<img src="http://regis.decamps.info/blog/wp-content/uploads/2012/02/device-2012-02-07-233746-150x150.png" alt="" title="Notification bar deployed, two notifications" width="150" height="150" class="alignnone size-thumbnail wp-image-2533" />](http://regis.decamps.info/blog/wp-content/uploads/2012/02/device-2012-02-07-233746.png)

You might wonder what <tt>contentIntent</tt> is. It is a container for starting an activity if the notification is « clicked » (in that case one would expect to display the content of the message). So I quickly create a MessageActivity, and the notification can now be built with:
  
[code]
  
int requestCode=0; // javadoc says « private code curently not used »
  
Intent intent = new Intent(context, MessageActivity.class);
  
PendingIntent contentIntent = PendingIntent.getActivity(context, requestCode, intent, Intent.FLAG\_ACTIVITY\_NEW_TASK);
  
[/code]

Since I’m always complaining, can anyone in the Android team explain why the put fields which are « not used » (sic)?

This eventually works and when we click on the notification, Android opens the MessageActivity
  
[<img src="http://regis.decamps.info/blog/wp-content/uploads/2012/02/device-2012-02-07-235349-150x150.png" alt="" title="MessageActivity opened when notification clicked" width="150" height="150" class="alignnone size-thumbnail wp-image-2534" />](http://regis.decamps.info/blog/wp-content/uploads/2012/02/device-2012-02-07-235349.png)

All this is not very complicated, but it is 14 lines of code just to add one notification. So [I externalized all this in a builder](https://gist.github.com/1762830), which makes things much quicker to use:



But it also introduces a bug. Imagine one of my notification doesn’t need to start an activity, it would make sense to do
  
[code]
  
displayNotification(« That will kill you », MessageActivity.class);
  
[/code]

But Pending intent doesn’t say it doesn’t accept <tt>null</tt> in the doc, nor does it raise a proper <tt>IllegalArgumentException</tt>.

Instead, your application will crash with
  
`<br />
 FATAL EXCEPTION: main<br />
 java.lang.RuntimeException: Unable to start activity ComponentInfo{info.decamps.droid.demo/info.decamps.droid.demo.NotifActivity}: java.lang.NullPointerException<br />
 	at android.app.ActivityThread.performLaunchActivity(ActivityThread.java:1956)<br />
 	at android.app.ActivityThread.handleLaunchActivity(ActivityThread.java:1981)<br />
 	at android.app.ActivityThread.access$600(ActivityThread.java:123)<br />
 	at android.app.ActivityThread$H.handleMessage(ActivityThread.java:1147)<br />
 	at android.os.Handler.dispatchMessage(Handler.java:99)<br />
 	at android.os.Looper.loop(Looper.java:137)<br />
 	at android.app.ActivityThread.main(ActivityThread.java:4424)<br />
 	at java.lang.reflect.Method.invokeNative(Native Method)<br />
 	at java.lang.reflect.Method.invoke(Method.java:511)<br />
 	at com.android.internal.os.ZygoteInit$MethodAndArgsCaller.run(ZygoteInit.java:784)<br />
 	at com.android.internal.os.ZygoteInit.main(ZygoteInit.java:551)<br />
 	at dalvik.system.NativeStart.main(Native Method)<br />
 Caused by: java.lang.NullPointerException<br />
 	at android.content.ComponentName.<init>(ComponentName.java:76)<br />
 	at android.content.Intent.</init><init>(Intent.java:3122)<br />
 	at info.decamps.droid.demo.BaseActivity.displayNotification(BaseActivity.java:37)<br />
 	at info.decamps.droid.demo.NotifActivity.onCreate(NotifActivity.java:12)<br />
 	at android.app.Activity.performCreate(Activity.java:4465)<br />
 	at android.app.Instrumentation.callActivityOnCreate(Instrumentation.java:1049)<br />
 	at android.app.ActivityThread.performLaunchActivity(ActivityThread.java:1920)<br />
</init>`

I think it reveals how poor the javadoc for Android is, and how fragile the framework is. It certainly does not explain why [Google engineers offer the same kind of buggy code](http://how2code.wordpress.com/2011/11/24/fatal-exception-intentservice-due-to-nullpointerexception-on-pendingintent-getactivity/). And it reminds us all that [Android fragmentation is a real problem](http://www.geek.com/articles/mobile/android-developers-see-device-fragmentation-as-huge-problem-2011045/), since [passing <tt>null</tt> apparently worked in the past](http://stackoverflow.com/a/4712111/94363).
