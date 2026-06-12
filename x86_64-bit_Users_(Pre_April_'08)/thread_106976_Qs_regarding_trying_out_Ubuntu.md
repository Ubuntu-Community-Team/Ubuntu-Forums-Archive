---
title: "Qs regarding trying out Ubuntu"
date: 2005-12-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by 3rdalbum on 2005-12-21
Hi. I'm thinking of downloading Ubuntu PPC - the Live CD. (I've ordered a set from ShipIt but they'll take another 3 weeks at least to get here, plus I'd rather check that it works before backing up my entire hard drive and repartitioning it).

Okay, so here are some little questions that would be really cool to get answered:

1. I'm running OS 9.1. Is there any way that the Live CD can stuff things up? (e.g. corrupt data on the hard disk, purge the PRAM, fiddle with the firmware).

2. I don't have a CD burner on my iMac, but I do on my 7500. The 7500 is running the Carbon version of Toast, i.e. the interface looks like an OS X application. Will it successfully burn the ISO disc?

3. My iMac's CD-ROM drive is playing up... if I can't get it to read a burnt disc, can I boot from a network disk? (a long shot, I know... the iMac is the Revision D; slotloading 333MHz)

4. Previous threads have mentioned that you need lots of RAM to use the Live CD. I only have 128 megs. Will this be enough to run the thing? I don't care about performance at this time.

5. Does Ubuntu read HFS+ disks? If so, could I specify my hard disk as a place to store a swap file? If not, could I possibly redirect the swap file to a USB Flash drive or SD card? (I realise it'll be mega slow).

6. My HD is partitioned in two: A 1.5 gig partition with System Folder and apps, and a 4.5 gig documents partition. If I decided to install Ubuntu perminantly, and reformat my documents partition to UNIX to hold Ubuntu, could the Mac OS still access this partition?

I appreciate any help you can provide. Thanks.

---

### Post by 23meg on 2005-12-21
1) No.

2) Yes.

3) Most likely no, depending on your hardware's support for network booting.

4) Yes.

---

### Post by muchmusic on 2005-12-21
[QUOTE=3rdalbum]5. Does Ubuntu read HFS+ disks? If so, could I specify my hard disk as a place to store a swap file? If not, could I possibly redirect the swap file to a USB Flash drive or SD card? (I realise it'll be mega slow)[/QUOTE]

Ubuntu can read them, but it takes a bit of work. You can't use the hfs+ partition as a swap though. AFAIK you can't use any USB devices for swap either out of the box.

{QUOTE=3rdalbum]6. My HD is partitioned in two: A 1.5 gig partition with System Folder and apps, and a 4.5 gig documents partition. If I decided to install Ubuntu perminantly, and reformat my documents partition to UNIX to hold Ubuntu, could the Mac OS still access this partition?[/QUOTE]

Mac OS 9 cannot access that partition. The closest you could get to what you want would be, I suppose three partitions, one for Mac OS one for Docs and one for Ubuntu but this would likely be a little painful to work with until you get used to it - in the interests of keeping things easy you may want to have two copies of documents until you get used to it instead.

---

### Post by muchmusic on 2005-12-21
[QUOTE=3rdalbum]5. Does Ubuntu read HFS+ disks? If so, could I specify my hard disk as a place to store a swap file? If not, could I possibly redirect the swap file to a USB Flash drive or SD card? (I realise it'll be mega slow)[/QUOTE]

Ubuntu can read them, but it takes a bit of work. You can't use the hfs+ partition as a swap though. AFAIK you can't use any USB devices for swap either out of the box.

[QUOTE=3rdalbum]6. My HD is partitioned in two: A 1.5 gig partition with System Folder and apps, and a 4.5 gig documents partition. If I decided to install Ubuntu perminantly, and reformat my documents partition to UNIX to hold Ubuntu, could the Mac OS still access this partition?[/QUOTE]

Mac OS 9 cannot access that partition. The closest you could get to what you want would be, I suppose three partitions, one for Mac OS one for Docs and one for Ubuntu but this would likely be a little painful to work with until you get used to it - in the interests of keeping things easy you may want to have two copies of documents until you get used to it instead.

---

### Post by 3rdalbum on 2005-12-24
Thanks for the help, I really appreciate it. Looks like I'll be joining the Ubuntu community on Boxing Day :-)

---

