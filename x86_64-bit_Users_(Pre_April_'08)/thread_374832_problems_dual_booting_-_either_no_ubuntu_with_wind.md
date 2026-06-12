---
title: "problems dual booting - either no ubuntu with windows or ubuntu with no windows"
date: 2007-03-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by nickdr on 2007-03-03
I have tried to install both edgy eft and feisty fawn herd 5 with this same problem.

My Setup:
 - 1 80gb hard drive
      - 25gb partition for win xp
      - 53gb ext3 partition for ubuntu
      - 2gb swap partition for ubuntu
- 1 250gb hard drive for all my windows stuff

i install ubuntu with the live cd installer and it goes fine without a hitch. then when i restart the grub menu only has ubuntu. at this point i still need windows so i did one of two things:
1) used Acronis OS Selector to see if it could find windows and ubuntu
    - finds windows
    - replaces grub as boot loader (=no more ubuntu)
2) used WinXp disk and fixmbr to get windows back
    - i have also tried Acronis after this to see if it could find ubuntu then, no such luck.

i have also tried to save the grub boot info on a different partition, other than hd0, this just makes the installer fail.

is there any way that i can get a boot loader that will allow me to boot windows and ubuntu? if there is away, preferably it should be a way that doesn't require too much technical knowledge, i really don't like messing with my computers boot stuff.

any help is greatly appreciated!

---

### Post by ssavelan on 2007-03-03
That is really interesting; I have never had any problem with GRUB (well, maybe not never).  Can you post more details?  ie.. what was the order that you installed the different OS's?

Also, this is posted on the 64-bit users part of the site. Are you trying the alternate 64-bit install?  I have generally had less problems thus far with the i386-generic.

---

### Post by Gerard Barberi on 2007-03-03
Can you also post Grub's config file.  It's possible to add Windows to it.

it's in /boot/grub/menu.lst

---

### Post by omrsafetyo on 2007-03-03
> **ssavelan said:**
> That is really interesting; I have never had any problem with GRUB (well, maybe not never).  Can you post more details?  ie.. what was the order that you installed the different OS's?

Also, this is posted on the 64-bit users part of the site. Are you trying the alternate 64-bit install?  I have generally had less problems thus far with the i386-generic.

He mentioned he was using the live CD... which is not the alternate 64-bit.

My bets on /boot/grub/menu.lst

---

### Post by nickdr on 2007-03-03
i am using the amd64 ubuntu

i have always had windows on first.

here is the grub:

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
timeout		3

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
# kopt=root=UUID=22378d45-2128-4502-9df9-b6c9cae004c8 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-9-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-9-generic root=UUID=22378d45-2128-4502-9df9-b6c9cae004c8 ro quiet splash
initrd		/boot/initrd.img-2.6.20-9-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-9-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-9-generic root=UUID=22378d45-2128-4502-9df9-b6c9cae004c8 ro single
initrd		/boot/initrd.img-2.6.20-9-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



again, thanks for the help.

---

### Post by nickdr on 2007-03-03
since grub is no longer my bootloader is it possible to add windows onto the grub config file and then reinstall grub? this should be possible through the live cd?

---

### Post by nickdr on 2007-03-03
well with enough fooling around i got it to work. here's what i did to get it to work for anyone else with a similiar problem
this worked for the 64-bit feisty fawn herd 5 release, but should work with any

1) i completely reinstalled ubuntu with the live cd installer
2) set up everything as you want it in installer
3) in final step (step 8 of 8) click advanced option
4) advanced option lets you chose where grub is installed

now grub by default installs to your MBR, master book record, or (hd0). this is a partition set aside, by default, during any OS installation. for me my windows boot record resided there. my first partition, (hd0,1) in grub, is my windows install. my second partition was where ubuntu was being installed, (hd0,2) in grub. so in the advanced option i put in:

hd0,2

this would install grubs boot loader with ubuntu.

5) since the grub boot loader is with ubuntu when you reboot it goes straight to windows, since grub isn't on the boot loader. however in windows when i installed Acronis OS Selector it was able to pick up the grub boot loader off of hd0,2. so now when i restart the acronis OS selector starts and it shows me windows and ubuntu.

i have decided that acronis wasn't able to do this before since when i either installed that or did fixmbr through windows it was rewriting the MBR and deleting the grub loader.

now i am by no means a professional in this field at all, so some of the facts that i have put forth may be inaccurate, i just assumed what made sense.

---

### Post by ssavelan on 2007-03-04
Great to hear of another 'mission accomplished.'

Could this have been an issue derived from using the AMD64 alternate.  I have tried the AMD64 a few times but have found that the x86 generic is less trouble for a lot of reasons.  Could this be one of those reasons?

---

