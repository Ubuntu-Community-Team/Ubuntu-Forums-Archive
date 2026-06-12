---
title: "ubuntu and vista64"
date: 2009-03-05
forum: x86 64-bit Users
---

### Post by victor7 on 2009-03-05
Have disk for ubuntu 8.10.  Want to install it in vista64 system.  Intel QX6850 on Asus P45 P5Q-E; visiontek HD 4870, 4mb, 2 400gb hard drives; 600w ps.  Trying to install it on Microsoft Virtual PC 2007.  I've tried install directly, test cd, install in safe mode, etc.  can't get there.  Am i missing something or is my system part of my problem?

---

### Post by marcelkoopman on 2009-03-06
Why install it virtually? Why not dual-boot?

---

### Post by Vince4Amy on 2009-03-06
Use VirtualBox

[http://www.virtualbox.org/](http://www.virtualbox.org/)

Microsoft Virtual PC does not support Linux Guests very good and they usually don't work well on there. You won't be able to get things like mouse pointer integration either.

---

### Post by victor7 on 2009-03-07
I'd be happy to dual boot, when I know how.  I'm suffering from input overload, though.  I have Fedore Linux 2and Linux, For Dummies (both published 2004) with their program disks.  I have NTFS partitions, but don't have a disk to repartition with.

I also have a new 8.10 disk from ODisk.com, along with 5 software library disks.  I've played with Ubuntu a little, and liked it ok, so prefer it,  but am open.  Can you direct, advise me as to where to get best install directions? I've been doing a lot of reading, as I indicated, so specific non-thinking directions would be appreciated.

---

### Post by sumit.kalra999 on 2009-03-07
Hi,
You should install ubuntu inside windows without using VirtualBox or Virtual PC.
To install linux inside windows:
1. Start your windows
2. Run Ubuntu CD
3. From menu option, select "install inside windows"
4. And let it happen
5. Your computer automatically restarts, select ubuntu to boot
6. And get it install successfully......

---

### Post by victor7 on 2009-03-09
OK! I had to reformat and reload xp pro and then install ubuntu, though.  First time thrugh it got hung up somewhere and corrupted my xp pro a little.  I could probably have gotten around it, but had nothing important there anyway.  Thanks.  I was eally tired of Virtual PC 2007.

Now, on to Samba, I guess.:D

---

### Post by itendo on 2009-03-20
was the corruption an overwrite problem in the partition? or did you not create a partition?

---

### Post by 3Miro on 2009-03-20
I cannot imagine Microsoft supporting in Virtual PC anything, but their own OS (i.e. other version of windows). Also, the Linux reference from 2004 would be grossly outdated, some general things would still hold (it would be fine if you are trying to learn how to use the console and/or scripting), otherwise it is outdated.

To run Windows and Linux together:
Option 1: Install Virtual box (it is free, just google it). Then you can run Linux under Windows or Windows under Linux, install one and run the other.

Option 2: If you have Windows already install, put the Ubuntu CD in and you can install Ubuntu in a folder under Windows (supposedly you can also remove it easily from within Windows). The disadvantage would be that Linux would run on the windows file system and thus be little slower then usual)

Option 3: Dual-boot, under Windows make two partitions, one about the size of your ram (or if you have <1GB you can make it bigger) and one at least 10 - 15GB. Then boot from the Ubuntu CD, say that you want to install and when asked about partitions, select Custom/Manual. Then select the small partition and make it swap and the other one make it ex3 and mount point /. (You can use the CD to partition the HD, I have done it myself several times, however, if you are more familiar with windows use the windows partitioner).

---

### Post by victor7 on 2009-03-30
Been away.  I installed a new 80gb hd and then installed xp pro;  then ubuntu as suggested.  I split the memory 40/40 and it works fine.  I can research with ubuntu and play games and do a couple other things with xp.  

Thansk again, all.

---

