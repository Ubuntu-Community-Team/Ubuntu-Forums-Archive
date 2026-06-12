---
title: "usb mount points are gone after update"
date: 2006-02-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by yoshu on 2006-02-09
Hello,

I am running a version of debian sid 64 bit (i would be using kubuntu's sid distro but I don't know where to access it and I would be using kubuntu breezy if it worked a little better on my system) and I have just done an update and an dist-upgrade.  This has lead to my usb drives not being recognized - i.e.., they don't pop up on the screen.    Needless to say this is a problem and I would like to fix it.  Any help would be appreciated.

My fstab looks like this

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
usbfs           /proc/bus/usb   usbfs   devmode=0666    0       0
/dev/sda2       /               reiserfs defaults        0       1
/dev/sda3       /home           reiserfs                         
reiserfs        defaults        0       2                       
/dev/sda1       none            swap    sw              0       0
/dev/sda4       /media/sda4     ntfs    ro,umask=000    0       0
/dev/cdrom      /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

and here are my system specs

Host/Kernel/OS  "cnotics" running Linux 2.6.14-kanotix64-9 x86_64 [ KANOTIX 64 2005-04 LITE ]
CPU Info        AMD Athlon 64 3000+ clocked at [ 1809.305 MHz ]
Videocard       nVidia NV40 [GeForce 6800 Ultra/GeForce 6800 GT]  X.Org 6.9.0  [ 1024x768 @76hz ]
Network cards   Marvell 88E8001 Gigabit Ethernet Controller, at port: a400
                nVidia CK804 Ethernet Controller, at port: b000
Processes 121 | Uptime 38min | Memory 491.801/497.266MB | HDD ATA Maxtor 6Y120M0 Size 123GB (6%used) | Client Shell | Infobash v2.50rc8

Thanks in advance.

edit: This is just a problem with kde, i can mount the device manually  mount -t vfat /dev/sdb1/ but I would like an auto mount option

---

