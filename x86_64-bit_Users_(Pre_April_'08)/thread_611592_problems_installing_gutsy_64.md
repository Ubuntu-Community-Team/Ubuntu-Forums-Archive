---
title: "problems installing gutsy 64"
date: 2007-11-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by svtfmook on 2007-11-13
i'm trying to install gutsy amd64.  my setup is:
amd opteron 165
asus a8n32 sli deluxe motherboard
2GB DDR500

now for my drives i have 3 250GB SATA drives
SDA - windows
SDB - where i'm trying to install gutsy 64
SDC - my feisty install

my problem is that during installation, the install fails saying that it cannot write to the hard drive and that the drive is bad.  however, i know that the drive is fine and it writes the file system to the drive.  what i think it is, is that when you see where it's installing the bootloader, it's saying hd0.  now i've tried sdb, scsi2, hd1, hd0, hd2, and none work.

anyone have any guidance as to how i can get this to install.

oh, and this is off the live cd as well.

---

### Post by azbarcea on 2007-11-13
I dont' seem to understand drives versus partition versus hard-disk:

What is that you have? 3 PARTITIONS and 1 HARD DISK (drive is the windows name for a partition)?
1. if u have 1 hard disk (SDA) (/dev/sda) the partions will be SDA1 (/dev/sda1), SDA2 (/dev/sda2) etc
2. if u have several hard-disks then u will have SDA (/dev/sda), SDB (/dev/sdb) etc and each hard disk has one or several partitions.

Now, another issue is: do you have RAID ? That is a "vector of hard-disk" that allows you to see several hard-disks as one. And than, you won't have sevarl hard-disks but u will see is as one. 

this link is the best i found for u. I hope it helps ... 
[http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon](http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon)

---

### Post by svtfmook on 2007-11-13
i have 3 250GB drives
the first one (sda) has a 120GB partition (sda1) on it with windows installed
the second (sdb) is empty
the third (sdc) has a 250GB partition(sdc2 ext3 root, sdc3 swap) with feisty installed on it.

i do not have a raid setup.

---

### Post by azbarcea on 2007-11-13
> 
my problem is that during installation, the install fails saying that it cannot write to the hard drive and that the drive is bad. however, i know that the drive is fine and it writes the file system to the drive. what i think it is, is that when you see where it's installing the bootloader, it's saying hd0.


1. u forgot about sdc1 ... ?!? maybe that one is the partition u want to install the bootloader (GRUB i guess) on

hd0 is the first hard-disk (u call it drive) ... for u is sda
therefore u must install grub on hd2 (means third hard-disk, sdc)
[http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon](http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon) .. pic11.jpg



after u reboot, the BIOS must try to boot from the third hard-disk also!
but when u get there, if u can't handle ... ask!

---

### Post by svtfmook on 2007-11-13
sdc1 was a partition that was an empty file system left over from my feisty install.  i upgraded and moved to sdc2, then resized sdc2, so sdc1 no longer exists.

right now, i have BIOS set to boot from the 2nd disk (hd1), so if i put grub on hd2 (sdc), then it wouldn't boot correct.

---

### Post by dabl on 2007-11-13
I would recommend using the Alternate Install CD -- at the end of the installation procedure it lets you tell it where you want Grub installed.

Also, before you start, I would use GParted and partition that 250GB drive as follows:

6GB -- (the future "/")
0.5GB -- (the future "swap")
the rest of it -- (the future "/home")

Go ahead and format them ext3 or reiserfs with GParted, and you won't have to format them while installing.  Then when you are installing with Alternate Install, just set the mount points as shown, and it should go down with no issues.

:)

---

### Post by svtfmook on 2007-11-14
i was able to get it installed and running using the alternate cd.

wow, much faster than 32bit feisty.

---

