---
title: "fsck strange problem"
date: 2009-10-09
forum: x86 64-bit Users
---

### Post by M. Fawzy on 2009-10-09
Hi all, 

this is my first topic here ... but I'm facing a really strange problem .... after installing windows 7 pro on my ubuntu jaunty 64 machine ... I removed the windows XP partition and created a new partition for win7 ... after that when I booted ubuntu wasn't there ... so I had to use super grub disk for win.. and this did the job for me ..... and I used my lovely ubuntu 64 for a while and everything was gr8... but my probleme now is that each time I start ubuntu it asks for the root password to do an FSCK check ... if I press ctrl-D it just restarts to the same screen ! ... I opened ubutu 32 (installed on a smaller hard drive for some testing issues) ... and when I look at my 320 gb hard at g-parted it all appears as unallocated space ! though I still can mount partitions ! and I don't know how to make fsck through my 32-bit ubuntu ! :D 

thnx in advance !

---

### Post by oldos2er on 2009-10-09
If you have an Ubuntu LiveCD, boot from it to run fsck on your unmounted partitions. Or, when you're running Ubuntu, run the command **sudo touch /forcefsck ** to run fsck on next boot up.

---

