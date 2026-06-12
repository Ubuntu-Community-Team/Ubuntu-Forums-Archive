---
title: "Problems dual-booting Vista &amp; Ubuntu 8.04"
date: 2008-07-07
forum: x86 64-bit Users
---

### Post by jje2 on 2008-07-07
_*Preamble:*_
My dad recently bought an HP Pavilion with an Intel Core 2 Quad 64bit CPU, 4GB RAM, etc., running Windows Vista (64bit). He does NOT have the software installation discs; just the computer, as it arrived (presumably OEM installation).

He decided he'd try Ubuntu by setting up a dual-boot installation. We got it from
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
(Selected options: Ubuntu 8.04 LTS Desktop Edition; 64bit AMD and Intel computers; United States OSU Open Source Lab.)

We burned the image file to disc, placed it in the drive, restarted the computer, went through all the installation steps (specifically, as delineated here: [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1) ), and everything seemed to go just fine (shrinking drive, and full installation; copying files, etc.).

*_The Problem_*
I cannot get the standard text menu to come up, from which to make an O/S boot-up selection. I saw that GRUB was being run as one part of the Ubuntu installation process, near the end. But, it is apparently having some problems, because the only thing that ever happens now is that Vista boots up exactly as if nothing whatsoever has happened to the computer. (I don't even know for SURE that Ubuntu really did install, although it behaved in perfect accordance with having done so---other than it being apparently invisible to boot-up.)

A little additional info:
[LIST]
[*] I freed 30GB of disk space for Ubuntu (through Vista's shrink interface). (This created 30GB of unallocated disk space.)
[*] I checked the burned CD for defects, and it passed inspection.
[*] I tried running a little more GRUB stuff to get it to work, but nothing has made any detectable difference.
[*] For any additional details, you can refer to the installation steps I followed, by referring to the apcmag link I provided above (which I followed exactly).
[/LIST]

**Final note: Although I'm not incompetent, I am somewhat of a Linux newbie (and definitely a multi-boot newbie), so please gear your responses accordingly. Thank-you, in advance! :)**

---

### Post by lisati on 2008-07-07
One thing to be aware of is a "Recovery Partition" - make sure you don't accidentally delet it!

If you boot from the Ubuntu LiveCD, go to the Terminal (it's on the Applications->Accessories menu) and type in
```
fdisk -l
```- post the output back here, and we'll be able to see what's actually there on your machine.

EDIT: There are probably other details that would be useful..like the contents of the data file used by Grub to choose between the different OS's on your system, but we can get to that in a moment.

---

### Post by erfahren on 2008-07-07
since it appears that GRUB didn't install correctly and the original master boot record (MBR) is still intact you might want to back it up - if you ever decide to remove Ubuntu it may make it easier
-- follow the Back up and Restore your MBR link [here]("http://www.users.bigpond.net.au/hermanzone/p18.htm#Restore_your_MBR_from_a_backup")

Another thing you might want to do before working on GRUB is boot back into Vista and burn off the Recovery DVD(s) - (most brand-name PCs don't come with disks anymore but provide a way to burn off a set - they usually have that recovery partition Lisati mentioned as well) - check the PC's manual for instructions (it should be in a folder off of the Start > All Programs menu)

Anyway - once you are prepared and determine if Ubuntu was actuaaly installed you can try setting up GRUB again using the LiveCD see:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[How to install Grub from a live Ubuntu cd]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by jje2 on 2008-07-07
Ok, I tried running fdisk -l, and it listed absolutely nothing.

Fortunately, I thought to try running it as: sudo fdisk -l, and it returned the following (which I am manually entering from the other computer's screen, so hopefully has no typos).

```
Disk /dev/sda: 360.0 GB, 3600080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

Device		Boot	Start	End	Blocks		Id	System
/dev/sda1	*	1	38576	309857968	7	HPFS/NTFS
/dev/sda2		38577	42400	30716280	5	Extended
/dev/sda3		42401	43777	11060752+	7	HPFS/NTFS
/dev/sda5		38577	42237	29406951	83	Linux
/dev/sda6		42238	42400	1309266		82	Linux swap / Solaris

Disk /dev/sdb: 360.0 GB, 3600080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

Device		Boot	Start	End	Blocks		Id	System
/dev/sdb1	*	1	38576	309857968	7	HPFS/NTFS
/dev/sdb2		38577	42400	30716280	5	Extended
/dev/sdb3		42401	43777	11060752+	7	HPFS/NTFS
/dev/sdb5		38577	42237	29406951	83	Linux
/dev/sdb6		42238	42400	1309266		82	Linux swap / Solaris
```

---

### Post by jje2 on 2008-07-07
Oh goody. I just found out that Dad ran some RAID 1 setup on the computer, which may or may not be affecting this. (Yet again, I simply lack the experience to know one way or the other.)

I just removed the side of the computer case to determine for certain how many physical drives there are: two. They are apparently identical, which is consistent with the fdisk report (two 360GB drives).

---

### Post by captainzott on 2008-07-20
when you get to the stage of modifying your menu.lst, (located:filesystem/boot/grub), heres a copy of mine which may help

All # are reminders and are not run. I boot into Vista by default, so my default is 4, (unbuntu would be 1)

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
default		4

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
# kopt=root=UUID=c0b39a10-9871-4ad6-b54c-52076bf6b2de ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=c0b39a10-9871-4ad6-b54c-52076bf6b2de ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=c0b39a10-9871-4ad6-b54c-52076bf6b2de ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

