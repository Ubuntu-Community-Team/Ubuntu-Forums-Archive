---
title: "Ndiswrapper"
date: 2008-01-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by enoughsaid05 on 2008-01-04
I have already installed the driver for my laptop wireless device, but it seems that nothing is working.

NDISWRAPPER shows that the driver has already been installed. But how do I choose which driver to use for my wireless?

---

### Post by luisromangz on 2008-01-04
You should try running lsmod, to see if ndiswrapper is being loaded. It could be that another driver (for example bcm43xx, although I don't know bucause you didn't tell which is your wireless card) is being loaded. If so, you should blacklist that driver, writing an entry in /etc/modprobe.d/blacklist. You should restart after doing that.

You should check also what ifconfig and iwconfig tells you when you make changes.

---

### Post by lvleph on 2008-01-04
did you run 
```
modprobe ndiswrapper
```
in terminal and then add ndiswrapper to /etc/modules? 
```
sudo gedit /etc/modules
``` Try that and see if things work.

---

