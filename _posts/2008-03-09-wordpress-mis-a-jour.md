---
id: 486
disqus_id: 486 http://regis.decamps.info/blog/?p=486
title: WordPress mis à jour
date: 2008-03-09T12:00:37+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/2008/03/wordpress-mis-a-jour/
permalink: /blog/2008/03/wordpress-mis-a-jour/
tmac_last_id:
  - ""
categories:
  - Brève
  - Général
tags:
  - Wordpress
---
Je viens de réaliser une mise à jour de WordPress. Cette nouvelle version corrige des failles de sécurité.

J’ai de nouveau appliqué le patch relatif au bug [#4287](http://trac.wordpress.org/ticket/4287) (le HTML généré est invalide: les liens dans les widgets ont tous le même identifiant id= »link »). 

Edit: unfortunately, the patch should be applied on wp\_widget\_links(), which is not a pluggable function. Andrew sugguests to [create a custom widget identical to the Links widget, but without the bug](http://www.vayanis.com/2007/08/09/wordpress-22s-link-widget-validation-errors/) (my suggestion is to write a [widget-plugin](http://automattic.com/code/widgets/plugins/) rather than defining the widget in the theme) .
