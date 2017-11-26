---
id: 287
disqus_id: 287 http://regis.decamps.info/blog/?p=287
title: Kde 3.5 on Gentoo
date: 2006-07-15T01:20:54+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/2006/07/kde-35-on-gentoo/
permalink: /blog/2006/07/kde-35-on-gentoo/
tmac_last_id:
  - ""
dsq_thread_id:
  - "555845695"
categories:
  - English
  - Linux
tags:
  - KDE
---
After syncing my gentoo portage, I have discovered many conflicts in my portage tree. KDE 3.5 has been marked stable on amd64, but the update could not be straightforward because of blocking packages.

<p align="left">
  I quickly found out that there was a conflict between monolithic packages and modulized packages (like kdebase vs kdebase-meta which simply requires konsole, kstart, kdepasswd, etc.) It took me much more time to understand the source of this conflict. It was pretty simple, though. In my world file, there was the very monolithic <strong>kde-base/kde</strong> (which was a mistake because I uninstalled it long ago).<br /> Then, I struggle longuer with the compilation of the individual packages. Whatever the order I tried, I was stopped with the error: <strong>xxx.moc: No such file or directory</strong> For instance:<br /> <code>make[1]: Entering directory `/var/tmp/portage/kdialog-3.5.0/work/kdialog-3.5.0'&lt;br />
Making all in kdeeject&lt;br />
make[2]: Entering directory `/var/tmp/portage/kdialog-3.5.0/work/kdialog-3.5.0/kdeeject'&lt;br />
make[2]: Nothing to be done for `all'.&lt;br />
make[2]: Leaving directory `/var/tmp/portage/kdialog-3.5.0/work/kdialog-3.5.0/kdeeject'&lt;br />
Making all in kdialog&lt;br />
make[2]: Entering directory `/var/tmp/portage/kdialog-3.5.0/work/kdialog-3.5.0/kdialog'&lt;br />
x86_64-pc-linux-gnu-g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/kde/3.5/include -I/usr/qt/3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -DNDEBUG -DNO_DEBUG -O2 -march=athlon64 -O2 -pipe -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION -c -o kdialog.o `test -f 'kdialog.cpp' || echo './'`kdialog.cpp&lt;br />
x86_64-pc-linux-gnu-g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/kde/3.5/include -I/usr/qt/3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -DNDEBUG -DNO_DEBUG -O2 -march=athlon64 -O2 -pipe -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION -c -o widgets.o `test -f 'widgets.cpp' || echo './'`widgets.cpp&lt;br />
x86_64-pc-linux-gnu-g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/kde/3.5/include -I/usr/qt/3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -DNDEBUG -DNO_DEBUG -O2 -march=athlon64 -O2 -pipe -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION -c -o klistboxdialog.o `test -f 'klistboxdialog.cpp' || echo './'`klistboxdialog.cpp&lt;br />
klistboxdialog.cpp:25:30: klistboxdialog.moc: No such file or directory&lt;br />
make[2]: *** [klistboxdialog.o] Error 1&lt;br />
make[2]: Leaving directory `/var/tmp/portage/kdialog-3.5.0/work/kdialog-3.5.0/kdialog'&lt;br />
make[1]: *** [all-recursive] Error 1&lt;br />
make[1]: Leaving directory `/var/tmp/portage/kdialog-3.5.0/work/kdialog-3.5.0'&lt;br />
make: *** [all] Error 2&lt;br />
!!! ERROR: kde-base/kdialog-3.5.0 failed.&lt;br />
Call stack:&lt;br />
ebuild.sh, line 1539:   Called dyn_compile&lt;br />
ebuild.sh, line 939:   Called src_compile&lt;br />
ebuild.sh, line 1248:   Called kde-meta_src_compile&lt;br />
kde-meta.eclass, line 410:   Called kde_src_compile&lt;br />
kde.eclass, line 164:   Called kde_src_compile 'all'&lt;br />
kde.eclass, line 306:   Called kde_src_compile 'myconf' 'configure' 'make'&lt;br />
kde.eclass, line 302:   Called die&lt;br />
!!! died running emake, kde_src_compile:make&lt;br />
!!! If you need support, post the topmost build error, and the call stack if relevant.&lt;br />
Done.&lt;br />
</code>
</p>

The clue was

`/usr/share/aclocal/linc.m4:1: warning: underquoted definition of AM_PATH_LINC<br />
run info '(automake)Extending aclocal'`

<p align="left">
  It sounds like automake was not up to date. Unfortunately it was (almost)<br /> <code>kro64 bin # emerge -s automake&lt;br />
Searching...&lt;br />
[ Results for search key : automake ]&lt;br />
[ Applications found : 2 ]&lt;br />
*  sys-devel/automake&lt;br />
Latest version available: 1.9.6-r2&lt;br />
Latest version installed: 1.9.6-r1&lt;br />
Size of files: 747 kB&lt;br />
</code>
</p>

<p align="left">
  I then gave a try to
</p>

`cd /usr/bin/<br />
mv automake automake-wrapper<br />
ln -s automake-1.9 automake`

<p align="left">
  And that worked 😉 automake-wrapper was guilty!
</p>

<p align="left">
  Hope this helps!
</p>
