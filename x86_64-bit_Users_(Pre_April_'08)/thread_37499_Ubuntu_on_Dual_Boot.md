---
title: "Ubuntu on Dual Boot"
date: 2005-05-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by jimwinfrey on 2005-05-27
My old dedicated Ubuntu computer died.  I want to install Ubuntu as a dual boot on a computer that has another distro on it.  I created a Reiser partition but Ubuntu does not want to go there, it wants to create its own partition out of the partition that has the other distro.  Are there any pitfalls in going ahead with this action?  I recall the first time I ever tried it, Ubuntu destroyed the boot record for the other distro, probably due to my lack of knowledge of what I was doing.  Any guidance would be appreciated.

Thanks,

Jim

---

### Post by jasmuz on 2005-05-27
[QUOTE=jimwinfrey]My old dedicated Ubuntu computer died.  I want to install Ubuntu as a dual boot on a computer that has another distro on it.  I created a Reiser partition but Ubuntu does not want to go there, it wants to create its own partition out of the partition that has the other distro.  Are there any pitfalls in going ahead with this action?  I recall the first time I ever tried it, Ubuntu destroyed the boot record for the other distro, probably due to my lack of knowledge of what I was doing.  Any guidance would be appreciated.

Thanks,

Jim[/QUOTE]
 Ubuntu likes for default Ext3 partitions.
But when you are about to install, and it asks you to delete the hole disk, do a expert install...there you can specify to use to that partition.

---

### Post by fistfullofroses on 2005-06-25
ALSO:

I would not recommend installing Ubuntu or any distro after installing Windows 
XP 32bit. Install Linux before install XP, and thereafter install a new boot manager
such as (GRUB or LILO or XOSL or whatever). Everytime I have known people to install Linux after WindowsXP, Windows XP becomes unbootable.

---

