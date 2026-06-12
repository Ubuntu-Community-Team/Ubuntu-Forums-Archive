---
title: "Dual boot Ubuntu with 2 hard drives for 32 and 64 bit"
date: 2007-08-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Handssolow on 2007-08-08
Mostly dual boot systems are XP and Ubuntu but I want to get gain experience using 64 bit Ubuntu on a Sata 2 whilst keeping my 32 bit Ubuntu OS relatively untouched on its older IDE drive.

Suggestions please. I assume I'd select the OS with Grub but which hard drive should boot first, have I a choice? Would I be able to transfer files across? Would I have to create a swap partition?

---

### Post by jpkotta on 2007-08-09
> **Handssolow said:**
> I assume I'd select the OS with Grub but which hard drive should boot first, have I a choice?

The hard drive that boots is independent of the drive your system is on.  The only difficulty is that the default configuration will assume that the hard drive you're installing to is the same as the one that gets booted.  You just have to tell grub otherwise.  

I recommend a single /boot partition if possible.  Make it about 200 MB.  That way all of the grub configuration will be in one place and it will be harder to screw it up.  Otherwise, read [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto) or search the forums or Google or ...  This is a common enough question that you will find what you need.

> **Handssolow said:**
> Would I be able to transfer files across?

Yes, file systems are independent of architecture.  A better solution to coping files back and forth is to put /home on its own partition (this is always a good idea anyway) and share it between your systems.

> **Handssolow said:**
> Would I have to create a swap partition?

No, just use the one you have already.  Think of swap as a type of filesystem, then consider the previous question.   In fact, since you have 2 hard drives, make a new swap partition on the new drive and have each system use both swaps.  Linux automatically stripes them (as in RAID 0), so you will get more throughput that way.

If you feel up to it, you can even use your 32-bit installation as a chroot for your 64-bit installation, and work around any 64-bit-related problems that way.

---

