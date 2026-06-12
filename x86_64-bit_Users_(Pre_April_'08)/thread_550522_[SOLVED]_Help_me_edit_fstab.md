---
title: "[SOLVED] Help me edit fstab"
date: 2007-09-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-09-14
I want to see what effect the noatime will have on my boot drive** (sda1) **with ubuntu 7.04 installed.  Below is my fstab but I don't know exactly where to insert the parameter.

Would some kind person give me a nudge in the right direction please?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2ecb5f72-d2ab-423f-9be2-37a7ed7b88fa /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=eeff1d26-f3c5-4734-9322-46b4cfe0d2ab none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0

# NTFS Data Drives
/dev/sdb1   /media/sdb1   ntfs-3g  defaults,locale=en_US.utf8    0    0
/dev/sdc1   /media/sdc1   ntfs-3g  defaults,locale=en_US.utf8    0    0
/dev/sdd1   /media/sdd1   ntfs-3g  defaults,locale=en_US.utf8    0    0
## End of Automatix mounted partitions

---

### Post by John.Michael.Kane on 2007-09-14
> **crjackson said:**
> I want to see what effect the noatime will have on my boot drive** (sda1) **with ubuntu 7.04 installed.  Below is my fstab but I don't know exactly where to insert the parameter.

Would some kind person give me a nudge in the right direction please?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2ecb5f72-d2ab-423f-9be2-37a7ed7b88fa /               ext3    defaults,errors=remount-ro **,noatime** 0       1
# /dev/sda5
UUID=eeff1d26-f3c5-4734-9322-46b4cfe0d2ab none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0

# NTFS Data Drives
/dev/sdb1   /media/sdb1   ntfs-3g  defaults,locale=en_US.utf8    0    0
/dev/sdc1   /media/sdc1   ntfs-3g  defaults,locale=en_US.utf8    0    0
/dev/sdd1   /media/sdd1   ntfs-3g  defaults,locale=en_US.utf8    0    0
## End of Automatix mounted partitions

I edited your post to show where it should go. before rebooting make sure you have backed up any data.

After rebooting run the command below, and you should see noatime listed
```
cat /proc/mounts
```

---

### Post by crjackson on 2007-09-14
This is what the command reports - I assume it all took effect since my apps. launch and close MUCH faster now.  Especially Firefox and Open Office word processor.

Thanks for your help...

charles@MSI-K8N-Neo4-SLI-Platinum:~$ cat /proc/mounts
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw 0 0
/dev/disk/by-uuid/2ecb5f72-d2ab-423f-9be2-37a7ed7b88fa / ext3 rw,data=ordered 0 0
/dev/disk/by-uuid/2ecb5f72-d2ab-423f-9be2-37a7ed7b88fa /dev/.static/dev ext3 rw,data=ordered 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
tmpfs /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw 0 0
usbfs /dev/bus/usb/.usbfs usbfs rw 0 0
udev /proc/bus/usb tmpfs rw 0 0
usbfs /proc/bus/usb/.usbfs usbfs rw 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
/dev/sdb1 /media/sdb1 fuseblk rw,nosuid,nodev,noatime,user_id=0,group_id=0,allow_other 0 0
/dev/sdc1 /media/sdc1 fuseblk rw,nosuid,nodev,noatime,user_id=0,group_id=0,allow_other 0 0
/dev/sdd1 /media/sdd1 fuseblk rw,nosuid,nodev,noatime,user_id=0,group_id=0,allow_other 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
charles@MSI-K8N-Neo4-SLI-Platinum:~$

---

### Post by John.Michael.Kane on 2007-09-14
> **crjackson said:**
> This is what the command reports - I assume it all took effect since my apps. launch and close MUCH faster now.  Especially Firefox and Open Office word processor.

Thanks for your help...

charles@MSI-K8N-Neo4-SLI-Platinum:~$ cat /proc/mounts
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw 0 0
/dev/disk/by-uuid/2ecb5f72-d2ab-423f-9be2-37a7ed7b88fa / ext3 rw,data=ordered 0 0
/dev/disk/by-uuid/2ecb5f72-d2ab-423f-9be2-37a7ed7b88fa /dev/.static/dev ext3 rw,data=ordered 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
tmpfs /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw 0 0
usbfs /dev/bus/usb/.usbfs usbfs rw 0 0
udev /proc/bus/usb tmpfs rw 0 0
usbfs /proc/bus/usb/.usbfs usbfs rw 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
/dev/sdb1 /media/sdb1 fuseblk rw,nosuid,nodev,noatime,user_id=0,group_id=0,allow_other 0 0
/dev/sdc1 /media/sdc1 fuseblk rw,nosuid,nodev,noatime,user_id=0,group_id=0,allow_other 0 0
/dev/sdd1 /media/sdd1 fuseblk rw,nosuid,nodev,noatime,user_id=0,group_id=0,allow_other 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
charles@MSI-K8N-Neo4-SLI-Platinum:~$

Looks golden. Your fstab is making use of noatime.

---

### Post by crjackson on 2007-09-14
> **SD-Plissken said:**
> Looks golden. Your fstab is making use of noatime.

Thanks for your quick help...

---

### Post by crjackson on 2007-09-15
Found some great UUID tweaks [here]("http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml") 

Posting it here because it was hard to find, and now I can refer back to my subscribed post for future reference.

---

### Post by Linicks on 2007-09-24
After doing a quick search here to see how to set noatime with grub/fstab (I am a lilo guy ;-) ) as my new laptop was polling hard drive, there is a typo that needs clearing up in case somebody doesn't know [why it doesn't work]:

> 
# /dev/sda1
UUID=2ecb5f72-d2ab-423f-9be2-37a7ed7b88fa / ext3 defaults,errors=remount-ro [COLOR="Red"]noatime[/COLOR] 0 1

should be (e.g.):


```
# /dev/sda1
UUID=2ecb5f72-d2ab-423f-9be2-37a7ed7b88fa / ext3 defaults,errors=remount-ro[COLOR="Red"][SIZE="5"],[/SIZE][/COLOR][COLOR="Red"]noatime[/COLOR] 0 1

```

Nick

---

### Post by crjackson on 2007-09-24
> **Linicks said:**
> After doing a quick search here to see how to set noatime with grub/fstab (I am a lilo guy ;-) ) as my new laptop was polling hard drive, there is a typo that needs clearing up in case somebody doesn't know [why it doesn't work]:



should be (e.g.):


```
# /dev/sda1
UUID=2ecb5f72-d2ab-423f-9be2-37a7ed7b88fa / ext3 defaults,errors=remount-ro[COLOR="Red"][SIZE="5"],[/SIZE][/COLOR][COLOR="Red"]noatime[/COLOR] 0 1

```

Nick

Thanks for the tip Nick.  I'm not sure the comma is mandatory, howeve I have since updated my fstab to make other changes and I DID include the comma.

---

### Post by crjackson on 2007-09-25
Nick, as you can see it's being fully recognized.  Thank you.

[B]charles@MSI-K8N-Neo4-SLI-Platinum:~$ cat /proc/mounts
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw 0 0
/dev/disk/by-uuid/2ecb5f72-d2ab-423f-9be2-37a7ed7b88fa / ext3 rw,noatime,data=writeback 0 0
/dev/disk/by-uuid/2ecb5f72-d2ab-423f-9be2-37a7ed7b88fa /dev/.static/dev ext3 rw,data=writeback 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
tmpfs /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw 0 0
usbfs /dev/bus/usb/.usbfs usbfs rw 0 0
udev /proc/bus/usb tmpfs rw 0 0
usbfs /proc/bus/usb/.usbfs usbfs rw 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
/dev/sdb1 /media/sdb1 fuseblk rw,nosuid,nodev,noatime,user_id=0,group_id=0,allow_other 0 0
/dev/sdc1 /media/sdc1 fuseblk rw,nosuid,nodev,noatime,user_id=0,group_id=0,allow_other 0 0
/dev/sdd1 /media/sdd1 fuseblk rw,nosuid,nodev,noatime,user_id=0,group_id=0,allow_other 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
charles@MSI-K8N-Neo4-SLI-Platinum:~$ [/B]

---

### Post by Linicks on 2007-09-25
It's good now.  From man fstab:

> The fourth field, (fs_mntops), describes the mount options associated with the filesystem.

       It is formatted as a comma separated list of options. ...

Before, it was only your removable media that was mounted noatime - this is usual, as you don't want to mark CD/DVD files when read e.g.  Now you can see mount / is noatime too.

Nick

[COLOR="Red"]EDIT:[/COLOR]  Actually, this thread should be moved to a more relevant forum, I think, as it has nothing to do with 64bit OS, but rather system administration/hardware.

---

### Post by dabl on 2007-09-25
@crjackson, I noticed you lost the "errors=remount-ro" option, in the course of your adventure.

I followed your link to the tweaks and tried those tips on my Gutsy system, and upon reboot it was seriously hosed up -- couldn't start the xserver and couldn't edit with nano either, because of the "read only" filesystem. Happily I have 2 other OS's installed, with which to save myself from ... err, **myself**.  :)

The "errors=remount-ro" option is gone from my Gutsy system too.

Anyway, I was wondering what you learned from your experiment?

Thanks!

---

### Post by Linicks on 2007-09-25
The "errors=remount-ro" option just does that - if you have a bad disk at boot, the last thing you need is to mount it read/write (rw) and really hose the thing if you need to recover data.

I don't know what you done, but just adding 'noatime' shouldn't hurt a fly - I guess you changed a few options from the other link supplied?

My advice:  Leave HD tweaking alone... you can get burnt fingers very easily.

Nick

---

### Post by crjackson on 2007-09-25
> **dabl said:**
> @crjackson, I noticed you lost the "errors=remount-ro" option, in the course of your adventure.

I followed your link to the tweaks and tried those tips on my Gutsy system, and upon reboot it was seriously hosed up -- couldn't start the xserver and couldn't edit with nano either, because of the "read only" filesystem. Happily I have 2 other OS's installed, with which to save myself from ... err, **myself**.  :)

The "errors=remount-ro" option is gone from my Gutsy system too.

Anyway, I was wondering what you learned from your experiment?

Thanks!

I have tweaked the drives on 3 of my systems.  They perform much faster and I've had no problems at all.  I'm using both SATA systems and IDE systems.  No issues at all...

---

### Post by crjackson on 2007-09-25
> **Linicks said:**
> The "errors=remount-ro" option just does that - if you have a bad disk at boot, the last thing you need is to mount it read/write (rw) and really hose the thing if you need to recover data.

I don't know what you done, but just adding 'noatime' shouldn't hurt a fly - I guess you changed a few options from the other link supplied?

My advice:  Leave HD tweaking alone... you can get burnt fingers very easily.

Nick

While I agree with Nick's advice about leaving the system alone, for me it's a learning venture.  I never worry at all about breaking my system.  I do full regular drive image backups, and i alway backup just before I make ANY changes.  If something goes wrong, it takes me less than 3 minutes to restore a working image.

The tweaks have given me a file system on par with NTFS performance, but at the cost of disaster recovery safeguards built into the file system.  Since I use a different method of disaster recovery, I opt for performance.

NICK - Do you have any idea why the remount-ro is lost?  Is something out of place or does in get turned off by the other settings?  Your thoughts?

---

### Post by Linicks on 2007-09-26
> **crjackson said:**
> 
NICK - Do you have any idea why the remount-ro is lost?  Is something out of place or does in get turned off by the other settings?  Your thoughts?

Nope - nothing should auto-update /etc/fstab, I guess.  I bet you removed it yourself when added the other options.

Nick

---

### Post by crjackson on 2007-09-26
**_Here's the fstab:_**

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2ecb5f72-d2ab-423f-9be2-37a7ed7b88fa /               ext3    defaults,errors=remount-ro,noatime,data=writeback 0       1
# /dev/sda5
UUID=eeff1d26-f3c5-4734-9322-46b4cfe0d2ab none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0

# Generated by Automatix
/dev/sdb1   /media/sdb1   ntfs-3g  defaults,locale=en_US.utf8    0    0
/dev/sdc1   /media/sdc1   ntfs-3g  defaults,locale=en_US.utf8    0    0
/dev/sdd1   /media/sdd1   ntfs-3g  defaults,locale=en_US.utf8    0    0
## End of Automatix mounted partitions
```
[B][U]
Here's the menu.lst[/U][/B]

```
 menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=2ecb5f72-d2ab-423f-9be2-37a7ed7b88fa ro

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
# defoptions=quiet splash rootflags=data=writeback vga=791

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
# altoptions=(recovery mode) single rootflags=data=writeback

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2ecb5f72-d2ab-423f-9be2-37a7ed7b88fa ro quiet splash rootflags=data=writeback vga=791
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2ecb5f72-d2ab-423f-9be2-37a7ed7b88fa ro single rootflags=data=writeback
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=2ecb5f72-d2ab-423f-9be2-37a7ed7b88fa ro quiet splash rootflags=data=writeback vga=791
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=2ecb5f72-d2ab-423f-9be2-37a7ed7b88fa ro single rootflags=data=writeback
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

**_Do you seen anything that should be changed?_**

---

### Post by Linicks on 2007-09-26
Ha har!  A gotcha here.

Using 'cat /proc/mounts' will not show it - if you think about it, you are not mounted ro as you have no disk errors!

But using 'mount' will show it, as that shows the raw options of the mount command as per /etc/fstab.

So, just look at output from 'mount' command - I think you will find all is in order.

```
nick@palantir:~$ mount
/dev/sda6 on / type ext3 (rw,noatime,errors=remount-ro)
```

If you do get disk error, then after reboot on bad disk I expect 'cat /proc/mount' to show that option ([remount] ro) also (only?).

Nick

---

### Post by crjackson on 2007-09-26
> **Linicks said:**
> Ha har!  A gotcha here.

Using 'cat /proc/mounts' will not show it - if you think about it, you are not mounted ro as you have no disk errors!

But using 'mount' will show it, as that shows the raw options of the mount command as per /etc/fstab.

So, just look at output from 'mount' command - I think you will find all is in order.

```
nick@palantir:~$ mount
/dev/sda6 on / type ext3 (rw,noatime,errors=remount-ro)
```

If you do get disk error, then after reboot on bad disk I expect 'cat /proc/mount' to show that option ([remount] ro) also (only?).

Nick

Got it, that makes perfect sense.  I noticed you have your options inside of (xxxx,xxx,xxx,xxx).  is there some significance to using the parins?

---

### Post by dabl on 2007-09-26
> **Linicks said:**
> Ha har!  A gotcha here.

Using 'cat /proc/mounts' will not show it - if you think about it, you are not mounted ro as you have no disk errors!



Excellent catch!

On mine, the Super User got rid of that ro option -- it caused all kind of trouble when his USB thumb drive happened not to be in the connector (as fstab thought it should be).   :)

---

### Post by Linicks on 2007-09-26
> **crjackson said:**
> I noticed you have your options inside of (xxxx,xxx,xxx,xxx).  is there some significance to using the parins?

Noooo.  That is output from 'mount' command [that adds the '(  )' ].

My fstab:

```
# /dev/sda1
UUID=f2bbc557-23c0-4afd-bf8b-d0e5d0957956 /               ext3    defaults,errors=remount-ro,noatime 0       1
```

So what you have done is all ok.


THIS thread needs moving to somewhere more relevant please mods :-)

Nick

---

