---
title: "Hardware RAID mounting problem"
date: 2007-09-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Roguespider13 on 2007-09-18
I recently built a new comp to be a file server for me and since I've had no problems with Ubuntu in the past I decided to keep with it. Although I did run into trouble on the install (had to turn set 'noapic') I got past that and continued on. But now I cannot use my RAID array. Here's what I have:

CPU: AMD Athlon 64 x2 4800+ 
MOBO: Gigabyte GA-M59SLI-S5
SATA HDDs: 160 GB (OS Drive), 500GB x8 (RAID Array)
RAID card: 3ware 9650SE-8LPML
OS: Ubuntu 7.04

Planned Array: 2.5 TB (Ubuntu file server) + 500 GB (for other data)

1. I installed Ubuntu just on a drive separate from the RAID ('OS drive'), though in the install I decided not to deal with the array (I wanted to get Ubuntu installed first).
2. After install Ubuntu and getting 'ubuntu-desktop' for gnome, I attempted to partition my RAID array using GParted and cfdisk. Neither seemed to support a partition > 2TB. 
3. I used Parted and was able to partition it correctly. Formated as XFS. Mounted it and was able to add folders.
4. After a restart, the RAID array, which had been mounted as /dev/sda1 changed its designation to /dev/sdb1. I edited fstab to compensate but the drive would not mount. After restarted drives changed again but wouldn't mount. I used UUID numbers instead but it would not mount (**NOTE: error was 'can't find superblock'**).
5. Repartition the drives and was not able to fix problem. 
6. I eventually decided to recreate the array and reinstall Ubuntu (setting up the RAID from the installer). Even after doing this it did not work. 
7. Reformatted the Array as ext3 (thinking the problem was with XFS) but even though Parted shows the partition as 2500 GB and ext3 filesystem, Ubuntu still only sees about 300-500 GB of space.

I appreciate any help on this. I've tried updating Ubuntu but with no help.

---

### Post by tszanon on 2007-09-19
I know it would be a waste of hardware, but have you tried to use software-RAID to see if it works?

Edit: nevermind, even if it works, I don't think that would be an acceptable solution for you.

---

### Post by Roguespider13 on 2007-09-19
Yeah, I spent over $500 on the RAID card so I wouldn't want to just put it aside. Also I have a friend who has the PCI-X version of this card (I have the PCI-E) and he doesn't have any problems.

---

### Post by psusi on 2007-09-19
Could you be more specific about the nature of the failure?  What command did you try to use to mount it?  What command did you use to format it?  What's your fstab look like?  What was the error message you got?  What is the output of dmesg after the error?

---

### Post by Roguespider13 on 2007-09-20
psusi,

I formated the drive using mkfs.xfs if I remember correctly the actual command was 'mkfs.xfs -L warehouse /dev/sdb1'

I then edited the fstab as so '/dev/sdb1  /warehouse  xfs  defaults  0   1'

I mount it with 'sudo mount -a'

The error I get is 'can't find superblock'

I'm not familar with dmesg so I don't know its output.

Now just last night, I repartitioned the drive with parted, created the partitions again, formatted it and then edited the fstab (this time to include the UUID but when I tried to mount it, it said the device didn't exist so I changed fstab again to use '/dev/sdb1' and then was able to mount the drive. It saw the 2.5TB partition. Once I restarted the comp, it gave me the 'can't find superblock' error again, tried changing to UUID and it also gave the superblock error.

---

### Post by Jouke74 on 2007-09-20
Maybe stating something a bit obvious, but does it work with a smaller RAID? E.g. 1 TB?

The file system maximum capacity is limited by the block size that you give. You may need to repartition / format using large file system a.k.a large blocks. 

From wiki:
Size limits

Ext3 has a relatively small maximum size for both individual files and the entire filesystem. These limits are dependent on the block size of the filesystem; the following chart summarizes the limits[5]:
Block size 	Max file size 	Max filesystem size
1KiB 	16GiB 	2TiB
2KiB 	256GiB 	8TiB
4KiB 	2TiB 	16TiB
8KiB 	16TiB 	32TiB

The 8KiB block size is only available on architectures which allow 8 KiB pages (such as alpha).

Still I would suggest to set-up a double raid and divide the diskload (I guess)? Also Raids can fail.

---

### Post by psusi on 2007-09-20
mkfs will not create a broken filesystem, and he said he is using xfs, not ext.  

Please run dmesg and post its output after this error.  Also, don't mount -a, mount /dev/sdb1 instead.  The error you were getting may have been from trying to mount something else.

---

### Post by Roguespider13 on 2007-09-20
psusi, I will try dmesg when I can (not at my computer now), but I did find these two things:

[https://bugs.launchpad.net/ubuntu/+source/parted/+bug/107326](https://bugs.launchpad.net/ubuntu/+source/parted/+bug/107326)
and
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/127125](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/127125)

While the second states the error again and more clearer, it seems like both are having the same problem and if NowakPL  is right in his comment about it (in the first link), it was caused by a gpt sync patch. How might I get a version of gpt without the patch?

---

### Post by Roguespider13 on 2007-09-21
I believe I'd solved the problem. It seems that it was the problem mentioned in the first launchpad link. Ubuntu's parted creates a corrupt gpt label when the partition is > 2 TB. I used a Live CD of GRML and it stated the the label was corrupt. Using it, I created a new label, partitioned the drive, and formated it and everything works.

Thank you for all your help.

---

