---
title: "Sharing /home partition with 32-bit and 64-bit Ubuntu, partition recommendations"
date: 2005-11-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by casfindad on 2005-11-29
I'm planning to build a 3800+ X2 dual core system soon, and I'm interested in installing both 32 and 64-bit versions of Ubuntu on it. (I think this would be "cleaner" and involve less fussing than trying to get chroot working.) I read in another post the recommendation to assign the same partition as /home for both installations. This would certainly simplify file sharing, but my concerns are:

Would sharing the /home partition between the 32 and 64-bit versions result in duplicate configuration files?

Would updates/changes to my configuration files under 32-bit (e.g. firefox bookmarks) be reflected when I run 64-bit and vice versa?

Would any problems arise from assigning the same partition as /home for both versions?

If this scheme is a good idea, I'm assuming that I could do it by manually assigning the /home partition during each installation. During the second installation, my guess would be that I assign /home to the same partition used in the first installation, but do not format in order to save the data from the first installation.

Finally, I'm looking at the following partition scheme for a 250 GB hard drive, your suggestions are appreciated:

12 GB 64-bit Ubuntu / partition
12 GB 32-bit Ubuntu / partition
Approx. 200 GB /home partition
2 GB swap
24 GB free to play with other OSs (MEPIS? Suse? XP if absolutely necessary)

I was planning on using ext3 for all the Linux partitions, NTFS or FAT32 for any Windows partition.

Thanks!

---

### Post by RAOF on 2005-11-29
I'd suggest FAT32 for any XP partition.  Sure, you don't get all the NTFS niceties (like actual file permissions, journalling, etc), but at least you can write to the drive from linux :)

Additionally, I might suggest trying the LVM options during the install.  LVM allows you to easily shrink/extend whatever partitions you create during the install (even on to different hard-drives, if you later add another one).  Next time I reformat, that's definitely what I'll do :)

If you have a shared /home, you will need to do pretty much what you suggested.  There shouldn't be any major problems, and your configuration should be shared between 64 & 32bit versions (which may or may not be a good thing).  The only obvious problem I could think of is users & permissions - you'll need to be careful to ensure that each user has the same userid on each install, because it is the uid number & not the username that is saved in the permission info on the drive.  If you've only got one user, it won't be a problem, and if you add users in the same order on each install it should also work (because uid's are assigned sequentially).

Ext3 is a fine filesystem.  I'm using ReiserFS (version 3, not the new v4), and that works just fine for me.  And I've been pretty hard on it - there've been quite a number of hard-resets it has recovered from perfectly.

---

### Post by n0ah420 on 2005-11-29
I currently have XP_64, Dapper 32, and Breezy 64.  The linux partitions share a single home directory.  I have only one issue which is Firefox on Breezy doesn't play well with Firefox on Dapper.  This is becuase of the Deer Park switch over.  This was easily fixed by using a 32-bit deer park on Breezy 64.  All in all its been great and I have no complaints.  Its nice to have the same settings in each distro.  My 60GB laptop is partioned this way:

XP_64 (NTFS): 8GB
Dapper32 (ext3): 10GB
Breezy64 (ext3): 10GB
Scratch (Fat32): 28GB
Home (ext3): 1.3GB
Swap: 1GB

---

### Post by casfindad on 2006-01-03
Good news: I built my system and successfully installed ubuntu + kubuntu. Yea!

Bad news: I ran into trouble installing both breezy 32-bit and 64-bit and sharing the home directory. I partitioned my drive with LVM (took a little experimentation, but thanks for the suggestion RAOF) pretty much as described above and then installed 64-bit Ubuntu followed by 32-bit Ubuntu, assigning the same partition for /home, without formatting. I did format the /boot partition with the second install, as I figured grub would need to be re-installed with both OSs in place.

After installation, I could choose either kernel during boot-up, and the 32-bit system would run fine. The 64-bit system, however, would not start the gui and defaulted to a command line boot. (Sorry I don't have the exact error messages, this was a week ago.) In a panic (sorry if that's a bad pun), I re-formatted everything and re-installed only the 32-bit system, leaving a partition available for 64-bit if needed.

If anyone has successfully set up a 32-bit and 64-bit dual boot with shared /home, I would very much appreciate step-by-step instructions, at least from the point of installing the second OS. Thanks!

---

