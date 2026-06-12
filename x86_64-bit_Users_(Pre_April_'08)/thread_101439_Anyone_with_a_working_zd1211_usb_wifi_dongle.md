---
title: "Anyone with a working zd1211 usb wifi dongle?"
date: 2005-12-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by krrh on 2005-12-09
I've been struggling for the last day or so getting the module for the Zydas 1211 wifi chipset to compile on Breezy PPC.

The problems range from not compiling with some source versions to compiling with many errors, inserting, but not connecting to my access point with other source versions.  The problems aren't unusual, judging by other posts on the forum regarding this chipset.

Before I repost the various log outputs, which don't really differ from what I've seen elsewhere with others' problems, I'm curious whether anyone has this chipset working on a ppc system.

---

### Post by six6 on 2005-12-12
It seems to be hit or miss depending on the driver revision and your kernel headers. Try downloading/compiling an older driver version.

It was working for me before I switched to using the native airport extreme drivers (which took an upgrade to Dapper) ;)

---

### Post by krrh on 2005-12-13
Ahh.  I've been considering the Dapper route.  Was it difficult getting Broadcom up and running? How reliable has the connection been?

But back to zd1211, I compiled the latest CVS two days ago, and the driver inserts with an error and works unreliably.  I also can't sent the bit rate higher than 1MB.  I suppose this is as good as it gets for a while.

---

### Post by nicodds on 2005-12-14
I'm using the driver available in dapper without any problems and the same has happened for breezy. Maybe the problem is in the fact that you have to work a bit by hand on the interface configuration.

After inserting the usb dongle, you have to do an "ifconfig wlan0 up" and by now the interface should be visible and configurable via "iwconfig".

---

### Post by clamshell77 on 2006-01-07
Hi all. I've tried to use my zd1211 wifi usb for many weeks without any results. After too many changes to my original ubuntu 5.10 (I tried to install anjuta ide 2.x too) i decided to install breezy again. After that without any changes(i've only installed linux-headers-2.6.12-9,gcc3.4,make, and the other software needed  to compile zd1211 driver) I tried to compile the zd1211 driver. I've tried to compile it before, but I had problems with compiling or even if driver has been compiled system didn't correctly recognise my wifi adapter . But now all okay. I'm sending this reply with my wifi connection.

I write my system configuration hoping it is useful for someone: Ibook Clamshell g3 300Mhz "Tangerine", Ubuntu 5.10 for ppc, linux kernel 2.6.12-9-powerpc, router wireless msi RG54G2, zd1211 usb wireless adapter.

P.S.: I've tried driver compilation several times, using different kernels, since December but now...:D 
P.S. 2: To the zd1211 linux driver developers(I downloaded driver from Sourceforge): THANK YOU VERY MUCH!!!

---

