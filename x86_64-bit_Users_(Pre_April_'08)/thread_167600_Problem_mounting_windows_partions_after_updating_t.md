---
title: "Problem mounting windows partions after updating to vanilla kernel 2.6.16.11"
date: 2006-04-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by searden on 2006-04-28
Hi, after updating the kernel to the latest version (2.6.16.11) i can no longer access the windows partions. Fstab reports the partion (/dev/sda7/) is already mounted at /media/windows/ but disks manager reports the device is inaccessible and won't let me browse the contents of the drive.](*,) Also the drive was formatted in ubuntu as a vfat partion so i could read and write to this in ubuntu and windows.

Can anyone help me out? i'm fairly new to this! :mrgreen:

---

### Post by yager on 2006-04-28
The standard request for this kind of help is for you to list the contents of the /etc/fstab file.  It may not be setup correctly after the update and needs a minor tweak.

---

### Post by searden on 2006-04-29
Hi, sorry here's my /etc/fstab/ conf file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults        0       0
/dev/sda5       /media/sda5     ntfs    defaults        0       0
/dev/sda6       /media/sda6     ntfs    defaults        0       0
/dev/sda7       /media/sda7     vfat    umask=000       0       0
/dev/hdc5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,auto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,auto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,auto  0       0

Also, do i have to edit the mtab file as well? 

Thanks for the help.

---

### Post by yager on 2006-04-29
[QUOTE=searden]/dev/sda7       /media/sda7     vfat    umask=000       0       0
[/QUOTE]

This entry shows that sda7 is mounted under the /media/sda7 folder.  Check to see if this is accessible and has the correct information available.  

If you want to change the folder it mounts to, change the /media/sda7 to the name of an existing folder where you want to mount it to.  Verify that the folder exists first and has the proper read. write, execute permissions set otherwise you will not be able to mount and use the drive as planned.

Check this link for more professional help.
[https://wiki.ubuntu.com/MountingWindowsPartitions?highlight=%28mount%29](https://wiki.ubuntu.com/MountingWindowsPartitions?highlight=%28mount%29)

I do not believe that you will need to touch the mtab file.

---

