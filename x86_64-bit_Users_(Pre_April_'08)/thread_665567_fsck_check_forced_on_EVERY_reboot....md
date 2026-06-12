---
title: "fsck check forced on EVERY reboot..."
date: 2008-01-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by mavicus on 2008-01-12
OS: Ubuntu 7.10 64bit

Every time I reboot my computer, I get a forced disk check on one of my partitions.
It is a 400GB SATA drive, the partition is 314GB and is partition 4 of 4.
It is not the partition that the OS is installed on, but it does have my home directories on it.
It previously and currently serves the same role, (with the same data that it has now) on a 32-bit version of Ubuntu 7.04. In other words, the same /home partition is used by both OSs, however I never boot into the 32bit anymore, it was a fallback while I tried out 64bit.

/dev/sdb1     ext2     1GB        used as a preboot partition
/dev/sdb2     ext2     24GB      used as root partition when booting 64bit 
/dev/sdb3     ext2     24GB      used as root partition when booting 32bit (only used once or twice)
/dev/sdb4     ext2     314GB    used as home

Here's the output:
```
/dev/sdb4 was not cleanly unmounted, check forced.
/dev/sdb4: 230536/41172992 files (3.2% non-contiguous), 59400728/82315051 blocks
```

Does the 3.2% non-contiguous have anything to do with it? it always comes up with the same output as above. Is that fixable?

It is noteworthy that I also booted into Windows XP occasionally, and that this drive gets mounted in Windows using some ext2 driver for Windows. I can't remember the name of it, and I have since removed Windows XP. Each time that I booted into Windows XP and returned to Ubuntu, I would NOT get the forced disk check for one session, but it would return on the next.

This is also the case when I booted into 32bit Ubuntu, it fixed the problem for the next single session in 64bit.

So it seems to me that the problem is probably just that the drive truly does not get properly unmounted by 64bit Ubuntu, but I have no idea of how to diagnose or fix problems of this type.

---

### Post by fjgaude on 2008-01-12
Show us your /etc/fstab file... that might give a clue.

```
gedit /etc/fstab
```

and also what this shows:

```
sudo fdisk -l
```

---

### Post by jrusso2 on 2008-01-12
For some reason its not shutting down correctly.  Sounds like its not unmounting on shut down.

---

### Post by crgutierrez on 2008-01-12
> **fjgaude said:**
> Show us your /etc/fstab file... that might give a clue.

```
gedit /etc/fstab
```

and also what this shows:

```
sudo fdisk -l
```

Have similar problem when starting 64bit partition

sda1 root 32 bit
sda2 home 32 bit
sda4 extended
sda 5 root 64 bit
sda6 swap

```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+  83  Linux
/dev/sda2           12749       25510   102510765   83  Linux
/dev/sda4           25511       30401    39286957+   5  Extended
/dev/sda5           25511       29674    33447298+  83  Linux
/dev/sda6           29675       30401     5839596   82  Linux swap / Solaris

```
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=224aa9fc-6c02-4a48-a054-a2df49e57d3e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=01a2cb19-3950-480e-9654-5b74b919f6fd /home           ext3    defaults        0       2
# /dev/sda5
UUID=d23c6629-1f3d-4c64-b84c-bee04beb7ef5 /media/sda5     ext3    defaults        0       2
# /dev/sda6
UUID=5a71460d-6ec8-4b38-9ffe-944a48278444 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

Also have a log of the error when loading 64 bit is necessary

```
Log of fsck -C -R -A -a 
Sat Jan 12 21:44:00 2008

fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Unable to resolve 'UUID=229e35e5-18bf-4742-b28b-169b247a0e67'

/dev/sda2: clean, 69251/12828672 files, 12530618/25627691 blocks
fsck died with exit status 8

Sat Jan 12 21:44:00 2008

```

Thanks for your help

---

### Post by MM23 on 2008-01-13
the UUID 229e35e5-18bf-4742-b28b-169b247a0e67 isn't anywhere in your fstab. not that it would prevent an unmount, but the fsck whining almost seems to imply it isn't mounting in the first place or it's mounting incorrectly.

a bit strange...

post your grub menu.lst/grub.conf (whichever you use)

---

### Post by dcstar on 2008-01-13
> **mavicus said:**
> 
..........
So it seems to me that the problem is probably just that the drive truly does not get properly unmounted by 64bit Ubuntu, but I have no idea of how to diagnose or fix problems of this type.

Chances are the /etc/fstab file on the 64 bit system is not correct, compare it with the one on your 32 bit system.

---

### Post by crgutierrez on 2008-01-13
To MM23

Gracias!

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
# kopt=root=UUID=224aa9fc-6c02-4a48-a054-a2df49e57d3e ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=224aa9fc-6c02-4a48-a054-a2df49e57d3e ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=224aa9fc-6c02-4a48-a054-a2df49e57d3e ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d23c6629-1f3d-4c64-b84c-bee04beb7ef5 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d23c6629-1f3d-4c64-b84c-bee04beb7ef5 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 7.10, memtest86+ (on /dev/sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

Txs

---

### Post by FurryNemesis on 2008-01-13
I'm getting the same fsck error on boot:

Here's the log:

Log of fsck -C -R -A -a 
Sun Jan 13 15:18:48 2008

fsck 1.40-WIP (14-Nov-2006)
/dev/sda4 is mounted.  e2fsck: Cannot continue, aborting.


/dev/sda1: recovering journal
/dev/sda1: clean, 138123/788704 files, 919703/1574362 blocks
/dev/sda2: clean, 34066/8011776 files, 8202212/16018813 blocks
fsck died with exit status 8

Sun Jan 13 15:18:48 2008
----------------

My fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=66499126-f933-4389-9c57-3a3869991941 /media/sda4     ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=aa8e99b2-e48b-4cb0-8b93-d6883b8e76a2 /media/sda1     ext3    defaults        0       2
# /dev/sda2
UUID=44e1c002-5b1f-4ef0-bb97-29fccb0c8c88 /media/sda2     ext3    defaults        0       2
# /dev/sda3
UUID=76467c4a-edbd-4e93-8c4d-61924a7d467d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


and output of $ blkid

/dev/sda1: UUID="aa8e99b2-e48b-4cb0-8b93-d6883b8e76a2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="44e1c002-5b1f-4ef0-bb97-29fccb0c8c88" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="7efb485b-9e8d-42b3-8a6e-b5929b8c014a" TYPE="swap" 
/dev/sda4: UUID="66499126-f933-4389-9c57-3a3869991941" SEC_TYPE="ext2" TYPE="ext3" 


I thought it was exiting because the UUIDs didn't match, but apparently I have errors on that disk. I'm at a loss as to what to do. Any help would be very appreciated.

---

### Post by fjgaude on 2008-01-13
Maybe these issues have something to do with the order in which the partitions are placed in the fstab file? The ascending placement determines the order in which they are mounted. Something to think about.

The UUID difficulties likely has to do with names changing when updating, upgrading the OS, eh?

---

### Post by mavicus on 2008-01-13
OP, and as requested by fjgaude, here's the contents of my /etc/fstab

```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb2 :
UUID=f72f0a5f-85e8-4a7d-9b09-8959f2e74b5e / ext2 defaults,errors=remount-ro 0 1
# Entry for /dev/sdb4 :
UUID=bb7bfadd-499b-40e3-8ad0-f75e481f55aa /home ext2 defaults 0 2
# Entry for /dev/hda1 :
UUID=5b51e339-e518-463f-9709-55899a2d2d04 /media/hda1 ext3 defaults 0 2
# Entry for /dev/sda1 :
UUID=7953b2a3-782d-44a2-97b2-a0f2ce23c3ef /media/sata500 ext3 defaults 0 2
# Entry for /dev/sdb1 :
UUID=a647f5b2-aa1a-4a59-9864-ab94ae7a3b47 /media/preboot ext2 defaults 0 2
# Entry for /dev/sdb3 :
UUID=aa8596e2-d69c-48e2-9007-f164acf7d7d5 /media/Ubuntu-7.04x32 ext2 defaults 0 2
# Entry for /dev/hda2 :
UUID=e710d0f4-782f-4888-b2f1-e339360addbe none swap sw 0 0
# Entry for /dev/hdb5 :
UUID=78513475-afa4-4d23-8c88-831311c00bd5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hdb1 /media/drive ntfs-3g defaults,locale=en_US.UTF-8 0 0
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0
```

And here is the output of fdisk -l
```

Disk /dev/hda: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd383ba6d

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3226    25912813+  83  Linux
/dev/hda2            3227        3736     4096575   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf941c38c

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9470    76067743+   7  HPFS/NTFS
/dev/hdb2            9471        9732     2104515    f  W95 Ext'd (LBA)
/dev/hdb5            9471        9732     2104483+  82  Linux swap / Solaris

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f1a4c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000322a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         131     1052226   83  Linux
/dev/sdb2             132        3890    30194167+  83  Linux
/dev/sdb3            3891        7650    30202200   83  Linux
/dev/sdb4            7651       48641   329260207+  83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000e913

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321    b  W95 FAT32

```

Also, dcstar, here is the contents of the old 32bit fstab, which I have not booted into in a while, and looks like it contains info on disks no longer present. I don't know what to look for to tell if the fstab is right or not, they are obviously different in some ways.

```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=aa8596e2-d69c-48e2-9007-f164acf7d7d5 / ext2 defaults,errors=remount-ro 0 1
# Entry for /dev/sda4 :
UUID=bb7bfadd-499b-40e3-8ad0-f75e481f55aa /home ext2 defaults 0 2
# Entry for /dev/sda1 :
UUID=a647f5b2-aa1a-4a59-9864-ab94ae7a3b47 /media/preboot ext2 defaults 0 2
# Entry for /dev/sda2 :
UUID=4ad196d4-74ef-40bf-baa3-38f0b363d13e /media/ubuntu-6.06 ext2 defaults 0 2
# Entry for /dev/sdb1 :
UUID=7953b2a3-782d-44a2-97b2-a0f2ce23c3ef /media/sata500 ext3 defaults 0 2
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sdd1 /media/ntfs01 ntfs-3g defaults,locale=en_US.UTF-8 0 0
```

---

### Post by Herman on 2008-01-13
Hello FurryNemesis,
> I thought it was exiting because the UUIDs didn't match, but apparently I have errors on that disk. I'm at a loss as to what to do. Any help would be very appreciated.It looks to me as if the UUID for your swap area doesn't match, but that shouldn't have anything to do with a fsck, here's what your /etc/fstab *should* look like. :)
Your fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0

# /dev/sda4
UUID=[COLOR=Black]66499126-f933-4389-9c57-3a3869991941[/COLOR] /media/sda4 ext3 defaults,errors=remount-ro 0 1 

# /dev/sda1
UUID=aa8e99b2-e48b-4cb0-8b93-d6883b8e76a2 /media/sda1 ext3 defaults 0 2 

# /dev/sda2
UUID=44e1c002-5b1f-4ef0-bb97-29fccb0c8c88 /media/sda2 ext3 defaults 0 2 

# /dev/sda3
UUID=[COLOR=Sienna]**7efb485b-9e8d-42b3-8a6e-b5929b8c014a**[/COLOR] none swap sw 0 0 

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0

```I have recently been working on an article on how to run smartmontools, it happens to be in my Knoppix page, but you can run smartmontools just as well from Ubuntu, the commands are the same. you just need to install it first, if you're using Ubuntu though. ```
apt-get install smartmontools
```If you still keep having your file system check run at start-up it might pay to make sure your hard disk is okay. Here is the link, [Check On Your Hard Disks With Smartmontools]("http://users.bigpond.net.au/hermanzone/p20.html#Check_On_Your_Hard_Disks_With").
Hopefully you'll be able to tell that your hard disk is okay. 

It's better to run e2fsck on an ext2 or an ext3 file system than just an fsck, because fsck will only run e2fsck for you, but without as much choice in the options. You can make a more effective file system check when you can use more specific options. 
Even if you don't know much about file system checking, you can always just use a [GParted -- LiveCD]("http://gparted.sourceforge.net/"). Right-click on your partition to be checked, and then click 'check' from the right-click menu. Click 'Apply' on the toolbar, and 'apply' in the confirmation box. GParted will run a pretty good e2fsck for you, it will fix most file system problems when your regular fsck isn't effective enough. You can also run the same thing from GParted in the Ubuntu LiveCD or from another installation of Ubuntu if you're multi-booting and you make sure you unmount the other Ubuntu first. 
Most of the time that will fix your problems. :)

Regards, Herman :)

---

### Post by crgutierrez on 2008-01-15
Mr. Herman

Sorry for the level of my stupid questions but, are they two fstab files because I'm running 2 versions in the same machine? Should the fstab be the same in both cases??????
I have tried to ask my questions at a simple level in another thread, as I got lost
[http://ubuntuforums.org/showthread.php?t=667827](http://ubuntuforums.org/showthread.php?t=667827)

Here is my situation

sda1 root 32 bit
sda2 home 32 bit
sda4 extended
sda 5 root 64 bit, which gives the forced fsck message
sda6 swap

Code:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+  83  Linux
/dev/sda2           12749       25510   102510765   83  Linux
/dev/sda4           25511       30401    39286957+   5  Extended
/dev/sda5           25511       29674    33447298+  83  Linux
/dev/sda6           29675       30401     5839596   82  Linux swap / Solaris

Code:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=224aa9fc-6c02-4a48-a054-a2df49e57d3e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=01a2cb19-3950-480e-9654-5b74b919f6fd /home           ext3    defaults        0       2
# /dev/sda5
UUID=d23c6629-1f3d-4c64-b84c-bee04beb7ef5 /media/sda5     ext3    defaults        0       2
# /dev/sda6
UUID=5a71460d-6ec8-4b38-9ffe-944a48278444 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

Also have a log of the error when loading 64 bit is necessary

Code:

Log of fsck -C -R -A -a 
Sat Jan 12 21:44:00 2008

fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Unable to resolve 'UUID=229e35e5-18bf-4742-b28b-169b247a0e67'

/dev/sda2: clean, 69251/12828672 files, 12530618/25627691 blocks
fsck died with exit status 8

Sat Jan 12 21:44:00 2008

Thanks for your help and a kg of Costa Rica Coffee for you

Thanks for your comments

---

### Post by Herman on 2008-01-15
:) Hello crgutierrez,
 > are they two fstab files because I'm running 2 versions in the same machine? There should be one /etc/fstab file in your i386 Ubuntu in partition 1 and another /etc/fstab file in partition 5.
>  Should the fstab be the same in both cases??????The files should be different.
The UUID numbers should be the same, but they should be listed in a different way..
Probably the partition 1's /etc/fstab will have partition 1 listed near the top of the file with it's UUID number, and it will have an 0 and a 1 after it,
The 0 means for not to dump (some kind of backup utility that some other operating systems use is called 'dump'.
 and the 1 means to check this partition first, by itself.

Then the rest of the file systems will be there with a 0 and a 2 after them. The 2 means they will be all checked
simultaneously to save time.

Partition 5's /etc/fstab will probably have partition 5 close to the top and with a 0 and a 1, then the rest underneath, with a 0 and a 2.

Most of the time it makes things easier to have the UUID numbers in /etc/fstab, but we need to remember to update our /etc/fstab files if we reformat a partition with a new file system, or delete a partition and replace it with a new one. (Such as commonly happens when we re-install an operating system.

The best way to get a list of your current file system UUID numbers is to use the command, 
```
ls /dev/disk/by-uuid/ -alh
```and compare the output from that command with the UUID numbers in our /etc/fstab file. We can copy the UUID number from the command and paste it into the file to overwrite and old file system numbers and replace them with the new number.
If you want to you can do that yourself, but if you want help, post your /etc/fstab file here from the 64 bit operating system and I'll see if I can edit it for you.

If you can't boot the 64 bit operating system you should still be able to get the /etc/fstab file out  of it this way,  [                                  Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") rescue your Linux system with a Live CD

Most of the time you can still boot, you just need to press 'ctrl'+'d' keys when it stops after the file system checks, and it will finish booting.

Regards, Herman :)

---

### Post by crgutierrez on 2008-01-15
SOLVED!!!!!!!!!!!
/etc/fstab file in 64bit installation had an error number for sda1
could fixed myself thanks to HERMAN!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by dcstar on 2008-01-17
> **crgutierrez said:**
> SOLVED!!!!!!!!!!!
/etc/fstab file in 64bit installation had an error number for sda1
could fixed myself thanks to HERMAN!!!!!!!!!!!!!!!!!!!!!!!!!

It is meant to, the root partition should be checked on every boot as it is the most important partition on your system, and if you allow it to stay (potentially) corrupted you could lose your whole system.

If you have a problem with the vital integrity checking process then fix the problem, don't just modify the system so it stops checking.

---

### Post by crgutierrez on 2008-01-18
David

The problem was that one the fstab files (the one for the 64bit version) had an error nunmber for the partition sda1. Once the error was fixed the loading of the 64bit went trough without problem, meaning the integrity checking goes trough without collapsing. I also had every partition checked toroughly with external tools before continuing.

I really appreciate your comments

Gracias

---

### Post by Herman on 2008-01-22
crgutierrez,
Thanks for the good feedback, it's nice to know your system is working properly now. Lucky you could fix it without more help from me, I was off-line for almost week because the telephone wires were cut and it took the phone company nearly a week to fix them.  

dcstar, 
Thanks for your comments too, I agree with you about file system checking, I  think is very important too. 

Regards, Herman :)

---

### Post by mavicus on 2008-02-25
OP here...

While I feel this thread veered from my original question and problem, I was eventually able to fix it myself by replacing the fstab of the 64 bit version with a copy of the fstab from the 32 bit version, EVEN THOUGH the 32 bit version contains incorrect references to EVERY drive on my system. It was a last resort that worked. The drive in question is referenced in the 32 bit fstab as sda, where in the 64 bit it is referenced as sdb.
The partitions on this drive mount as sdb on both systems, regardless of what the fstab says.

I am confused, and my fstab is now different than the end result of my drives after they mount, but the problem is fixed. I am more lost than before, but I have no unclean unmounts.

Thanks to dcstar for at least pointing me to the fstab files.

---

### Post by crgutierrez on 2008-02-25
Exactly! There should be no difference in the numbering of the partitions between both fstab files. And believe me, I don-t know either why it happened, but I guess it was the secquences of the installations. By now I really only use the 64 bit version and only once in a while I have trouble with the scanner. By the way Quickstart is a wonderfull tool you will find in the forum that allows easy editing of fstab and other relevant files

---

### Post by pww on 2008-02-25
Herman and All, thanks for all the info in this thread.

I had a similar problem when screwing around with my partition sizes:  The UUID's change.
However, I was unable to determine the correct UUID's, but discovered that you don't need them.  Use the <file system> name instead.  Here's my fstab to demonstrate, it has both UUID's and file system names:

# /etc/fstab: static file system information.
#
# <file system> <mount point>                     <type>        <options>        <dump>  <pass>
proc            /proc                             proc          defaults         0       0
# /dev/sda1
UUID=38eebfc2-3eb5-49b6-bc6a-fb8825d4a569 /       reiserfs      notail           0       1
# /dev/sda8
UUID=8747a6da-79d1-48f7-af60-7b4b47fe3336 /home   reiserfs      defaults         0       2
# /dev/sda5
/dev/sda5     /media/sda5-backup                  vfat          defaults,utf8,umask=007,gid=46   0       1
# /dev/sda7
/dev/sda7     /media/sda7-scratch                 reiserfs      defaults         0       2
# /dev/sdb2
/dev/sdb2     /media/sdb2-media                   reiserfs      defaults         0       2
# /dev/sdb3
/dev/sdb3     /media/sdb3-backup                  vfat          defaults,utf8,umask=007,gid=46   0       1
# /dev/sdb5
/dev/sdb5     /media/sdb5-tbird-mail              reiserfs      defaults         0       2
# /dev/sdb6
/dev/sdb6     /media/sdb6-data                    reiserfs      defaults         0       2
# /dev/sda6
UUID=4282b0af-3ed2-402d-a788-9f3d953ce39e  none   swap          sw               0       0
# /dev/sdb4
/dev/sdb4     none                                swap          sw               0       0
/dev/hdc      /media/cdrom0                       udf,iso9660   user,noauto      0       0
/dev/hdd      /media/cdrom1                       udf,iso9660   user,noauto      0       0
/dev/fd0      /media/floppy0                      auto          rw,user,noauto   0       0

Is one way better than the other, UUID v file system name, and why please?
fstab also shows my vfat partitions pass=1.  Should this be pass=2 or is there a need for vfat to be pass=1 for some reason?

blkid was also mentioned.  Where does blkid get the data from?  Does the system use blkid data for anything?  Mine shows this, which was once correct, many moons ago, but is now total rubbish::

~$ blkid
/dev/sda1: UUID="38eebfc2-3eb5-49b6-bc6a-fb8825d4a569" TYPE="reiserfs"
/dev/sda5: LABEL="1_BACKUPS" UUID="4648-6F8D" TYPE="vfat"
/dev/sda6: UUID="4282b0af-3ed2-402d-a788-9f3d953ce39e" TYPE="swap"
/dev/sda7: UUID="b22e6092-13e8-4015-9d4c-a7e9a982015c" TYPE="reiserfs"
/dev/sda8: UUID="8747a6da-79d1-48f7-af60-7b4b47fe3336" TYPE="reiserfs"
/dev/sdb1: LABEL="2-DATA" UUID="460F-DBD3" TYPE="vfat"
/dev/sdb2: LABEL="2-MEDIA" UUID="8C1F-B836" TYPE="vfat"
/dev/sdb3: LABEL="2-BACKUP" UUID="D22F-9AB1" TYPE="vfat"
/dev/sdb4: UUID="48a3f59a-6a29-4a76-bab4-925cac2dd7fa" TYPE="swap"
~$

Any guidance on this is appreciated.  Thanks in advance.
Regards
Peter.

---

### Post by Herman on 2008-02-26
:) Hello mavicus,
I'm sorry, I didn't realize your problem wasn't already solved by dcstar's good advice.

If you would like specific help, it would be great if you could post here the output from the command 'ls /dev/disk/by-uuid/ -alh'```
ls /dev/disk/by-uuid/ -alh
```Did you edit your 32 bit installation's /etc/fstab file when you installed in it your 64 bit version?
```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config --
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0

[COLOR=Red] # Entry for /dev/sda3 :
UUID=aa8596e2-d69c-48e2-9007-f164acf7d7d5 / ext2 defaults,errors=remount-ro 0 1
[/COLOR] 
# Entry for /dev/sda4 :
UUID=bb7bfadd-499b-40e3-8ad0-f75e481f55aa /home ext2 defaults 0 2

# Entry for /dev/sda1 :
UUID=a647f5b2-aa1a-4a59-9864-ab94ae7a3b47 /media/preboot ext2 defaults 0 2

# Entry for /dev/sda2 :
UUID=4ad196d4-74ef-40bf-baa3-38f0b363d13e /media/ubuntu-6.06 ext2 defaults 0 2

# Entry for /dev/sdb1 :
UUID=7953b2a3-782d-44a2-97b2-a0f2ce23c3ef /media/sata500 ext3 defaults 0 2

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sdd1 /media/ntfs01 ntfs-3g defaults,locale=en_US.UTF-8 0 0
``` I don't think dcstar would have intended to have you booting your 64 bit kernel but mounting your 32 bit / (root), so you would want to change the first entry to
```
# Entry for /dev/sdb2 :
UUID=f72f0a5f-85e8-4a7d-9b09-8959f2e74b5e / ext2 defaults,errors=remount-ro 0 1
```> I was eventually able to fix it myself by replacing the fstab of the 64 bit version with a copy of the fstab from the 32 bit version, EVEN THOUGH the 32 bit version contains incorrect references to EVERY drive on my system. It was a last resort that worked. The drive in question is referenced in the 32 bit fstab as sda, where in the 64 bit it is referenced as sdb.
The partitions on this drive mount as sdb on both systems, regardless of what the fstab says. The drive references in your present /etc/fstab files are behind hash marks '#', meaning they are comments there for your reference, but the operating system ignores them, so they can be wrong without affecting the operating system's performance at all.
Although, it would be better if they were correct.
> I am confused, and my fstab is now different than the end result of my drives after they mount, but the problem is fixed. I am more lost than before, but I have no unclean unmounts. I'm confused too.
Your entry for /dev/sda4 , the partition with the file system  you are saying was being fscked on every reboot is exactly the same in both /etc/fstab files, so it makes no sense to me at all why your 32 bit /etc/fstab should be better than your 64 bit /etc/fstab. :confused:
There must be a detail there somewhere I have missed. I have looked and looked and I can't for the life of me see any difference.

One question I have is, why are some of your file systems listed as ext2 and not ext3? Do you really prefer to use ext2 rather than ext3?

Regards, Herman :)

---

### Post by peddy on 2008-02-26
I also have this problem. I thought it was normal ubuntu behavior until I read this thread :P

---

### Post by randiroo76073 on 2008-02-26
Here's a little more on this:
[http://ubuntuforums.org/showthread.php?t=564631](http://ubuntuforums.org/showthread.php?t=564631)

---

### Post by Herman on 2008-02-26
The first thing to do is run a better file system check from your Ubuntu Live CD or a [Gnome Partition Editor]("http://gparted.sourceforge.net/") LiveCD and see if that clears the problem.

Here's how to do it from the command line, [                      Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem") - from a Live CD - command line.

Here's how to use Gnome Parition Editor, but you need a Ubuntu Gutsy or later LiveCD, [                         Running a filesystem check with GParted]("http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_with_GParted_") a user freindly GUI method

The other main cause of the Ubuntu boot process beiing interrupted with a  file system check that can't run is when the /etc/fstab file has not been updated since partition changes have been made.
Here's how to fix that, [                          About /etc/fstab files with UUID filesystem ID added]("http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with").

Regards, Herman :)

---

### Post by randiroo76073 on 2008-02-27
Your site is great Herman, also use your SuperGrub disk :)  Have recommended it to alot of converts.

---

### Post by Herman on 2008-02-27
> Your site is great Herman :) Thank you.,>  also use your SuperGrub disk :)  Have recommended it to alot of converts.  :)That's good.
adrian15 is the developer of Super Grub DIsk, he is the one who deserves the credit. 
Super Grub Disk is  very often the fastest way to get operating systems to boot. It saves a lot of work for most people, because otherwise they would have to learn how to use GRUB's Command Line, but if they're new to Linux they might find that quite a challenge.  I have some documentation for it. Super Grub DIsk has its own documentation now as well.
Anyhow, keep up the good work!

Regards, Herman :)

---

