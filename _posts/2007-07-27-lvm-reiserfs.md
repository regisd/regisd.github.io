---
id: 443
disqus_id: 443 http://regis.decamps.info/blog/?p=443
title: LVM + ReiserFS
date: 2007-07-27T19:46:06+00:00
layout: post
guid: http://regis.decamps.info/blog/2007/07/lvm-reiserfs/
permalink: /blog/2007/07/lvm-reiserfs/

dsq_thread_id:
  - "753839011"
categories:
  - Hightech
tags:
  - Linux
---
```
regis ~ % df                                                                                           [kro64]<br />
Filesystem            Size  Used Avail Use% Mounted on<br />
/dev/mapper/system1-mdv--root<br />
                      4,0G  531M  3,4G  14% /<br />
/dev/sda3             3,9G   49M  3,9G   2% /boot<br />
/dev/mapper/raidvg-home<br />
                      4,9G  4,0G  920M  82% /home<br />
/dev/sdb5             3,0G  1,4G  1,6G  48% /mnt/gentoo<br />
/dev/mapper/system-opt<br />
                       11G  7,3G  2,8G  73% /mnt/gentoo/opt<br />
/dev/mapper/system1-tmp<br />
                      6,9G  157M  6,7G   3% /tmp<br />
/dev/mapper/system1-mdv--usr<br />
                      7,9G  6,2G  1,8G  79% /usr<br />
/dev/mapper/system-local<br />
                      3,8G  3,8G   14M 100% /usr/local<br />
``` 

Oooops! It’s not the first time that I perform this task, but it’s always so good to see LVM and Reiserfs in action:
  
`[root@kro64 ~]# lvresize -L+1G /dev/system/local<br />
  Extending logical volume local to 4,76 GB<br />
  Logical volume local successfully resized<br />
[root@kro64 ~]# resize_reiserfs /dev/system/local<br />
resize_reiserfs 3.6.19 (2003 www.namesys.com)<br />
resize_reiserfs: On-line resizing finished successfully.<br />
` 

_Et voilà_!
  
```
[root@kro64 ~]# df /usr/local/<br />
Filesystem            Size  Used Avail Use% Mounted on<br />
/dev/mapper/system-local<br />
                      4,8G  3,8G  1,1G  79% /usr/local<br />
```
