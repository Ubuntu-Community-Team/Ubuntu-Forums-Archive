---
title: "mdadm 100% CPU Usage (constant)"
date: 2008-09-23
forum: x86 64-bit Users
---

### Post by impactdni on 2008-09-23
I have been running mdadm with the following arrays for about 2 years now:
/boot raid1 (2x100mb partitions)
/     raid0 (2x10gb paritions)
/home raid5 (3x490gb partitions)

All the partitions are on WD 500gb drives (nothing special) and the partition tables follow:
/dev/sda1   *           1          12       96358+  fd  Linux raid autodetect
/dev/sda2              13       60801   488287642+   5  Extended
/dev/sda5              13         135      987966   fd  Linux raid autodetect
/dev/sda6             136        1352     9775521   fd  Linux raid autodetect
/dev/sda7            1353       60801   477524061   fd  Linux raid autodetect

Using drives sda, sdc, sdd.
1 -- /boot
5 -- swap (unused/off currently)
6 -- /
7 -- /home


About a month ago I installed extra ram and upgraded to 64bit ubuntu, but upon setting up the arrays and getting everything working, I've noticed mdadm is always maxed at 100% CPU (1 of 4 cores at 100% constantly)...

No obvious errors/messages in dmesg or /var/log/messages.
The only thing I can find that seems out of place is in /var/log/syslog:
Sep 23 21:09:01 x2 mdadm: NewArray event detected on md device /dev/md1
Sep 23 21:09:32 x2 last message repeated 444 times
Sep 23 21:10:33 x2 last message repeated 817 times
Sep 23 21:11:34 x2 last message repeated 858 times
Sep 23 21:12:34 x2 last message repeated 824 times
Sep 23 21:13:34 x2 last message repeated 795 times
Sep 23 21:14:34 x2 last message repeated 770 times
Sep 23 21:15:34 x2 last message repeated 753 times
Sep 23 21:16:34 x2 last message repeated 733 times
Sep 23 21:17:01 x2 last message repeated 325 times

Obviously in rapid succession, but I can't seem to find anything letting me know whats going on there...
/dev/md1 is my planned swap partition, but its unused/unmounted, mdadm --detail doesn't give any information:
root@x2:/home/impact# mdadm --detail /dev/md1
/dev/md1:
        Version : 00.90.03
  Creation Time : Sat Oct  6 12:28:04 2007
     Raid Level : raid0
   Raid Devices : 2
  Total Devices : 3
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sun Oct 28 21:35:36 2007
          State : active, Not Started
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1

     Chunk Size : 64K

           UUID : b9f190e5:42307fbf:51eb6a99:431ffebe
         Events : 0.5

    Number   Major   Minor   RaidDevice State
       0       8        5        0      active sync   /dev/sda5
       1       8       53        1      active sync   /dev/sdd5

       2       8       37        -      spare   /dev/sdc5



Anyone have any suggestions as to where to go on this?

---

