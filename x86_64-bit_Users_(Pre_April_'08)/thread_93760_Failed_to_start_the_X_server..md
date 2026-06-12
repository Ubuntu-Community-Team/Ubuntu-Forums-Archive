---
title: "Failed to start the X server."
date: 2005-11-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by nighthawk39 on 2005-11-22
Hi, I'm pretty new to the world of Linux but I like what I see.  Especially Ubuntu. :)  So far here's my history:

- Knoppix 3.9 LiveCD
- Ubuntu 5.04 LiveCD i386
- Ubuntu 5.10 LiveCD i386
- Ubuntu 5.10 on VMWare Workstation
**- Now I am trying to run the 5.10 LiveCD (64-bit) without success**

My error? **_Failed to start the X server._**  This happens right before Ubuntu should be showing the login screen.

I think it is something to do with my video card, and it's the 64-bit version causing problems becuase:
- when searching for a solution every single topic I found had users with the same series of GFX card (Radeon x700 or above)
- to confirm it wasnt the 64-bit CD causing the problem I tried the 32-bit LiveCD and found it ALSO does not work (I had only used it on an older computer before)

My (new) PC specs:

Pentium D 830 3.0ghz dualcore EM64T (64-bit)
*ATI Radeon X800 GTO 256MB GDDR3 (PCI-e)*
1024MB DDR2 RAM
The motherboad is a 64-bit compatible ASUS, I just don't remember the model right now

The old computer that the 32-bit LiveCD worked on had a P4 2.0ghz, 512 DDR and a GeForce2 mx400 64MB (AGP).

Anything would be helpful!  I am anxious to get this running! :) Thanks.


Edit: Also posted this is the [Absolute Beginner Talk]("http://www.ubuntuforums.org/forumdisplay.php?f=73") forum since that might be more appropriate. :)

---

### Post by Snakez on 2005-12-12
I'm having the exact same problem.

I'm using Asus K8N4-E motherboard (supports 64-bit processors), AMD64 3000+ and as my video card, Radeon X800 XL 256... My X server or what ever you call it, doesn't start and I'm really pissed :???: I'm really hopingf the latest release, Dapper Drake Ubuntu 6.04, has somewhat solved the mystery of making Radeon x700 and above cards work properly... Any ideas how to solve this problem in starting the X server with these Radeon cards? Or should I just buy some crappy Nvidia card :p  But as nighthawk mentioned, if someone knows how to solve this nasty problem, be my guest... Report back here and please, some guaranteed working solutions, I've spend hours and days trying to use some of the "working solutions" I've found on this forum and other places with no luck, otherwise I wouldn't be writing this damn post and using Ubuntu ;) 
So any suggestions from the higher powers and linux-masters :)  I'm an expert with windows and I've trained my skills with linux with other distros so I'm not a complete newbie or beginner ;)

---

### Post by Ferrat on 2005-12-12
The problem I belive is that they are PCI-E cards, try searching for how to make Ubuntu/ (X) properly recognize a PCI-E 

I have a X800 Series card but AGP and that works (well execpt for the F*pip*ing Hardware OpenGL render that just won't kick in >_< (work in progress on fixing that)

---

### Post by amohanty on 2005-12-12
I am surprised you are having problems. I have the A8N-E and  Radeon X300 SE (low end but works for me) on the PCI-E and Ubuntu recognized it fine, though  have yet to get fglrx on 5.10 working on it.

If you have installed Ubuntu can you post the /var/log/Xorg.0.log file, so you can find out where it crashed and burned. 

ALternatively log into console mode and do the following:

```
startx | tee error.log
```

and post the contents of error.log

HTH

---

### Post by RAOF on 2005-12-12
Someone has recently got the livecd to work.  If I remember correctly, it was by booting the livecd with "live-expert", and then accepting the defaults for all the questions **except** the X-org video driver.  Set that to "vesa", and it should load a GUI for you.

Incidentally, ATI cards suck in linux.  If you filtered this forum, I reckon you'd find that almost a quater of all posts are about "My ati card doesn't work" :(

---

### Post by Aphorism on 2005-12-13
Edit your /etc/X11/xorg.conf file and start out with the Driver set to "vesa" as opposed to "ati".  Work your way forwards from there.

Good luck.

---

