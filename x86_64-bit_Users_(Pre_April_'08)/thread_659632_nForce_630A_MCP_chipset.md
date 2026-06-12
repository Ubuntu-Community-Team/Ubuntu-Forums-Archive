---
title: "nForce 630A MCP chipset"
date: 2008-01-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by marx2k on 2008-01-05
Just purchased an AMD X2 5600+ and placed it onto an ASRock ALiveNF7G-HDReady motherboard that uses onboard GeForce7050 video and an nForce 630A MCP chipset, 

First off, Ubuntu LiveCD wouldn't boot unless it was forced into safe graphics mode.

Upn LiceCD booting, I checked "lspci"  and I get a number of "nVidia Corporation Unknown device"

Fine. I installed Ubuntu Gutsy and rebooted. Booted fine, I executed the command "sudo update-pciids" and still I get the same issue:

```

00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 0562 (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0e.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0f.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:10.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:11.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation Unknown device 053b (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:0a.0 Mass storage controller: Promise Technology, Inc. 20269 (rev 02)

```

Everything does work fine, however. But this can be an issue when I need to (for instance) boot normally with a LiveCD.  I checked on nVidia's website and they are saying that their nForce driver packages (none for the Debian architecture) are now deprecated and the drivers should already be in the kernel (They are saying Fedora runs this fine)

So I am wondering...at this point, do I just wait? Or is there something that can actually be done in regards to this issue?

---

### Post by marx2k on 2008-01-07
Anyone? I sure hope someone can help out with this.   It does not look as though nVidia is being any help

---

### Post by Yellow Pasque on 2008-01-07
So are you still having video issues or are the uknown PCI names your only issue?
[https://bugs.launchpad.net/ubuntu/+source/pciutils/+bug/96114](https://bugs.launchpad.net/ubuntu/+source/pciutils/+bug/96114)

---

### Post by marx2k on 2008-01-07
unknown PCI values are my only issue.. but it does become a large issue when certain programs need to know that certain pieces of hardware exist and are unable to get that information because of unknown PCI info. 

Or does this never become a problem?

---

### Post by Yellow Pasque on 2008-01-07
In my experience, adding the pci ids doesn't make hardware work. As long as Linux recognizes the address and class of device, you should be good to go.

---

### Post by marx2k on 2008-01-07
A small update to my issue. Through BIOS settings I have fixed most of the problem.  I have narrowed it down to two BIOS changes ... 

I upped the PCI Latency Clock to 64 (from 32) and I also enabled the HPET Table.

So now I have:
```

00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:10.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:11.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7050 PV / nForce 630a (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:0a.0 Mass storage controller: Promise Technology, Inc. 20269 (rev 02)

```

Still, two unknowns:
```

00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)

```

I know this is probably not going to affect anything, but I'm one of those people who obsess over stupid stuff like this (and any errors in dmesg) until they're fixed.

So it looks as though these PCI ID's were in the pciid database, but the problem was on the user end. I wonder how to get those last two to show up....

---

