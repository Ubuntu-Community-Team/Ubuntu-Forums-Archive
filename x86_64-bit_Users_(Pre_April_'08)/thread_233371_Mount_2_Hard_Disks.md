---
title: "Mount 2 Hard Disks"
date: 2006-08-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by joeinazyes on 2006-08-10
This is my first post and it is filled with newbie naivete.

I just installed DD 6.06 64-bit version on my system, which contains 2 80GB hard disks. Both disks are fomatted with Ext3.  The OS files are fine and run well on hda.  However, I don't understand why I can't use hdb normally and add folders and files as I do in MS Windows XP.  I don't understand why the 2nd disk (hdb) doesn't mount on boot so that I can access it like I do /home on hda.  hdb contains a blank 74.5GB partition.

Do I have to do some type of command line wizardry just to create folders and write files to a 2nd blank hard disk?

If I am in the wrong forum, I apologize and please direct me.

---

### Post by swamytk on 2006-08-10
1. Launch System->Administration->Gnome Partition Editor 
2. Select /dev/hdb at top right corner of application.
3. Create partition as you want.
4. Mount the partition.

---

### Post by hopstah on 2006-08-10
if you want it to auto mount at boot, copy and paste the contents of your /etc/fstab file

edit: into this thread

---

### Post by mikeescott on 2006-08-10
How would I mount the same drive that has files on it I want to keep?

---

### Post by joeinazyes on 2006-08-10
> **hopstah said:**
> if you want it to auto mount at boot, copy and paste the contents of your /etc/fstab file

edit: into this thread

I've already done what the first respondent suggested, several times and can mount the drive manually that way.  However, I can't add folders and files as I would do normally with an external USB FAT32 HD.  That's what I would like to do with the internal IDE slave drive (hdb) AND have that drive mount automatically on boot.

OK, here's the file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

