---
title: "Intel VS NVidia Graphic Card"
date: 2013-04-19
forum: Wine
---

### Post by GameX2 on 2013-04-19
Hi,


I can't get 2 games to under Wine properly.  Harry Potter and the Deathly Hallows, Part 1 & 2...

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=22361](http://appdb.winehq.org/objectManager.php?sClass=version&iId=22361)
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=23935](http://appdb.winehq.org/objectManager.php?sClass=version&iId=23935)

I get that very strange graphic glitche when starting gameplay.  Also, tje main menu does not appear, in Part 2 (Black screen):
[https://dl.dropboxusercontent.com/u/67605655/HP7.png](https://dl.dropboxusercontent.com/u/67605655/HP7.png)

Colors look ugly!

I've contacted the Wine testor.  He told me that it was a problem with my Intel graphic card:

> Hi

I read you comentary, and say this, if you have use INTEL IGp  this game dont work properly, I recomend use NVIDIA graphic card, NVIDIA have more compatibility compared with AMD and in last order INTEL

INTEL graphics dont support OpenGL complete specs and for that many game or dont run or have many graphic glitches

> Sorry but in your case, the guilty is intel IGP and Intel support on linux

If you have linux distro in 32 bit is more compatible, but intel no have hardware OpenGL specs complete and intel drivers dont work good with wine

Nvidia works better (privative driver is required)


=(

I am screwed?
I've tried installing an experimental NVidia Driver, after a system backup.  That way:

[www.techlw.com/2012/08/install-latest-intel-gpu-drivers-in.html](www.techlw.com/2012/08/install-latest-intel-gpu-drivers-in.html)
[http://www.webupd8.org/2012/12/use-nvidia-experimental-drivers-310.html](http://www.webupd8.org/2012/12/use-nvidia-experimental-drivers-310.html)

I managed, by doing this, to display the Copyright screen, and the main menu, as well.  But now, when gameplay start, I get music and sound, I can also move, but the screen just look black and white.  I can't see anything.

Well.
What I find confusing, is that I always thought NVidia graphic cards were a bad choice for Linux.  Why, exactly?  I do know they use proprietary drivers, but other than that..  Why would Intel be non-working, in that case?

Is there a possible workaround?  By any chance, that game will eventually be compatible with Intel ?
I'm on a laptop, so I couldn't replace the graphic card (well, I guess). =(


Thanks

---

### Post by Mark Phelps on 2013-04-19
Nvidia has tended to be the better choice of video chipsets for graphics over the years -- but the proprietary drivers are generally required -- and if you don't have an Nvidia video chipset, then you're NOT going to be able to use their drivers.  

Intel drivers are installed during setup. If you want to see if there are newer versions of Intel drivers available, check the link:

[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=17045&lang=eng]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=17045&lang=eng")

---

### Post by GameX2 on 2013-04-19
> **Mark Phelps said:**
> Nvidia has tended to be the better choice of video chipsets for graphics over the years -- but the proprietary drivers are generally required -- and if you don't have an Nvidia video chipset, then you're NOT going to be able to use their drivers.  

Intel drivers are installed during setup. If you want to see if there are newer versions of Intel drivers available, check the link:

[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=17045&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=17045&lang=eng)

Thanks, I check this.

I believe I was confused and had a bad opinion of Nvidia of Linux, because they use proprietary drivers, and that apparently cause trouble to developpers ?
I can also mention the "NVidia.. F--- YOU!" from Linus Torvalds!

From what I've read, they're cards are actually more compatible than the Intel ones.

---

