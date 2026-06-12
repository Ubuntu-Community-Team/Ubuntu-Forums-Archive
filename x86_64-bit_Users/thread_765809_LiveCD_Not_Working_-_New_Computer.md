---
title: "LiveCD Not Working - New Computer"
date: 2008-04-24
forum: x86 64-bit Users
---

### Post by wagb278 on 2008-04-24
I just received my new computer. The Ubuntu 7.10 Desktop 32-bit and 64-bit do not boot.  LiveCD of Gparted does work. I partitioned disks using this. 

The Ubuntu 7.10 server (32-bit) CD installed. But did not detect the Ethernet connection (motherboard). Booting after the install completed Apache2 can't figure out who he is; presumably due to the Ethernet port not functioning. Boots to the login prompt and I can login.  Have not tried adding desktop on top of server 'cause I want 64-bit.
 
All CDs were ISO burned (1X) after verifing the checksums. 32-bit desktop and server were actually used to successfully install on other computers. The 64-bit (ver 7.10) desktop CD runs Memory Test, but Install, Safe Graphics Mode and other options will not execute to completion.  I have no other 64-bit machine to test the CD. Symptom is after a minute or so the display shuts down and I get a rapid beeping.

I suspect my problem is related to video card incompatabilities/lack of drivers.

I am downloading the new 8.04 64-bit desktop at this time (slowly).  Maybe that will have the fixes I need. Too bad my computer had to arrive on the first day of the new release going active.

The computer significant components are:
  Intel DP35DP motherboard (latest BIOS) with Q6600 processor (Quad)
  4 gig RAM
  MSI nVidia GeForce 9600GT w/512 RAM video card
  2 SATA Hard Drives

My desire is to for a 64-bit desktop with LAMP. 

Any ideas to get the Ethernet detected / activated?
I dont see any benefit to setting /etc/network/interfaces until the port is active - right?
Should I try adding desktop (32-bit) to verify the video card & drivers?  Remember I really want the 64-bit working.  I suppose the 64-bit CD could be bad, but I have never had problems burning and the working 32-bit desktop LiveCD gives the same symptoms as the 64-bit CD.

Any suggestions are welcome.  Thanks!

---

### Post by Patsoe on 2008-04-24
Well, that is a very new video card. I can imagine this was (part of) the problem for 7.10. 

Shoot me if this is a terrible question, but is the ethernet enabled in the BIOS? I'm just thinking, support for Intel ethernet chips is supposed to be pretty good...

> ...I get a rapid beeping.

Are the fans properly spinning up?

---

### Post by ASULutzy on 2008-04-25
> **Patsoe said:**
> Well, that is a very new video card. I can imagine this was (part of) the problem for 7.10. 

Shoot me if this is a terrible question, but is the ethernet enabled in the BIOS? I'm just thinking, support for Intel ethernet chips is supposed to be pretty good...



Are the fans properly spinning up?

Yea, rapid beeping is not good and likely has little to do with Ubuntu... Check to make sure your fans are going.

---

### Post by wagb278 on 2008-04-25
Thanks for the sugestions.  I will check this weekend (my next chance to play with this). 

Beeping only happens when trying to install from one of the desktop LiveCDs.  I am sure the case exhaust fan continues to run, not sure about CPU and/or Graphics card fans. The case is an Antec brand with the big 120 fan and you know it is running. Remember that Gparted Live CD worked just fine.  Ubuntu 7.10 Server installed (less Ethernet).  But that doesn't use a GUI (command line only).  I downloaded the 8.04 64-bit desktop overnight so I will burn that and have a third CD to try.

The first thing I did when powering up the machine was inspect the BIOS settings, but I can't remember seeing an Ethernet enable/disable setting.  I will check BIOS first thing.  

Thanks.

---

### Post by wagb278 on 2008-04-26
I'm up and running with Ubuntu 8.04 64-bit!  The 8.04 LiveCD worked like a champ - "It just works".  So, for anyone with an Intel dp35dp motherboard and nVidia 9600 you should update to the 8.04 version of Ubuntu.

My thanks to all of the Ubuntu team!

---

