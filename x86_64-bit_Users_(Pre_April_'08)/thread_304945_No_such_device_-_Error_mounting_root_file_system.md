---
title: "No such device - Error mounting root file system"
date: 2006-11-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by minijai on 2006-11-22
Hello,
I've installed Ubuntu 6.06 LTS since September and all go right.

However yesterday when I started my computer fail.

I get the follow message:

Error mounting root file system and show me a black console (BusyBox) to write commands that don't respond.

I don't installed any software or hardware recently..

I use Ubuntu 6.06 LTS for AMD x64 - generic, using a MAXTOR SATA Hardrive, and my kernel version is 2.6.16-27.
I've proved to start with acpi=off parameter in the kernel but nothing happends!!!!!

If I boot with live-CD I can mount /dev/sda3 and I can access to any file, so the hard drive is OK!!!!

Any idea!!!



The output of fdisk -l is below, and menu.lst too.

```
---------------------------------------------------------------------
Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       19122   153597433+   7  HPFS/NTFS
/dev/sda2           19123       19253     1052257+  82  Linux swap / Solaris
/dev/sda3           19254       30005    86365440   83  Linux
/dev/sda4           30006       30515     4096575    b  W95 FAT32

--------------------------------------------------------------------------
``````
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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
updatedefaultentry=true

## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-27-amd64-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-amd64-generic
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-amd64-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.15-27-amd64-generic
boot

#title          Ubuntu, kernel 2.6.15-26-amd64-generic
#root           (hd0,2)
#kernel         /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sda3 ro quiet splash
#initrd         /boot/initrd.img-2.6.15-26-amd64-generic
#savedefault
#boot

#title          Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
#root           (hd0,2)
#kernel         /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sda3 ro single
#initrd         /boot/initrd.img-2.6.15-26-amd64-generic
#boot

#title          Ubuntu, kernel 2.6.15-25-amd64-generic
#root           (hd0,2)
#kernel         /boot/vmlinuz-2.6.15-25-amd64-generic root=/dev/sda3 ro quiet splash
#initrd         /boot/initrd.img-2.6.15-25-amd64-generic
#savedefault
#boot

#title          Ubuntu, kernel 2.6.15-25-amd64-generic (recovery mode)
#root           (hd0,2)
#kernel         /boot/vmlinuz-2.6.15-25-amd64-generic root=/dev/sda3 ro single
#initrd         /boot/initrd.img-2.6.15-25-amd64-generic
#boot

#title          Ubuntu, kernel 2.6.15-23-amd64-generic
#root           (hd0,2)
#kernel         /boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/sda3 ro quiet splash
#initrd         /boot/initrd.img-2.6.15-23-amd64-generic
#savedefault
#boot

#title          Ubuntu, kernel 2.6.15-23-amd64-generic (recovery mode)
#root           (hd0,2)
#kernel         /boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/sda3 ro single
#initrd         /boot/initrd.img-2.6.15-23-amd64-generic
#boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
-------------------------------------------------------------------------
```Thanks, I need Help!!!!! ](*,)

---

### Post by RAOF on 2006-11-22
That's quite odd.  Could you provide the contents of /etc/fstab, too?  That's where the root filesystem is actually specified.  Maybe that's got wronged somehow?

---

### Post by minijai on 2006-11-23
I've booted with live-cd and mounted "/dev/sda3" and here is the content of the fstab file.!!


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/sda2       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda4       /media/puente   vfat    iocharset=utf8,umask=000 0      0
```



Any idea!!!!
thanks.- ](*,)

---

### Post by minijai on 2006-11-23
[SIZE="3"]Someone has a solution for my problem!!!!
I need help!!!

Thanks.-[/SIZE]

---

### Post by rjpiercy2 on 2006-11-26
Hi Minijai,

I have a similar problem.

One thing I was able to do is edit my grub menu and boot into 2.6.15-25-386.  

That is the last kernel I was able to use sucessfully.  Hopefully this will be an option for you.

As far as why 2.6.15-26-386 and 2.6.15-27-386 hanging on boot, I am still trying to figure that one out.

---

### Post by minijai on 2006-11-27
Hi rjpiercy2,

When I arrived at home I'll probe it.!!

But, I've tried boot from 2.6.15-23 to 2.6.15-27 kernels without any result.
I don't remember if I've installed  the 2.6.15-25 kernel version.
(In addition I run ubuntu in AMDx64.)


thanks..

---

### Post by minijai on 2006-11-27
It doesn't boot!!!!

I've try to boot with 2.6.17-25-amd64-generic kernel but nothings happend!!

I'm in the same point "Error mounting root file system..."

Any idea!!!!
](*,)

---

