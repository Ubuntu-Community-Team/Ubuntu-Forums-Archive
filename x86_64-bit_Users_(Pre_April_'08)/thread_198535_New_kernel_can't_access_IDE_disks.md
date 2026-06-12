---
title: "New kernel can't access IDE disks"
date: 2006-06-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by mooshie on 2006-06-17
Hello,

I'm running 6.06 with three Seagate Barracuda 80gb ATA drives. One is a root disk on one device and two others on another device. When I installed the base system, all three were accessible, but when I upgraded to 6.06, only the root drive was mountable. The other drives can be browsed with fdisk, and they show up in the disk utility, but I cannot mount them, or even format them. The two disks are using XFS, but my root disk is also using XFS.

Is it possible to be able to "see" drives without being able to format them (the error I get is that they are busy)? I've been messing with this for almost a week with no avail... thanks for any help

Nate


P.S. Almost every IDE option in the kernel build is checked, including XFS support.

---

### Post by Kablooie!! on 2008-01-15
Hi Mooshie,

Did you ever solve this problem?  I'm having the same problem right now.

Thanks,
Kablooie!!

---

