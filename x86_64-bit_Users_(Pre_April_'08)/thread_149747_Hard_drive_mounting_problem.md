---
title: "Hard drive mounting problem"
date: 2006-03-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by AntEater on 2006-03-24
I've just installed Ubuntu (64bit) on a cluster of machines.  I have been trying to mount a secondary hard drive but I am unable to do so.  

# mount /scratch_net/
mount: /dev/hdb1 already mounted or /scratch_net busy

The drive is not in use.  "df" shows nothing for this device.  /etc/mtab does not list the device.  "lsof" shows nothing holding the drive device or mount point.

This is the line from /etc/fstab
/dev/hdb1       /scratch_net    reiserfs defaults        0       2

I've tried reformatting the drive both from the commandline and from the GUI disk management tool.  The disk management tool shows the drive as being "inaccessible" in the status: section.  I've checked the log files and "dmesg" output after attempting to to mount the drive but nothing of interest shows up related to the drive.  I've checked the jumpers on the drive and it is setup properly as a slave on the first IDE channel.  I swapped out this drive with another 300GB drive, partitioned and formatted with the same problems.

This is weird.  Any help in figuring out how to mount this drive would be greatly appreciated.

My system specs:
Ubuntu 5.10 (AMD x86-64)
kernel: 2.6.11-9-amd64-k8-smp
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4600+
RAM: 3GB
Drive: 40gb seagate Barracuda
Drive: 300gb Seagate barracuda

---

### Post by maury on 2006-03-24
Here are some notes that I made while getting my backup drive mounted and working, Hopefully you may find some clues there,

Procedure for auto mounting /dev/hdc1 in ubuntu
1-Using Terminal: sudo nautilus and put in password
2-Create a extdrive folder in the media folder
3-Create a link to the extdrive folder and leave it in the media folder
4-save and exit
5- using terminal: sudo gedit and goto etc/fstab and open it
6- add this line to fstab:  /dev/hdc1    /media/extdrive    ext3    defaults,rw    0 0 
Save and exit.and Reboot.
You should see a "extdrive" icon on the desktop and you should be able to access the drive. 
Note! New fastab is as fillows

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc1       /media/extdrive    ext3    defaults,rw    0 0        
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

------------------------------------------
Note! To get to ROOT in Ubuntu simply goto term.
sudo -s
password:
and your in root. 
---------------------------

---

