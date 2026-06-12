---
title: "Hardware RAID on SunFire X2200"
date: 2007-01-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by lizbaner on 2007-01-02
Hello,
I can't configure properly disk mirroring based on hardware RAID in SunFire X2200 M2 machine. Even if BIOS and RAID controllers report good configuration of both disks (500MB SATA) mirrored into one array, the installer of Ubuntu sees still two separate disks.
Can anyone help me?
Thanks in advance,
-- 
Lucas

---

### Post by akkornel on 2007-03-20
Hello!  I'm currently looking into the purchase of a SunFire X2200, so this topic definitely interests me.  I wanted to ask, which version of Ubuntu were you thinking of using?  Also, when you bought the server, did you just get the two built-in drives, or did you also purchase an add-on RAID card?

Anyway, I'm not sure if this is correct, but here's what I've found so far:  It appears that the X2200 M2 includes NVIDIA NVRAID.  I don't know if it can be disabled, or if you have to use it.  This type of RAID, where alot of work is done by the CPU, is called "fakeraid" by many; in order to take advantage of it, you have to use the dmraid package, which will recognize the RAID set and make it appear in the /dev/mapper directory (like LVM partitions do).

For more information on running Ubuntu using dmraid, see the following:
* [http://htglimited.com/2007/02/24/ubuntu-on-sun-fire-x2200](http://htglimited.com/2007/02/24/ubuntu-on-sun-fire-x2200)
* [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

NOTE: On page 6 of the "Sun Fire X2200 M2 Server Operating System Installation Guide" (December 2006), there is the warning "The onboard NVIDIA NVRAID only supports the Windows OS for a true hardware RAID."  Maybe that means that only Sun-supported thing to do is to use software RAID (md), completely deactivating the hardware RAID.

So, the question is:  Is it possible to bypass the hardware RAID (nvraid) and just use md, or do you have to use NVIDIA's nvraid and dmraid

---

