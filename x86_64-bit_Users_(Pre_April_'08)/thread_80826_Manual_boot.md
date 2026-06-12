---
title: "Manual boot"
date: 2005-10-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by kioshi on 2005-10-23
Hi people, i have a doubt...  i ve been trying to install yaboot again with no success... but I managed to boot my hd system from the CD using hd:3,/boot/vmlinux but it says i have to configure the root to root=/dev/hda3 and I dont know how to do that.... Could anyone help me with manual booting the system in the HD from the yaboot in the Ubuntu PPC CD?

Thanks!

---

### Post by Rovenhot on 2006-01-01
The "root=..." is an argument to the kernel.

By the way, how did you boot using that kernel?  I had the same problem, and was given the same instructions, but I'm not clear as to how execute the kernel.  Is it done on the Open Firmware command line?

---

