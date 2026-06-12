---
title: "Compiz crashing, sometimes entire Xorg on 9.10"
date: 2009-11-05
forum: x86 64-bit Users
---

### Post by tonymaro on 2009-11-05
I upgraded from Jaunty to Karmic using the update-manager.  In addition to the 4 times longer boot time I'm now having severe crashes from both Compiz and Xorg.

Compiz will crash many times during the day.  Sometimes it leaves the window decoration and just kills the compositor (which takes out my Avant) other times I end up with no decoration on my windows at all - which makes it hard to move anything ;-)

Then about once a day Xorg will completely crash and dump me to the login screen for no apparent reason.

I thought perhaps it's an NVidia driver thing so I upgraded to the 190 in PPA, to no avail.

The only log entry I've snagged so far has to do with Compiz and is located in DMESG:

[89801.823713] compiz.real[2536]: segfault at 10 ip 00007fa174ab1ea7 sp 00007fff4cc8a3a8 error 4 in libGLcore.so.190.42[7fa173f07000+ecb000]

Before upgrading my NVidia driver to the PPA version it of course gave the same error but reported libGLcore.so.185.[something]

I've checked bug reports and can't find any reports in Karmic that sound similar to mine.  Everyone else reporting the libGLcore crash were from older distributions and claimed to have been solved in an update.

Running AMD64 with a dual-head config.

LSPCI output:
```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GTS] (rev a1)
02:00.0 Ethernet controller: Intel Corporation 82572EI Gigabit Ethernet Controller (Copper) (rev 06)
03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
```

Anyone have any ideas?  By next week I'll be ready to blow it away and install Jaunty again - I can't work this way.

---

