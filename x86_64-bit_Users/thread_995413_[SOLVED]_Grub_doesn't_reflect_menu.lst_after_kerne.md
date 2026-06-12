---
title: "[SOLVED] Grub doesn't reflect menu.lst after kernel upgrade (8.04.1)"
date: 2008-11-27
forum: x86 64-bit Users
---

### Post by OlorinIWas on 2008-11-27
Kubuntu 8.04.1 x64

So I updated my 2.6.24-21-rt to 2.6.24-22-rt and updated the /boot/grub/menu.lst...which while omitting my vista and 8.10 installations (I assume this is correlated), has the lines which I am immediately concerned with:
> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=0d5cc1f6-b9f0-4d38-8814-f80ee0f66327 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-rt root=UUID=0d5cc1f6-b9f0-4d38-8814-f80ee0f66327 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-rt

title		Ubuntu 8.04.1, kernel 2.6.24-22-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-rt root=UUID=0d5cc1f6-b9f0-4d38-8814-f80ee0f66327 ro single
initrd		/boot/initrd.img-2.6.24-22-rt

title		Ubuntu 8.04.1, kernel 2.6.24-21-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-rt root=UUID=0d5cc1f6-b9f0-4d38-8814-f80ee0f66327 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-rt

title		Ubuntu 8.04.1, kernel 2.6.24-21-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-rt root=UUID=0d5cc1f6-b9f0-4d38-8814-f80ee0f66327 ro single
initrd		/boot/initrd.img-2.6.24-21-rt

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

...however the actual grub menu at boot shows my original options, vista, 8.10, and two old kernels for this (8.04.1) installation, but not the new 2.6.24-22-rt...it also shows a kernel that I have uninstalled..

Obviously I've tried update-grub and grub-install "(hd0)" && update-grub...I've purged, reinstalled, and tried grub2...nothing gets grub to respond. I'm not that familiar with grub, I was assuming menu.lst would be a plain text document, which it is not...don't know if that would be an issue.

Thanks..

---

### Post by caljohnsmith on 2008-11-27
How about opening a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like.

---

### Post by CholericKoala on 2008-11-27
Are you sure there isnt an extra menu.lst hiding around?  what does sudo locate menu.lst give?

---

### Post by OlorinIWas on 2008-11-27
sudo fdisk -lu:
> Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2f5ab7fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    32499494    16249716    7  HPFS/NTFS
/dev/sda2   *    32499495  1250258624   608879565    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000be383

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    15518789     7759363+  83  Linux
/dev/sdb2        15518790    27310499     5895855   83  Linux
/dev/sdb3       967868055   976768064     4450005   82  Linux swap / Solaris
/dev/sdb4        27310500   967868054   470278777+  83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00023c7e

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    16386299     8193118+  83  Linux
/dev/hdb2       615916035   625137344     4610655   82  Linux swap / Solaris
/dev/hdb3        22523130   615916034   296696452+  83  Linux
/dev/hdb4        16386300    22523129     3068415   83  Linux

Partition table entries are not in disk order
Note: sector size is 2048 (not 512)

Disk /dev/sdc: 521 MB, 521011200 bytes
212 heads, 60 sectors/track, 20 cylinders, total 254400 sectors
Units = sectors of 1 * 2048 = 2048 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          60      254399      508680    6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 60) logical=(0, 1, 1)

sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system":
> sda and hdb report 'GRUB'...sdb and sdc don't report anything...I have no idea what sdc is...and hdb is a sata drive as well...sdb has / and /home for this os
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}':
> 8200
sudo dd if=/dev/hdb bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}':
> 8200

thanks for the responce, sorry it took a while, I've been fiddling...I can boot that kernel by editing an old boot line at grub startup, but that doesn't help much..

---

### Post by OlorinIWas on 2008-11-27
> **CholericKoala said:**
> Are you sure there isnt an extra menu.lst hiding around?  what does sudo locate menu.lst give?

> /boot/grub/menu.lst
/boot/grub/menu.lst~
/usr/share/doc/grub/examples/menu.lst
/usr/share/doc/memtest86+/examples/grub-menu.lst
/var/lib/ucf/cache/:var:run:grub:menu.lst


is that ok?..

---

### Post by CholericKoala on 2008-11-27
^^ yea it looks alright.  Just wanted to make sure that you were actually booting from the menu.lst you thought you were.

---

### Post by John Jason Jordan on 2008-11-27
In case it helps, I had a related problem recently, documented here:

[http://ubuntuforums.org/showthread.php?t=983486]("http://ubuntuforums.org/showthread.php?t=983486")

---

### Post by caljohnsmith on 2008-11-27
OK, you've got multiple linux partitions, and it looks like Grub is using the menu.lst in either sdb1 or hdb1. How about when you boot into Kubuntu post the output of:
```
 mount | grep " / " | awk '{print $1}'
```
And that will show which partition you are in. Then do the following:
```

mount | grep " / " | grep sdb1 && sudo mount /dev/hdb1 /mnt
mount | grep " / " | grep hdb1 && sudo mount /dev/sdb1 /mnt
ls -l /mnt
cat /mnt/boot/grub/menu.lst
```
And please post the output.

---

### Post by OlorinIWas on 2008-11-27
> **caljohnsmith said:**
> OK, you've got multiple linux partitions, and it looks like Grub is using the menu.lst in either sdb1 or hdb1. How about when you boot into Kubuntu post the output of:
```
 mount | grep " / " | awk '{print $1}'
```
And that will show which partition you are in. Then do the following:
```

mount | grep " / " | grep sdb1 && sudo mount /dev/hdb1 /mnt
mount | grep " / " | grep hdb1 && sudo mount /dev/sdb1 /mnt
ls -l /mnt
cat /mnt/boot/grub/menu.lst
```
And please post the output.

 mount | grep " / " | awk '{print $1}':
> /dev/sdb1
mount | grep " / " | grep sdb1 && sudo mount /dev/hdb1 /mnt:
> /dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
mount: /dev/hdb1 already mounted or /mnt busy
mount: according to mtab, /dev/hdb1 is already mounted on /mnt
mount | grep " / " | grep hdb1 && sudo mount /dev/sdb1 /mnt:
> nt /dev/sdb1 /mnt
ls -l /mnt:
> total 112
drwxr-xr-x   2 root root  4096 2008-11-24 18:29 bin
drwxr-xr-x   3 root root  4096 2008-11-27 19:44 boot
lrwxrwxrwx   1 root root    11 2008-10-31 03:44 cdrom -> media/cdrom
drwxr-xr-x   4 root root  4096 2008-10-31 04:00 dev
drwxr-xr-x 110 root root 12288 2008-11-27 19:51 etc
drwxr-xr-x   2 root root  4096 2008-10-31 03:41 fuckit
drwxr-xr-x   2 root root  4096 2008-10-31 03:35 home
lrwxrwxrwx   1 root root    32 2008-11-27 19:44 initrd.img -> boot/initrd.img-2.6.27-9-generic
lrwxrwxrwx   1 root root    32 2008-10-31 03:45 initrd.img.old -> boot/initrd.img-2.6.27-7-generic
drwxr-xr-x  15 root root  4096 2008-11-24 18:45 lib
drwxr-xr-x   2 root root  4096 2008-11-24 18:45 lib32
lrwxrwxrwx   1 root root     4 2008-10-31 03:44 lib64 -> /lib
drwx------   2 root root 16384 2008-10-31 03:35 lost+found
drwxr-xr-x   3 root root  4096 2008-10-31 03:57 media
drwxr-xr-x   2 root root  4096 2008-10-31 03:35 MediaI
drwxr-xr-x   2 root root  4096 2008-10-31 03:35 MediaII
drwxr-xr-x   2 root root  4096 2008-10-20 07:27 mnt
drwxr-xr-x   2 root root  4096 2008-10-31 03:44 opt
drwxr-xr-x   2 root root  4096 2008-10-20 07:27 proc
drwxr-xr-x   2 root root  4096 2008-11-13 17:20 root
drwxr-xr-x   2 root root  4096 2008-11-27 19:40 sbin
drwxr-xr-x   2 root root  4096 2008-10-31 03:44 srv
drwxr-xr-x   2 root root  4096 2008-10-14 08:02 sys
drwxrwxrwt   4 root root  4096 2008-11-27 19:50 tmp
drwxr-xr-x  12 root root  4096 2008-11-24 18:45 usr
drwxr-xr-x  14 root root  4096 2008-10-31 03:56 var
lrwxrwxrwx   1 root root    29 2008-11-27 19:44 vmlinuz -> boot/vmlinuz-2.6.27-9-generic
lrwxrwxrwx   1 root root    29 2008-10-31 03:45 vmlinuz.old -> boot/vmlinuz-2.6.27-7-generic
drwxr-xr-x   2 root root  4096 2008-10-31 03:35 windows

cat /mnt/boot/grub/menu.lst:
> # menu.lst - See: grub(8), info grub, update-grub(8)
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# kopt=root=UUID=98214d2d-9828-4012-ac0f-b9ddad098be1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=98214d2d-9828-4012-ac0f-b9ddad098be1

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

title           Ubuntu 8.10, kernel 2.6.27-9-generic
uuid            98214d2d-9828-4012-ac0f-b9ddad098be1
kernel          /boot/vmlinuz-2.6.27-9-generic root=UUID=98214d2d-9828-4012-ac0f-b9ddad098be1 ro quiet splash
initrd          /boot/initrd.img-2.6.27-9-generic
quiet

title           Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid            98214d2d-9828-4012-ac0f-b9ddad098be1
kernel          /boot/vmlinuz-2.6.27-9-generic root=UUID=98214d2d-9828-4012-ac0f-b9ddad098be1 ro  single
initrd          /boot/initrd.img-2.6.27-9-generic

title           Ubuntu 8.10, kernel 2.6.27-7-generic
uuid            98214d2d-9828-4012-ac0f-b9ddad098be1
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=98214d2d-9828-4012-ac0f-b9ddad098be1 ro quiet splash
initrd          /boot/initrd.img-2.6.27-7-generic
quiet

title           Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid            98214d2d-9828-4012-ac0f-b9ddad098be1
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=98214d2d-9828-4012-ac0f-b9ddad098be1 ro  single
initrd          /boot/initrd.img-2.6.27-7-generic

title           Ubuntu 8.10, memtest86+
uuid            98214d2d-9828-4012-ac0f-b9ddad098be1
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista/Longhorn (loader)
root            (hd0,1)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title           Ubuntu 8.04.1, kernel 2.6.24-21-rt (on /dev/sdb1)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-21-rt root=UUID=0d5cc1f6-b9f0-4d38-8814-f80ee0f66327 ro quiet splash
initrd          /boot/initrd.img-2.6.24-21-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title           Ubuntu 8.04.1, kernel 2.6.24-21-rt (recovery mode) (on /dev/sdb1)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-21-rt root=UUID=0d5cc1f6-b9f0-4d38-8814-f80ee0f66327 ro single
initrd          /boot/initrd.img-2.6.24-21-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title           Ubuntu 8.04.1, kernel 2.6.24-19-rt (on /dev/sdb1)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-19-rt root=UUID=0d5cc1f6-b9f0-4d38-8814-f80ee0f66327 ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title           Ubuntu 8.04.1, kernel 2.6.24-19-rt (recovery mode) (on /dev/sdb1)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-19-rt root=UUID=0d5cc1f6-b9f0-4d38-8814-f80ee0f66327 ro single
initrd          /boot/initrd.img-2.6.24-19-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title           Ubuntu 8.04.1, memtest86+ (on /dev/sdb1)
root            (hd1,0)
kernel          /boot/memtest86+.bin
savedefault
boot


just to reiterate...sdb didn't respond 'grub', but I don't know how you know where it's booting from...hdb1 isn't mounted on this os...but it is the / for 8.10

---

### Post by OlorinIWas on 2008-11-27
Ok, thanks y'all, I edited grub on hdb1 manually...and presto...

sorry for being so thick. thanks again.

---

### Post by caljohnsmith on 2008-11-28
> **OlorinIWas said:**
> Ok, thanks y'all, I edited grub on hdb1 manually...and presto...

sorry for being so thick. thanks again.
Glad you have it working, that's what counts. If you want your sdb1 Kubuntu partition to be in charge of the Grub menu on start up instead, let me know and I can help if you like. Otherwise, cheers and have fun with all your OSes. :)

---

### Post by philinux on 2008-11-28
Grub gets messy dont it.

I've got 2 hard drives. Disk 1 has Intrepid and disk 2 has Jaunty.
I've simplified grub on disk 1 to boot Jaunty using this.
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#
title        Whatever's on SDB
configfile   (hd1,0)/boot/grub/menu.lst

[http://ubuntuforums.org/showthread.php?t=861205&highlight=grub](http://ubuntuforums.org/showthread.php?t=861205&highlight=grub)

---

