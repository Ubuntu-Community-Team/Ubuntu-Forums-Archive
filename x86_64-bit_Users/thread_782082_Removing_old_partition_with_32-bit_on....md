---
title: "Removing old partition with 32-bit on..."
date: 2008-05-04
forum: x86 64-bit Users
---

### Post by Martyn12 on 2008-05-04
Hello guys and gals,

I recently upgraded some of my hardware and decided to try the 64-bit version of Ubuntu. At the time it seemed a good idea to make it a dual boot system in order to revert to the (original and working) 32-bit system if things went t**s-up with the 64-bit version. 

Anyway, the 64-bit version is working fine and dandy, so before you lose all interest in this missive I would value your opinions on the best way to remove the old 32-bit version (with some bits in my home directory that I can backup easily) and reclaim the disk space for the 64-bit version. 

Thanks for your thoughts people,


Martyn.

PS - Currently I have the 32-bit directories mounted through the 64-bit version so that I can access my work on those home directories. Problem is, it is far from an elegant solution.

---

### Post by Nubsauce on 2008-05-04
What I've done in the past is just copy the data that I need to the partition I want to use and remove the old partition and move the free space to the partition I'm wanting to use full time.

I've done this in the past without much trouble and have never experience data loss.  However, I do this from live CDs and don't mount either partition at all.

That being said, I'm not sure if this is the way you want to go about doing it or if you're worried about losing data.  I keep important stuff backed up on a hard drive that never gets touched except for storing backups.

---

### Post by Kilz on 2008-05-05
> **Martyn12 said:**
> Hello guys and gals,

I recently upgraded some of my hardware and decided to try the 64-bit version of Ubuntu. At the time it seemed a good idea to make it a dual boot system in order to revert to the (original and working) 32-bit system if things went t**s-up with the 64-bit version. 

Anyway, the 64-bit version is working fine and dandy, so before you lose all interest in this missive I would value your opinions on the best way to remove the old 32-bit version (with some bits in my home directory that I can backup easily) and reclaim the disk space for the 64-bit version. 

Thanks for your thoughts people,


Martyn.

PS - Currently I have the 32-bit directories mounted through the 64-bit version so that I can access my work on those home directories. Problem is, it is far from an elegant solution.

Just copy over the files first. Then I recommend using [a partitioning C]("http://gparted.sourceforge.net/livecd.php")D to remove the old install. This is because you can have problems if you mess with mounted partitions. With the partitioning cd, none of the partitions on the hard disk are mounted. The CD should also let you resize the partition you use now.
Alternately you could leave the partitions as they are now and just delete everything but your data files. That way you have a separate partition you can mount in any version you install without moving files around. use ```
gksudo nautilus
``` to launch nautilus in admin mode and delete away.

---

### Post by Martyn12 on 2008-05-05
OK fellas, thanks for your thoughts. 

I do want to maintain the data so will make up-to-date backups then do as suggested with the partitioning CD. 

Thanks again - all the best. 


Martyn.

---

