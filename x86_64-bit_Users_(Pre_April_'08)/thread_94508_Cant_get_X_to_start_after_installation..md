---
title: "Cant get X to start after installation."
date: 2005-11-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Anttu^^ on 2005-11-24
Hi i have a problem getting x to start after i had installed ubuntu 64 bit edition.
My hardware is 

ASUS A8N-E
AMD Athlon 64 3200+
ATI X1800 XL
2x512 ddr 3200

i guess that it has something to do with my 3d card?? but i am pretty new to linux... so can some one explain how to get it configured right, if it is even possible to get it to work or is it to new????

thanks :)

---

### Post by korakde on 2005-11-27
Hi, I have a similar problem with XServer. 
You could check on these links:
[http://ubuntuforums.org/showthread.php?t=85295](http://ubuntuforums.org/showthread.php?t=85295)
[http://ubuntuforums.org/showthread.php?t=94480](http://ubuntuforums.org/showthread.php?t=94480)
They could  be useful.
I've  started a new thread on the problem.
[http://ubuntuforums.org/showthread.php?t=95776](http://ubuntuforums.org/showthread.php?t=95776)
 Hope something comes up

---

### Post by jluquette on 2005-11-27
Hey there everybody.  I'm new to Linux, Ubuntu and AMD 64.  I'm having exactly the same problem (kind of refreshing to see I'm not alone).  I first made a DVD Live copy and it crashed just as X tried to begin.  So, I made an install DVD and it crashed in the same spot.  So, I made a CD install copy and the whole installation process went perfect until it booted up the first time and crashed right when it was asking me to login.  Got an error saying that X didn't start - possibly because I didn't have it set up right.  Well, I didn't do anything to set it up at all - was all automatic up to that point.  I went to X's web site and read some trouble shooting info.  Of course, there's NEVER a mention of the problem that YOU are having but I may have stumbled upon something that may relate here.  It mentioned that X could only automatically recognize PCI and AGP.  HMMMMM, I have PCI Express:confused:  graphics built into my motherboard.  Could it be that X cannot recognize this? Do any of you others have PCI Express?  I really need some help from some one who knows something about UNIX, Ubuntu. Linux, AMD ...

---

### Post by Patsoe on 2005-11-28
I had this problem too. I have a pretty recent ATi card, which is only supported by the  closed-source driver from ATi (and ubuntu doesn't pack closed-source drivers by default...)

You will have to change the file /etc/X11/xorg.conf from the command line. Replace the driver 'ati' by 'vesa'. 

After that, you will probably be able to enter X, and then you can do the things outlined here:
[http://ubuntuforums.org/showthread.php?p=408111](http://ubuntuforums.org/showthread.php?p=408111)

---

### Post by Anttu^^ on 2005-11-29
okey thanks :cool: i will se if will get it to work :smile: 

and the new ati drivers should support Ubuntu 5.10 too :eek:

---

