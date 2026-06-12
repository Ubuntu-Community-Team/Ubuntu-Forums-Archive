---
title: "64bit kernel version"
date: 2008-10-05
forum: x86 64-bit Users
---

### Post by emid on 2008-10-05
What is the latest kernel for the 64 bit version of Hardy?  I'm running 2.6.24-17-generic right now.  The reason I'm asking is because I noticed that on my 32bit laptop I'm running 2.6.24-19-generic.

---

### Post by rsambuca on 2008-10-06
It should be the same one.

[http://packages.ubuntu.com/hardy/linux-image-2.6.24-19-generic](http://packages.ubuntu.com/hardy/linux-image-2.6.24-19-generic)

---

### Post by emid on 2008-10-06
> **rsambuca said:**
> It should be the same one.

[http://packages.ubuntu.com/hardy/linux-image-2.6.24-19-generic](http://packages.ubuntu.com/hardy/linux-image-2.6.24-19-generic)

That's weird, now I'm wondering why my desktop never got the update.  Any thoughts to that effect?

---

### Post by rsambuca on 2008-10-06
Check to make sure you have your repos enabled.

---

### Post by Sef on 2008-10-06
> Check to make sure you have your repos enabled.


System > Administration > Software Sources

---

### Post by emid on 2008-10-06
They are all enabled, at least the relevant ones.

---

### Post by rsambuca on 2008-10-06
can you post the output of ```
cat /etc/apt/sources.list
```and ```
uname -a
```

---

### Post by popat007 on 2008-10-07
I think the kernels are updated but you must be having lock in menu.lst in /boot/grub
```

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=true
```

Change it to false might resolve the prob.

---

### Post by emid on 2008-10-07
Here's the result from "uname -a":
```
Linux d-desktop 2.6.24-17-generic #1 SMP Thu May 1 13:57:17 UTC 2008 x86_64 GNU/Linux

```

Here's my sources.list:
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ hardy main restricted
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ hardy-updates main restricted universe
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ hardy universe
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ hardy multiverse
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ hardy-backports main restricted universe multiverse
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ hardy-backports main restricted universe multiverse

deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ hardy-security main restricted
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ hardy-security main restricted
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ hardy-security universe
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ hardy-security universe
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ hardy-security multiverse
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ hardy-security multiverse

# Miro
deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu hardy/

#Medibuntu
deb http://packages.medibuntu.org/ hardy free non-free
# deb-src http://packages.medibuntu.org/ hardy free non-free


#XBMC SVN
#deb http://ppa.launchpad.net/team-xbmc-svn/ubuntu hardy main
#deb-src http://ppa.launchpad.net/team-xbmc-svn/ubuntu hardy main

#XBMC
deb http://ppa.launchpad.net/team-xbmc-hardy/ubuntu hardy main
deb-src http://ppa.launchpad.net/team-xbmc-hardy/ubuntu hardy main


#Ekiga SVN
# deb http://ppa.launchpad.net/sevmek/ubuntu hardy main
# deb-src http://ppa.launchpad.net/sevmek/ubuntu hardy main

#Ekiga 3 SVN
deb http://snapshots.ekiga.net/snapshots/ubuntu/ hardy main

```

---

### Post by emid on 2008-10-07
> **popat007 said:**
> I think the kernels are updated but you must be having lock in menu.lst in /boot/grub
```

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=true
```

Change it to false might resolve the prob.

Mine is already set to false.

---

### Post by rsambuca on 2008-10-07
Strange.  Is it possible your grub menu.lst wasn't updated at the last kernel update?  Post your /boot/grub/menu.lst.

---

### Post by emid on 2008-10-07
Here's my menu.lst file:
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
# kopt=root=UUID=89349e35-ca6d-439b-9c1b-4a5836661d5f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,1)

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
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=89349e35-ca6d-439b-9c1b-4a5836661d5f ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=89349e35-ca6d-439b-9c1b-4a5836661d5f ro single
initrd		/boot/initrd.img-2.6.24-17-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

I do remember editing this file a while ago because it had like a million items in the list.  I thought I had been pretty careful in removing the correct items from it, but perhaps I messed it up.  I do see now that there is a parameter for limiting how many entries are visible when you boot.

---

### Post by rsambuca on 2008-10-07
Open up the Synaptic Package Manager and search for linux-image.  See which kernels you have installed on your system.  My guess is the new kernel is installed, but your grub needs to be updated to actually use it.

---

### Post by emid on 2008-10-07
It looks like you're right. Synaptic shows that the newer kernel is installed.  How do I update grub to reflect that?

---

### Post by rsambuca on 2008-10-07
From the looks of things, you have XP on the first partition of the first drive (hd0,0), and Ubuntu on the second partition of that drive (hd0,1).  For some reason, you have the grub root set at (hd2,1), which is the 2nd partition of your 3rd drive.  What is the output of ```
fdisk -l
```

---

### Post by emid on 2008-10-07
Here's the output of "fdisk -l":
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00095c55

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a93aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007348a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdd: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4ee04ee0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       14352   115282408+   7  HPFS/NTFS
/dev/sdd2           14353       19203    38965657+  83  Linux
/dev/sdd3           19204       19452     2000092+  82  Linux swap / Solaris

Disk /dev/md0: 1000.2 GB, 1000210300928 bytes
2 heads, 4 sectors/track, 244191968 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

```

Basically, I have four drives.  The 160gb that has windows and ubuntu on it, and three 500gb drives in a raid 5 array using mdadm.

---

### Post by rsambuca on 2008-10-07
Basically what is happening is that your grub setup doesn't know where it's root drive is (the line that says #groot=(hd2,1)).  What you want to do is set that groot line to the drive and partition with your ubuntu grub on it, and then run a grub-update command.  The problem is that I have no idea how the designations work in a RAID array.  Hopefully someone else can help out here.  Keep us posted.

As a temporary fix, you can just manually change the two entries in your /boot/grub/menu.lst for the ubuntu "kernel" and "initrd" lines.  This will get you booting into the new kernel, but upon the next kernel update, grub won't be updated again.

---

### Post by emid on 2008-10-07
When you say Ubuntu grub, do you mean the drive and partition where ubuntu is located?  I figure I can make an educated guess about what the proper designation would be.  I think the RAID array doesn't really come into it, I'd just have to account for the actual drives themselves (maybe:)) .  If I'm wrong it wouldn't be the end of the world.

---

### Post by rsambuca on 2008-10-07
Try opening a terminal and entering the grub shell by using ```
sudo grub
```Then at the grub prompt, type ```
find /boot/grub/stage1
```It will spit out a location in the form of (hdX,Y).  Then try entering that as the root location for grub by entering ```
root (hdX,Y)
```using the numbers that were given above.  Then install back to the MBR by entering ```
setup (hd0)
```

---

### Post by emid on 2008-10-08
OK, I did what you listed and rebooted, no change.  It still listed the same kernel options.

---

### Post by rsambuca on 2008-10-08
Sorry, other than just manually editing the kernel and initrd lines, I don't know how you can have it automatically updated.

---

### Post by emid on 2008-10-08
> **rsambuca said:**
> Sorry, other than just manually editing the kernel and initrd lines, I don't know how you can have it automatically updated.

I see, well thanks anyways for trying, I appreciate it.

---

