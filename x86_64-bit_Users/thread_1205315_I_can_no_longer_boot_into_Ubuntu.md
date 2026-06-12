---
title: "I can no longer boot into Ubuntu"
date: 2009-07-05
forum: x86 64-bit Users
---

### Post by acidblue on 2009-07-05
After installing the linux-rt kernel, i can't boot my pc.
At first i got an cmos check sum error which usually means 
the cmos battery is dead, so i replaced it.

I no longer get the error but now all i get is a >Grub prompt.
What happened?
Is grub now corrupt/missing?
How do i re-install grub?

I checked my bios and all my drives are detected, resaved cmos.
still can''t boot Ubuntu.
Pleas advise.

---

### Post by drave99 on 2009-07-08
use a live recovery cd. system rescue or somesuch

---

### Post by j0eb0b on 2009-07-10
Download SuperGrub.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Save it to a CD as an ISO file.  Set you PC bios to look for the CD/DVD drive as the first boot device.  Boot up SuperGrub and have it fix your MBR.  It is easy to use and there is documentation as well as a help forum if you get stuck.

Good Luck.

---

