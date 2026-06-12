---
title: "GRUB Hard Disk Error"
date: 2007-04-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by jfdill_2 on 2007-04-11
After the latest batch of updates for Dapper LTS, my system comes up with:

GRUB Hard Disk Error

This is on a PowerEdge 1950 with hardware RAID1 PERC5i, 2 SATA disks, has worked fine for at least 6 months.  I can boot into rescue mode on the Dapper LTS amd64 CD and see the disks, everything is there, the disks work fine, I think this is some sort of problem with GRUB, probably the new version of GRUB that was one of the updates.

Anybody else seen this or have any other ideas?

Thanks.

Update:

BIOS 1.1.0 on the 1950 is buggy, downloaded and installed 1.3.7, but that still didn't fix the problem.

Found this page on the GRUB error, obviously is in Stage 1 system is not able to grab Stage 1.5 or 2 from the hard drive.  I'm thinking the update to GRUB "broke" this, will see if I can find the .deb for the old version and revert.

[http://neon.polkaroo.net/~mhoye/blarg/archives/003382.php](http://neon.polkaroo.net/~mhoye/blarg/archives/003382.php)

Update:

Interesting, I tried installing LILO, but it's still giving GRUB Hard Disk Error.  Wonder where the heck GRUB is installed?  Will have to check that lilo.conf more carefully.

---

### Post by Kilz on 2007-04-11
> **jfdill_2 said:**
> After the latest batch of updates for Dapper LTS, my system comes up with:

GRUB Hard Disk Error

This is on a PowerEdge 1950 with hardware RAID1 PERC5i, 2 SATA disks, has worked fine for at least 6 months.  I can boot into rescue mode on the Dapper LTS amd64 CD and see the disks, everything is there, the disks work fine, I think this is some sort of problem with GRUB, probably the new version of GRUB that was one of the updates.

Anybody else seen this or have any other ideas?

Thanks.

Update:

BIOS 1.1.0 on the 1950 is buggy, downloaded and installed 1.3.7, but that still didn't fix the problem.

Found this page on the GRUB error, obviously is in Stage 1 system is not able to grab Stage 1.5 or 2 from the hard drive.  I'm thinking the update to GRUB "broke" this, will see if I can find the .deb for the old version and revert.

[http://neon.polkaroo.net/~mhoye/blarg/archives/003382.php](http://neon.polkaroo.net/~mhoye/blarg/archives/003382.php)

Update:

Interesting, I tried installing LILO, but it's still giving GRUB Hard Disk Error.  Wonder where the heck GRUB is installed?  Will have to check that lilo.conf more carefully.

before you do anything else, if it just saying it cant find the drive? Perhaps it isnt looking in the right place. When the /boot/grub/menu.lst is replaced it makes a backup menu.lst~ you might want to see if the backup works.

---

### Post by jfdill_2 on 2007-04-11
> **Kilz said:**
> before you do anything else, if it just saying it cant find the drive? Perhaps it isnt looking in the right place. When the /boot/grub/menu.lst is replaced it makes a backup menu.lst~ you might want to see if the backup works.

Thanks for the suggestion, but that was the first thing that I tried, I also tried an older backup of menu.lst that I had.  In the end, I got it working correctly with LILO.

---

### Post by mloisg on 2007-04-13
I'm having the "same" problem. Got upgrades yesterday, this morning no boot. Grub comes up with "could not find hard drive". The drive does not show up when typing (hd[TAB]
Which is wierd since bios finds the drive, and the drive can be mounted from the ubuntu install cd. 

Ubuntu 6.10/amd64, Sata drives, worked fine for moths. Have no more details since I'm at work atm.

---

