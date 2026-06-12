---
title: "Linux Frustration on Particular Box"
date: 2006-12-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by reversengineer on 2006-12-06
I've been running into a brick wall with this box when it comes to Linux.
It's an AMD Athlon 64-bit 3400+ box with 1.5 gigs of ram, 160 gigs of storage and an lspci of:

```

0000:00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a2)
0000:00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a2)
0000:00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
0000:00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
0000:00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
0000:00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
0000:00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f2)
0000:00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f2)
0000:00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
0000:00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a2)
0000:00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a2)
0000:00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)
0000:05:07.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
0000:05:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

```
This isn't exactly a throw-away box so I'm sure you can understand my frustration of having to stick with Windows on hardware that's capable of doing so much more.

For some reason Ubuntu (Breezy only. Newer versions won't detect my hard drive or network card) is about all I can get to install (and boot after the installation ](*,) ) so it looks like I'm sticking with it....which isn't really a bad thing since it's a pretty great OS. I've successfully upgraded to Dapper but I've had to stick with the origional 2.6.12 kernel instead of the 2.6.15 that is installed with Dapper.
Here is what I <i>think</i> I know about my problem, and why:
Every kernel that I've tried that wasn't 2.6.12 hasn't worked. That is, kernel versions greater than 2.6.12 won't boot. Now, I read somewhere online that 2.6.12 has to be compiled with a gcc of version 3.4 (or lower I'm assuming). If this is correct then I think I can attribute my problem to newer kernels being compiled with the upgraded gcc-4, which I have had problems with in the past when working with Gentoo. Maybe there is a bug with gcc-4 and my hardware? (which is doubtful, because I know many people use the nforce4 chipset without any problems) The simple answer to this might be to try compiling a kernel with gcc-3.4, but I've run into a problem with that in itself. I'm under the impression that typing "export CC=/usr/bin/gcc-3.4" into the terminal will switch the version, but "gcc -dumpversion" still gives me 4.0.3 as the version. 
Can anyone give me any advice?

---

### Post by hainesr on 2006-12-07
When you say it won't boot with a kernel version greater than 2.6.12, what do you mean? How far through the boot process does it get, etc?

If it just hangs in the middle of booting try changing the boot line in grub: Change "quiet" to "verbose". What does that say? Where does it get stuck?

Cheers,
Rob

---

