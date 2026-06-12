---
title: "WICD problems"
date: 2008-10-03
forum: x86 64-bit Users
---

### Post by driverfred on 2008-10-03
Recently WICD has been refusing to connect to the internet, on my WEP network it flashes between saying "02WIRLESSBOX: validating authentication" and "none: validating authentication"  I dont however think that it is a WEP problem as i have tried it with both an unsecured network and with a WPA encryption, both of which flash between "02WIRLESSBOX: obtaining ip address" and "none: obtaining ip address"

I have an Atheros AR5007 wireless card and if i do lspci i get:

> 00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
1a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
1a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
1a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
1a:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller


Thanks :)

---

### Post by VotaVader on 2009-06-06
Hi! I was wondering if you had managed to fix this problem, because I´m having the exact same one. Wicd worked fine for a while, but now it can´t get past the Validating Authentincation part of the connection. It also does that thing where it changes from "SSID: Validating Authentication" to "none: Validating Authentication". I'm using ndiswrapper, but if I choose that option in the preferences, it tries to connect for half a second, and then fails. It's the same with all other drivers I try to choose except with wext (which was the option that worked before, but now doesn't).
Thanks for any help.

---

### Post by cybrsaylr on 2009-06-06
Using WICD for a week or two with no problems.
Like WICD better than network manager so far. WICD seems to give better wireless results and connects faster, at least so far on my Toshiba laptop with Atheros.

---

### Post by AClark on 2009-06-06
I have recently set up a 64-bit Jaunty box and WiCd works OK so far.

I have always preferred it on my other machines - easier to configure and more info about whats going on IMO.

My $16 Rosewill card worked out of the box - using rt61pci driver.

I have had a problem after resuming from S3 suspend but several other things happen such as not able to shut down and others so I don't think it's a WiCd problem.

Sorry I can't offer any concrete help just some encouragement to keep trying (and a bump) :)

---

