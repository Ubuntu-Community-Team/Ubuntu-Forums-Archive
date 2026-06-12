---
title: "Server 6.06 v64bit NOT INSTALLING on New Intel DG33BU"
date: 2007-06-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by mcgheen2 on 2007-06-24
Im trying to install ubuntu server 6.06 64bit on my Intel DG33BU board with (G33/ICH9/82566) chips, w/sata 160g western digital. I changed the option in bios for (Configure sata as) to IDE when I install it goes to the load screen asking what options i want to do.  I selet install on hard disk then it says loading linux kernel, it goes to 100% then to the next screen (Decompressing linux...Done. then its says booting kernel. and it just sits there, I let it sit for over half hour. Still nothing i tried the 32 bit v. also, still same thing. Ive tried to install windows thinking maybe theres a problem with hardware, but it installs just fine. Anyone have a clue or direction?

---

### Post by tooql4life on 2007-06-29
Kindly delete all the partitions and try...It should work ](*,)](*,)

---

### Post by smothepeanut on 2007-07-02
Same problem here and with 7.04.

I tired the text install and worked fine however the kernel (2.6.20) doesn't support the chipset.

I upgraded the kernel to 2.6.22 via the package manager, however devices (mainly the on board network card) wont work.


Any help would be grateful.

Thanks

---

### Post by jespdj on 2007-07-02
Ubuntu 6.06 (Dapper Drake) does not install on my system either, and it is because of a bug in the Linux kernel.

I have an Asus motherboard with an Intel P965 chipset (Asus P5B Deluxe/WiFi-AP). This chipset doesn't support IDE (it only supports SATA) so Asus put a separate IDE controller on the motherboard, by JMicron. My CD/DVD drive is connected to that controller.

Linux can't access the CD because there's a kernel bug, so that it doesn't work with the JMicron controller. This bug was solved in Ubuntu 6.10.

Your problem sounds like it could be the same thing. Have you tried a newer version of Ubuntu than 6.06?

---

### Post by fugitivo on 2007-07-04
I'm using Intel DG33BU and Ubuntu 7.04 Desktop. Installation worked out of the box, but no network card support (had to download and compile intel drivers) and should use VESA for Xorg (intel driver doesn't work, maybe kernel doesn't support this chipset).
Upgrading to gutsy and kernel 2.6.22-7 seems to detect the chipset, but network card doesn't work (it's weird, icmp packets work, like ping, but not tcp or udp), and xorg intel driver crashes when using opengl or fullscreen apps.

---

