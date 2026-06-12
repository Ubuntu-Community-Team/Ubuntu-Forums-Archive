---
title: "Network on Ubuntu x64"
date: 2007-02-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by JKoder on 2007-02-23
Hello
I tried Ubuntu X64 and beside the splash screen is a bit ugly ( does not matter for the moment ), i have some problems with my ethernet card.
I have a Realtek ethernet card and i know there is a module named rt1896 or something like that. If i insert the required module in the Kernel , i will have network, but the Network icon in Gnome it telling me that there is not device available. How can i solve this so the network icon will tell me that there is a device ?

Thank you !
( i am really new to 64 bit OS )

---

### Post by xopher on 2007-03-12
The network icon, ie. the panel applet, is probably just misconfigured.

do a ifconfig -a to check what your ethernet device is called, then change the device value the applet uses to what it should use. eg. from eth0 to eth1 if that's the case.

---

