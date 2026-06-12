---
title: "Can WinXp-32 and Kubuntu Hardy 8.04 64-bit  share a RAID0 drive?"
date: 2008-05-10
forum: x86 64-bit Users
---

### Post by rwillia2001 on 2008-05-10
Hi,

I am building a new audio/video workstation. It will dual boot XP pro-32bit and kubuntu Hardy 8.04/KDE4 64-bit. The OSs will dual boot from a single system drive (no RAID here!). 

I would like to include in the system a temp/scratch RAID0 virtual disk for the doubled read/write performance. This will be for working with "disposable" very large HiDef video files before projects are backed up somewhere else. There will be no critical data going on the RAID0 drive.

I will be using an Asus P5E mobo with the ICH9R controller.

WinXP 32 and 64 install fine using the Intel ICH9R controller and properly recognise an array defined in the mobo BIOS. My previous experience with feisty 64 bit and RAID, (with the dmraid fakeRAID driver) was that it could not recognise an array as a single drive. 32 bit dmraid DID work for me under 32 bit feisty. 

Does anybody know if this 64-bit dmraid problem has been resolved, allowing me to safely use the fast RAID0 array with both OSs? Alternatively, is there a way to disable mounting the RAID0 array when kubuntu boots? In other words could I make it a Windows only RAID0 array? 

Many thanks in advance for any help,

RMW

---

### Post by fjgaude on 2008-05-10
I don't know of anyone using 64-bit Hardy and dmraid... can't say what it is like.

Why should Ubuntu show the raid0 at bootup... it will likely mount the two drives as independent units. You wish for them to not show at all?

---

### Post by rwillia2001 on 2008-05-10
Thanks for the update on 64-bit dmraid. 

Yes, if Hardy 64 bit is completely blind to the RAID0 array, it will only have to deal with the windows fakeRAID driver, and hopefully be way more stable. Without correctly installed functioning dmraid  Hardy will indeed see it as 2 separate drives; this could mess up the RAID array from the point of view of windows (so then triggering needless rebuilds). 

Is there an easy way to have Hardy never ever mount the 2 drives in the RAID0 array? 

Thanks again,

Roy

---

