---
title: "can't mount my hard drive"
date: 2006-01-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by gurdy on 2006-01-21
Hi! In my lab I'm running Breezy Badger on a dual-867 Mac MHz G4 with an 80 GB drive, and after using Synaptic to update Ubuntu, we couldn't save anything to disk -- we got messages that the hard drive was read-only. We also couldn't mount a CD to burn and we couldn't mount a USB thumb drive to save onto, and Nautilus crashed and then we couldn't open any applications. When we tried to restart the computer (by choosing Log Out), the computer wouldn't shut down all the way, and we had to hold down the power button to turn it off. On restart, the computer said we had to run fsck manually, which I did, and it reported many, many errors (none of which I know much about --which is perhaps part of the problem), all of which I said to fix. Now it won't boot. 

Then I tried booting from a Breezy PPC live CD in rescue mode, and it couldn't mount any of the partitions on the hard drive. 

So I tried booting from a Gentoo PPC live cd, and when I try to mount the Linux partition (which in my case is /dev/hda3) by issuing the command:

mount /dev/hda3 /mnt/gentoo

I get these error messages:

EXT3-fs: journal inode is deleted
mount: wrong fs type, bad option, bad superblock on /dev/hda3, or too many mounted file systems

One of my students had about 2 weeks of work on this drive which she unfortunately did not back up. Any suggestions on:
* how I might go about retrieving the data from the drive, or 
* figuring out if the data is still there in any useful condition, or
* on resources that I could turn to, by which I could quickly learn some strategies for dealing with the situation?

Thanks!

---

### Post by slux on 2006-01-22
I'd start with fscking the partition you're trying to mount before anything else. If that doesn't let you mount it again, things are looking very difficult but you could still use forensics tools such as Autopsy and the Sleuth kit for searching the disk. I'd still be hopeful about a simple fsck being able to fix it enough for accessing.

---

### Post by Ptero-4 on 2006-01-23
Try to mount it as ext2. By the message it seems that the journal is gone and the system would have more luck treating that partition as a unjournalled ext2 one.

---

