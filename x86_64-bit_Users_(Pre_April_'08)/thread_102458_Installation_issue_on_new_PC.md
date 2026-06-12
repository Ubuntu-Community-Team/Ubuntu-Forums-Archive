---
title: "Installation issue on new PC"
date: 2005-12-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by andrewsawyer on 2005-12-12
Hiya,

I've had Breezy running with no problems in 32bit on two laptops and a desktop.  Today, I assembled a 64bit machine, and I have tried to install the 64Bit Ubuntu on it.  The system installs fine (I asked it to erase the entire disk), however when it ejects the cd and reboots, I get the following message, and then the systems hangs:

```
NVIDIA Boot Agent 201.0462
Copyright (C) 2001-2004 NVIDIA Corporation
Copyright (C) 1997-2000 Intel Corporation
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting NVIDIA Boot Agent
```

This message appears directly after the Verifying DMI Pool Data.... and Boot from CD/DVD messages (just before the GRUB should load).

Can someone please help me find a cure for this?  The specifics of my pc are below:

CPU: AMD Athlon 3800+ 64bit Dual Core
Motherboard: Gigabyte GA-K8N-Pro-SLI
Graphics Card: 6600GT Series (SLI)
Ram: 2Gb
HDD: 250Gb SATA2

If it helps, the LiveCD ran without issue.  Also, when the partition section came up, I chose:

Erase entire disk: SCSI2 (0,0,0) (sda) - 250.1 GB ATA WDC WD2500J

Rather than

Erase entire disk and use LVM: SCSI2 (0,0,0) (sda) - 250.1 GB ATA

Edit: Just tried the second of these two partition options, but still having the same problem.  For what it's worth, I'm currently using it to write this (using the LiveCD and a wireless connection), so there is no problem with the PC.  I have also checked the disk using the Disk utility as well as fdisk, and I can access it fine.

Any help really would be very much appreciated.  I've been looking forward to getting this up and running for a while now!

Andy

FIXED: Had to disable the Raid controller from the Bios.  All seems to be working now.  Hopefully this might help someone else out in the future :-)

---

