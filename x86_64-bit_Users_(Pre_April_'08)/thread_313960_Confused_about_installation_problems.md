---
title: "Confused about installation problems"
date: 2006-12-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Guns90 on 2006-12-06
Hi.  I can't find a solution to system freezes during instaltion on my 64 bit sysytem.  I can do anything I want on my 32bit Dapper system.  I love it, and I thank all of you for helping me to get there.  HOWEVER; I have done several searches on the subject of 64 bit freezes, and I have found many 'suggestions' to try various things. I've tried all that I've found, but nothing has worked. 

I've just built my first 64bit system and I have not been able to get ubuntu loaded on it without it freezing.  I've tried to do the install like my 32 bit system - windoze on hda1, and ubuntu on hdb1.  Everything on Windoze works perfectly, but every time I install Dapper ubuntu (several times) it freezes when I get to the point where it says 'Installtion complete.  Remove the CD from the CD-ROM drive and press any key to continue.'  At this point, its frozen. The mouse will still move, but not allow me to click on anything. Nothing else works. If I hit the reset button, the computer reboots, but as soon as it gets to where Grub should tell me to decide which OS I want, I get 'Error 17. Cannot mount this hard drive.  Please press any key to continue...'  At this point the computer is froze again.  Suggestions please.

ASUS A8N-E
AMD ATHLON 64, 3800
EGVA 7600GTS
1 GB Kingston HyperX RAM
hda1 - 40GB Seagate IDE 
hdb1 - 250GB Western Digital SATA
Samsung DVD/CD
Viewsonic VE710b

Gary

---

### Post by hainesr on 2006-12-07
Just a shot in the dark, but do you have the latest BIOS for your motherboard?

Cheers,
Rob

---

### Post by Guns90 on 2006-12-08
Sorry it took so long to get back to you.  I've been going nuts trying to get this thing working.  

To answer your question, yes the BIOS is the latest.  I finally gave up on Edgy and tried Dapper AMD64 6.01.1.  It worked perfectly.  I removed it and reinstalled Edgy and I got the same problem.  The best I can figure is that either I have a bad copy of Edgy, or it's a bug of some kind.  I've reinstalled Dapper and will just stick with that until Fluffy (or whatever they call next version) comes along.  Thanks for your response,though.  Gary

---

### Post by bAnj0 on 2006-12-08
maybe check the md5sum of the iso file you have downloaded or maybe the cd is broken.

by the way the first beta of feisty is out, you can give it a try.
it has 2.6.19 kernel. I gave it a try and it works fine on my conroe.

---

