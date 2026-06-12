---
title: "Wine crash help"
date: 2008-06-13
forum: Wine
---

### Post by Boo355 on 2008-06-13
I am a windows gamer who has just recently moved to ubuntu 
Hardy Heron 8.04

I am using wine 1.0rc4

I have installed a few of my games including cod4 and crysis
 when i run either of these games wine just closes am i doing something wrong here i have tryed both games with no-cd/dvd cracks to no availe


system

gigabyte qd6 am2+ main board
Amd x2 4400 @ 2.40 GHz
Sapphire ati xt 3870 512 meg gddr5
8 gig ddr2 ocz 800MHz
4 sata II wd 250 gig HDD (have not looked at raid in ubuntu yet)

---

### Post by cogadh on 2008-06-13
Crysis does not work in Wine:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=5880](http://appdb.winehq.org/objectManager.php?sClass=application&iId=5880)
CoD4 requires some very specific configuration to work and you cannot use the "out of the box" installation of Wine, you need to patch and compile it yourself:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10429](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10429)

Generally speaking, newer games (less that a year or two old) are less likely to work with Wine than anything older. In the future, you really should check AppDB first before trying to run anything in Wine. It will tell you what you might need to do to get your apps running in Wine, but it will also tell you what apps you shouldn't bother with trying (yet).

---

### Post by Sleaka J on 2008-06-13
Even older games (3+ years) are not guaranteed to work. Take The Sims 2 for instance. It was released in 2004 and it still doesn't work at all:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1942](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1942)

Anything working in Wine is a case by case basis.

---

