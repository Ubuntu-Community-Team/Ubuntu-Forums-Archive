---
title: "Mounting problem"
date: 2007-02-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Acoja on 2007-02-10
I just updated my 64 Edgy with the new kernel and i have a slight problem.
The problem is mounting the NTFS partitions on boot up. I checked everything, and as I can see the fstab looks very normal, but it won't mount my partitions. My fstab looks like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=b17e4027-a42f-4ae9-8f1e-074eba01d038 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=78F8C54AF8C506FA /media/windows    ntfs-3g    defaults,locale=en_US.utf8    0       0
# /dev/sda5
UUID=205C23EA5C23BA04 /media/D       ntfs-3g    defaults,locale=en_US.utf8    0       0
# /dev/sda6
UUID=208C26BA8C2689FC /media/E       ntfs-3g    defaults,locale=en_US.utf8    0       0
# /dev/sda7
UUID=8051cd54-173f-45bd-9aab-b6b8379f2853 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

``` 

IF somebody knows how to fix my little problem, i would be much obliged.

---

