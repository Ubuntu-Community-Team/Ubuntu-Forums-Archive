---
title: "How can I change primere hdd"
date: 2008-08-30
forum: x86 64-bit Users
---

### Post by gretarsson on 2008-08-30
Hi 
I have 2 hdd one 500Gb (empty) and one 250Gb (ubuntu start up disk) but that one is nearly full and I like to move every thing from that disk into 500Gb hdd and used as primer disk (start up disk) can I do that in simple way or do I have to install new ubuntu into it and copy me home folder into it?

---

### Post by TatuSalin on 2008-08-31
For changing the boot order you must modify boot loader options. There is always MBR on the disk, where OS installation is located. 

One way is to copy whole disk to another and then modify startup options.

Create a shell script that will copy disk(250GB) content to disk(500GB)

and run it.

Please remember always check as a root the names of the disks.
#fdisk -l shows devices that are found.

Create with vi editor a shell script and name it something.sh
run it as a root user.

You must also make it executable for root user.
#chmod 700 [script_name].sh

*********************************************************************
#!/bin/sh

dd if=/dev/hda1 of=/dev/hda2&

exit 0 
*********************************************************************

Remember that dd command is very dangerous if you don't know how it works.

Make always backup before start doing something.

There is also need to modify bootloader options so that your machine starts from this another disk.

Please read more instruction for example from the page below: 
[http://www.yolinux.com/TUTORIALS/LinuxTutorialInitProcess.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialInitProcess.html)
:guitar:

---

### Post by Chibone on 2008-09-01
You can also clone it with [Gparted]("http://gparted.sourceforge.net/") by downloading the ISO or running it on the Ubuntu live cd.  Just copy the whole disk over from your primary to the empty one and then grow the partitions on your new primary as needed.

Just wanted to remind you like the person above me to be careful; make a backup and test if your new primary is working before getting rid of the old one.

---

