---
title: "amd64 - GRUB freeze on TEXT install"
date: 2006-06-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by TJInc. on 2006-06-16
Hi all,

Here is some background information.

1. no luck using live cd version 32bit or 64bit on a amd64x2 (AM2) with RAID-0 setup in bios. System would hang prior to actual hard drive install. Ran a memory test with no problems.
NOTE: system did no behave any differently without RAID.

Tried Alternative amd64 CD. Used TEXT based install and system will always FREEZE at 50% when installer is seting up GRUB. System is setup for RAID-0 using the debian installer, whilst setting up partitions as noted in other postings.

Tried EXPERT mode and install still freezes at 50% with GRUB setup. System is also setup for RAID-0 at this point.

Any thoughts on this matter. I think it is something to do with the boot partition, but no sure. In expert mode, i know one can pick to use LILO instead of GRUB. Does anyone have any experience with this, as it becoming very frustrating.

I quite sure it's something to do with GRUB not identifying the place to install the boot loader, because when setting up RAID there is no where to indicate which of the joined array partitions are bootable. 

Hope this makes sense.

Regards

---

### Post by wilborm on 2006-10-06
I have the same problem. Ubuntu 6.06 AMD64 version ran OK as a LIVE CD on my custom-built AMD64x2, set up with Windows XP and Freespire Linux in separate partitions. Trying to install Ubuntu in the Freespire partition I received an error message at the end of the installation about an error in the Windows XP partition that needed to be fixed. Installation halted. On reboot, system stopped with a message GRUB error 15.
Had to reinstall Freespire to correct what seems to be a boot manager problem.

Windows XP is 32-bit. If the boot manager is located on the Windows partition, maybe the 64-bit Ubuntu version has trouble accessing it?

---

