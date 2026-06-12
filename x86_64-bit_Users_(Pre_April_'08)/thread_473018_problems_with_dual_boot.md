---
title: "problems with dual boot"
date: 2007-06-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Dr. Z2A on 2007-06-13
Hey all.  I recently installed Ubuntu on my friend's computer and set up a dual boot with Windows XP Media Center edition (using GRUB as the boot loader).  The system boots into Ubuntu just fine, but problems arise when booting into XP.  When one tries to boot into xp it says "starting up ..." and stops at that point.  I can still mount the partition (NTFS) under linux and all of the data is there.  When I tried to boot into a windows xp install cd (32 bit) and ran FIXMBR the computer just displayed a blank cursor when it booted up afterward until I restored GRUB.

Here is his menu.lst:
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=623b05e4-10a3-4a73-8051-b9c7817b5e7e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=623b05e4-10a3-4a73-8051-b9c7817b5e7e ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=623b05e4-10a3-4a73-8051-b9c7817b5e7e ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
#root		(hd0,0)
rootnoverify	(hd0,0)
#savedefault
#makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP rec.
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

I edited this section a bit earlier:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
#root		(hd0,0)
rootnoverify	(hd0,0)
#savedefault
#makeactive
chainloader	+1
```
I added the rootnoverify thing and commented out savedefault and makeactive.  Before when the root, savedefault, and makeactive lines weren't commented and there was no rootnoverify I think it said "loading ..." and stopped at that point when I tried to boot Windows XP.

---

### Post by Kilz on 2007-06-13
dose

Windows NT/2000/XP rec.

load?

---

### Post by Dr. Z2A on 2007-06-13
> **Kilz said:**
> dose

Windows NT/2000/XP rec.

load?
yeah it boots, thats some kind of recovery partition (FAT32).  It doesn't really do anything but offer to reformat your harddrive though (pretty much useless).

---

### Post by Dr. Z2A on 2007-06-15
*bump* Does anyone have an idea of what I need to do?  I really need to figure this out.

---

### Post by ©TriMoon® on 2007-06-15
Maybe an output of "**fdisk -l**" will help ppl to help you out more...

---

### Post by david_2001 on 2007-06-15
You'll need to run "sudo fdisk -l".  In the meantime, "makeactive" should definitely be uncommented in menu.lst but my suspicion is that the Windows installation itself is broken.

---

### Post by Dr. Z2A on 2007-06-17
heres the output of fdisk -l:
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

	Device      Boot      Start         End      Blocks   Id  System
	/dev/sda1   *           1       29451   236565126    7  HPFS/NTFS
	/dev/sda2           37759       38913     9276120    c  W95 FAT32 (LBA)
	Partition 2 does not end on cylinder boundary.
	/dev/sda3           29452       37414    63962797+  83  Linux
	/dev/sda4           37415       37758     2763180    5  Extended
	/dev/sda5           37415       37758     2763148+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

Another friend of mine also recently informed me that for NTFS resizing I should defrag beforehand.  I neglected to defrag before I resized the NTFS partition so that probably created the problem.

---

