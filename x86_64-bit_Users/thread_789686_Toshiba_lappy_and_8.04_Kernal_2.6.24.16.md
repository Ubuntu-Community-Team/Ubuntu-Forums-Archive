---
title: "Toshiba lappy and 8.04 Kernal 2.6.24.16"
date: 2008-05-10
forum: x86 64-bit Users
---

### Post by two00lbwaster on 2008-05-10
I've just splashed out for myself on one of these 17" widescreen Toshibas; the Equium L350-10L To be exact.  The problem I had is that I couldn't get the Ubuntu 8.04 x64 CD to boot past the selection screen I just end up with a message 

edit:
```
[INDENT]Check root= bootarg cat /proc/cmdline[/INDENT]
[INDENT]or missing modules, devices: cat /proc/modules ls /dev[/INDENT]
ALERT! /dev/disk/by-uuid/a82642c-bd98-471c-b11a-581682fe56aa does not exist. Dropping to a shell!
``` 

So the boot has failed for some reason.

So I wondered whether gutsy x64 would work and it did fine.  So I installed it and then ran the update.  Result was exactly the same, however, this time I pressed escape to get into grub and selected the gutsy 2.6.22.14 generic kernal and all is well.

I've looked in the logs but can't see anything to do with the 2.6.24.16 kernal in there.

---

### Post by Yellow Pasque on 2008-05-11
Hi. Please run these commands and post the output in [ code ][ /code ] blocks:
```
cat /etc/fstab
cd /dev/disk/by-uuid; ls -la
cat /boot/grub/menu.lst
```

---

### Post by two00lbwaster on 2008-05-11
Thanks for the reply.  Right here are the results of the commands that you asked me to run.

```
richard@richard-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=a82642c8-bd98-471c-b11a-581682fe56aa /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=32B8D620B8D5E301 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=F496DB1A96DADC64 /media/sda3     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=b6be3a39-b921-424d-8f94-f137d30f1999 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

```
richard@richard-laptop:~$ cd /dev/disk/by-uuid; ls -la
total 0
drwxr-xr-x 2 root root 120 2008-05-11 12:04 .
drwxr-xr-x 6 root root 120 2008-05-11 12:04 ..
lrwxrwxrwx 1 root root  10 2008-05-11 12:04 32B8D620B8D5E301 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-05-11 12:04 a82642c8-bd98-471c-b11a-581682fe56aa -> ../../sda2
lrwxrwxrwx 1 root root  10 2008-05-11 12:04 b6be3a39-b921-424d-8f94-f137d30f1999 -> ../../sda4
lrwxrwxrwx 1 root root  10 2008-05-11 12:04 F496DB1A96DADC64 -> ../../sda3

```

```
richard@richard-laptop:/dev/disk/by-uuid$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=a82642c8-bd98-471c-b11a-581682fe56aa ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a82642c8-bd98-471c-b11a-581682fe56aa ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a82642c8-bd98-471c-b11a-581682fe56aa ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a82642c8-bd98-471c-b11a-581682fe56aa ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a82642c8-bd98-471c-b11a-581682fe56aa ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

Hope this ca help with the diagnosis.

---

### Post by Yellow Pasque on 2008-05-11
Awesome! Let's try to mount by /dev id instead of the UUID.
```
gksudo gedit /etc/fstab
```
Change the following and save. Then try and boot the 2.6.24-16 kernel:
```
# /dev/sda2
UUID=a82642c8-bd98-471c-b11a-581682fe56aa /               ext3    defaults,errors=remount-ro 0       1
```
--->
```
/dev/sda2  /  ext3    defaults,errors=remount-ro  0 1
```

---

### Post by two00lbwaster on 2008-05-11
Sorry the g/f sent me off to the shops :)

Right carried out the above and got the error message below:

```
udevd-event[1515]: run_program: '/sbin/modprobe' abnormal exit
```

I've changed the line I replaced back to what it was, for now.

---

### Post by two00lbwaster on 2008-05-13
Nobody else help here or experience the same issues?

---

### Post by jonty_rocks3 on 2008-05-17
I have same laptop and having same problem of modprobe. Really need help too :( if you find out please post it or pm me!
Cheers

---

### Post by Yellow Pasque on 2008-05-17
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/96084](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/96084) is the closest thing I could find. If the suggested fix (adding irqpoll to the boot options) does not work, I suggest registering a Launchpad account and posting your info in that thread.

---

### Post by two00lbwaster on 2008-05-22
Unfortunately, I've gone to 64bit Vista, it eats 1GB+ of RAM!!!!!, and I am running Ubuntu 8.04 under VMware 64bit(32bit Ubuntu because the beta doesn't work with 64bit operating systems as far as I've been able to conclude from it not working on any system or OS so far).  

The reason for that was I lost wireless, and even reinstalling 7.10 didn't bring it back.  

However, Vista works just fine :(

---

