---
title: "Desktop doesn't start"
date: 2006-04-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by newbdude on 2006-04-24
I just installed Ubuntu 5.10 on my iMac G3. I log in (I've tried failsafe too!!), and the login sound goes off, but nothing loads....ever! I left it alone for an hour and nothing. No logo, panel, desktop, background....nothing! I checked the different conosles (ctl+alt+f1 etc) for errors, but theres nothing unusual. Im really banging my head against a wall here ](*,)  so any help is appericiated!
Thanks!

---

### Post by rmjokers on 2006-04-25
The first thing to try is reconfiguring the X server.  Sometimes the install just doesnt get it right.  Try:

sudo dpkg-reconfigure xserver-xorg

---

### Post by jdp on 2006-04-25
This is a known problem with iMacs.  Do as rmjokers suggests.  But, be sure you have the date set correctly, as it seems that you may well be having that problem.

The date bug generally invloves Gnome failing to start any futher than login and the initial drums.  The display problems would involve not getting any video or an unchangeable 640x480 screen.  Fixing both is probably needed on an iMac G3.  To help prevent the date bug, sheck the voltage of the PRAM battery and if it's near 3v or less, replace it.

---

