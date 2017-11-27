---
id: 972
disqus_id: 972 http://regis.decamps.info/blog/?p=972
title: MP550 support for linux
date: 2009-12-02T13:44:16+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=972
permalink: /2009/12/mp550-support-for-linux/
tmac_last_id:
  - ""
dsq_thread_id:
  - "557940178"
categories:
  - English
  - Informatique
tags:
  - HOWTO
  - Imprimante
  - Linux
  - Scanner
---
On many forums, I’ve read my brand new Canon Pixma MP550 would not be supported under Linux.

Well, that’s incorrect 🙂 [Mandriva linux](http://www.mandrivalinux.com/) does not provide out-of-the-box support, but you’ll find official Canon drivers for this very nice printer on the [Canon Australian web site](http://www.canon.com.au/Support-Services). Strangely enough, they are not on the sites in other countries :-/

Here are my instructions:

## Go to Canan Australia Support services

Go to <http://www.canon.com.au/Support-Services>

## Open the download link for my printer<figure id="attachment_973" style="width: 363px" class="wp-caption alignnone">

<img src="/blog/wp-content/uploads/2009/12/screenshot-7.png" alt="Search for Printer" title="Search Printer" width="363" height="83" class="size-full wp-image-973" srcset="/blog/wp-content/uploads/2009/12/screenshot-7.png 363w, /blog/wp-content/uploads/2009/12/screenshot-7-350x80.png 350w" sizes="(max-width: 363px) 100vw, 363px" /><figcaption class="wp-caption-text">First, search for my printer (in my case MP550)</figcaption></figure> <figure id="attachment_974" style="width: 591px" class="wp-caption alignnone">[<img src="/blog/wp-content/uploads/2009/12/screenshot-8.png" alt="Then, Follow the download link" title="Search results" width="591" height="144" class="size-full wp-image-974" srcset="/blog/wp-content/uploads/2009/12/screenshot-8.png 591w, /blog/wp-content/uploads/2009/12/screenshot-8-350x85.png 350w" sizes="(max-width: 591px) 100vw, 591px" />](/blog/wp-content/uploads/2009/12/screenshot-8.png)<figcaption class="wp-caption-text">Follow the download link</figcaption></figure> 

## Download the driver

Browse the results and find the Canon driver for linux.<figure id="attachment_976" style="width: 566px" class="wp-caption alignnone">

<img src="/blog/wp-content/uploads/2009/12/screenshot-9.png" alt="The Canon driver for linux " title="Canon driver for linux (RPM)" width="566" height="97" class="size-full wp-image-976" srcset="/blog/wp-content/uploads/2009/12/screenshot-9.png 566w, /blog/wp-content/uploads/2009/12/screenshot-9-350x59.png 350w" sizes="(max-width: 566px) 100vw, 566px" /><figcaption class="wp-caption-text">The Canon driver for linux </figcaption></figure> 

You find, the source code, the Redhat RPM package, and the Debian DEB package.

You’ll also find the drivers for the scanner.

For a RPM-based distribution, download the RPM packages for 

the printer
:   [MP550 series IJ Printer Driver Ver. 3.20 for Linux (rpm Packagearchive)](http://support-au.canon.com.au/EN/search?v%3aproject=ABS-EN&v%3afile=viv_A9C4v0&v%3astate=root%7croot-20-20%7c0&opener=full-window&url=http%3a%2f%2fsupport-au.canon.com.au%2fcontents%2fAU%2fEN%2f0100235702.html&rid=Ndoc21&v%3aframe=redirect&&sid=6)

the scanner
:   [MP550 series ScanGear MP Ver. 1.40 for Linux (rpm Packagearchive)](http://support-au.canon.com.au/EN/search?v%3aproject=ABS-EN&v%3afile=viv_A9C4v0&v%3astate=root%7croot-20-20%7c0&opener=full-window&url=http%3a%2f%2fsupport-au.canon.com.au%2fcontents%2fAU%2fEN%2f0100237102.html&rid=Ndoc24&v%3aframe=redirect&&sid=6)

## Install the drivers

Unpack the archive

    root@localhost /tmp # tar xzvf cnijfilter-mp550series-3.20-1-i386-rpm.tar.gz

run the install script

    cd cnijfilter-mp550series-3.20-1-i386-rpm
    ./install.sh
    

## That’s it

Check in the [CUPS adminsitration](http://localhost:631/printers/?) that the printer was added, and print the test page.
