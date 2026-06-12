---
title: "usb stick mounts only within 5 minuts of startup"
date: 2007-11-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by steveyeager on 2007-11-20
I have most everything working, but auto mounting my usb stick.  Strange thing is, if I insert the stick into the usb port within 5 minutes of starting the system, or reinsert the stick within 5 minutes of removing it, and it auto mounts perfectly.  I get an icon on my desktop and it opens a file manager for the drive.
t
But if you let 5 minutes go by after startup or after I remove the stick, it ignores the stick.

I noticed one thing: when it works, the stick on the light flashes when first inserted, quickly goes off, it stays of for a second or so, then comes back on and it auto mounts.  When it does not work, the light comes on when the stick is inserted and says on for several minutes, then goes out - and of course it does not mount and cannot be manually mounted (at least not with the command I have tried).

So, how can I resolve this?

---

### Post by mouseboyx on 2007-11-21
if you know the device identifier remove it from /etc/fstab
i had this similar problem in fiesty, i don't remeber how i fixed it. you need to edit some [COLOR=Red]F[/COLOR]ile [COLOR=Red]S[/COLOR]ystem file.
post the contents of /etc/fstab

---

### Post by steveyeager on 2007-11-21
my /etc/fstab is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=04968e31-05c5-48d3-bea4-c43650e38c33 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=5C27FDCF2176638D /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=62DC6C64DC6C3507 /media/sda3     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=5ef93914-b519-4fd6-93e5-214eeeb222d7 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

When it works, the stick mounts as /media/disk and it is a link to /dev/sdb.

---

### Post by steveyeager on 2007-11-27
Resolved.  I start up with "noapic" and "irqfixup" and usb devices always automount.

---

