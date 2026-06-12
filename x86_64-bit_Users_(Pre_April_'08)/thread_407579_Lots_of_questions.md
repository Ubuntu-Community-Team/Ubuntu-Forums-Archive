---
title: "Lots of questions"
date: 2007-04-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Rev.Smokey.Joe on 2007-04-12
Ok, so after some tinkering I finally got Ubuntu to install on my system.
AMD X2 4400
2 gigs RAM
two 250 gig WD SATA drives.
two nVidia 7800gt cards in SLi
a8n sli premium mobo

I downloaded the AMD64 bit install disc.  After messing around with getting the disc to boot, (vesa driver issue that I found the answer here, thanks BTW), I finally got my hard drive partitioned and set-up.  That took some time as well.  But here's the 1st issue, when I told Gparted to part out my drive, I told it to leave 2 partitions unformatted.  These will be used in my windows xp dual boot config.  Gparted decided to put ext2fs on these partitions and I'm afraid of just deleting the partitions and formatting them as NTFS.  Why you may ask, well because when I last did that, I fooked up the partition table and had to completely wipe the disk and start all over.

here's the partitioning layout:
sdb1  -  Windows Page file (3 gigs)  (was meant to be unformatted, but formatted as ext2, via Partition Magic)
sdb2  -  Linux /boot ext2 (512 megs)
sdb3  -  Linux / ext3 (170 gigs)
sdb4  -  Windows back-ups (~60 gigs)  (was meant to be unformatted, but formatted as ext2, via Partition Magic)

When installing Ubuntu I created the partitions in gparted, and told it not to format them, but it did anyway.

Final question, when I boot up the computer, it says that I'm running the *-generic kernel.  Why is that?  shouldn't I be running the AMD64 bit kernel?  Did Ubuntu decide to install a gerneic kernel instead?

Oh, and I'm not new to Linux, just new to Ubuntu.  I had Gentoo installed on this drive before I decided I wanted something a bit easier to manage.  Gentoo is great and all, but man, the upkeep and 3 day install just made me want to go with a simpler distro.  Besides, Gentoo was a great hands on experience to Linux.  It taught me a lot.

---

### Post by dabl on 2007-04-12
The new 64-bit (K)Ubuntu kernels don't identify themselves uniquely as such, they carry the same version number as the 32-bit.  But try to install some (non-packaged) 32-bit app that does a scan for kernel-compatibility, and you'll find out quick that you're on a 64-bit kernel. :)

---

### Post by kuja on 2007-04-12
You should be able to delete those two empty partitions without any problem, be sure to do it with a live cd (so that none of the partitions on the drive willb e mounted while you're doing it). Oh, and do be careful. Oh, and one other thing, if something does go south, there's a lovely program called testdisk which may be able to save the ship :) testdisk can be found in Ubuntu's Universe repository.

The kernel you're using is the AMD64-bit kernel, it's just called generic (because it's for all amd64/em64t processors).

---

### Post by Rev.Smokey.Joe on 2007-04-13
Thanks.  Worked liked a charm.  I was nervous about just deleting those partitions since it corrupted my partition table last time I did it.  But this time it worked wonderfully!

---

