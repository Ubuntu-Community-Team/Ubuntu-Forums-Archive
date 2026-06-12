---
title: "problem with Wine and graphics driver"
date: 2014-07-14
forum: Wine
---

### Post by sparky741pa on 2014-07-14
Hello all!  I swapped out my ATI Radeon graphics card, which was giving me problems, to an Nvidia GeForce 8400 GS.  Graphics work great now, but I realized yesterday that when I wanted to setup a Windows program with Wine(which was previously installed), that it is no longer listed in my applications.  I entered the command line in terminal to reinstall, but it says it must remove so and so portion of my nvidia drivers in order to do so.  Has anyone else run into this?  I am already running Win XP virtually with VirtualBox for certain programs I have, but I hate to lose that functionality that Wine provides as well.  Any ideas?

---

### Post by mooreted on 2014-07-14
How did you install the Nvidia drivers?

---

### Post by sparky741pa on 2014-07-16
I believe I used the command:

```
[COLOR=#141414][FONT=Georgia]sudo apt-get install nvidia-current[/FONT][/COLOR]
```

to get the drivers installed.

---

### Post by Toz on 2014-07-16
*Since this question is related to Wine, it would best be placed in the **Wine** subforum. Moving.*

---

### Post by sparky741pa on 2014-08-13
Any ideas? Anyone?

lspci results

```
mike@MyComputer:~$ lspci00:00.0 Host bridge: NVIDIA Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:07.0 PCI bridge: NVIDIA Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: NVIDIA Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: NVIDIA Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: NVIDIA Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: NVIDIA Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: NVIDIA Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: NVIDIA Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: NVIDIA Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: NVIDIA Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: NVIDIA Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: NVIDIA Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 SATA controller: JMicron Technology Corp. JMB360 AHCI Controller (rev 02)
02:06.0 PCI bridge: PLX Technology, Inc. PEX8112 x1 Lane PCI Express-to-PCI Bridge (rev aa)
02:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
03:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 8400 GS Rev. 3] (rev a2)
03:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)

```

---

### Post by sparky741pa on 2014-08-19
*bump*

---

### Post by chip6162 on 2014-10-11
I have the same problem in Kubuntu 14.04.  When I installed wine on my machine with nVidia driver, it uninstalled part of the nVidia driver, and now my digital HDMI sound does not work.

[WineHQ says this is a packaging issue with Canonical]("https://forum.winehq.org/viewtopic.php?f=8&t=23419&p=96444&hilit=nvidia+conflict+ubuntu#p96444").

At the moment, I have no solution, but in my case, I don't have to have  WINE, but I do need the nVidia driver as this is my media PC and it powers my sound system.

Today I plan to reinstall the nVidia driver with the apt-get command shown in message 3 and see if the two will co-exist. If not, then I will remove WINE and try the nVidia install again.  I'll report back on what I find.

Frank.

---

### Post by Michael_Burry on 2014-10-20
> **sparky741pa said:**
> I believe I used the command:
[SIZE=1][[COLOR=#ffffff]free instagram followers[/COLOR]]("http://iogrip.com/free-instagram-followers/")[COLOR=#ffffff]
[/COLOR][[COLOR=#ffffff]winrar password remover[/COLOR]]("http://iogrip.com/winrar-password-remover/")[/SIZE]
```
[COLOR=#141414][FONT=Georgia]sudo apt-get install nvidia-current[/FONT][/COLOR]
```

to get the drivers installed.
Ill give this a go on my pc, I haven't installed drivers yet, ill let you know what happens.

---

### Post by adec2 on 2014-10-20
This always works for me in Kubuntu but try at your own risk!

sudo apt-add-repository ppa: xorg-edgers/ppa  (minus the space before the xorg, for some reason this forum wants to place a face picture there lol)
sudo apt-get update
sudo apt-get install nvidia-343 nvidia-settings-343

replace 343 with 340 or 331 depending on which driver you want. Some may say don't install all the updates from this ppa if you keep it in your sources but i've never had a problem with it

---

