---
title: "World of Warcraft crashes to desktop after intro movies"
date: 2008-04-15
forum: Wine
---

### Post by zaxour on 2008-04-15
Hi guys, 

I've been trying to get WoW working on a friends laptop that is using the ATI IGP 340(I think,somewhere in that series, it uses the plain "ati" driver under xorg).  Not the best, but it works fine under Windows with all the settings turned down.  Problem is, under WINE, it crashes right back to the desktop after the two intro movies and there are no non-fixme messages in the wine terminal.  I've tried everything from editing the config.wtf, to turning off pixel shading and setting the sound to OSS.

I've searched high and low for the better part of three days to see if there was anyone that may have had the same problem, but with no luck.  Is there any solution to this?  Your help is greatly appreciated.

---

### Post by Kinst on 2008-04-15
Did you try ATI's fglrx driver?

---

### Post by zaxour on 2008-04-15
I wasn't sure how to set it; I tried setting it as the driver under xorg.conf, but it caused the xserver to crash, so I had to revert.

---

