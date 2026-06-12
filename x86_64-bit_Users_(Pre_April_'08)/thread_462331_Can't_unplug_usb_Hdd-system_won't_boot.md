---
title: "Can't unplug usb Hdd-system won't boot"
date: 2007-06-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mr_bleu on 2007-06-02
I've tried searching for the answer to my puzzling problem, to no avail.  I can not unplug my usb drive and boot my system.  I have linux installed in my laptop's hdd and the usb drive.  I've tried editing grub menu list, but I don't know what exactly to change.  

Grub menu.lst:

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
splashimage=(hd0,1)/boot/100_1325.JPG
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		4

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kernel	/vmlinuz root=/dev/hda1 ro
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
##      kopt_2_6_8=root=/dev/hda1 ro
##      kopt_2_6_8_2_686=root=/dev/hda1 ro
# kopt=root=UUID=5f00c0be-7f6f-4062-b96a-d52f35dd9da1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,1)
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
## e.g. defoptions=vga=791 resume=/dev/hda1
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
##      howmany=2
howmany=2

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=5f00c0be-7f6f-4062-b96a-d52f35dd9da1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=5f00c0be-7f6f-4062-b96a-d52f35dd9da1 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Any help is Greatly Appreciated.
I get 
"Grub loading.......error 21"   when I unplug the usb drive.
:(:(
P.S.  I had the same problem with suse.

---

### Post by david_2001 on 2007-06-02
> **Mr_bleu said:**
> I've tried searching for the answer to my puzzling problem, to no avail.  I can not unplug my usb drive and boot my system.  I have linux installed in my laptop's hdd and the usb drive.  I've tried editing grub menu list, but I don't know what exactly to change.  

Grub menu.lst:

[Cut]

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hda1 ro
##      kopt_2_6_8_2_686=root=/dev/hda1 ro
# kopt=root=UUID=**5f00c0be-7f6f-4062-b96a-d52f35dd9da1** ro

[Cut]

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=**5f00c0be-7f6f-4062-b96a-d52f35dd9da1** ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=**5f00c0be-7f6f-4062-b96a-d52f35dd9da1** ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
Error 21 = Selected disk does not exist.  My guess would be that the UUID for hd0 in your menu.lst refers to your usb drive and not to the linux root partition on your system's hard disk drive.  Take a peek in /etc/fstab or use "sudo vol_id -u [device]" to find the correct UUID to use.  Alternatively, substitute the correct device name, e.g. /dev/sda1, for the UUID.  (Don't forget to check that there really is a linux kernel installed on your hard drive before changing menu.lst!)

---

### Post by Mr_bleu on 2007-06-02
It's trying to boot from the USB disc which is unplugged.  I have linux installed on my internal hdd as well.  It was installed there first.  I'd like to be able to unplug the usb drive and use that for when I go visiting; just need the mouse and drive.

---

### Post by david_2001 on 2007-06-02
> **Mr_bleu said:**
> It's trying to boot from the USB disc which is unplugged.
That's what I was trying to fix by suggesting what to change in the menu.lst on your hard disk so that grub no longer tries to boot the kernel on the usb disk (you'll have to boot with the usb disk inserted in order to make the changes).  Making the usb disk usable on other machines is a different problem, and one that is outwith my experience.

---

### Post by Mr_bleu on 2007-06-02
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=5f00c0be-7f6f-4062-b96a-d52f35dd9da1 ro quiet splash
In fstab they are listed correctly as far as I can tell:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=c02858ca-e2e7-4a5a-aa85-9369238a9b9b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=5f00c0be-7f6f-4062-b96a-d52f35dd9da1 /media/sda1     ext3    defaults        0       2

---

### Post by david_2001 on 2007-06-02
> **Mr_bleu said:**
> root (hd0,0)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=5f00c0be-7f6f-4062-b96a-d52f35dd9da1 ro quiet splash
In fstab they are listed correctly as far as I can tell:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=c02858ca-e2e7-4a5a-aa85-9369238a9b9b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=**5f00c0be-7f6f-4062-b96a-d52f35dd9da1** /media/sda1     ext3    defaults        0       2

I was right, the UUID for your usb disk (/media/sda1) matches the UUID for hd0 in your menu.lst file.  What you need to do is edit menu.lst and replace all instances of 5f00c0be-7f6f-4062-b96a-d52f35dd9da, as highlighted in my first post, with c02858ca-e2e7-4a5a-aa85-9369238a9b9b, i.e. with the UUID for the linux root partition on your hard disk.  Save the file, shut down your system, remove the usb disk and start it up again.

EDIT: And hot-pluggable media such as usb disks really shouldn't be listed in fstab.  Edit /etc/fstab and delete:
> # /dev/sda1
UUID=5f00c0be-7f6f-4062-b96a-d52f35dd9da1 /media/sda1     ext3    defaults        0       2

---

### Post by Mr_bleu on 2007-06-02
sda1 is my internal drive.  sdb1 is my usb drive.

---

### Post by david_2001 on 2007-06-02
> **Mr_bleu said:**
> sda1 is my internal drive.  sdb1 is my usb drive.
Doesn't matter if you are using UUID's to identify drives.  Anyway, is your system's hard disk really mounted as /media/sda1?  If that is the case then was the menu.lst you quoted in your first post /boot/grub/menu.lst or /media/sda1/boot/grub/menu.lst?  If it was /boot/grub/menu.lst then you need to post /media/sda1/boot/grub/menu.lst and /media/sda1/etc/fstab so we can do further diagnosis.  EDIT: And, as you have probably realised, it's /media/sda1/boot/grub/menu.lst that has to be correct in order to get your system to boot without the usb disk.

---

### Post by Mr_bleu on 2007-06-02
I booted into ubuntu on the usb drive. It's the default.  I then ran:

djr@djr-laptop:~$ cd /media/sda1/boot/grub
djr@djr-laptop:/media/sda1/boot/grub$ sudo gedit /boot/grub/menu.lst
Password:




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
# kopt=root=UUID=c02858ca-e2e7-4a5a-aa85-9369238a9b9b ro

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
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=c02858ca-e2e7-4a5a-aa85-9369238a9b9b ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=c02858ca-e2e7-4a5a-aa85-9369238a9b9b ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu, kernel 2.6.20-16-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=5f00c0be-7f6f-4062-b96a-d52f35dd9da1 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=5f00c0be-7f6f-4062-b96a-d52f35dd9da1 ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


Then I went to /media/sda1/etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5f00c0be-7f6f-4062-b96a-d52f35dd9da1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=8d019312-db53-42ff-808a-12acaa921330 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by david_2001 on 2007-06-03
> **Mr_bleu said:**
> I booted into ubuntu on the usb drive. It's the default.  I then ran:

djr@djr-laptop:~$ cd /media/sda1/boot/grub
djr@djr-laptop:/media/sda1/boot/grub$ sudo gedit /boot/grub/menu.lst


You will have to boot into Ubuntu on the usb drive and then enter the following command in order to see the menu.lst that needs to be modified (there's no need to use sudo to just view the file):
```
gedit /media/sda1/boot/grub/menu.lst
```

PS.  Hope the [COLOR="SandyBrown"][reinstall]("http://ubuntuforums.org/showpost.php?p=2771699&postcount=6")[/COLOR] solves your problems.
> **Mr_bleu said:**
> I don't remember the exact location, (I'm reinstalling at the moment) but I do believe it's in the /usr/bin/ folder.  You can check by going to System>administration>synaptic manager.
Then type aegis in the Search box after hitting the button.  Right click and view Properties?  If that's right (it's somewhere right there) it'll show you where the files are installed.  It IS possible to get a virus in linux.  It's just not as common as with mr. gates' software.

---

