---
title: "Wifi for my laptop please?"
date: 2008-08-25
forum: Wine
---

### Post by Albed 1 on 2008-08-25
I have an Acer Aspire 3000. Due to some...careless clicking I wiped windows from my top and have been trying to get used to things since. So far I'm enjoying Unbuntu, but my brother is driving me nuts about the lack of internet so can someone please help me get my wifi working? Greatly appreciated. ^_^







jester@blaque-top:~/bcm43xx$ lspci -nn
00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] 760/M760 Host [1039:0760] (rev 03)
00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] SG86C202 [1039:0002]
00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] [1039:0963] (rev 25)
00:02.1 SMBus [0c05]: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller [1039:0016]
00:02.5 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 [IDE] [1039:5513]
00:02.6 Modem [0703]: Silicon Integrated Systems [SiS] AC'97 Modem Controller [1039:7013] (rev a0)
00:02.7 Multimedia audio controller [0401]: Silicon Integrated Systems [SiS] AC'97 Sound Controller [1039:7012] (rev a0)
00:03.0 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.1 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.2 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002]
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet [1039:0900] (rev 91)
00:06.0 CardBus bridge [0607]: Texas Instruments PCI1510 PC card Cardbus Controller [104c:ac56]
00:0b.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter [1039:6330]
02:00.0 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
02:00.1 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
jester@blaque-top:~/bcm43xx$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:16:36:0f:9d:d8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=173 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:16:ce:00:47:af
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
jester@blaque-top:~/bcm43xx$ uname -m
i686

---

### Post by kaboodle_fish on 2008-08-25
Does this thread help?

[http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)

---

### Post by nickgaydos on 2008-08-25
If you are able to get on Ethernet, go to Add/Remove Programs and search for Windows Wireless Drivers and install it. Download the specific driver for your WLAN card and open up WWD. Click install new driver and search through your wireless cards drivers and choose the .inf. This worked for me on Ubuntu 8.04.1

---

