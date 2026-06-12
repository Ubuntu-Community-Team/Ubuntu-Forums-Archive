---
title: "Dual boot ubuntu x86 - AMD64"
date: 2009-10-13
forum: x86 64-bit Users
---

### Post by notrump3 on 2009-10-13
I had dual boot Vista-Ubuntu (8.0.4 i386 Desktop) working great.  It is time to get rid of Vista and I decided to install Ubuntu (8.0.4 AMD64) on that partition instead.

Install worked great, all is loaded, but now GRUB can not find my previous partition!

I've gone through several threads and can't seem to find something that works.  

From [http://ubuntuforums.org/showthread.php?t=1093613](http://ubuntuforums.org/showthread.php?t=1093613)  I ran the boot_info script and it provided the attached output.

I realize the structure is not optimal at this point.  It is a function of when it was installed.  I need both partitions working for the forseable future so would prefer to not wipe out that partition.

Fundamentally I want to be able to boot to sda3 (AMD64) or sda5 (i386).

All help is welcome!

---

### Post by sub50hz on 2009-10-14
I'm not sure I understand... if there's no vital data left from Vista, why not re-install Ubuntu while formatting the entire drive, and use Gparted to create another partition later on?

---

### Post by notrump3 on 2009-10-14
There is still valid data and configurations on the other ubuntu partition that I'd prefer to keep.

I've since tried a GRUB reinstall that suggested to use the LiveCD and not format the partitions... this ended in an error when writing to the sda1 (boot) parition.  Now I can't boot off the hd at all!

---

