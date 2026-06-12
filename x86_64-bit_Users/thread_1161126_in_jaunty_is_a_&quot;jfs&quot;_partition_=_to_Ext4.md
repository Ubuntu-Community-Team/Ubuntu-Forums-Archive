---
title: "in jaunty is a &quot;jfs&quot; partition = to Ext4"
date: 2009-05-16
forum: x86 64-bit Users
---

### Post by ken78724 on 2009-05-16
In a Jaunty upgrade from 64 bit 8.10 intrepid, how does one gain JFS/Ext4 advantages, i.e., speedier HD? Clarifying on a 750 gib HD partitioned 4 times, I have the following results from applications > accessories > terminal when I type blkid in terminal, it says /dev/sda1 is Ext3 but no
partition says Ext4 is mentioned:

/dev/sda1: UUID="c3d97030-c966-4676-b2e9-2ad5c108876f" TYPE="ext3"
/dev/loop0: TYPE="squashfs"
/dev/sda2: UUID="09961f1c-be60-462f-af06-c470fda332c8" TYPE="swap"
/dev/sda3: UUID="86b1a8d8-bfe1-49cd-95d3-b7a16f936a80" TYPE="reiserfs"
/dev/sda5: TYPE="swap" UUID="0109bf53-e029-4eaf-88b5-8ca49a573538"

So I went for a clarification, I entered "sudo blkid" in terminal and my password.... and got the following:
k78724@Kproductions:~$ sudo blkid
[sudo] password for k78724:
/dev/sda1: UUID="c3d97030-c966-4676-b2e9-2ad5c108876f" TYPE="ext3"
/dev/sda3: UUID="592b9750-fb3d-4bc7-aec1-ebf11d615975" SEC_TYPE="ext2"
TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="0109bf53-e029-4eaf-88b5-8ca49a573538"
/dev/sda4: UUID="767c4efa-c577-44ac-8451-d445f987b53c" TYPE="jfs"

The last output says nothing about Ext4, but it confirms the TYPE="jfs" for /dev/sda4 

From the output, am I running in the jfs, Ext4, Ext 2 or Ext3 partition?

Advise me! Please anyone who understands the output, tell me which partition am I using and if not in jfs or Ext4, can I gain the speedier advantages without a new install in other than the swap partition?

Advice sought.  :)

Kenneth Koym

---

### Post by whoop on 2009-05-17
I'm not sure of what you are asking but jfs != ext4. jfs is a filesystem developed by ibm.

I have written a tutorial on how to convert existing ext2 and ext3 partitions to ext4:
[http://ubuntuforums.org/showthread.php?t=1118295](http://ubuntuforums.org/showthread.php?t=1118295)

Hope this answers your questions...

---

### Post by Yellow Pasque on 2009-05-17
I personally wouldn't try to convert from ext3 just for speed/performance, and if I did, I'd be sure to have everything backed up.

How did you get a JFS partition? Are you running a server here or connected to a network?

> From the output, am I running in the jfs, Ext4, Ext 2 or Ext3 partition? It's hard to tell without looking at /etc/fstab and/or mount output.

Also, if you have jfs and reiserfs partitions, make sure you have the "jfsutils" and "reiserfsprogs" packages installed so Ubuntu can fsck those file systems if necessary.

---

### Post by pixel :-) on 2009-05-17
note that apart sda1 all uuid have changed, even sda3 was claimed as reisers becomes ext3, sda2 disapears, and sda4 appears as jfs

You are networked somehow or what? The above sais that you changed all your disks exept sda1 that is ext3.

And just trust us, don't go for ext4

> Problems can arise if the system crashes before the actual write occurs. In this situation, users of ext3 have come to expect that the disk will hold either the old version or the new version of the file following the crash. However, the ext4 code in the Linux kernel version 2.6.28 will often clear the contents of the file before the crash, but never write the new version, thus losing the contents of the file entirely.

---

### Post by Arup on 2009-05-18
I have been on ext4 since day one of Jaunty install and have never faced any issues, I get the benefits of better speeds specially when transferring files of over four gb size. I do have UPS back up so my PC wont' be shut down dirty thereby leading to data loss. ext4 will be standard soon, the new Fedora 11 will offer it as standard default so I am sure all these so called issues have been taken into consideration before making this move.

---

