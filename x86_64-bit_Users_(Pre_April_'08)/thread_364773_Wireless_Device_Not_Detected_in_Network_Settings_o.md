---
title: "Wireless Device Not Detected in Network Settings on Kubuntu"
date: 2007-02-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Nameless on 2007-02-18
Hi all, I'm back to using Kubuntu now that Edgy works on my laptop.  I just did a fresh install today, but I'm having trouble with the wireless.  I have a broadcom card (4306) and I've read a ton of tutorials, but I'm missing the one that addresses my problem.  I cannot even see the device in my network settings.  

I've installed ndiswrapper and I'm pretty sure I did that correctly, but when I attempt to go set up the wireless part and enter my WEP key I run into trouble. 

Using KWiFi Manager &/Or the Wireless Assistant, I get a "Wireless device not detected" message and the program exits.  If I go into System Setting > Network Settings I only see my wired LAN.  

What am I missing here?  Is there something more  I should do.  Here's one output that I think is relative.  If there is another I should post, please let me know. 

If there is something I need to read about this or a tutorial, just point me to that.  For the life of me, though, I couldn't find one when I searched. 

My lspci seems to show that my card is installed?  Shouldn't Kubuntu pick it up in the Network Settings? 
```


00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 5a36
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 10)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 01)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
03:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
03:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
03:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
03:04.4 Class 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
03:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


```

---

### Post by NullHead on 2007-04-19
Did you try.

```
sudo ndiswrapper -m
```

Your card is detected > 03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by jfranks on 2007-04-26
I have the exact same problem.  I have been using kubuntu for about 6 weeks now.  Yesterday I let the battery run out.  Once I returned home and plugged in I found that no network utility would find my wireless device.  I have installed all updates, and am running feisty, an upgrade from an edgy clean install.  

When I run lspci I see my wireless card.

05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)


However, Knetwork Manager, KWiFi, and Wireless LAN Man can not find a wifi device.  What can I do???  When I revert back to my vista install, wireless works fine, as well as if I boot from the Feisty fawn DVD.

Does anyone have any suggestions???

Thanks

EDIT:  If this is in the wrong thread please move.  I have a dual core intel T2050 laptop, not an AMD x86-64

---

### Post by NullHead on 2007-04-26
Yep it's the wrong one ... but are you using ndiswrapper?

---

