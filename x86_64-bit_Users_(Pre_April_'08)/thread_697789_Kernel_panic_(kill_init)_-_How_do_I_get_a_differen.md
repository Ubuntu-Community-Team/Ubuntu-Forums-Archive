---
title: "Kernel panic (kill init) - How do I get a different kernel?"
date: 2008-02-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by lapsey on 2008-02-15
I'm using vanilla gutsy but things are not going well.

After the latest episode of 64-bit SATA fun (IE, crashing with SATA errors), I ran fsck on all partitions (all fine) and restarted.

Now it gets to "Kernel panic - not syncing: Attempted to kill init!" and stops there every time.

I apparently only have one kernel in /boot : 2.6.22-14-generic, so booting into an older one is not an option.

**Can the system be properly started with a different kernel, and if so how do I get it on there?** I am currently using a Live CD.

---

### Post by Yellow Pasque on 2008-02-15
Can you mount the filesystem with the LiveCD? If you can, look in /boot/grub/menu.lst for the root device and look at /boot/grub/device.map to make sure the device is mapped correctly. You  can get the /dev path info with:
```
sudo lshw -businfo -C disk
```

---

### Post by lapsey on 2008-02-15
/dev/sda1 is root, /dev/sda2 is home

the map seems to match, so thats not an issue:

menu.lst:
```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=c3219c70-0cb6-4a8f-b5$
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=c3219c70-0cb6-4a8f-b5$
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

```

device.map:
```
(hd0)   /dev/sda
```

dev paths seem normal:
```

Bus info          Device     Class       Description
====================================================
scsi@0:0.0.0      /dev/sda   disk        74GB WDC WD800AAJS-00
ide@0.0           /dev/hda   disk        PIONEER DVD-RW DVR-112D
                  /dev/hda   disk        
scsi@6:0.0.0      /dev/sdb   disk        1900MB ZEN Stone
                  /dev/sdb   disk        1900MB
scsi@7:0.0.0      /dev/sdc   disk        STORAGE DEVICE
                  /dev/sdc   disk        
scsi@7:0.0.1      /dev/sdd   disk        STORAGE DEVICE
                  /dev/sdd   disk        
scsi@7:0.0.2      /dev/sde   disk        STORAGE DEVICE
                  /dev/sde   disk        
scsi@7:0.0.3      /dev/sdf   disk        STORAGE DEVICE
                  /dev/sdf   disk        

```

i tested fsck again and found and fixed errors, but this didnt change anything.


what next?

---

### Post by Chame_Wizard on 2008-02-19
hai,i am new here,also have the same problem 

something seems to be wrong here:confused::

> # menu.lst - See: grub( 8 ), info grub, update-grub(8 )
#            grub-install(8 ), grub-floppy(8 ),
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
# kopt=root=UUID=57eaed1c-4908-4e68-b782-991471c9da22 ro

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic
root=UUID=57eaed1c-4908-4e68-b782-991471c9da22 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic
root=UUID=57eaed1c-4908-4e68-b782-991471c9da22 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic
root=UUID=57eaed1c-4908-4e68-b782-991471c9da22 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic
root=UUID=57eaed1c-4908-4e68-b782-991471c9da22 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by Yellow Pasque on 2008-02-19
Hi Chame_Wizard, can you run some commands for me to make sure we're booting off the correct disk?
```
cat /boot/grub/device.map
sudo fdisk -l
sudo lshw -businfo -C disk
cd /dev/disk/by-uuid; ls -l
```

---

### Post by Chame_Wizard on 2008-02-19
i am using the 7.10 live cd.

my system
Mainboard :	Asrock 939Dual-SATA2
Processor :	AMD Athlon 64 3700+ @ 2200 MHz
Physical Memory :   1024 MB DDR-RAM 400 mhz
Hard Disk :	WDC WD2500KS-00MJB0  (250 GB)
Video Card :	Nvidia Corp GeForce 7600 GS
Device Audio :	Audigy LS Series
DVD-Rom Drive :	Optiarc DVD RW AD-7173A
Network Card :	Acer Labs Incorporated (ALi/ULi) ULi M5263 Fast Ethernet Controller
Operating System DUAL BOOT :	Microsoft Windows XP Professional 5.01.2600 Service Pack 2 & Kubuntu 7.04 Feisty Fawn  64-bit(2.6.20.16)




my partition: 
```
ubuntu@ubuntu:~$ sudo fdisk -l


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x42954294

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15358   123363103+   7  HPFS/NTFS
/dev/sda2           15359       30026   117820710   83  Linux
/dev/sda3           30027       30401     3012187+   5  Extended
/dev/sda5           30027       30401     3012156   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       11489    92285361    7  HPFS/NTFS
/dev/sdb2           11490       24028   100719517+   7  HPFS/NTFS
/dev/sdb3           24029       30401    51191122+   7  HPFS/NTFS

```

```
ubuntu@ubuntu:~$ cd /dev/disk/by-uuid; ls -l
total 0
lrwxrwxrwx 1 root root 10 2008-02-20 00:50 0264802A64802311 -> ../../sdb3
lrwxrwxrwx 1 root root 10 2008-02-20 00:50 36F850FAF850B9B7 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-02-20 00:50 4C94049E94048D20 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-02-20 00:50 57eaed1c-4908-4e68-b782-991471c9da22 -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-02-20 00:50 93cda1d9-3609-49dd-87ab-a7674c623cab -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-02-20 00:50 AAB826D9B826A433 -> ../../sdb2
ubuntu@ubuntu:/dev/disk/by-uuid$   

```

1st and 3rd command aren't working
```
ubuntu@ubuntu:~$ cat /boot/grub/device.map
cat: /boot/grub/device.map: No such file or directory[/QUOTE]

[QUOTE]ubuntu@ubuntu:~$ sudo lhsw -businfo -C disk
sudo: lhsw: command not found

```

also tried 

```

root@ubuntu:~# sudo mkdir /media/sda2
mkdir: cannot create directory `/media/sda2': File exists
root@ubuntu:~# sudo mount /dev/sda2 /media/sda2

mount: /dev/sda2 already mounted or /media/sda2 busy
mount: according to mtab, /dev/sda2 is already mounted on /media/sda2
```

---

