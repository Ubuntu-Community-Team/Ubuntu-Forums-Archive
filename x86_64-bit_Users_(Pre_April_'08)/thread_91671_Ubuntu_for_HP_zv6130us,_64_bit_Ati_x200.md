---
title: "Ubuntu for HP zv6130us, 64 bit/ Ati x200"
date: 2005-11-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by gbailey on 2005-11-17
Hi, my name is Gerald Bailey and I am interested in discovering the world of linix. What prompted me is that I like the idea of open sourcing and also believe that knowledge should be free. I had no idea where to start learning and was talking to a customer(I do Tech support for D-Link) who recomended ubuntu to me. Since I have recently purchased a HP ZV6130us with a 64 bit processor and there are no other OS's out there to utilize it, I have tried to use the CD live, and the dvd image to know avail. Ubuntu goes through it's configuration and just freezes to a blank screen. Another freind of mine can use the same CD on his Mac G4 and it works fine. I keep thinking it could be the graphics card, is that right? Any Ideas on how I can proceed?

---

### Post by JuanC on 2005-11-17
Try this thread :
[http://www.ubuntuforums.org/showthread.php?t=36991](http://www.ubuntuforums.org/showthread.php?t=36991)

---

### Post by gbailey on 2005-11-17
Thank you for the direction!

---

### Post by almahtar on 2006-04-10
You're going to love Dapper.  I have a zv6130us as well, and had tons of problems with Breezy.  It took me a long time to get my 3d working, get the wireless working, etc.  In Dapper flight 6 it all works *beautifully*.

To get your 3d working you just install the xorg-driver-fglrx package in synaptic and change the line that says 'driver    "ati" ' to 'driver    "fglrx" ' in /etc/X11/xorg.conf.

To get your wireless working use Ndiswrapper, there are a few tutorials for Broadcom 43xx under Dapper.  Linux is worth it- keep on trying and post if you have problems!

---

