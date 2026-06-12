---
title: "Sata &amp; Intel64 Hard Drive Woes"
date: 2007-02-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Margueritte on 2007-02-16
Good morning
I have just installed an Intel 775 Core2 "Isleton" , with a Western Digital 160GB SATA Drive.
No Windows installed, only Ubuntu / Kubuntu 6.06 Dapper AMD64.

My problem is that my machine is not booting from the hard drive, only booting from CD.

I am still pretty new at this, have been running Ubuntu for approx 6 months.

I have checked various files that have been mentioned in other Forum Postings, here is the list.


fdisk - info


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1             5099    40957686   83  Linux
/dev/sda2            5100         19122   112639747+  83  Linux
/dev/sda3           19123        19457     2690887+  82  Linux swap / Solaris

cat /etc/fstab - info
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc               /proc            proc    defaults        0       0
/dev/sda1       /                   ext3    defaults,errors=remount-ro 0       1
/dev/sda2       /home           ext3    defaults        0       2
/dev/sda3       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


device.map

(hd0)   /dev/sda


Don't seem to find menu.1st, does this need to be created??


Thank you for your help
Margueritte

---

