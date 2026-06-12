---
title: "partition problem"
date: 2007-11-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by htakai on 2007-11-15
I am installing ubuntu 7.10 on a server with RAID 5, 7 Terabytes. I install the system and then manually configured /dev/sdb1 where the RAID is. I am using parted to create the partition table. Everything goes very well with this and I am able to mount the entire 7 Terabytes. 

HOWEVER, when I reboot the system, the partition is GONE.

I looked at /proc/partitions BEFORE and AFTER the reboot and the partition size for /dev/sdb1 has *magically* changed!!!

Has anyone seen this problem, and if yes, is there a FIX???

Cheers, Helio

---

### Post by fjgaude on 2007-11-18
Well, I've not seen the problem but wonder about the filesystem handling over 4 TBs... the normal kernel is set to use 4 KB blocks and that equates to the 4 TBs. Your 7 TBs is interesting. Have you tried setting the filesystem block size to 8 KB or higher? And are you using ext3 filesystems?

---

### Post by hangfire on 2007-11-18
If you have a single 7TB partition, please reconsider the wisdom of doing this- it may take several hours to FSCK on reboot, even if it is a very fast RAID.

-HF

---

### Post by htakai on 2007-11-18
Thanks for the tips. What I don't understand is that I can mount the file system ONCE and I can create directories, etc.... However, everything disappears when I reboot the system. I will try to partition into smaller segments and see what happens.

---

### Post by htakai on 2007-11-21
An Update on this. We were unable to solve this issue in Ubuntu.

Instead, we installed Debian (the last release) that recognizes the 7 Terabytes as a single partition, and it is working well so far.  We also noticed that Ubuntu gparted does not see the large disk but Debian's gparted does.

---

