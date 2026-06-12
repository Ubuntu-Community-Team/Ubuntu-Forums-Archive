---
title: "Can't boot xp"
date: 2008-08-04
forum: x86 64-bit Users
---

### Post by Tolian Soran on 2008-08-04
Hi, 

I'm a total newbie to linux, so excuse me if I failed to see the obvious solutions 

Since I installed Ubuntu 7.10 I can't boot win xp from Grub. I read like a million posts about this problem, tried a lot of solutions but nothing doesn't seem to work.

I'm posting grub/menu.lst.....

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=a7ffed38-30aa-4cae-8759-573008af38a5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,8)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-15-generic
root		(hd1,8)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=a7ffed38-30aa-4cae-8759-573008af38a5 ro quiet splash
initrd		/boot/initrd. img-2.6.22-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root		(hd1,8)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=a7ffed38-30aa-4cae-8759-573008af38a5 ro single
initrd		/boot/initrd. img-2.6.22-15-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,8)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a7ffed38-30aa-4cae-8759-573008af38a5 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,8)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a7ffed38-30aa-4cae-8759-573008af38a5 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,8)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Windows XP
root (hd1,0)
map (hd1,0) (hd0,0)
map (hd0,0) hd1,0)
makeactive
chainloader +1
```




Any help would be much appreciated.

---

### Post by tamoneya on 2008-08-04
go into ubuntu and please run the following command so that we can see your partition layout:```
sudo fdisk -l
```Then post the results here.

---

### Post by Tolian Soran on 2008-08-05
```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c786d9e

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1282    10297633+   7  HPFS/NTFS
/dev/hda2            1283        9729    67850527+   f  W95 Ext'd (LBA)
/dev/hda5            1283        5374    32868958+   b  W95 FAT32
/dev/hda6            5375        9729    34981506    7  HPFS/NTFS

Disk /dev/hdb: 320.0 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x67c6d1fd

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1      620181   312571192+   f  W95 Ext'd (LBA)
/dev/hdb5               2       41292    20810664    b  W95 FAT32
/dev/hdb6           82501      347927   133775176+   7  HPFS/NTFS
/dev/hdb7          347928      620181   137215984+   7  HPFS/NTFS
/dev/hdb8           80695       82500      910192+  82  Linux swap / Solaris
/dev/hdb9           41293       80694    19858576+  83  Linux

Partition table entries are not in disk order
```


I think this is it...

---

### Post by tamoneya on 2008-08-05
okay the last set of lines should be this:
```
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by Tolian Soran on 2008-08-05
> **tamoneya said:**
> okay the last set of lines should be this:
```
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

I try that, I just get a blinking _ on the screen ctr+alt+del doesn't work, just a button restart...

Any more ideas? 

btw. Thanks for replaying so quickly and thanks for caring :)

---

### Post by tamoneya on 2008-08-05
do you have any oddities to your windows XP installation like RAID or some weird partitioning.  Your partitioning scheme is rather complex.  Can you tell me a little bit more about what each of your partitions is.

---

### Post by Tolian Soran on 2008-08-05
yeah, I have 3 hard drives (one is not showing at all)

2 ata drives and one sata drive, and one of my cd-rom's is on a PCI ata controler...

If you need more info, just say..

---

### Post by tamoneya on 2008-08-05
okay im not seeing anything obviously wrong.  Therefore my only way I can think of fixing it now is to use the XP install disk in repair mode.  From there you can reinstall the XP boot loader into the mbr.  Then once XP is fixed you use the ubuntu liveCD or super grub to reinstall grub over the windows boot loader.

[http://support.microsoft.com/kb/314503](http://support.microsoft.com/kb/314503)
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Tolian Soran on 2008-08-06
> **tamoneya said:**
> okay im not seeing anything obviously wrong.  Therefore my only way I can think of fixing it now is to use the XP install disk in repair mode.  From there you can reinstall the XP boot loader into the mbr.  Then once XP is fixed you use the ubuntu liveCD or super grub to reinstall grub over the windows boot loader.

[http://support.microsoft.com/kb/314503](http://support.microsoft.com/kb/314503)
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

I will try that, and post the results, tnx for your help...

---

