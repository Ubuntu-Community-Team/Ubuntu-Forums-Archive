---
title: "Reinstalling GRUB"
date: 2007-10-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Guns90 on 2007-10-15
Good Morning.  I haven't been able to find an answer to my exact need.

Computer "A" was a 64-bit system dual-booted with Windows XP on hda1 and 64-bit Fiesty on hdb1.  It booted directly into Windows at start-up.  I have now removed hdb1 from the system, corrected the BIOS, and repaired GRUB on hda1 using the Windows XP CD.  I plan on installing another hdb1 later and dual-boot with Ubuntu.  This I know how to do.

Computer "B" is a 64-bit system that currrently has one hdd with Windows VISTA.  I want to install hdb1 from computer "A" and boot directly into VISTA at start-up.  I know that I need to change BIOS to boot-up into hdb1.  I also know that I'm going to run into a GRUB problem at boot-up because hda1 doesn't have GRUB on it and GRUB on hdb1 is set up expecting Windows XP and not VISTA.   I don't know how to address this problem.  What do I need to do. please?  Thanks.

---

### Post by Kilz on 2007-10-15
You should be able to insert the install cd and use rescue a broken system to install grub on the new computer as long as linux/grub is still on that drive.

---

### Post by Guns90 on 2007-10-15
Well.......    I couldn't get it to work, so I just did a clean install of 7.04 AMD64 on hdb1.  Everything went well and is working fine; however, I'm having trouble getting my 64bit version of VISTA to boot up first.  I found a thread that said to change the /boot/grub/menu.lst, but I can't seem to find the right command/sequence.  If you (or anyone else) could help, I sure would appreciate it.  Here is my menu.lst:

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
# kopt=root=UUID=16e19da9-254f-4bf3-9417-222f759f86d6 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=16e19da9-254f-4bf3-9417-222f759f86d6 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=16e19da9-254f-4bf3-9417-222f759f86d6 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=16e19da9-254f-4bf3-9417-222f759f86d6 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=16e19da9-254f-4bf3-9417-222f759f86d6 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by John.Michael.Kane on 2007-10-15
Your options.
[Dualboot Two Hard Drives]("http://ubuntuforums.org/showthread.php?t=179902")
[WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")
[GrubHowto]("https://help.ubuntu.com/community/GrubHowto?highlight=%28grub%29")
[Recovering Ubuntu after installing Windows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub")

---

### Post by Guns90 on 2007-10-15
Hello again, SD-Plissken.  Yes, the first reference was the one I had found and was trying to use, but couldn't get it right.  I just found the the problem.  I was cutting and pasting from the reference 'as is', but I finally figured out it was the " root (hd0,0)" in my system instead of the root (hd1,0) listed in the reference.   Thanks for the references.  Gary

---

### Post by John.Michael.Kane on 2007-10-15
> **Guns90 said:**
> Hello again, SD-Plissken.  Yes, the first reference was the one I had found and was trying to use, but couldn't get it right.  I just found the the problem.  I was cutting and pasting from the reference 'as is', but I finally figured out it was the " root (hd0,0)" in my system instead of the root (hd1,0) listed in the reference.   Thanks for the references.  Gary

I'm glad you were able to resolved the issue. If you should have any other problems please post.

---

