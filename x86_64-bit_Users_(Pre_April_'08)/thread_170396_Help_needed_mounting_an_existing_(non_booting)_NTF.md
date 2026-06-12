---
title: "Help needed mounting an existing (non booting) NTFS RAID (0) in Breezy"
date: 2006-05-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by sjashton on 2006-05-04
I have been searching for a way to read (and hopefully write) to my RAID array that  I use in WindowsXP, if anyone can help i would appreiate it. I have ASUS A8V Deluxe MB which has 2 SATA controllers - Promise and VIA. I have a single 80GB on the Promise which is partitioned into roughly 50/30 (XP boots from the 50, and Ubuntu on the 30) and 2*250GB on the VIA under RAID0 which in my windows setup i use to store media files, i would like these files to be available to my Ubuntu system. When i go into disk manager the partitions on the dual boot disk are as one would expect but the 2 larger disks are listed in the side panel but only one shows a partition although it is inaccesable with an unknown file system. The second one just says there aren't know partitions on the disk. Is there any way of getting Ubuntu to see 2 disks in the same way my windows system does. I get the impression (maybe falsely) it may be possible due to the fact that i am not booting from this array. 

Any help would be gratefully recieved

---

### Post by neouser99 on 2006-05-04
its most likely that the windows raid is a 'fake' raid. did you have to install drivers (f6) during the windows install for the raid to be recognized? if this is the case i was unable to get it to work in a similar situation about a year ago, but things might have changed.

this might help you out, although it is discussing things from scratch, and gentoo related, not ubuntu:

[http://gentoo-wiki.com/HOWTO_Gentoo_Install_on_Bios_(Onboard)_RAID]("http://gentoo-wiki.com/HOWTO_Gentoo_Install_on_Bios_(Onboard)_RAID")

-neo

---

### Post by sjashton on 2006-05-04
I can't remember if i installed the VIA driver when i created the RAID but i guess i must of done as i always followed the instructions in the MB manual and the F6 driver install command is clearly stated. I dunno, maybe i'll have to go for some other (external) storage option i need to have my media backed up anyway.

---

