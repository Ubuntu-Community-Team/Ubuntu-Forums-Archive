---
title: "Another EDUP Problem"
date: 2008-02-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by bethnesbitt on 2008-02-08
I bought a new EDUP pci 2.4ghz wireless adapter from ebay.  I've tried everything to get ubuntu amd64 to reconize it with no success.

Yes I have tried ndiswrapper, madwifi and all the linux header files.  I even downloaded a ninux driver from sourceforge.  Nothing still but a bunch of un-needed files now all over the place that I am going to have to get rid of.

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions

lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 RAID bus controller: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
**00:06.0 Unclassified device [0013]: Central System Research Co Ltd Unknown device 0013 (rev 08)** <------ (assuming this is the driver since everything else I recognized and Ubuntu recognizes with no problems)
00:07.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter


I see quite a few people have bought this, and posted helps, some even said they got it to work and it works great.  Well okay goodie, so how did you do it?!?

---

### Post by bethnesbitt on 2008-02-08
Well i am getting somewhere.  I bought 2 of these cards, one for a pc running XP computer and one for a pc running ubuntu.

On xp while installing the driver, xp locks up, in ubuntu after installing the driver using ndiswrapper, the computer locks up when rebooting.  (Before it finishes rebooting).

After doing a hard restart, kubuntu loads, but still no driver, which I think explains why I still do not see anything.  (This is the same thing with the XP machine).

If nobody can relate or answer, well I guess I can keep trying and maybe find a solution.  (Or somebody might have one?).  I noticed alot of people are buying them on ebay and not saying if they ever got it to work.  Hate to see so many people with a card sitting in their desk drawers.

---

