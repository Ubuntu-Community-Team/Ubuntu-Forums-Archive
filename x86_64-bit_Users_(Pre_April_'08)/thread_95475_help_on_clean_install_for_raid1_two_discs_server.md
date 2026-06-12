---
title: "help on clean install for raid1 two discs server"
date: 2005-11-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by ryedawg on 2005-11-26
hi everyone, i just joined this forum as i have bought a new linux server and it contains two amd64 hard drives. I am installing the ubuntu breezy badger from the install disk and would like to run plesk 6.5 over top after im done. I want to mirror the two discs for back up purposes so i want to use raid1.

heres my pickle...when i run the install cd it asks me how i would like to partition my discs before continuing

erase entire disk: IDE1 master (hda) - 80.1 GB SAMSUNG SP0822N
erase entire disk: IDE1 slave (hdb) - 80.1 GB SAMSUNG SP0822N
erase entire disk and use LVM: IDE1 master (hda) - 80.1 GB SAMSUNG 
erase entire disk and use LVM: IDE1 slave (hdb) - 80.1 GB SAMSUNG
use the largest continuous free space
maually edit partition table


im not sure how to choose it....if i use the largest continuous free space it partitions my master only and does raid 1 on it. but the other one is still empty??? 

any helo or guidance would be appreciated..thanx in advance, ryedawg

---

### Post by usacomp2k3 on 2005-12-12
Is there a step-by-step guide for creating a raid1 volume using a fakeraid controller?

---

