---
title: "Should I go down to 32-bit?"
date: 2009-08-26
forum: x86 64-bit Users
---

### Post by rhaces on 2009-08-26
Hi All, here are my specs:
```
Ubuntu 9.04 64 bit
Dell M1530 Laptop
Intel(R) Core(TM)2 Duo T6400 @ 2.00GHz
3 GB Ram
160 GB HD
```

I've been questioning myself if I should go down to 32 bits since I've experience some problems with the 64 bits, my main tasks are:

```
DEVELOPER:
mysql 5.1 Server
mysql GUI Tools
apache 2 Server
php Server
VMWare with a Win XP Guest
Pentaho Data Integration (A Javabased app used to do ETL-Extract Transform Load)
COMMON:
firefox 3.5
Pidgin
OpenOffice
mPlayer
```

My main concern is that if I downgrade to 32 bit, VMWare and the Javabased apps will performance will decline, so the question is, How much will this apps performace go down??

Thanks for your help
Rodrigo

---

### Post by andrew.46 on 2009-08-26
Hi rhaces,

I can only answer for MPlayer on your list and I realise that it is not central to your question. As you may already know a major shortcoming with MPlayer on a 64bit system is the lack of external codecs available to enable playback of many windows-only media files. This is slowly changing as developers write native implementations for some of these codecs but I believe the 32bit MPlayer will always have the upper hand in this area.

Andrew

---

### Post by VioletsPie on 2009-08-26
The million-dollar question I guess rhaces would be what problems are you experiencing and what workarounds there might be. In other words, are your problems so large that it is worth a wipeout?

As far as performance, based on your specs there most likely would be no perceivable difference in performance.

---

### Post by tuxxy on 2009-08-26
rhaces I wouldn't personally as I much prefer 64-bit.  What are the specific problems  which are forcing you to downgrade to 32-bit? and are there no solutions other than downgrading.

---

### Post by rhaces on 2009-08-26
The question, what kind of problems have I got?, well at least the once I can remember now are:
- Flash: This is a big issue, If I use the 64 bit flash plugin downloaded from the lab of adobe, firefox crashes every 5 minutes or so, if I use the flash from atp with the nspluginwrapper, flash pages start consuming too much CPU and flash videos are bumpy (I have a huge machien, a core 2 dow with 3 gb of ram) the npviewer.bin consumes a lot of CPU
- Eclipse based app: I use an eclipse based app, even I have been able to run eclipse with the 64 bit, I can't find the way of using this app, I have to go with VMWare and WinXP to use it
- Codecs
- Other installs: I can't remember now what was it, but there were a couple of apps that I wanted/needed and couldn't install

> **VioletsPie said:**
> As far as performance, based on your specs there most likely would be no perceivable difference in performance. 

I guess that if VioletsPie quote is true, then I will go down to 32 bits (Under the pretext of upgrading to 9.10) and see what happens!!!

---

### Post by Yellow Pasque on 2009-08-27
> but I believe the 32bit MPlayer will always have the upper hand in this area.

I'm pretty sure I've seen guides to run MPlayer32 on a 64-bit system.

---

### Post by VioletsPie on 2009-08-27
Great thread on video : [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

About 32 on 64 : [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790) 

Just do some searching, be specific, you'll be surprised.

---

### Post by dk06 on 2009-08-27
Do you have enough room to dual-boot? Then you don't have to choose.

VMware w/64bit is really nice and I wouldn't want to have to downgrade to 32bit

Also,
What about the 32bit w/PAE?
I know it's not a 64 bit but may be the next best option

OR

What about running your 32bit in a VM?

---

### Post by terabyte1 on 2009-08-27
Ahh! Andrew.46 has it! 

If you are running 64-bit, some of the programs you *normally* use, have not caught up with 64-bit and are still using bog-standard 32-bit because that is more stable. Daah-Raahh!:guitar:

Cheers!

---

