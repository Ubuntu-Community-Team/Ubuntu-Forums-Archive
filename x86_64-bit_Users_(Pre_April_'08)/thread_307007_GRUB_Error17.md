---
title: "GRUB Error:17"
date: 2006-11-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by vikrant_me on 2006-11-25
My Ubuntu wont start and gives a GRUS error:17  is there a fix without having to re-install GRUB? Here are my sudo gedit /etc/fstab and sudo fdisk -l

fstab:

unionfs / unionfs rw 1 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda7 swap swap defaults 0 0


fdisk -l:

ubuntu@ubuntu:/etc$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           2        9729    78140160    f  W95 Ext'd (LBA)
/dev/sda5               2        5223    41945683+   b  W95 FAT32
/dev/sda6            5224        7518    18434556   83  Linux
/dev/sda7            7519        7836     2554303+  82  Linux swap / Solaris
/dev/sda8            7837        9143    10498446    b  W95 FAT32
/dev/sda9            9144        9729     4707013+   b  W95 FAT32

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2677    21502971    7  HPFS/NTFS
/dev/sdb2            2678        9728    56637157+   f  W95 Ext'd (LBA)
/dev/sdb5            2678        9728    56637126    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3189    25615611    7  HPFS/NTFS
/dev/sdc2            3190        9729    52532550    f  W95 Ext'd (LBA)
/dev/sdc5            3190        9729    52532518+   7  HPFS/NTFS

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/sdd2            2551        9729    57665317+   f  W95 Ext'd (LBA)
/dev/sdd5            2551        5161    20972826    b  W95 FAT32
/dev/sdd6            5162        7772    20972826    b  W95 FAT32
/dev/sdd7            7773        9729    15719571    b  W95 FAT32

Also my /boot does not have a /grub/menu.lst :

ubuntu@ubuntu:/boot$ sudo ls -a -ll
total 10331
-rw-r--r-- 1 root root  260598 2006-05-23 14:09 abi-2.6.15-23-amd64-generic
-rw-r--r-- 1 root root   62867 2006-05-23 13:44 config-2.6.15-23-amd64-generic
-rw-r--r-- 1 root root 7787184 2006-05-31 01:14 initrd.img-2.6.15-23-amd64-generic
-rw-r--r-- 1 root root   94760 2005-10-25 10:36 memtest86+.bin
-rw-r--r-- 1 root root  887284 2006-05-23 14:09 System.map-2.6.15-23-amd64-generic
-rw-r--r-- 1 root root 1484727 2006-05-23 14:09 vmlinuz-2.6.15-23-amd64-generic

---

### Post by geek_Man on 2006-11-26
Vikrant_me,
when GRUB gives you that error, is that after you have chosen what OS to boot? Or does it give you Error 17 without even showing you the menu? You're menu.lst (BTW), should be in /boot/grub/menu.lst. So cd to /boot/grub and then ls -a -ll.

---

### Post by vikrant_me on 2006-11-26
I havent setup my GRUB for multiboot i just press F8 and choose the HDD on which linux is and boot frm it, when i choose the HDD the eeeor comes up before anything loads, also i dont have a /boot/grub folder! see:

ubuntu@ubuntu:/$ cd /boot/grub
bash: cd: /boot/grub: No such file or directory

when i did mount in /dev/sda6 /mnt/one the /mnt/one/boot/grub/menu.lst shows me:


title Ubuntu, kernel 2.6.15-27-amd64-generic
root (hd0,7)
kernel /boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/sda8 ro quiet splash
initrd /boot/initrd.img-2.6.15-27-amd64-generic
savedefault
boot

title Ubuntu, kernel 2.6.15-27-amd64-generic (recovery mode)
root (hd0,7)
kernel /boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/sda8 ro single
initrd /boot/initrd.img-2.6.15-27-amd64-generic
boot

title Ubuntu, kernel 2.6.15-23-amd64-generic
root (hd0,7)
kernel /boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/sda8 ro quiet splash
initrd /boot/initrd.img-2.6.15-23-amd64-generic
savedefault
boot

title Ubuntu, kernel 2.6.15-23-amd64-generic (recovery mode)
root (hd0,7)
kernel /boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/sda8 ro single
initrd /boot/initrd.img-2.6.15-23-amd64-generic
boot

title Ubuntu, memtest86+
root (hd0,7)
kernel /boot/memtest86+.bin
boot

(I have a feeling the path is incorrect as this is wher my linux is :
/dev/sda6 5224 7518 18434556 83 Linux
/dev/sda7 7519 7836 2554303+ 82 Linux swap / Solaris)

and 

ubuntu@ubuntu:/boot$ ls -a -ll
total 10331
-rw-r--r-- 1 root root  260598 2006-05-23 14:09 abi-2.6.15-23-amd64-generic
-rw-r--r-- 1 root root   62867 2006-05-23 13:44 config-2.6.15-23-amd64-generic
-rw-r--r-- 1 root root 7787184 2006-05-31 01:14 initrd.img-2.6.15-23-amd64-generic
-rw-r--r-- 1 root root   94760 2005-10-25 10:36 memtest86+.bin
-rw-r--r-- 1 root root  887284 2006-05-23 14:09 System.map-2.6.15-23-amd64-generic
-rw-r--r-- 1 root root 1484727 2006-05-23 14:09 vmlinuz-2.6.15-23-amd64-generic

                i guess i have to re-install grub...il need help with that i have read on this forum how to but some or the other error pops up.

---

### Post by vikrant_me on 2006-11-27
deleted

---

### Post by geek_Man on 2006-11-27
You could reinstall GRUB, I guess. It's really easy to do.
In the terminal type:```
grub
```then type ```
root (hd0,5)
```then```
setup (hd0)
```it'll do some stuff and if it all goes well it'll say it's done. Then type: ```
quit
```
HOPEFULLY GRUB will work then, but if not we can go over your menu.lst. We'll get it to work eventually, so don't give up!

---

### Post by born yesterday on 2006-12-02
absolute first time around the block here, so take this for what it's worth...

Been sittin on this error 17 problem for a couple of days.  Read a couple hundred posts about it, then saw some guy here->> [http://forums.gentoo.org/viewtopic.php?t=120802](http://forums.gentoo.org/viewtopic.php?t=120802) mention that he forgot to update his BIOS.  Checked mine and of course, it's set to boot from the CD drive first then the hard drive because, of course, I was just working off of the live CD.  Anyway, changed to boot from the hard drive only, rebooted, and error 17 went away.  

Since CD drive was first boot device, was grub treating that like my hda?

---

### Post by geek_Man on 2006-12-02
If it was then that would be VERY strange. I've never heard of that. Now what if you try it again with the CD back in?

---

