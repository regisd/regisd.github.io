---
id: 109
disqus_id: 109 http://regis.decamps.info/blog/?p=109
title: Makefile LaTeX
date: 2005-06-19T19:43:48+00:00
excerpt: "J'ai retrouvé mon Makefile qui permet de produire rapidement des documents écrits en LaTeX."
layout: post
guid: http://regis.decamps.free.fr/wordpress/?p=109
permalink: /blog/2005/06/makefile-latex/

dsq_thread_id:
  - "671540774"
categories:
  - Dev
tags:
  - Build system  
---
* \`make\` construit le Postscript (Requires latex, glosstex, bibtex, makeindex).
  
* \`make pdf\` construit le PDF (il est possible de préciser make nomdefichier.pdf) (Also requires For PDF, also requires pstopdf, thumbpdf.)
  
* \`make pub\` construit le PDF et le copie (avec \`scp\`) sur un répertoire distant. (For publication, requires scp and the corresponnding RSA key for total comfort)

```
 # Makefile for latex project, with glossary, index, and bibliography.
 # Use this Makefile with GNU make to build your PS/PDF document from 
 # .tex sources. See bellow for details.
 
 # 
 # This program is free software; you can redistribute it and/or
 # modify it under the terms of the GNU General Public License
 # as published by the Free Software Foundation; either version 2
 # of the License, or (at your option) any later version.
 #
 # This program is distributed in the hope that it will be useful,
 # but WITHOUT ANY WARRANTY; without even the implied warranty of
 # MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 # GNU General Public License for more details.
 #
 # You should have received a copy of the GNU General Public License
 # along with this program; if not, write to the Free Software
 # Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.
 #
 # Copyright (C) 2003 - Regis Decamps &lt;decamps @ users.sf.net>
 
 ## SYNOPSIS.
 # You sources must compile with latex.
 # Namely, all graphics must be in PS/EPS format.
 # 
 # =make= build the PS.
 # =make pdf= builds the PDF.
 # =make pub= builds the PDF and copies the PDF to you remote directory
 #
 # Requires latex, glosstex, bibtex, makeindex.
 # For PDF, also requires pstopdf, thumbpdf.
 # For publication, requires scp.
 
 
 # This is the name of the project (i.e. the source is PROJECT.tex
 # and the PS will be called PROJECT.ps
 # If you don't define this, you can still use =make report.pdf= for instance
 PROJECT= report
 # Where the PDF should be copied with =make pub=
 PUBLISH= rs0.cs.man.ac.uk:public_html/pub
 	
 
 # Defines commands. You don't need to change this on a standard Unix
 # distribution.
 LATEX= latex
 DVI2PS= dvips -Ppdf -G0 
 PS2PDF= ps2pdf -dPDFsettings=/prepress 
 GLOSSTEX= glosstex
 MAKEINDEX= makeindex
 BIBTEX= bibtex
 THUMBPDF=thumbpdf
 
 ## You don't need to look what's further.
 TEXAUX = *.out *.aux *.lof *.lot *.log *.toc *.glo 
 GLOSSTEXAUX = *.gxs *.gxg
 MAKEINDEXAUX = *.glg *.glx *.ilg *.ind *.idx
 BIBTEXAUX = *.bbl *.blg
 THUMBPDFAUX = *.tpt
 
 all: ${PROJECT}.ps
 ps: ${REPORT}.ps
 pdf: ${REPORT}.pdf
 	
 clean: 
 	rm ${TEXAUX} ${GLOSSTEXAUX} ${MAKEINDEXAUX}  ${PROJECT}.ps ${REPORT}.pdf ${BIBTEXAUX} ${THUMBPDFAUX} *.dvi *~
 
 
 # We build a x.pdf file out of the source x.tex
 %.dvi: %.tex %.gdf %.bib *.tex *.bib *.sty
 	${LATEX} $*
 	${BIBTEX} $*
 	$(GLOSSTEX) $*.aux $*.gdf
 	$(MAKEINDEX) $*.gxs -o $*.glx -s glosstex.ist -t $*.glg
 	$(LATEX) $*
 #	$(GLOSSTEX) $*.aux $*.gdf
 #	$(MAKEINDEX) $*.gxs -o $*.glx -s glosstex.ist -t $*.glg
 	$(LATEX) $*
 
 # We build the PS from the DVI
 %.ps: %.dvi *.tex *.bib *.sty
 	$(DVI2PS) $*.dvi -o $*.ps
 
 # We build the PDF from the PS
 %.pdf: %.ps *.tex *.bib *.sty
 	$(PS2PDF) $*.ps $*.pdf
 	${THUMBPDF} $*.pdf
 	
 pub: ${PROJECT}.pdf
 	scp ${PROJECT}.pdf ${PUBLISH}
```
