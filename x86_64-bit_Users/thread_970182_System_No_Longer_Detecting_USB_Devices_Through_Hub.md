---
title: "System No Longer Detecting USB Devices Through Hub"
date: 2008-11-03
forum: x86 64-bit Users
---

### Post by hocmin on 2008-11-03
Using 8.04.

I've been using a usb hub on my system for several months now and recently my system has stopped detecting when I plug new devices into it.  If I unplug the hub and plug it into another port on the back of my box, the system then recognizes the devices hooked into it

I'm not sure what's changed.  I assume it was an update.  Any suggestions on how I could fix this would be appreciated.

---

### Post by MightySeb on 2008-11-05
I've been experiencing the same problem. From what I found, it looks like a kernel problem.

There is a (temporary, I hope) workaround: once you have plugged in something in your hub, pass this commend in a terminal.

> lsusb

This should "activate" your hub, until next reboot. (Well at least, it worked for me :P )

Most of the credit goes to this tread :

[http://georgia.ubuntuforums.org/showthread.php?t=899285&highlight=usb+hub](http://georgia.ubuntuforums.org/showthread.php?t=899285&highlight=usb+hub)

---

