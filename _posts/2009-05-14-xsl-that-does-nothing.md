---
id: 881
disqus_id: 881 http://regis.decamps.info/blog/?p=881
title: xsl that does nothing
date: 2009-05-14T21:31:51+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=881
permalink: /blog/2009/05/xsl-that-does-nothing/

categories:
  - Programmation
tags:
  - XML
---
Well, it does one thing: it writes the input XML as is:
  
[code]
  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

<xsl:template match="/">
  
<xsl:copy-of select="." />
  
</xsl:template>

</xsl:stylesheet>
  
[/code]
