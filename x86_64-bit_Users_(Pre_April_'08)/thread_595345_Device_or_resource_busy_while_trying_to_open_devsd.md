---
title: "Device or resource busy while trying to open /dev/sda1 (EVMS)"
date: 2007-10-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by ednspace on 2007-10-28
Trying to get google earth to stop crashing and taking out X windows I tried the following suggestion from a forum post

sudo apt-get remove evms
sudo update-initramfs -u

after this I did a reboot and the system came up to a black screen only X seemed to be running however stalled.  So I switched to console 1 and decided to undo what I just did, by apt-get install evms
sudo update-initramfs -u

reboot

system dumps to a command shell with, Device or Device or resource busy while trying to open /dev/sda1

after exit or ctrl d the system boots and works fine.  Only other thing I notice as it boots is that it searches the CDROM drive frequently.

I am not sure what I have done, I am even unsure if I truely need EVMS or not.

Possibly fstab is the problem however I am nervous to change it.
fstab says

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/KiWi-root /               ext3    defaults,errors=remount-ro 0       1
#/dev/sda1
UUID=4dd851bc-eec1-45b4-ad4d-fd554e41fa8b /boot           ext3    defaults        0       2
/dev/mapper/KiWi-swap_1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


fsck Log reports:
fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
fsck died with exit status 8


/boot
initrd.img-2.6.20-16-generic  initrd.img-2.6.22-14-generic 
Any help would be greatly appreciated,
ED

---

### Post by ednspace on 2007-10-29
Would seem as though this issue is solved.
  
Commented out the UUID line in fstab and all works now, system boots normally.
Still researching Evolution Volume Manager and its effects.  It seems that /dev/mapper was all ready mounting my root file system and then the UUID line was coming up in fstab and it was trying to mount again.

I promise to be more careful entering commands and pushing enter.
I promise to be more careful entering commands and pushing enter. 
I promise to be more careful entering commands and pushing enter. 
I promise to be more careful entering commands and pushing enter. 
repeat till at 100

Thanks all who took the time to look and think about my question.
ED

---

