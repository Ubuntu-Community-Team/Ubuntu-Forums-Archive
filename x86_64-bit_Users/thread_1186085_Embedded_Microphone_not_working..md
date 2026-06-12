---
title: "Embedded Microphone not working."
date: 2009-06-13
forum: x86 64-bit Users
---

### Post by Jolzath on 2009-06-13
All right so I have a set of embedded microphones by Altec Lansing on my tx1308nr (tx1000z) laptop, all of the guides talk about the microphone jack not for the embedded microphones. I would like to use those microphones to record my voice and such, after all they are there for my use. I have tried to look for the microphone first through the Voulme appelet, but only the front mic is able to be controled via HDANVidia (Alsa Mixer) when recording using sound recorder, it does not find anything to record (as in the recorded data is blank). Please help me.

If you need a file posted I will give it to you. (Such as the one I am about to give you now)

Output of lspci
```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)

```

---

### Post by Jolzath on 2009-06-14
Sorry to bump but this is something I would like to know how to fix.

---

### Post by gradinaruvasile on 2009-06-14
Open volume control by clicking the speaker icon, click preferences, tick everything.
Still no mic?

open a terminal, type

alsamixer

Press tab, u are now in the capture tab. What is there? Post a screenshot.

---

### Post by Jolzath on 2009-06-14
> **gradinaruvasile said:**
> Open volume control by clicking the speaker icon, click preferences, tick everything.
Still no mic?

open a terminal, type

alsamixer

Press tab, u are now in the capture tab. What is there? Post a screenshot.

Amusing, I needed to install Alsamixer XD... wait... I thought it was installed by default...

---

