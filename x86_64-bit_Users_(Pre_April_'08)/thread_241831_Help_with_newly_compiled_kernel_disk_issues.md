---
title: "Help with newly compiled kernel disk issues"
date: 2006-08-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by quik77 on 2006-08-22
Hi all finally made the switch over to Ubuntu the other day (new system amd x2 etc) and installed 64bit ubuntu, than for somereason after getting nvida drivers and wow on wine and all my drives to work, I decided to compile a fresh kernel

so last night I compiled the 2.6.17.9 ? kerenl everything worked, than the xorg update broke on me and i downgraded, wow works got the lastest nvida drivers via method 2, but..

none of my drives aside from the one with my root partition will mount.

I've tried setting up my fstab tried the gnome disk manager, is there something I need to do when I compiled that kernel? or is there somehtign else I need to do to get permission to mount them (aside from using sudo/gksudo?)

my fstab is below](*,) 

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


/dev/hdb1  /home/robert/hdb1  vfat  nls=utf8,umask=0000 0 0
/dev/hda1  /home/robert/hda1  ntfs  nls=utf8,umask=0222 0 0
/dev/hdb2  /home/robert/hdb2  ext3 defaults,errors=remount-ro 0       1
/dev/hda2  /home/robert/hda2  vfat  nls=utf8,umask=0000 0 0


---

### Post by RAOF on 2006-08-23
For us to help, you'll need to post the actual errors when you try to mount those partitions.  When you run "sudo mount *foo*", you get some errors?  And it'll probably say "check dmesg logs for more details".  Post both, and we can see what's happening.

---

### Post by quik77 on 2006-08-23
ok will do as soon as I get home from work

---

