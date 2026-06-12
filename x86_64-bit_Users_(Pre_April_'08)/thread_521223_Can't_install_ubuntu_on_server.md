---
title: "Can't install ubuntu on server"
date: 2007-08-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by splatman on 2007-08-09
I am trying to install Ubuntu on a new server, but I never get into the installer as it stops after selecting install with an error message saying "Soft lockup detected on CPU#5" and if left another one appears saying the same thing but for CPU#0. I have tried using the x64 versions of the Desktop, Alternate and server cds, but all just do the same (well the desktop gets stuck on the splash screen).

Server Specs:

Intel SR2500ALBRP Chassis and Motherboard
2 x Intel E5320 Quad Core (1.86Ghx, 8Mb cache, 1066Mhz) Xeon CPU
4GB (4x 1GB) Kingston 667Mhz DDR2 ECC Fully Buffered CL5 Ram
3 x 250GB Seagate Sata HDD in RAID 5

---

### Post by heimo on 2007-08-09
Just couple ideas how you could further diagnose what part of system is causing it. Try with older version of Ubuntu or Debian. It's probably kernel version and multicore related. Just to make sure, you're installing natively, not using any virtualization? (I've run to this problem in Xen, but not solved it.)

---

### Post by splatman on 2007-08-09
Yep native install, I'll look at some older versions this afternoon (need to download them first).

Update:

I have just booted from the 6.06 server cd, and am into the installer.

---

### Post by splatman on 2007-08-10
Got it installed, however I guess because of the RAID (The installer showed me all 3 drives and the RAID drive), grub can't find the drive (Error 21), I've found [this](http://www.binf.ku.dk/~hanne/technotes/ServerInstallation/) which looks like exactly the problem I'm having, I was just wondering if there was another way of accomplishing this, that isn't as long winded.

---

### Post by michael37 on 2007-08-12
> **splatman said:**
> Got it installed, however I guess because of the RAID (The installer showed me all 3 drives and the RAID drive), grub can't find the drive (Error 21), I've found [this](http://www.binf.ku.dk/~hanne/technotes/ServerInstallation/) which looks like exactly the problem I'm having, I was just wondering if there was another way of accomplishing this, that isn't as long winded.

My experience with PowerEdge servers is that this is a very common problem.  I think this FAQ (esp the part about megaraid_sas and other megaraid family drivers) is on the issue.

---

### Post by sdowney717 on 2007-08-13
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

