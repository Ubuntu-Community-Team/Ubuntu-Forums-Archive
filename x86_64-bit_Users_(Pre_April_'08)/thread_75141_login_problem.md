---
title: "login problem"
date: 2005-10-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by eph on 2005-10-13
Hi!

I really have a hard time figuring out how to make this work.  My system is an AMD 64 3000+ on an MSI RS480 motherboard.

I have installed the 64 bit version of breezy badger and it goes to the graphical login screen. But after i log in, the system just freezes. No error messages, it just hangs.

I really want ubuntu to work. Can anybody help me out. 

Cheers.

---

### Post by Chetamonye on 2005-10-13
I had the same problem.  My graphics card(on board ATI) was the problem.  At the logon screen I hit CTRL-ALT-F1 to shell to a command line.  Login in and edit xorg.conf.  I change ati to vesa  under the device section.  I haven't installed the latest ATI drivers yet, but I am able to log in and see everything.  

Good luck, Chet

---

### Post by lackaff on 2005-10-13
I had the same problem with the ECS MS480-M motherboard (onboard ATI video). Changing the driver to vesa also allowed me to reach the GNOME desktop. However, I still have several kinks to work out:

Boot takes several (6-7) minutes, seems to hang on module loading. I'll track down some log details later and post them.
After booting, the desktop and applications are unreasonably slow and unresponsive. What should I look at to help diagnose this issue?

I've generally had much better luck with nVidia video than ATI, and have ordered a 6200TC-based card to drop in.

For what it's worth, my box also contains an Athlon64 3000+ processor, a single 512MB stick of PC3200 memory, and a pair of PATA hard drives. Suse 10.0 (amd64) installed OK (and boots normally), but also has a very laggy GNOME desktop. I haven't yet had time to look into it further.

I'm new to 64-bit linux, but look forward to figuring it all out. I just wanted to add my MS480 mobo issues to the thread...

Cheers.

---

### Post by Chetamonye on 2005-10-13
Mine is an AMD 64 3200+ on an MSI RS480 motherboard.  I get PCI errors as soon as I boot up.  Each distro I try gives a different error.  Only breezy 64 preview didn't give me the error.  And of course Win Xp.  Breezy RC gives the same error.

When I initially install I get a long boot up time.  After that, it's pretty fast.  Much faster than Mepis(currently using on another machine).

I've found that I have less problems running Breezy 386.  

Does sound work for you? 


Chet

---

### Post by RAOF on 2005-10-13
[QUOTE=lackaff]...Changing the driver to vesa also allowed me to reach the GNOME desktop...

...the desktop and applications are unreasonably slow and unresponsive....[/QUOTE]
I suspect that the vesa driver is actually your (performance) problem here.  IIRC it doesn't actually supply any X-acceleration, so it should be slow as molasses.

---

### Post by tymek666 on 2005-10-14
if you don't want to use vesa driver you can add NoAccel option under device section in xorg.conf file.

---

### Post by eph on 2005-10-17
hooray! i got it working. thanks::D

---

