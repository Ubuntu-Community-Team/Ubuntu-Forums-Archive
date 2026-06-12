---
title: "Ubuntu RAID issues preventing boot"
date: 2009-07-27
forum: x86 64-bit Users
---

### Post by Platypus123 on 2009-07-27
Last week I installed 9.04 and I tried moving my Vista NTFS RAID 1 partition to Ubuntu.  I could see the drives, but they were recognized as two drives instead of one.  After reading around the forums, I knew either dmraid or mdadm should make it work.  I couldn't get dmraid to work so I tried with mdadm (first mistake).  

After what I thought was a successful mount of the two drives appearing as a mirrored array in Ubuntu (md0), I rebooted.  At boot, I can no longer get into either Ubuntu or Vista.  Ubuntu tells me that my device is not recognized and that it's dropping to shell (initramfs), when I try to boot into Vista to fix the Ubuntu boot, I'm told that I'm 'Missing Operating System'.  Both OS's are on different hard drives (Ubuntu on 80GB drive and Vista on mirrored Raptors).  

I can boot the Live CD, but I can't mount my Ubuntu file system because it thinks that my Ubuntu drive is part of my RAID set (???).  I can fdisk-l and still see all of my drives and partitions, but I can't mount Ubuntu to fix it.

I know the answer is in here somewhere.  I don't want to keep reformatting as I'll never learn anything. 

Help!

---

### Post by snek on 2009-07-27
First off it would probably be helpful to paste some of the output and configs you're using.
Right now it's pretty unclear what the problem is exactly.

For one you will want to paste the output of fdisk -l and probably also /boot/grub/menu.lst

It sounds like you made an array from the wrong drives, one of them being your ubuntu installation and that GRUB is now pointing to some partition which it can't use.

---

### Post by punkybouy on 2009-07-27
First off, can you tell us whether this is hardware raid or software raid?  Secondly can you be more specific about what you mean by "moving" your Windows partition.  In any case here are some tips.  If your RAID is hardware based then you need a driver for the RAID card/chip and in Windows that driver has to be installed BEFORE the rest of the installation begins.  I believe it is called "slipstreaming".  In XP it was done by pressing the F6 key during installation bootup and at the proper time installing the RAID card driver via floppy disk.
In Windows I don't think the system partition can be put on a RAID 1 partition if that partition is software based in Windows.
I have not investigated sofware RAID too much in Linux but again whatever driver is used has to be loaded before the rest of the OS.
I have used hardware RAID cards with Linux and they are setup to present to the OS what appears to be a single disk but the OS still has to recognize the particular chipset and load the appropriate driver.  Not set up that way but if the hardware RAID merely presents a bunch of disks to the OS you could assemble those loose disks into a virtual disk via software in the OS.  Hope this helps.

---

### Post by punkybouy on 2009-07-27
On second thought go with investigating the boot loader, grub probably in Linux although Windows has a boot loader too.  Once you make a choice of OS from whatever boot loader menu it should know which system partition to load.

---

### Post by Platypus123 on 2009-07-27
Below, please find a copy of fdisk-l:

> root@ubuntu:/media# fdisk -l

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ee08d83

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9791    78643200    7  HPFS/NTFS
/dev/sda2            9791       13055    26214400    7  HPFS/NTFS
/dev/sda3           13055       61031   385372160    7  HPFS/NTFS

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ee08d83

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9791    78643200    7  HPFS/NTFS
/dev/sdb2            9791       13055    26214400    7  HPFS/NTFS
/dev/sdb3           13055       61031   385372160    7  HPFS/NTFS

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        9360    75184168+  83  Linux
/dev/sdd2            9361        9729     2963992+   5  Extended
/dev/sdd5            9361        9729     2963961   82  Linux swap / Solaris

Disk /dev/sde: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8578505

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        9040    72610816    7  HPFS/NTFS

Disk /dev/sdf: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8578505

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1        9040    72610816    7  HPFS/NTFS

Disk /dev/md0: 74.3 GB, 74353410048 bytes
2 heads, 4 sectors/track, 18152688 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table


As you can see, my Ubuntu file system is at sdd1.  Here is the contents of menu.lst:

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=0f71f34d-62e4-4789-a27d-9b0d28afb329 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0f71f34d-62e4-4789-a27d-9b0d28afb329

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		0f71f34d-62e4-4789-a27d-9b0d28afb329
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=0f71f34d-62e4-4789-a27d-9b0d28afb329 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		0f71f34d-62e4-4789-a27d-9b0d28afb329
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=0f71f34d-62e4-4789-a27d-9b0d28afb329 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		0f71f34d-62e4-4789-a27d-9b0d28afb329
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=0f71f34d-62e4-4789-a27d-9b0d28afb329 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		0f71f34d-62e4-4789-a27d-9b0d28afb329
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=0f71f34d-62e4-4789-a27d-9b0d28afb329 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		0f71f34d-62e4-4789-a27d-9b0d28afb329
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0f71f34d-62e4-4789-a27d-9b0d28afb329 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		0f71f34d-62e4-4789-a27d-9b0d28afb329
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0f71f34d-62e4-4789-a27d-9b0d28afb329 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		0f71f34d-62e4-4789-a27d-9b0d28afb329
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


My Vista OS is installed on the mirrored Raptors at sde1 and sdf1 in FakeRAID.  When I used mdadm to try and get Ubuntu to recognize them as one drive is where I started having problems.  

How do I recover without reformatting?

---

### Post by snek on 2009-07-28
To check the setup of md0 you can
```
sudo cat /proc/mdstat
```

This will tell you which partitions the md0 is made of.
Somehow I think you made the array on wrong partitions.
However, I think mdadm is not the way to go since you are using NTFS.
I've only really used it with special raid partitions, this is a special partition type used for softraid in the partition manager. Preferably I even set it up during the initial Ubuntu install.

Wish I could be of more help but I have no way of testing any of this.

---

### Post by punkybouy on 2009-07-28
When you boot up do you get the option of which OS to choose? Since you have more than one drive is your bios configured to point to any particular drive as its boot drive?  Some older motherboards with both SATA and IDE ports will still look for an OS on the IDE port first. What about jumper settings on the drives?  Some require drives to jumpered to the "cable select" position.

---

### Post by punkybouy on 2009-07-28
Can you try disconnecting the drives of the Windows OS and see if Linux boots up?

---

### Post by Platypus123 on 2009-08-14
I obliterated Vista and reformatted all NTFS drives to EXT4.  I've had enough of Windows anyway. EXT4 is much faster! It's like SSD speeds!  I moved the date off of my array first and implemented a software RAID with MDADM.  

Thanks!

---

