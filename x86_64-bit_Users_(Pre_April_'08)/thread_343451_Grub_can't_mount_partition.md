---
title: "Grub can't mount partition"
date: 2007-01-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by oddabe19 on 2007-01-21
Hey guys,
So I installed 64bit edgy today, and i've been using linux for about 6 years and never ran into this problem (this is also the first time i've used 64bit though).

I formated / as xfs instead of ext3 (i like xfs).  So when I rebooted, grub yells "YO! Error 17 Dude! I can't mount the partition!"

I assume it's because of the xfs format, but does anyone else have this problem?

/ is on hdb2, /boot is on hdb1, with hdb set to boot in bios.  All other systems work (XP Pro, 2k)

---

### Post by kuja on 2007-01-21
Weird, so long as you have /boot on a non-xfs partition, it should boot okay .. not sure what to tell you.

---

### Post by oddabe19 on 2007-01-21
actually, i went and reinstalled it with ext3.

I still have the same problem.

I have no idea why. Winxp launches great, but memtest, and the kernels can't be mounted for some odd reason or another.

---

