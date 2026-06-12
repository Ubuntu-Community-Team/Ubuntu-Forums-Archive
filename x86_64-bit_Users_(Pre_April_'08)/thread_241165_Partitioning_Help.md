---
title: "Partitioning Help"
date: 2006-08-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by covert215 on 2006-08-21
Hi.  I'm trying to create a dual-boot on my eMachines T6524.  It has a 200GB hard drive in 2 partitinos.  182GB or so main partition in NTFS and a 5GB or so as a backup in FAT.  I'm in Ubuntu Live right now and I'm liking it.

I tried to install the OS, but I ended up with some errors in the partitioning.  I tried to reduce the 182GB partition to 40GB.  I then created an extended partition with a 100GB(/home and shared) ext3 logical, 40GB (ubuntu)logical, and a 2GB swap.  I received an error trying to resize the 182GB partition.  How should I go about this?  I was forced to use the extended partition because I would have had more than 4.

---

### Post by Kilz on 2006-08-22
> **covert215 said:**
> Hi.  I'm trying to create a dual-boot on my eMachines T6524.  It has a 200GB hard drive in 2 partitinos.  182GB or so main partition in NTFS and a 5GB or so as a backup in FAT.  I'm in Ubuntu Live right now and I'm liking it.

I tried to install the OS, but I ended up with some errors in the partitioning.  I tried to reduce the 182GB partition to 40GB.  I then created an extended partition with a 100GB(/home and shared) ext3 logical, 40GB (ubuntu)logical, and a 2GB swap.  I received an error trying to resize the 182GB partition.  How should I go about this?  I was forced to use the extended partition because I would have had more than 4.

As a t6524 owner who uses Ubuntu let me say I have always had problems resizing partitions. It must just be the disk. Most of the time when I try I end up corupting the drive and having to wipe it down. 
Other than that you will have few problems with the box, other than the ATI radon x200 most of them have. The proprietary driver is presently giving me fits.

---

### Post by covert215 on 2006-08-22
What was your ultimate solution to the resizing?  Was it wiping it?  That would be the worst-case scenario for me.

Should I start looking for websites that will host backups for you? :cry:

---

### Post by Kilz on 2006-08-22
> **covert215 said:**
> What was your ultimate solution to the resizing?  Was it wiping it?  That would be the worst-case scenario for me.

Should I start looking for websites that will host backups for you? :cry:

Everything I tried just made it worse. The partition would grow it seemed.
I have a feeling you are going to have a hard time backing up 182gig online.

---

### Post by covert215 on 2006-08-22
Only 30.2 GB are in use :)

I have it all defragged to the beginning of the drive.

---

### Post by covert215 on 2006-08-22
help?

---

### Post by covert215 on 2006-08-22
it still wouldn't resize even when I only tried to resize the 1 partition

---

### Post by Lonthong on 2006-08-22
Sorry, content deleted.

---

### Post by VirtuAlex on 2006-08-22
I'm ashamed to suggest this, but try partition magic...

---

### Post by John.Michael.Kane on 2006-08-22
covert215 have you tried the [**[COLOR="Red"]GParted-livecd[/COLOR]**]("http://gparted.sourceforge.net/livecd.php")

Lonthong posting of (Warez) info is against forum policy

---

### Post by covert215 on 2006-08-22
Too late.  I was using GParted.  Someone suggested that I use chkdsk in Windows and then do it.  I did and it got halfway through the partitioning before I received another error.  I click ok and found that my hard drive had been wiped.

---

### Post by John.Michael.Kane on 2006-08-22
covert215 where do you stand now with this issue? 

Are you atleast able to install ubuntu or any other distro for this matter?

---

### Post by covert215 on 2006-08-22
I'm starting from scratch trying to set up a dual boot.

I'm splitting partitions like this:
5GB FAT(recovery...its automatic)
35GB NTFS primary (windows install)
147GB extended
110GB ext3 logical (shared)
35GB ext3 logical (ubuntu)
2GB swap logical

---

### Post by VirtuAlex on 2006-08-22
> **covert215 said:**
> I click ok and found that my hard drive had been wiped.
Sorry about that... then partition first, then install win, and after that install linux

---

