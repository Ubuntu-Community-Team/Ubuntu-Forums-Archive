---
title: "Install dapper on ppc"
date: 2006-05-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by benoitc on 2006-05-14
Hi all,

I'm trying to install dapper on ppc with rthe livecd. When I use the gui to install it doesn't ptopose to me too create the boot partion needed by yaboot. Should I patition the disk on command line ?

---

### Post by BoneKracker on 2006-05-16
<Edit: the short answer is "yes, if you know what you're doing".>
<original response below>

Could you provide more detail?

My experience with the installer's automatic partitioning is that it will not allow you to proceed without a bootable partition.  Are you multibooting with an already installed linux?

Did you use the automatic partitioning, or did you configure the partitions manually?

Could you provide your partition table for your disk/disks?

---

### Post by jdp on 2006-05-16
The last I heard, the LiveCD GUI installer is borked on PPC.  Using the IntallerCD seems to work fine.

---

### Post by BoneKracker on 2006-05-17
I hadn't used the partitioner on the LiveCD before.  I just checked it out on a G4.  I will definitely continue to do it manually.

Other than partitioning, the ubuntu install is about as hard as making toast.  Unfortunately, the graphical partitioner leaves something to be desired.  Personally, I'd be happier with a prettied-up version of what's on the install disks.

---

### Post by BoneKracker on 2006-05-17
If you've already burned the LiveCD (and haven't downloaded/burned the Install CD), it may work to do the partitioning first (from CLI in LiveCD run mac-fdisk) then run the LiveCD installer.   I've got it running now and will post results.

---

