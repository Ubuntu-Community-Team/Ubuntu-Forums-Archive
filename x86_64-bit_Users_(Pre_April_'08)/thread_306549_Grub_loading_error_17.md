---
title: "Grub loading error 17"
date: 2006-11-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by blroth on 2006-11-25
Big trouble!  I am running XP on a SATA drive, Dapper on another drive.  All was fine until I added another SATA drive and installed edgy.  Upon the reboot after installing edgy, I get the following error message:

Grub loading, stage 1.5
Grub loading, please wait error 17

and the system hangs.

F8 will allow win XP to boot,  the above message on the Dapper drive, operating system error on the edgy drive.  Anyone with ideas of where to go from here:   Please help!  Thanks!

---

### Post by incubus on 2006-11-25
blroth,

It's probably the boot order of the hard drives. You have GRUB installed in the MBR and it's set up to look for a specific hard drive number. By installing the new one, it probably changed the numbers.

You could check your BIOS setup and make sure the old one is still the one listed in the boot sequence. Also, by the way, did you change any cable order?

Software-wise, you could run a Live CD and try to reinstall GRUB.

Let us know if the BIOS setup doesn't work.

incubus

---

### Post by blroth on 2006-11-25
Thanks for the reply.  I've been at this all day and I am learning alot, but not enough!  I am answering this post from the newly installed Edgy!  I have been in and out of bios, tried many posted suggestions from the forums with the live CD, all to no avail!  It appears that grub installed on hd2,o (the drive with Edgy), but during set up, it was going to load on hd0(Dapper)!  I was able to get into edgy by changing root from (hd0,0) to (hd2,0)!  I still cannot get into Dapper which greatly upsets me!  It is a disappointment that I can load XP!  I will keep working to find a solution, as I am not willing to reinstall Dapper as it was running perfectly!

---

### Post by incubus on 2006-11-25
Good. I don't think you'll have to reinstall Dapper at all.

The problem is probably related to GRUB not being able to find your Dapper root partition.

Can you post your grub menu.lst file so we can take a look?

incubus

---

### Post by blroth on 2006-11-25
I will gladly post the grub menu.lst file, but I really don't know how to access it!!!  I have not been able to access Dapper at all.    Any thoughts?  Thanks again.

---

### Post by blroth on 2006-11-26
I think I have the menu list:

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
# kopt=root=/dev/hda1 ro

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

title		Ubuntu, kernel 2.6.15-27-amd64-generic Default
root		(hd0,0)
kernel		/boot/vmlinuz root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-amd64-generic Default (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz root=/dev/hda1 ro single
initrd		/boot/initrd.img
boot

title		Ubuntu, kernel 2.6.15-26-amd64-k8 Previous
root		(hd0,0)
kernel		/boot/vmlinuz.old root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img.old
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-amd64-k8 Previous (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz.old root=/dev/hda1 ro single
initrd		/boot/initrd.img.old
boot

title		Ubuntu, kernel 2.6.15-27-amd64-k8
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-amd64-k8 root=/dev/hda1 ro quiet splash
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-amd64-k8 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-amd64-k8 root=/dev/hda1 ro single
boot

title		Ubuntu, kernel 2.6.15-27-amd64-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-amd64-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-27-amd64-generic
boot

title		Ubuntu, kernel 2.6.15-26-amd64-k8
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-amd64-k8 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-amd64-k8
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-amd64-k8 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-amd64-k8 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-26-amd64-k8
boot

title		Ubuntu, kernel 2.6.15-26-amd64-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
boot

title		Ubuntu, kernel 2.6.15-25-amd64-k8
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-amd64-k8 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-amd64-k8
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-amd64-k8 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-amd64-k8 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-25-amd64-k8
boot

title		Ubuntu, kernel 2.6.15-25-amd64-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-amd64-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-amd64-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-amd64-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-25-amd64-generic
boot

title		Ubuntu, kernel 2.6.15-23-amd64-k8
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-amd64-k8 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-amd64-k8
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-amd64-k8 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-amd64-k8 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-amd64-k8
boot

title		Ubuntu, kernel 2.6.15-23-amd64-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-amd64-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-amd64-generic
boot

title		Ubuntu, kernel 2.6.12-10-amd64-k8-smp
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-amd64-k8-smp root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-amd64-k8-smp
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-amd64-k8-smp (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-amd64-k8-smp root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-10-amd64-k8-smp
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-amd64-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-amd64-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-10-amd64-generic
boot

title		Ubuntu, kernel 2.6.12-9-amd64-k8-smp
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-amd64-k8-smp root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-amd64-k8-smp
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-amd64-k8-smp (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-amd64-k8-smp root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-9-amd64-k8-smp
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-9-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda7
title		Microsoft Windows XP Professional
root		(hd2,6)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda6
title		Microsoft Windows XP Professional
root		(hd2,5)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Microsoft Windows XP Professional
root		(hd2,4)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd2,0)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda7
title		Microsoft Windows XP Professional
root		(hd2,6)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda6
title		Microsoft Windows XP Professional
root		(hd2,5)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

---

### Post by blroth on 2006-11-27
Problem solved!!!  The install of Edgy altered Grub to point to both Dapper and Edgy, therefore stopping the boot process.  I dug up a live Breezy CD which allowed me to get into Dapper and once that was done, I was able to correct Grub through the terminal!  Now I can play with Edgy, work with Dapper and ignore XP!  Life is good again!

---

