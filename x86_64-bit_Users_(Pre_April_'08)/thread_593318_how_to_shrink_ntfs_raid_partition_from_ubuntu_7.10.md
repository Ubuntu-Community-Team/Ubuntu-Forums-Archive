---
title: "how to shrink ntfs *raid* partition from ubuntu 7.10 live cd"
date: 2007-10-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by SimonHF on 2007-10-27
I have an ASUS P5B Deluxe motherboard with hardware raid controller on board. There are four 400GB drives. Two are striped (800GB) and two are mirrored (400GB). Both are formatted with NTFS. The 800GB partition boots XP. I have booted ubuntu 7.10 and need to shrink the 800GB partition and create a bootable partition to install ubuntu 7.10. I'm confused as to what to mount and which commands to use to get the job done. Here's some info:

ubuntu@ubuntu:~$ more /proc/partitions
major minor  #blocks  name

   8     0  390711384 sda
   8     1  781401568 sda1
   8    16  390711384 sdb
   8    32  390711384 sdc
   8    33  390700768 sdc1
   8    48  390711384 sdd
   8    49  390700768 sdd1
   8    64   16121855 sde
   8    65   16121824 sde1
   7     0     661012 loop0

So I'm guessing that ubuntu 7.10 actually sees both the four physical drives (sda, sdb, sdc, & sdd?) and the 3 logical partitions; the one stripped partition (sda1?) and the mirrored partition as two partitions (sdc1 & sdd1?).

So which commands to mount sda1, shrink it, and create a new bootable partition?

---

### Post by dcstar on 2007-10-27
> **SimonHF said:**
> I have an ASUS P5B Deluxe motherboard with hardware raid controller on board. There are four 400GB drives. Two are striped (800GB) and two are mirrored (400GB). Both are formatted with NTFS. The 800GB partition boots XP. I have booted ubuntu 7.10 and need to shrink the 800GB partition and create a bootable partition to install ubuntu 7.10. I'm confused as to what to mount and which commands to use to get the job done. Here's some info:

ubuntu@ubuntu:~$ more /proc/partitions
major minor  #blocks  name

   8     0  390711384 sda
   8     1  781401568 sda1
   8    16  390711384 sdb
   8    32  390711384 sdc
   8    33  390700768 sdc1
   8    48  390711384 sdd
   8    49  390700768 sdd1
   8    64   16121855 sde
   8    65   16121824 sde1
   7     0     661012 loop0

So I'm guessing that ubuntu 7.10 actually sees both the four physical drives (sda, sdb, sdc, & sdd?) and the 3 logical partitions; the one stripped partition (sda1?) and the mirrored partition as two partitions (sdc1 & sdd1?).

So which commands to mount sda1, shrink it, and create a new bootable partition?

**System-Administration-Partition Manager** should allow you to access and work on all detected partitions.

The hardware RAID should be irrelevant, as it seems sda1 is your 8G partition as detected by Ubuntu.

---

### Post by SimonHF on 2007-10-27
Sorry, I forgot to say that the GUI gparted application doesn't appear to recognize the drive configuration. When I start it then it shows only one greyed-out 400GB drive and claims that it is unformatted (because gparted doesn't work with NTFS?). This is why I resorted to the command line in the first place.

---

### Post by SimonHF on 2007-10-28
So I tried running gparted again and had a closer look at all the options etc. It seems that it does list the 4 physial drives. But it only lists them as 4 partitions whereas on the command line (see above) there are 7 partitions listed. It seems that the 2 400GB drives with XP which form a stripped 800GB bootable drive are not recognized as NTFS or bootable by gparted. Whereas the other 2 400GB drives --- with XP which form a single mirrored 400GB drive -- are individually recognized as being formatted with NTFS. So how to get gparted to recognize the logical raid partitions?

---

### Post by SimonHF on 2007-10-29
I discovered that somebody in the ubuntu German forum has a very similar problem (but also not solution):
[http://www.ubuntu-forum.de/thread.php?postid=158195#post158195](http://www.ubuntu-forum.de/thread.php?postid=158195#post158195)

He also has the Intel ICH8R raid controller. Is this a general problem?

---

### Post by SimonHF on 2007-10-29
Anyway... the solution to the problem seems to be to load the 'dmraid' package as detailed in this German (sorry) blog:
[http://blog.thehobbit.de/2007/09/26/intel-matrix-storage-support-oder-ich8r-mit-ubuntu-704-live-cd/](http://blog.thehobbit.de/2007/09/26/intel-matrix-storage-support-oder-ich8r-mit-ubuntu-704-live-cd/)

---

### Post by garretwp on 2007-10-29
dmraid is a new version of software raid for linux. It allows you to use a software/raid controller that are built into a lot of the new boards. The raid controller on your motherboard is not a true hardware raid controller. You still need software to setup and run the raid. Dmraid should allow you to see the raid devices that were created and formated with ntfs.

- Garrett

---

