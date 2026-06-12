---
title: "Continuing problems with mdadm and Raid"
date: 2008-06-18
forum: x86 64-bit Users
---

### Post by ddales on 2008-06-18
Hi all,

I'm having a problem with my raid device which I use strictly for data, no booting from there.

I have a 200G drive which contains the OS and from which I boot.

I also have 4x400G drives configured in a RAID5 with mdadm which I use for only storing data.

The problem is Hardy seems to randomly renumber the /dev entries for my partitions screwing up my mdadm config.  Generally, my 200G drive is recognized as /dev/sda1.  My RAID is generally recognized as /dev/sd[b c d e]1.  Every once in a while, and I can't seem to recreate the problem at will, my 200G drive will be recognized as /dev/sde1 which really confuses my mdadm/RAID.

#####  FDISK
root@ubu:~# fdisk -l

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bc71a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24041   193109301   83  Linux
/dev/sda2           24042       24792     6032407+   5  Extended
/dev/sda5           24042       24792     6032376   82  Linux swap / Solaris

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ba0bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801   fd  Linux raid autodetect

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00077874

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       48641   390708801   fd  Linux raid autodetect

Disk /dev/sdd: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006e295

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       48641   390708801   fd  Linux raid autodetect

Disk /dev/sde: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000978be

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       48641   390708801   fd  Linux raid autodetect

Disk /dev/md0: 1200.2 GB, 1200257236992 bytes
2 heads, 4 sectors/track, 293031552 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
#####

##### MDADM.CONF
root@ubu:~# cat /etc/mdadm/mdadm.conf
DEVICE partitions
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=9ad6c7c9:756e61fa:3d9f210c:139ce351 devices=/dev/sdb1,/dev/sdc1,/dev/sdd1,/dev/sde1
#####

##### FSTAB
root@ubu:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=805a0afe-4ef2-47aa-a241-4911c0cc2847 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=bee1e46e-ae02-4d4c-b616-abdc91b150d3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#
# Data Directory Shared Samba
/dev/md0 /data auto defaults 0 3
#####


Any ideas?

---

