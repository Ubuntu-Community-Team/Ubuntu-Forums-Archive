---
title: "gutsy boot problem... might fsck"
date: 2008-03-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by solarin_kb on 2008-03-19
Ok I have some serious issue with my Linux partition.  I may have to fsck it (unmounted of course) but I'm not sure if there are other options present.  I am hoping for some good advice on how to recover here.

I am running Ubuntu 7.10 gutsy on an HP dv9000 series notebook.  It's one of those preinstalled vista machines.  I felt I wanted to try ubuntu after using SUSE for so long on my desktop.  I shrunk my vista partition and booted into Live gutsy.  I then partitioned up and found myself on cloud 9 for a few days.

BitTorrent gave me some hassles (bad sector error/failures if I remember correctly) and I decided to restart Ubuntu.  After doing so, I ended up in Error 17 hell from Grub.  So I booted into LiveCD and decided to try my luck at the terminal to see what was wrong.  Here are my findings:

```
root@ubuntu:/# /sbin/fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e045244

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10412    83632704+   7  HPFS/NTFS
/dev/sda2           13505       14593     8747392+   7  HPFS/NTFS
/dev/sda3           10413       10655     1951897+  82  Linux swap / Solaris
/dev/sda4           10656       13504    22884592+  83  Linux

Partition table entries are not in disk order

```

```
root@ubuntu:/# mount /dev/sda4 /ubuntu
mount: you must specify the filesystem type
root@ubuntu:/# mount -t ext3 /dev/sda4 /ubuntu/
mount: wrong fs type, bad option, bad superblock on /dev/sda4,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I can mount the other NTFS partitions just fine.

```
root@ubuntu:/# fsck.ext3 /dev/sda4
e2fsck 1.40.2 (12-Jul-2007)
Couldn't find ext2 superblock, trying backup blocks...
Superblock has an invalid ext3 journal (inode 8).
Clear<y>? no

fsck.ext3: Illegal inode number while checking ext3 journal for /dev/sda4

```

I have spent far too much time tonight researching possible avenues through forums like this one to no avail.  Everyone appears to have slightly different issues so far.  I will research more tomorrow but I am hoping someone may be able to shine some light over here for me.

Thanks.

---

### Post by solarin_kb on 2008-03-19
Something to add:


```
root@ubuntu:/# dumpe2fs /dev/sda4
dumpe2fs 1.40.2 (12-Jul-2007)
dumpe2fs: Bad magic number in super-block while trying to open /dev/sda4
Couldn't find valid filesystem superblock.

```

---

### Post by Herman on 2008-03-21
:) Hello solarin_kb,
Try looking at some of these links and see if they will be of any help to you,
[Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem") - from a Live CD - command line

[                        Running a check for bad blocks on your hard disk]("http://users.bigpond.net.au/hermanzone/p10.htm#bad_blocks_check")

[What to do if you have a bad ext3 superblock]("http://users.bigpond.net.au/hermanzone/p10.htm#superblock_restoration_frombackup")

[How to take a look at your ext3 superblock]("http://users.bigpond.net.au/hermanzone/p10.htm#take_a_look_at_your_ext3_superblock")

Regards, Herman :)

---

### Post by solarin_kb on 2008-03-22
Thanks for the links.  They are quality.  Unfortunately, I did not get a reply for a while so I had to run fsck and it basically cleared it all into lost+found.  So here I am with a newly formatted partition with everything setup how I prefer.  I used dd this time to image the partition. ;)

---

### Post by Herman on 2008-03-22
I'd be buying a new hard disk if that happened to me.

---

### Post by solarin_kb on 2008-03-23
I sincerely do not believe it was a problem with the hard disk.  I was getting some strange errors from bittorrent along with Nautilus (the infamous problem with too many file handles).

---

### Post by Herman on 2008-03-23
Oh, bittorrent, yes, I have read that those type of programs can be hard on file systems. 
Maybe just run your file system checks much more frequently then, your file system is probably doing a lot more work than average, and may just need checking a lot more often to fix problems while they're still small.

Regards, Herman :)

---

