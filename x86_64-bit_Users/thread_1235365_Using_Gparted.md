---
title: "Using Gparted"
date: 2009-08-09
forum: x86 64-bit Users
---

### Post by wfp on 2009-08-09
So this is what I would like to do I have some extra space on my drive, and want to try out Saybayon64.  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18763   150713766   83  Linux
/dev/sda2           18764       19457     5574555    5  Extended
/dev/sda5           18764       19457     5574523+  82  Linux swap / Solaris

So should I just put in the Ubuntu live cd, and unmount /dev/sda1. Then resize sd1, and then remount sda1. Does that sound correct could use some feedback do not want to bork my system. Thanks

---

### Post by drs305 on 2009-08-09
Your plan will be the easiest to execute. Remember to back up your really important files before doing any repartitioning work.

Also check that both sda1 and the swap partition (sda5) are unmounted. You can umount swap in gparted by selecting the partition and then Partition, Swapoff.

---

### Post by wfp on 2009-08-09
Great Thank you for your help.

---

### Post by Barafu Albino Cheetah on 2009-08-09
**First**: If you ever use fdisk and any of its GUIs, be sure that you either use 32bit kernel and app, or both 64bit kernel and app. If you use 32bit fdisk, compiled on 32bit kernel, with 64bit kernel, you may mess up everything. Ubuntu liveCD is OK in this aspect, but there can be problems with sabayon and chrooting. 
**Second**: Your plan in resizing is OK. Just remember that you may have only 4 primary partitions. Don't bother with LVM before trying it in virtualbox. 
**Third**: Be very cautious with bootloader. My advise to you is to install sabayon's loader onto floppy, then add sabayon to the ubuntu launcher.

---

