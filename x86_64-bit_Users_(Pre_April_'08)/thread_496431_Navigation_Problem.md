---
title: "Navigation Problem"
date: 2007-07-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by sfarber on 2007-07-09
Hello.
Since I was installing the 64bit version (New installation) I am unable to open Places->Computer. 
It seems to try but there is nothing, and all the icons in Desktop are gone.

What can be wrong?

Shay.

---

### Post by Ocxic on 2007-07-09
?!?! That is very odd, did you check your cd after you burned it, could be a gitch.

open a terminal and type "mount" (without quotes) and post the output, and "cat /etc/fstab" as well. just to make sure all your drives are there.

I'm pretty sure this is just some weird problem, I'm kinda having the same thing right now as I can;t get my volumes to show on my desktop ether, so the two may be related..

---

### Post by sfarber on 2007-07-10
Well, This is the "mount" output :

/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sda5 on /media/sda5 type ntfs (rw,nls=utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)

This is the "/etc/fstab"

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=504b010f-01f0-47f8-a6a8-344b576c8be2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=2A246345246312DD /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=B8D806FAD806B722 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=fd966c01-43f1-43f7-a865-0226348dbc7c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

P.S.
From other programs I can see the drivers (For example from MediaPayer, etc.)
But when I want just open the folder Computer from the menu Places, it does't work.
I think there is a problem with the software of viewing folders.

---

