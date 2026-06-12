---
title: "Grub Issues"
date: 2005-11-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by ghostpsalm on 2005-11-20
```
grub> geometry (hd0) 9001 255 63
drive 0x80: C/H/S = 9001/255/63, The number of sectors = 144601065, /dev/mapper/via_cfdehjfb
   Partition num: 0,  Filesystem type is reiserfs, partition type 0x83
   Partition num: 1,  Filesystem type is reiserfs, partition type 0x83
   Partition num: 2,  Filesystem type is reiserfs, partition type 0x83
   Partition num: 3,  Filesystem type unknown, partition type 0x83

grub> root (hd0,1)
 Filesystem type is reiserfs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found


```

It all looks fine until that last point, however:

```
root@ubuntu:/# ls -la /boot/grub/
total 177
drwxr-xr-x  2 root root    352 2005-11-20 06:08 .
drwxr-xr-x  5 root root    688 2005-11-21 06:04 ..
-rw-r--r--  1 root root     45 2005-11-20 06:08 device.map
-rw-r--r--  1 root root   8116 2005-11-20 06:08 e2fs_stage1_5
-rw-r--r--  1 root root   7908 2005-11-20 06:08 fat_stage1_5
-rw-r--r--  1 root root   8608 2005-11-20 06:08 jfs_stage1_5
-rw-r--r--  1 root root   3787 2005-11-20 06:08 menu.lst
-rw-r--r--  1 root root   7316 2005-11-20 06:08 minix_stage1_5
-rw-r--r--  1 root root   9588 2005-11-20 06:08 reiserfs_stage1_5
-rw-r--r--  1 root root    512 2005-11-20 06:08 stage1
-rw-r--r--  1 root root 105576 2005-11-20 06:08 stage2
-rw-r--r--  1 root root   9468 2005-11-20 06:08 xfs_stage1_5
```

Can anyone please help me with this?  DO I need to change the permissions?

---

### Post by casper_2095 on 2005-11-20
Not sure how this is a problem specific to 64, but don't see why permissions would be your problem.  Are your RAID issues mentioned in the other thread a complicating factor?  My experience with RAID was to turn off all the fake raid windows-centric rubbish at the bios and do all raiding with software.  The VIA firmware stuff was a collosal waste of time in my experience.  Is there a second disk on this machine?

---

### Post by casper_2095 on 2005-11-20
Where is "bzImage" ?

[http://forums.gentoo.org/viewtopic.php?t=122656](http://forums.gentoo.org/viewtopic.php?t=122656)
Try googling for grub +"error 15"

---

### Post by casper_2095 on 2005-11-20
What about "bzImage" ?

[http://forums.gentoo.org/viewtopic.php?t=122656](http://forums.gentoo.org/viewtopic.php?t=122656)
Try googling for grub +"error 15"

---

### Post by psusi on 2005-11-21
[QUOTE=casper_2095]Not sure how this is a problem specific to 64, but don't see why permissions would be your problem.  Are your RAID issues mentioned in the other thread a complicating factor?  My experience with RAID was to turn off all the fake raid windows-centric rubbish at the bios and do all raiding with software.  The VIA firmware stuff was a collosal waste of time in my experience.  Is there a second disk on this machine?[/QUOTE]


It took me a while but I finally got linux to play nice with the fakeraid.  It is nice because I can dual boot with my old winxp install which is using the proprietary drivers.  Also with software raid, you can not boot from a raid0.  I wrote up a howto on the wiki if you are interested.  

For the OP: permissions should not matter.  Do you have a seperate partition for /boot or is it just part of partition 1?  Could you show the output of the p command in fdisk and /etc/fstab?

If you use a seperate partition for /boot like I do, then THAT is the partition you need to tell grub is the root.

---

### Post by casper_2095 on 2005-11-21
This is raid1...  No. I didn't need a seperate /boot partition. I did investigate and experiment for the need of such. In the end /boot is on the root partition.
```

$ sudo fdisk /dev/sda
Command (m for help): p

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         243     1951866   82  Linux swap / Solaris
/dev/sda2             244        1459     9767520   fd  Linux raid autodetect
/dev/sda3            1460       11185    78124095   fd  Linux raid autodetect
/dev/sda4           11186       24321   105514920    5  Extended
/dev/sda5           11186       24194   104494761   83  Linux
/dev/sda6           24195       24321     1020096   83  Linux

```

---

### Post by casper_2095 on 2005-11-21
I should probably add that
- /dev/sdb is identical
- there are two raid1 partitions
- there are two non-raid partitions per drive

fstab is...
```

# <file system> <mount point>   <type>  <options>               <dump>  <pass>
proc            /proc           proc    defaults                0       0
/dev/md0        /               ext3    defaults,noatime,errors=remount-ro 0       1
/dev/md1        /foo           ext3    defaults,noatime        0       2
/dev/sda5       /bar          ext3    defaults,noatime        0       2
/dev/sdb5       /biddle          ext3    defaults,noatime        0       2
/dev/sda1       none            swap    sw,pri=1                0       0
/dev/sdb1       none            swap    sw,pri=1                0       0
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto      0       0

```

---

### Post by psusi on 2005-11-22
My question about /boot was directed at the OP.  You are running mdraid with no problems aren't you?  

[QUOTE=casper_2095]I should probably add that
- /dev/sdb is identical
- there are two raid1 partitions
- there are two non-raid partitions per drive

fstab is...
```

# <file system> <mount point>   <type>  <options>               <dump>  <pass>
proc            /proc           proc    defaults                0       0
/dev/md0        /               ext3    defaults,noatime,errors=remount-ro 0       1
/dev/md1        /foo           ext3    defaults,noatime        0       2
/dev/sda5       /bar          ext3    defaults,noatime        0       2
/dev/sdb5       /biddle          ext3    defaults,noatime        0       2
/dev/sda1       none            swap    sw,pri=1                0       0
/dev/sdb1       none            swap    sw,pri=1                0       0
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto      0       0

```[/QUOTE]

---

