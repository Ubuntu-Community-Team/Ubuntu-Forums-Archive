---
title: "Problems with ATI X1300PRO"
date: 2007-12-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by electronul on 2007-12-13
I have use this [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")
guide to install the ATI X1300PRO PCI-Express video card. The problem is when I run fglrxinfo the driver listed is MESA, and NOT ATI. I tried to re-enable the ATI accelerated graphics driver in the restricted drivers, but that didn't work. After that I've made a search of the xserver-xorg-video-all packages, in the Synaptic Package Manager, and after that I've remove them. And restart.
The problem, when I use the fglrxinfo the driver isntalled is still MESA, and NOT ATI.
If anyone knows a solution, please HELP!!!

P.S. I know there are a lot of threads for this video card, or ATI video cards... and I've read part of them, but I can't get it to work... not at all, and it's driving me crazy...

---

### Post by elliotjreed on 2007-12-13
I have the same card, all I did was:

```
dpkg-reconfigure xserver-xorg
```

perhaps with a* sudo* in fornt

when a list appears, select fglrx

it should work from there, if it fails and you get a blank screen: run ubuntu safe mode (from GRUB) and type the command again selecting MESA

---

