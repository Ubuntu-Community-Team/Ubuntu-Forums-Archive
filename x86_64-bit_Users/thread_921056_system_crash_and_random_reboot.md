---
title: "system crash and random reboot"
date: 2008-09-15
forum: x86 64-bit Users
---

### Post by xigen on 2008-09-15
My Studio Ubuntu system is rebooting when I am working with Firefox3 or Opera.

I tested the disk - fsck, and all appears OK.
I tested the memory - memtest (4hrs) and there were no errors.

What would you suggest I try?

All the best, 

MW

Linux wilson 2.6.24-19-rt #1 SMP PREEMPT RT Wed Aug 20 20:13:12 UTC 2008 x86_64 GNU/Linux
wilson@wilson:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f1)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a4)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f3)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
01:06.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
04:00.0 VGA compatible controller: ATI Technologies Inc RV630 [Radeon HD 2600 Series]
04:00.1 Audio device: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]

---

### Post by Jouke74 on 2008-09-16
What is use? 
What pages are you watching? 
Flash involved? 
Java involved?

Given that it is only with Internet use, I suggest you check the installation of Flash and Java. Still, issues with these are not supposed to crash your whole computer so there might be something wrong with your ethernet connection (Nvidia CK804). Check your ethernet + connection cable + modem.

---

### Post by Crafty Kisses on 2008-09-16
It could be a overheating issue, sure sounds like it.

Post your X logs.

---

### Post by xigen on 2008-09-16
> **Jouke74 said:**
> What is use? 
What pages are you watching? 
Flash involved? 
Java involved?

Given that it is only with Internet use, I suggest you check the installation of Flash and Java. Still, issues with these are not supposed to crash your whole computer so there might be something wrong with your ethernet connection (Nvidia CK804). Check your ethernet + connection cable + modem.


Hello,

Use - Flash website(s), and web surfing.  Applications running: just Firefox.

The cat5 cable is the same one which has been in use on this system for over a year.

Overheating - is unlikely. I used Kbuntu for a year on this system and it did not crash.

One possibility - I did attempt to install wifi drivers.  I wonder if that is causing some trouble?

Thoughts? suggestions?

All the best,
MW

---

### Post by xigen on 2008-09-17
Beware of the wrath of the silent fan ...

Yes. It was overheating.  The silent fan got clogged w/ dust.

As always - thank you everyone.

Chers,

MW
:KS

---

