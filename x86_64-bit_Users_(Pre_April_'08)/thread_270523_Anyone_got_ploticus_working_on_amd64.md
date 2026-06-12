---
title: "Anyone got ploticus working on amd64?"
date: 2006-10-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by martinfowler on 2006-10-03
I get a segmentation fault whenever I try to run ploticus on my amd64 dapper system. I'd like to know if it's just me or if others have the same problem.

Details
=========

springbank$ uname -a
Linux springbank 2.6.15-27-amd64-generic #1 SMP PREEMPT Sat Sep 16 01:50:50 UTC 2006 x86_64 GNU/Linux

springbank$ linux32 ploticus -debug -png pie

Got command line arg(s): -png
Got command line arg(s): pie
Device code is g
Setting output file name to out.png
Version: pl 2.20
Script file is: pie
Script file successfully opened
Executing page
Executing getdata
filling data set# 0
Segmentation fault

The file 'pie' is the file from <http://ploticus.sourceforge.net/gallery/clickmap_pie.htm>. It plots fine on my 32 bit Ubuntu system.

---

### Post by kuja on 2006-10-04
I've no idea, as I've never used ploticus. Did you install from a package or compile from source? If not the latter, I would recommend compiling from source just to see if it works any better. Another thing you might try is to contact the ploticus newsgroup, found [here.](http://tech.groups.yahoo.com/group/ploticus/)

---

