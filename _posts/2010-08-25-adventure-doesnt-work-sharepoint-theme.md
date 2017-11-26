---
id: 1397
title: 'Adventure (doesn&rsquo;t) work &#8211; SharePoint Theme'
date: 2010-08-25T19:51:41+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=1397
permalink: /2010/08/adventure-doesnt-work-sharepoint-theme/
dsq_thread_id:
  - "189257914"
wordbooker_options:
  - 'a:8:{s:18:"wordbook_noncename";s:10:"668d48937e";s:18:"wordbook_page_post";s:4:"-100";s:18:"wordbook_orandpage";s:1:"2";s:23:"wordbook_default_author";s:1:"1";s:23:"wordbook_extract_length";s:3:"256";s:19:"wordbook_actionlink";s:3:"300";s:18:"wordbook_attribute";s:0:"";s:29:"wordbooker_status_update_text";s:33:"New blog post :  %title% - %link%";}'
tmac_last_id:
  - ""
categories:
  - Informatique
tags:
  - SharePoint
---
Let&rsquo;s put aside the fact that the « Adventure works » theme in SharePoint has justified text everywhere&#8230;

I have been wondering how to change the company in the footer of the page:
  
[<img class="alignnone size-medium wp-image-1398" title="adventure screenshot" src="http://regis.decamps.info/blog/wp-content/uploads/2010/08/adventure_screenshot-350x236.png" alt="Screenshot of the &quot;adventure works&quot; theme" width="350" height="236" srcset="http://regis.decamps.info/blog/wp-content/uploads/2010/08/adventure_screenshot-350x236.png 350w, http://regis.decamps.info/blog/wp-content/uploads/2010/08/adventure_screenshot.png 994w" sizes="(max-width: 350px) 100vw, 350px" />](http://regis.decamps.info/blog/wp-content/uploads/2010/08/adventure_screenshot.png)

Well, it is defined in the master page <tt>OrangeSingleLevel.master</tt> with:
  
`<br />
<asp:Literal runat="server" Text="<%$Resources:cms,masterpages_companyname_linktext%>"/><br />
` 

This mean that modifying the company name requires to:

  * change the master page on each site that uses this theme to use your own resource file, eg. replace <tt>Resources:cms</tt> by <tt>Resources:brandedcms</tt>
  * create a new resource file <tt>brandedcms.resx</tt> and package it in a solution<sup><a href="#footnote_0_1397" id="identifier_0_1397" class="footnote-link footnote-identifier-link" title="as explained by&nbsp;Edgar">1</a></sup>
  * ask a system administrator to deploy this solution

In a word: it&rsquo;s painful. My recommandation: don&rsquo;t follow Microsoft practices.

I think the best practice is to place such variables in a list, so that anyone can edit them ; resource file should be used only to store (language dependant) constants.

<ol class="footnotes">
  <li id="footnote_0_1397" class="footnote">
    as <a href="http://blog.nftinside.com/post/2009/03/11/CustomSiteActionxml-pour-site-de-publication-%3A-fichier-de-ressource-obligatoire">explained by Edgar</a> [<a href="#identifier_0_1397" class="footnote-link footnote-back-link">&#8617;</a>]
  </li>
</ol>