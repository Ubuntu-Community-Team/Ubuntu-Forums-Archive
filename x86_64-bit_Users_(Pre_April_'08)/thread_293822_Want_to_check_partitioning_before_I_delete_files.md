---
title: "Want to check partitioning before I delete files"
date: 2006-11-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by rhomp2002 on 2006-11-05
While upgrading to Edgy I messed up a couple of times and now I have multiple versions out there.  I would like to get rid of the excess.  I did a -l and a fstab which I am attaching.  From reading this I am assuming that I need to keep ID 83 and get rid of ID 82?  Just wanted to check before I screwed it up again.

Thanks.

dick@breezydapper:~$ sudo fdisk -l
Password:

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4491    36073926    c  W95 FAT32 (LBA)
/dev/sda2           10565       14921    34997602+   f  W95 Ext'd (LBA)
/dev/sda3            6548        8979    19535040   83  Linux
/dev/sda4            8980       10564    12731512+  83  Linux
/dev/sda5           14456       14921     3743113+  83  Linux
/dev/sda6           10712       10892     1453819+  82  Linux swap / Solaris
/dev/sda7           10637       10711      602374+  82  Linux swap / Solaris
/dev/sda8           13179       14196     8177053+  83  Linux
/dev/sda9           14197       14244      385528+  82  Linux swap / Solaris
/dev/sda10          10893       12120     9863878+  83  Linux
/dev/sda11          13081       13178      787153+  82  Linux swap / Solaris
/dev/sda12          10565       10636      578277   82  Linux swap / Solaris
/dev/sda13          14245       14441     1582371   82  Linux swap / Solaris
/dev/sda14          14442       14455      112423+  82  Linux swap / Solaris

Partition table entries are not in disk order
dick@breezydapper:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda10 -- converted during upgrade to edgy
UUID=936a68ea-70b3-4084-89f1-a258994c0da0 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda13 -- converted during upgrade to edgy
UUID=f7a4da97-bc8e-44aa-ad7e-2c52f6f48d8b none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0 


Any help would be appreciated.  :confused: :mrgreen: :???:

---

### Post by RAOF on 2006-11-06
Wow, that's a lot of partitions.  Looks like you should be able to get rid of /dev/sda[3-9,11,12,14].

Then you're probably going to want to fire up a live CD and reclaim all that lost space.

---

### Post by rhomp2002 on 2006-11-06
That is pretty much what I thought.  I may need to keep the ones that are not tagged Linux-Solaris (wherever those came from!!).  The Linux-solaris are definitely not being used in my opinion.  

I am not completely sure of what that fstab is telling me about the files.  Are they saying that only the ones with mounting points listed are being used?  That is why I am wanting to get a second or third or fourth etc opinion before I screw it all up.   I can get rid of certain ones that I know for sure are not in use but not sure about the others.  

I have a lot of experience on computers but it has almost all been on mainframes except for my browsing now.  I never even got a PC until after I retired so when it comes to some of this stuff it is all Greek to me.  Now if you want to know about COBOL or VSAM or OS/MVS, I'm your man.  This stuff is something I am trying to learn about now and it does not come easy when you are in your upper 60's.

---

### Post by RAOF on 2006-11-06
> **rhomp2002 said:**
> ...
I am not completely sure of what that fstab is telling me about the files.  Are they saying that only the ones with mounting points listed are being used?
...

That's exactly what it's saying.  It's saying that only /dev/sda10 and /dev/sda13 are being mounted anywhere, so everything else (except for the Windows partitions) are just lying idle.

---

### Post by rhomp2002 on 2006-11-06
OK, I got rid of the partitions above 10 since I was not using them.  Now when I try to get rid of the partitions below sda10 it says I have to get rid of the ones higher in the list first.  Since sda10 (in the extended part) is the main file I want, how can I copy it so the sda number is lower and I can then get rid of the other partitions I don't need.   I would also like to merge a couple of them and get the home partition out of the extended file.  
](*,)

---

### Post by RAOF on 2006-11-06
> **rhomp2002 said:**
> OK, I got rid of the partitions above 10 since I was not using them.  Now when I try to get rid of the partitions below sda10 it says I have to get rid of the ones higher in the list first.  Since sda10 (in the extended part) is the main file I want, how can I copy it so the sda number is lower and I can then get rid of the other partitions I don't need.   I would also like to merge a couple of them and get the home partition out of the extended file.  
](*,)

What partition editor are you using?  You should be able to use a LiveCD (such as the Ubuntu live cd) and gparted to remove the other partitions, move the partition you want around, and then resize it to fill the avaliable space.

---

### Post by rhomp2002 on 2006-11-07
I have been using GPARTED from the System Admin icon.  I haven't run the Live CD Gparted since I loaded Breezy the last time.  I m afraid I will do something wrong but if I use the Live CD rather than the Install CD I should be OK.  I will have to try that one.  What I want to do is copy the sda10 into the unallocated area right after the Windows section.  Then I can get rid of all the crap and have a pretty clean file setup.  With the Live CD I guess I can do the unmount and the copy and then get rid of the crap and be home free - unless I really screw it up.  Then I will be back installing Breezy and then updating to Dapper and then updating to Edgy.  Don't want to do that and lose all the stuff I have out there now.:confused: :confused: :-k

---

