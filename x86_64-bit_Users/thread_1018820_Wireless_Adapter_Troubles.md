---
title: "Wireless Adapter Troubles"
date: 2008-12-22
forum: x86 64-bit Users
---

### Post by varean on 2008-12-22
Hey everyone, I just reinstalled Ubuntu but this time 64bit and I am having a bit of trouble getting my Linksys WUSB11 v2.4 adapter to work.  lsusb detects the device but when I try to connect to a network from the desktop (via the icon in the corner) I create a new connection and type in the essid but it doesn't connect to it. I tried doing:

iwconfig wlan0 essid myessid
iwconfig up

but still no dice. Anyone got any ideas why its detecting me adapter but not letting me use it?

---

### Post by Titan8990 on 2008-12-23
Its probably loading the wrong drivers for it which is a common issue with non-custom kernels.

Do you get an error if you do:


iwlist wlan0 scanning

---

