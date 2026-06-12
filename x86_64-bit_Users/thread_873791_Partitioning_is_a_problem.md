---
title: "Partitioning is a problem"
date: 2008-07-29
forum: x86 64-bit Users
---

### Post by skaufman on 2008-07-29
Hi all.  I am bewildered, as I cannot resize the boot disk.  I just started installation of the x64 compatible version of Heron.  I have an XP Pro x64 boot disk, a 3-disk RAID0 data disk, and a backup disk.  I also have 16GB RAM.

I am given the option of using all of one of my disks or choosing the largest available contiguous space.  If I select the latter, I get an error message.  What I cannot do is the normal thing:  resize "C:" and install Ubuntu as a dual-booted OS.

What on earth could be going wrong?!?

---

### Post by skaufman on 2008-07-29
Guys, I posted this issue on the install subforum, but I think it's a 64-bit issue.  I created a live CD, but when I arrive at the place where I wanted to resize the boot drive to allow space for a Ubuntu partition, I only get the options of using the whole drive, using some other whole drive, manual install, or using the first & largest contiguous space (which throws an error if I select it).  I use XP Pro x64, with SATA drives (Dell Precision 690).  Disk 0 has a 47MB EISA Configuration, then 150 GB NTFS, the latter being a boot partition for XP.  Disk 1 is a 700 GB NTFS for backup.  Disk 2 is a RAID0 900 GB NTFS virtual drive.

This is very, very, very strange.  I am NOT given an option to shrink Disk 1.

Any insights would be really appreciates.

Thanks in advance.

---

### Post by wpshooter on 2008-07-29
What is the error message ?

---

### Post by Sef on 2008-07-29
Merged threads.

---

### Post by skaufman on 2008-08-01
I don't know what "merged threads" means, Sef, but I do know what an unhelpful post is.

Actually, wpshooter, it seems that THIS error was mine, as there was no unallocated space on the drives.  I had already formatted them appropriately.

Of course, after much effort, I have still failed to get a bootable Linux system.  But I will express my displeasure elsewhere.

---

### Post by tamoneya on 2008-08-01
merged threads means that you shouldnt make the same post in two separate forums.  Sef helped you out by fixing your mistake.

EDIT: as for this error message issue you said :> If I select the latter, I get an error message.

wpshooter is just trying to help so instead of being sharp with him you could try to listen.

---

### Post by skaufman on 2008-08-01
wpshooter, this will probably be my last post here.  First, thanks for trying to help--nobody else cared to (the preferred personal style here seems almost a parody of the old-time Unix System Administrator).  Second, I erred in thinking that with this option, the installer wanted an available partition, when it really wanted a large unallocated part of a disk.  So, in this sense, the installer's error message was CORRECT:  there was no unallocated space to use.  But third, after spending many hours trying one way then another to get this OS to boot, even going so far as to give it finally a hunk of unallocated disk and giving it carte blanche to choose its own defaults, I still didn't end up with a bootable OS.

tamoneya, I don't think I was sharp with wpshooter originally, but I realize that this was a possible interpretation.

---

