---
title: "Dual Boot upgrade from 32 to 64"
date: 2008-01-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by tbzep on 2008-01-05
I'm currently dual booting 32bit gutsy 7.10 with Vista.  I'd like to give 64bit a shot (AMD 64 X2 5200+).  Before I get into it, I'd like to know what I'm looking for.  Will the live CD only show me the ubuntu partition?  I don't want to wipe out the windows partitions accidently and have to reinstall everything.

---

### Post by ~LoKe on 2008-01-05
The LiveCD will show you all partitions, but it should be fairly obvious which one is which (as opposed to the partitioner on the windows cd, ugh).  Look for the filesystem formatted as "ext3", that should be your ubuntu partition.  Your Windows partition will be formatted as "NTFS".

---

### Post by Sukarn on 2008-01-05
> **~LoKe said:**
> The LiveCD will show you all partitions, but it should be fairly obvious which one is which (as opposed to the partitioner on the windows cd, ugh).  Look for the filesystem formatted as "ext3", that should be your ubuntu partition.  Your Windows partition will be formatted as "NTFS".

Just a small addition, windows partitions could be either NTFS or FAT32

---

### Post by tbzep on 2008-01-05
Thanks, I'm up and running 64 now and updating. 

For others who may ask, you will need to skip the "guided" partitioning and go manual.  There you can delete your old partition and create a new one.  For some reason, there were several gigs of unused space, from the first dual boot install.  I was able to add it to the new partition so the only unusable hard disk space is what Vista has wasted. ;)

---

