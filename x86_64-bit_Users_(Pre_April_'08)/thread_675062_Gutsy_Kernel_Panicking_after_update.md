---
title: "Gutsy Kernel Panicking after update?"
date: 2008-01-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by j-hon on 2008-01-22
Hi guys, I'm having some strange trouble.  After coming back from Christmas break, I went to update-upgrade my school/work computer and got caught in a snag.  The computer froze in the updating process, which necessitated a restart.  

After restarting the computer, I was aghast to find out that my kernel was in a severe state of panic.  Specifically, it was panicking over :
```
"not syncing :VFS: Unable to mount root fs on unknown - block(0,0).
```

It also does this whenever I try to go to recovery mode, so I am forced to boot from the LiveCD.

I've read the other threads where people are having similar issues, and I presume it came from something in the update.  None of the other proposed fixes have worked, so I decided to create a new thread.

Here's my Menu.lst, if it will help.  Thanks guys.

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
# kopt=root=UUID=49f1242d-06ae-4d77-8534-320c218aa58c ro

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
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=49f1242d-06ae-4d77-8534-320c218aa58c ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=49f1242d-06ae-4d77-8534-320c218aa58c ro single 
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by PmDematagoda on 2008-01-22
In addition to the menu.lst, could you please post the results of:-
```
blkid
```

---

### Post by j-hon on 2008-01-22
> **PmDematagoda said:**
> In addition to the menu.lst, could you please post the results of:-
```
blkid
```

Sure!

I got :
```
/dev/sdb1: UUID="8a165738-311c-4180-b061-4634da389311" SEC_TYPE="ext2" TYPE="ext3" 

```

---

### Post by PmDematagoda on 2008-01-22
So now you should change the menu.lst since the entry in the menu.lst is obviously wrong.

Open menu.lst for editing using gedit and then edit the last lines so that they look like this:-
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		[COLOR="Red"]**(hd1,0)**[/COLOR]
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=[COLOR="Red"]**8a165738-311c-4180-b061-4634da389311**[/COLOR] ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		[COLOR="Red"]**(hd1,0)**[/COLOR]
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=[COLOR="Red"]**8a165738-311c-4180-b061-4634da389311**[/COLOR] ro single 
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		[COLOR="Red"]**(hd1,0)**[/COLOR]
kernel		/boot/memtest86+.bin
quiet

```

---

### Post by tobr on 2008-01-23
I have the same problem with Kubuntu 7.10 32bit. Today after 2 months break I updated. Download OK (172MB), during applying changes (60%) error box that something wrong and installation is to be stopped not to damage the system. After restart Kernel panic.

RAMDISK: ran out of compressed data
invalid compressed format (err=1)
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block(0,0)

Yesterday I did fresh installation of Kubuntu on another PC on dedicated HDD. Install OK and Kubuntu was working. Then update notification about available updates. Adept updater downloaded 472MB of updates and the scenario was the same. It was fresh install on empty HDD and update imediatelly after fresh install with default options (nothing changed in the system).

Can be damaged update files on czech mirror server which is default for me?

---

### Post by tobr on 2008-01-23
OK, everything is working by now. Problem was with the corrupted file /boot/initrd.img-2.6.22-14-generic. I only copied correct file from another installation and Kubuntu boots again :-) The same helped with both my Kubuntu damaged installations.

Note: I don't have dedicated partition for boot so that the corruption was definitelly caused by download process not by known issue with full boot partition.

to j-hon: if your installation is still not working, look at the size of the mentioned file (in 32bit version should be 7,523,474B by now).

---

### Post by j-hon on 2008-01-23
I changed my Menu.lst file to reflect the changes that you posted above, but now grub throws```
Error 17: Cannot mount selected partition
```

tobr -   I looked at the file that you specified, and found two.  One is initrd.img-2.6.22-14-generic (which is 0kb), and the other is initrd.img-2.6.22-14-generic.bak (which is 6.9MB).  Which one am I looking for, and how can I tell if it has been corrupted?

Thanks,

Jeremy

---

### Post by PmDematagoda on 2008-01-23
Concerning the new error, please post the output of:-
```
sudo fdisk -l
```

---

### Post by tobr on 2008-01-24
So you definetelly have the same error as I had. My kernel was about 1MB but not complet as well.

The length of the file should be around 6.9MB (as I mentioned above). The file with the extension bak is probably the backup of the present kernel before update. The length 0kB is wrong. I took the file from another installation and copied. But I suppose you can try to delete the file with the 0kB length /boot/initrd.img-2.6.22-14-generic and to rename the file with the bak extension (remove extension). Nothing worse can happened :-). Not sure about the changes You did before with the Menu.lst. If the rename does not work, You can try to put your old menu.lst file back. But to be honest my menu.lst looks similar to the proposed one.

1) Try to use as /boot/initrd.img-2.6.22-14-generic your backup (/boot/initrd.img-2.6.22-14-generic.bak)
2) If not working, try to return your before working menu.lst back (but backup your changed one for case that it would be needed later)
3) If not working, try to use /boot/initrd.img-2.6.22-14-generic from another (K)ubuntu (must be same 32bit as yours) with the same version updated OK (You can ask somebody to send it by mail)

By the way this is very well known error and developers are aware of it for ages :-( The problem often happens when you have small dedicated boot partition and after several updates the backups of kernels fill the partition up and the newest kernel is then not complete. Not my case, I have boot in root partition but the result is the same as well.

---

### Post by j-hon on 2008-01-24
> **PmDematagoda said:**
> Concerning the new error, please post the output of:-
```
sudo fdisk -l
```


```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29157   234203571   83  Linux
/dev/sda2           29158       30394     9936202+   5  Extended
/dev/sda5           29158       30394     9936171   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1cf33b56

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

```


Thats what I got from the fdisk command.  I'm going to try playing with the kernel, and I'll  post back.

---

### Post by j-hon on 2008-01-24
I moved my original kernel (non-.bak) to another directory, and stripped the backup extension off the backup kernel.  When I did this however, I noticed that the backup file type had changed to a cpio type.  

This seemed to have no effect, as I'm still getting the error 17 message upon boot.

Ugh... Everything was working so well until this last update....

---

### Post by PmDematagoda on 2008-01-24
I am sorry, but are you sure that you got this on blkid:-
```
/dev/sdb1: UUID="8a165738-311c-4180-b061-4634da389311" SEC_TYPE="ext2" TYPE="ext3"

```
because the following line implies that it is the Windows partition:-
```
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS
```

---

### Post by j-hon on 2008-01-24
Yes, I did it again and got the same thing. 

However, I realized that I still had my external HD plugged in, and I think it's reading that.  

After unplugging the external HD, I get this:
```
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="49f1242d-06ae-4d77-8534-320c218aa58c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="a7a80ba1-c69a-4224-892e-ab1adc5ca041" TYPE="swap" 
ubuntu@ubuntu:~$ 

```

---

### Post by PmDematagoda on 2008-01-24
It seems strange that your external HDD is causing that blkid confusion. Did you try booting Ubuntu with your external HDD removed?

---

### Post by j-hon on 2008-01-24
Yes, I tried booting without the HD installed, still getting the error 17.  Though now I wonder if my Menu.lst right the first time?  How can I check and confirm that?


EDIT****

I changed my Menu.lst to reflect what I got from blkid (regarding the UUID) and now I'm back to a Kernel panic.  Though this time it just tells me that the kernel won't sync, and that it's attempting to kill Init.
I tried swapping my (formally the .bak kernel) kernel for the one off the Ubuntu 64 desktop live cd, but I'm still getting the same error.  Strangely enough, upon renaming/copying kernel from the cd, the icon changes from a blank page looking icon, to one of an open box from the archive manager.  I don't know if this is normal or not, as I can't open/read the file.

So as it stands at the moment, my menu.lst UUID matches my blkid UUID's, I'm directing grub to hd0(0), and I'm using the kernel from the live cd.  I'm still receiving a Kernel sync error upon boot.

---

### Post by j-hon on 2008-01-25
Bump

---

### Post by j-hon on 2008-01-29
Bump again.

Anyone have any Ideas?

---

