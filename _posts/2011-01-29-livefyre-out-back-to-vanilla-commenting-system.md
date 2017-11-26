---
id: 1664
title: Livefyre out. Back to Vanilla commenting system.
date: 2011-01-29T15:45:53+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=1664
permalink: /2011/01/livefyre-out-back-to-vanilla-commenting-system/
wordbooker_options:
  - 'a:8:{s:18:"wordbook_noncename";s:10:"bf6b8bd70c";s:18:"wordbook_page_post";s:4:"-100";s:18:"wordbook_orandpage";s:1:"2";s:23:"wordbook_default_author";s:1:"1";s:23:"wordbook_extract_length";s:3:"256";s:19:"wordbook_actionlink";s:3:"300";s:18:"wordbook_attribute";s:0:"";s:29:"wordbooker_status_update_text";s:33:"New blog post :  %title% - %link%";}'
tmac_last_id:
  - ""
dsq_thread_id:
  - "555130484"
categories:
  - English
  - Général
tags:
  - Commenting system
  - OpenID
  - Wordpress
---
[Livefyre commenting system](http://livefyre.com/) promises to make a revolution in blogs by managing their comments with many benefits:

  * more discussion thanks to real-time 
  * more comments and feedback thanks to an easier login mechanism
  * and more trust, with a reputation system accross all blogs

Despite these nice ideas, it has several drawbacks

  * you depend on another site. It can be down or [slow](http://www.google.com/buzz/109077227750219303548/YcUtKWPeWsv/I-have-activated-Livefyre-on-my-wordpress-blog#1285749173086000).
  * you can’t manage user accounts any more
  * the real time technology is likely to be blocked in most companies by their firewalls
  * log in can only be done via what Livefyre provides, i.e. Facebook connect and twitter. [Facebook is blocked in many companies](http://www.cmswire.com/cms/enterprise-20/facebook-number-1-blocked-site-according-to-opendns-report-009938.php) and everybody doesn’t have a twitter account.
  * the thread level is not backed-up in WordPress. The day you quit Livefyre, you lose the hierarchy of the discussion. And some formatting too.
  * it is not open-source software.

That’s why I’m back to Vanilla WordPress comments. 

However, I think it’s good to see who posts, and I have disabled anonymous comments. And I try to make login as smooth as possible. I think OpenID is good, but it needs to be done properly, otherwise [you end up like 37signals](http://www.janrain.com/blogs/janrains-take-37signals-decision-remove-openid-login).

I made a hack on my WordPress theme, in order to have a « one-click » login.
  
[code]
  
< ?php elseif ( get\_option('comment\_registration') && !$user_ID ) : // If registration required and not logged in. ?>

<div id="comment_login" class="messagebox">
  < ?php //regis hack for smooth login if (function_exists('rpx_configured') && rpx_configured() ) { $login_link="javascript:showRPX('rpxlogin');"; printf (rpx_small_buttons()); } // existing code elseif (function_exists('wp_login_url')) { $login_link = wp_login_url(get_permalink()); } else { $login_link = get_option('siteurl') . '/wp-login.php?redirect_to=' . urlencode(get_permalink()); } ?><br /> < ?php printf(__('You must be <a href="%s">logged in to post a comment.’, &lsquo;inove’), $login_link); ?> </div> 
  
  <p>
    [/code]
  </p>
  
  <p>
    As a result, unknown users the the comment box like this.<br /> <a href="http://regis.decamps.info/blog/wp-content/uploads/2011/01/Capture-d’écran-2011-01-29-à-15.36.12.png"><img src="http://regis.decamps.info/blog/wp-content/uploads/2011/01/Capture-d’écran-2011-01-29-à-15.36.12-350x82.png" alt="" title="Comment box for not logged-in users" width="350" height="82" class="alignnone size-medium wp-image-1667" srcset="http://regis.decamps.info/blog/wp-content/uploads/2011/01/Capture-d’écran-2011-01-29-à-15.36.12-350x82.png 350w, http://regis.decamps.info/blog/wp-content/uploads/2011/01/Capture-d’écran-2011-01-29-à-15.36.12.png 612w" sizes="(max-width: 350px) 100vw, 350px" /></a>
  </p>
  
  <p>
    When they click the icons or follow he link they have the <a href="http://regis.decamps.info/blog/2010/10/fini-les-mots-de-passe-sur-wordpress/">Janrain engage login box, like before</a>. My hack simply removes the login page.
  </p>
