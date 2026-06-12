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

### Post by Margueritte on 2007-02-16
Addendum to Post

I found menu1st  - this is the output of it :

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
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-23-amd64-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-amd64-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-23-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by mixmaster on 2007-02-16
You do not appear to have any partition flagged as bootable.  Here is my fdisk output:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3845    30884931   83  Linux
/dev/sda2           18667       19457     6353707+   5  Extended
/dev/sda3            3846       18666   119049682+  83  Linux
/dev/sda5           18667       19457     6353676   82  Linux swap / Solaris


Note the * on the first partition.

If you boot from CD you should be able to flag the bootable partition using your favourite partion management tool

---

