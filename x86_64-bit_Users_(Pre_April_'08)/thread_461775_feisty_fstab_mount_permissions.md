---
title: "feisty fstab mount permissions"
date: 2007-06-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by brian183 on 2007-06-02
I have a problem trying to get the owner set to my login of mounted drives within fstab.  I have two brand new drives with freshly made primary partitions and ext3 filesystem.  Any way I try mounting these drives I cannot get them to be owned by my login name (NOT ROOT) therefore I cannot write to either of these drives.  I've been at this all day and I can't seem to solve it.

Trying to mount /dev/sdb1 and /dev/sdc1.

My fstab now:
[PHP]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0cc6c339-1f47-4939-a740-745413e9e72f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=02f126e2-b830-482e-84e2-99ea609deb86 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


/dev/sdb1	/media/HDD1	ext3	rw,user		0	1
/dev/sdc1	/media/HDD2	ext3	rw,user		0	1[/PHP]


fdisk list:

[PHP]Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       47890   384676393+  83  Linux
/dev/sda2           47891       48641     6032407+   5  Extended
/dev/sda5           47891       48641     6032376   82  Linux swap / Solaris

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801   83  Linux

Disk /dev/sdc: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       36481   293033601   83  Linux
[/PHP]


My system specs:
nvidia 590 chipset
AMD64 X2 4200+ CPU
geforce 7900 GS KO
ubuntu 7.04 64 bit


Thank you.

---

### Post by Kilz on 2007-06-02
Have you just tried to change the owner of the folder you are mounting the drive to?
```
sudo chown -R YourLogin:users media/HDD1
sudo chown -R YourLogin:users media/HDD2
```
Change YourLogin to your username

---

### Post by brian183 on 2007-06-02
That did it.  I could have sworn I tried that exact command but I kept getting "operation not permitted" even with sudo.
Thanx

---

