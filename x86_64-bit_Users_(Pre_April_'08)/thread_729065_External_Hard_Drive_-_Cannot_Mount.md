---
title: "External Hard Drive - Cannot Mount"
date: 2008-03-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by snakevet on 2008-03-19
I have just installed Gutsy 64 bit.  Unfortunately I have had nothing but problems since I made the switch.  I was using PCLinux but wanted a 64 bit system so I tried the 'buntus.  My latest problem (# 12 in this weeks glitch list)  is that I cannot mount my external hard drives.  They are ntfs. The fdisk output is below.  They mounted seamlessly under PCLinux with no problems at all, but everytime I try to mount them in the 'buntus I get the following error.

"hal-storage-removable-mount-all-options refused uid 1000"  I was hoping they would mount automatically, but they don't.  Any suggestions?

fdisk output.

Disk /dev/sdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6b210fac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       36481   293033601    7  HPFS/NTFS

Disk /dev/sdd: 122.9 GB, 122941341696 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac1035b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           2       14946   120045712+   f  W95 Ext'd (LBA)
/dev/sdd5               2       14946   120045681    7  HPFS/NTFS

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001dc2b

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdk: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5e46d638

   Device Boot      Start         End      Blocks   Id  System
/dev/sdk1   *           1       19457   156288321    7  HPFS/NTFS

---

### Post by felker2 on 2008-03-19
Does this help: [http://ubuntuforums.org/showthread.php?t=601210](http://ubuntuforums.org/showthread.php?t=601210) ?

---

