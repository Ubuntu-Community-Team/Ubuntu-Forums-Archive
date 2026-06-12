---
title: "GRUB 1.5 Error 2"
date: 2008-09-03
forum: x86 64-bit Users
---

### Post by rolsen106 on 2008-09-03
I installed Umbuntu, and when I try to start without CD, I get 
Loading GRUB 1.5
Error 2

Then it freezes.

AMD Athlon with twin hard drives RAID 0.

HELP!

---

### Post by NFITC1 on 2008-09-03
Any error with GRUB essentially means that it can't boot. 

From the GRUB Documentation (which is understandably complicated looking)
> 
Error messages reported by GRUB:

. . .

[Error] 2 : Bad file or directory type
[INDENT]This error is returned if a file requested is not a regular file, but something like a symbolic link, directory, or FIFO.[/INDENT] 
So this means that it's looking for something it can't find or isn't there. The easiest solution to this is to format the Drive you installed it on and try to install again.

Make sure you're installing on the Master HDD and the boot order lists that drive above any other bootable devices.

---

