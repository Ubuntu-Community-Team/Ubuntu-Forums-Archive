---
title: "Partition table destroyed"
date: 2007-02-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by fugrank on 2007-02-05
So, I recently installed ubuntu for the first time. My graphics card is x800GTO so the installation with the regular cd didn't go so well. The alternative installation worked like a charm, and I soon had 32-bit ubuntu up and running. I was quite impressed with it and decided to try out the 64-bit version. 

Ok, so for hardware/software background, I have one ATA hard drive (disk 0) and two SATA hard drives (disk 1 and 2). 250, 120 and 250 Gb respectively. Disk 0 had bootmagic installed on the first partition (fat 32) and I had 2 or 3 other partitions with just data on the rest of the drive. Disk 1 had four partitions prior to installing ubuntu 64-bit. 1 - windows xp, 2 - windows vista, 3 - 32bit ubuntu, 4 - swap. There are about 32 gb unallocated at the end of this drive. Disk 2 is a single NTFS partition for holding data.

And now, onto the problem. I installed 64-bit ubuntu with the oem alternative install. It went fairly smoothly. I let it add grub loader as I did in the first install.  Boot up does not work without the cd for some reason, so I let it boot with the cd and selected boot from hard disk. I chose normal boot for the 64-bit and quickly remembered I needed to boot into recovery mode, so I hit the reset button. Following this, everything screwed up. Choosing boot from hard disk from the cd menu resulted in a failure to boot from hard disk error.  I took out the cd and it let the computer boot to wherever.  It chose the vista bootscreen. I booted into vista and realized everything from Disk 0 was gone. I don't have much set up for vista so I proceeded to restart and log into XP. Disk manager showed Disk 0 as completely unallocated, and uninitialized.  When I ran some partition recovery software, it found two ext3 partitions of I believe 7 mb. I'm still running some recovery stuff, and crossing my fingers on being able to at least find some stuff.

Any ideas on what caused this? Or any other solutions to rebuilding Disk 0? Also, sorry for being so verbose. Thanks.

EDIT: Oops, I left out some important information.  The distro I was using was 6.10, and I also cannot boot into either ubuntu at this point.

---

### Post by msandersen on 2007-02-05
Did you ask it to do anything to this partition when installing? Even adding a bootloader? In the Launchpad bugzilla [bug #48299]("https://launchpad.net/ubuntu/+source/gparted/+bug/48229") describe a problem with GParted (actually Parted which it relies on) corrupting partition tables in certain circumstances. See the post by Szaka, the author of ntfsresize, and the [link]("http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html#troubleshoot") posted to troubleshoot partition table corruption.

---

### Post by fugrank on 2007-02-05
> **msandersen said:**
> Did you ask it to do anything to this partition when installing? Even adding a bootloader? In the Launchpad bugzilla [bug #48299]("https://launchpad.net/ubuntu/+source/gparted/+bug/48229") describe a problem with GParted (actually Parted which it relies on) corrupting partition tables in certain circumstances. See the post by Szaka, the author of ntfsresize, and the [link]("http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html#troubleshoot") posted to troubleshoot partition table corruption.

I did not touch that partition at all. I think I did try to do a recovery of the 64-bit install with the install disk, but nothing on the corrupted disk.

---

### Post by kuja on 2007-02-06
Well, if your partition is corrupted and needs rescuing, try the program "testdisk", it's in the Universe repository. I think the Knoppix CD includes it (wonderful recovery tool).

---

### Post by darkhorseporter on 2007-02-07
Testdisk seconded here.  I just today repaired a destroyed partition table with it.  Easy if you're careful and read.

---

### Post by fugrank on 2007-02-08
WOW, now I know what to use if this ever happens again (hopefully it doesn't). It blows away all the commercial apps I tested.  Thanks a lot for the tip. I still am interested in where I went wrong in the installation so I can avoid going through this (again).  Is there any way the new vista boot structure could have caused it? Or the interruption of the Ubuntu boot up?

---

