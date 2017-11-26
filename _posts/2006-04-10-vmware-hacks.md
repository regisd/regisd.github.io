---
id: 250
title: VMware hacks
date: 2006-04-10T20:14:37+00:00
author: Régis
excerpt: How to hack VMware player to build your own images.
layout: post
guid: http://blog.decamps.info/?p=250
permalink: /2006/04/vmware-hacks/
tmac_last_id:
  - ""
dsq_thread_id:
  - "590956419"
categories:
  - English
  - Informatique
tags:
  - HOWTO
---
This week-end, I have played with \[VMware player\](http://www.vmware.com/download/player/) which is a free (as beer) tool to run an existing VMware image. 

There are already several nice [community-made images](http://www.vmware.com/vmtn/appliances/community.html) you can download and play with. This is very convenient to

* try another operating systems like \[Haiku operating system\](http://haiku-os.org/) or \[Gentoo linux\](http://gentoo.org/)
  
* try softwares without to deal with a long or complex installation procedure, like \[open ACS content management system\](http://www.jsequeira.com/projects/oasisvm/) or \[Bugzilla\](http://bugzilla.org/)

Why not hack an existing image to install something else? For exemple, you can download the gentoo image and install \[mediawiki\](http://www.mediawiki.org/) on top of it, thus making a new « mediawiki VMware image » (based on gentoo linux). If we go a little step further, you an even \[change the operating system\](http://www.hackaday.com/entry/1234000153064739/). 

When you have a closer look, you’ll discover that a VMware image is described with a simple text-based file with the extension `.vmx`. This files has a syntax similar to Java properties files. Most parameters are straightforward, you can change the `displayName` for instance.

Now, you can even change the virtual harddisks. The disks are described in `ide<a>.<b>`. There are only 4 IDE disks available in the guest operating system (plus the floppy disk):

* ide0.0 is `/dev/hda` (C: on DOS)
  
* ide0.1 is `/dev/hdb` (D: on DOS)
  
* ide1.0 is `/dev/hdc` (E: on DOS)
  
* ide1.1 is `/dev/hdd` (F: on DOS)

For instance

<pre>ide0:0.present = "TRUE"
ide0:0.fileName = "gentoo.vmdk"
ide0:0.deviceType = "disk"
ide0:0.redo = ""
</pre>

VMDK files are virtual disks. They are not easy to generate properly, that’s why I recommand to base your hacked image on an existing image (provided by VMware themselves ;-))

Note that you can also mount an iso image (from the host OS) into your CDROM drive (inside the guest OS):

<pre>ide1:0.present = "TRUE"
ide1:0.fileName = "ubuntu-5.10-install-i386.iso"
ide1:0.deviceType = "cdrom-image"
ide1:0.startConnected = "FALSE"
ide1:0.autodetect = "TRUE"
</pre>

Or if you’d like, you let your real CDROM drive (which is `/dev/hda` in my host system) be visible inside the guest OS 

<pre>ide1:0.present = "TRUE"
ide1:0.fileName = "/dev/hda"
ide1:0.deviceType = "cdrom-raw"
</pre>

Finally, and this was the most tricky, you can use a real harddisk partition inside the guest host. Here is how to have /dev/hdc2 visible as /dev/hdd inside the guest:

<pre>ide1.1:present = "TRUE"
ide1.1:filename = "/dev/hdc2"
ide1.1:redo = ""
ide1.1:deviceType = "ata-hardDisk"
</pre>

If I find some time, I’ll tell you what I have found out on `vmdk` files.
