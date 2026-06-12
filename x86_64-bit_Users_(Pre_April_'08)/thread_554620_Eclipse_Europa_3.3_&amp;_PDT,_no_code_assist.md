---
title: "Eclipse Europa 3.3 &amp; PDT, no code assist?"
date: 2007-09-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by panosru on 2007-09-19
I have installed Eclipse Europa 3.3 on my Ubuntu 7.04 Feisty 64bit and i
installed  PDT 1.0 for my PHP coding, the problem is that code assists works
only for my custom code not for PHP's functions/objects/variables etc.. 

My java version is: 
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0-b105, mixed mode)

Eclise:
Eclipse SDK

Version: 3.3.0
Build id: I20070625-1500

Downloaded file:
eclipse-SDK-3.3-linux-gtk-x86_64.tar.gz

Web Standart Tools:
Web Standard Tools

Version: 2.0.0.v200706041905-7C-18k0IWJZ93WDDJlQ60nUjTdJp
Build id: 200706212235

PDT Version:
PDT SDK Feature
1.0.0.v20070917-2-84D22O_ccQjOTYSW8RZHIFIXR

This also reported to [https://bugs.eclipse.org/bugs/show_bug.cgi?id=203953](https://bugs.eclipse.org/bugs/show_bug.cgi?id=203953)

If anyone could help i would appreciate it :D

---

### Post by vrix on 2007-09-25
I use ctrl+<space> after typing in few php keywords. You can check out Help->Help Contents->PDT User Guide->References->keymap.

hope this helps.

(updated) just realized you got different problem when I looked at your bug report to eclipse. anyway...

---

### Post by kenjo on 2007-09-25
I've got the same thing going on, only mine doesn't even complete the custom functions.  I have no code completion at all in any php files, unless I hop out of php into html or javascript, then it does fine.  My php functions don't even fold, and I can't browse them with the project outline.

---

