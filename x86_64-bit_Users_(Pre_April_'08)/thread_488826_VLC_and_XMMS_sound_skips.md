---
title: "VLC and XMMS sound skips"
date: 2007-06-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by desiDragon on 2007-06-30
Hey I just installed ubuntu 7.04 on my computer. I am a fairly new linux user. I've worked a few kinks but this one i can't seem to understand how to fix. I installed VLC and XMMS and the sound is very choppy, before i didn't have sound at all so I went to the ubuntu guide and used the surrond sound guide to get proper sound to work. Sound worked in some instances like the systems sound, like start up and open and close windows, but when i used xmms or vlc sound started skipping? any clue...any help would be appreciated...thanks

---

### Post by frostie on 2007-07-01
I know that in VLC to correct the sound I went to:

Preferences>Audio>Output Modules>ALSA

clicked on Refresh List and then tried the options. hw:0,0 worked for me.

hth

---

### Post by praxis22 on 2007-07-01
open a terminal:

Applications -> Accessories -> Terminal

Then type: **lspci** into that terminal, it will print a lot of information.

Copy that information into this thread, that will tell us what kind of hardware you have.

---

### Post by desiDragon on 2007-07-02
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
01:07.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
01:07.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
01:08.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
01:08.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
01:08.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01)
05:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]
05:00.1 Display controller: ATI Technologies Inc RV530 [Radeon X1600] (Secondary)

---

### Post by raijinsetsu on 2007-08-21
I have this problem too, and almost the exact same specs. My best guess is that we have a 64-bit version of VLC. If I open my Messages window while VLC is playing, I notice lots of PTS errors, and one thing in particular "mpgato32fixed ...". I forget the specifics because I'm at work, ATM. When I go home, I'm going to try uninstalling VLC and then reinstall forcing the architecture to 32bit. As far as I've found, this sound "chop" or garble only happens for me in 64-bit media players.

---

