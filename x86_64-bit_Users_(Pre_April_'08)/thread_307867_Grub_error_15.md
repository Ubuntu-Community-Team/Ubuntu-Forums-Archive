---
title: "Grub :error 15"
date: 2006-11-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by vikrant_me on 2006-11-27
When i bootup this is the output on my screen:

Booting ubuntu kernel 2.6.15-27-amd64-generic
root(hd0,7)
Filesystem is fat, partitiontype 0xb
kernel /boot/vimlinuz-2.6.15-27-amd64-generic
root=/dev/sda8 ro quiet splash
Error15:File not found

.............................................................................

This is my menu.lst

title           Ubuntu, kernel 2.6.15-27-amd64-generic
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/sda8 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-amd64-generic
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-amd64-generic (recovery mode)
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/sda8 ro single
initrd          /boot/initrd.img-2.6.15-27-amd64-generic
boot

title           Ubuntu, kernel 2.6.15-23-amd64-generic
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/sda8 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-amd64-generic
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-amd64-generic (recovery mode)
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/sda8 ro single
initrd          /boot/initrd.img-2.6.15-23-amd64-generic
boot

title           Ubuntu, memtest86+
root            (hd0,7)
kernel          /boot/memtest86+.bin
boot
 
...................................................................

This is my sudo fdisk -l

ubuntu@ubuntu:/mnt/window/boot/grub$ sudo fdisk -l

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

..................................................................................................

I have a feeling its just a issue with the wrong path to my linux partition, aslo cd /boot/grub  gives me:

ubuntu@ubuntu:/boot$ cd grub
bash: cd: grub: No such file or directory

but when i mount it and then the grub folder is visible with all the files in it, dunno if thats really a problem*

---

### Post by geek_Man on 2006-11-27
It is looking in the wrong partition. Boot up with the Live CD and in the terminal type:```
gksudo gedit /dev/sda6/boot/grub/menu.lst
``` From there change all the entries of that kernel to (hd0,5). Example:```
title Ubuntu, kernel 2.6.15-27-amd64-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/sda8 ro quiet splash
initrd /boot/initrd.img-2.6.15-27-amd64-generic
savedefault
boot
``` That should work.

---

