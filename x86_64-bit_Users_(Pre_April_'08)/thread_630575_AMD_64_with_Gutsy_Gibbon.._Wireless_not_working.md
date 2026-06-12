---
title: "AMD 64 with Gutsy Gibbon.. Wireless not working"
date: 2007-12-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by unc2nyu on 2007-12-03
new computer. vista installed but i want kde instead.

installed the os gutsy gibbon. 

wireless not working. network manager doesn't even see any wireless networks available. i've tried to manually configure the network but it doesn't work.  i've enabled and disabled the network; nothing changed. i can get online with a connection directly to the modem (using dsl) but not wirelessly.  everything is enabled and i've tried to even remove network manager and installed wifi-radar but it didn't do anything. it actually crashes. 


Help needed if anyone can give it please !!!!


:KS

---

### Post by John Jason Jordan on 2007-12-03
> **unc2nyu said:**
> new computer. vista installed but i want kde instead.

installed the os gutsy gibbon. 

wireless not working. network manager doesn't even see any wireless networks available. i've tried to manually configure the network but it doesn't work.  i've enabled and disabled the network; nothing changed. i can get online with a connection directly to the modem (using dsl) but not wirelessly.  everything is enabled and i've tried to even remove network manager and installed wifi-radar but it didn't do anything. it actually crashes. :KS
There are tons of makes and models of wireless chips and each one requires a different driver and different configurations. From a terminal run the command "lspci." Scan through the results looking for the wireless component. Post back the line(s) relating to the wireless component so people on the forums can see what make and model it is. Then you will be more likely to get specific help.

---

### Post by unc2nyu on 2007-12-03
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
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
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)

---

### Post by NullHead on 2007-12-03
It looks as if you don't have a wireless card. Do you know the specific make a model of the card? that might help in our quest for wireless freedom.

EDIT: hmm looks like you have something hear, but linux isn't detecting it correctly ... the brand and model would help us with this. Look at this phantom devise hear.> 00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915

---

### Post by unc2nyu on 2007-12-04
Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)

the best i can do i'm not the brightest when it comes to computers... :)

---

### Post by John Jason Jordan on 2007-12-04
> **unc2nyu said:**
> Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)

the best i can do i'm not the brightest when it comes to computers... :)
I can sympathize. When I first started some of these things were confusing too. 

"Ethernet" refers to the wired connection. It is for connecting an ethernet cable to the ethernet jack on your computer. The ethernet jack looks like a phone jack but is slightly wider. Ethernet on Ubuntu is usually referred to in software as "eth0," although that may differ depending on various things. The wireless connection doesn't have a jack (duh!). It is usually referred to in software as wlan0 or sometimes as eth1. 

So the Realtek device is not your wireless device. It also appears that Ubuntu not only did not configure your wireless chip, it didn't even see it.

At this point I would call the manufacturer of the computer and ask their technical support for the make and model of wireless installed in the computer.

I should also ask if this is a laptop (almost all of which come with wireless installed by default) or a desktop (few of which come with wireless). If it is a desktop that would explain why Ubuntu did not detect the wireless - it isn't there.

---

### Post by unc2nyu on 2007-12-04
it does have wireless because its a laptop. when i first opened the computer to check everything out wireless worked in vista...  unfortunately now i can't even put vista back on the computer as the main operating system to see if wireless works... i have tried xp but that doesn't work... right now i've tried opensuse, kubuntu and ubuntu 7.10 live cd's. at first i thought it was just a live cd, but when i install it still doesn't pick it up either. i'll have to check the specifications on the wireless and see what's going on... 

my 2006 model gateway laptop didn't have a wireless switch and always worked with kubuntu feisty, the new 2007 model gateway has a wireless switch.. Yes It is turned on and enabled in BIOS, but still doesn't work... i'll have to get back with the wireless in depth information but thanks for all you guys' help :)

---

### Post by NullHead on 2007-12-06
> **unc2nyu said:**
> it does have wireless because its a laptop. when i first opened the computer to check everything out wireless worked in vista...  unfortunately now i can't even put vista back on the computer as the main operating system to see if wireless works... i have tried xp but that doesn't work... right now i've tried opensuse, kubuntu and ubuntu 7.10 live cd's. at first i thought it was just a live cd, but when i install it still doesn't pick it up either. i'll have to check the specifications on the wireless and see what's going on... 

my 2006 model gateway laptop didn't have a wireless switch and always worked with kubuntu feisty, the new 2007 model gateway has a wireless switch.. Yes It is turned on and enabled in BIOS, but still doesn't work... i'll have to get back with the wireless in depth information but thanks for all you guys' help :)

I would try mepis next. [http://www.mepis.org/](http://www.mepis.org/) it has very nice auto detecting software.

---

### Post by nickiank on 2007-12-24
I'm running into a similar problem with a budget Gateway notebook a relative gave me as a gift. After some poking around, and being thoroughly kerflummoxed by the seeming invisibility of the wireless device under Linux, it seems that the wireless device is *not* on the PCI bus like you'd expect for an internal wireless device, but is instead hooked in via USB!

Here's the output of lsusb:

```

nkeiser@learnhow:~$ lsusb
Bus 005 Device 002: ID 0bda:8189 Realtek Semiconductor Corp.
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```

Weird, huh? This is the first I've seen of this, but I guess I shouldn't be overly surprised given that it's a budget model. I'm tempted to poke around to get it working, but OTOH, isn't USB slower than PCMCIA?

At any rate, if you're having this same issue of an "invisibile" wireless device on the PCI bus, it *might not be there* in the first place. lsusb and see what comes of it. HTH!

---

### Post by nickiank on 2007-12-24
Well of course I should've Googled me up some info first:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek")

Quick summary before you read: no native support for the internal wifi on my notebook, and it looks as though the only option at this point is using a Windows driver for the device w/ ndiswrapper. Yuck.*

Hopefully you're not stuck with the same device as me and will have better luck...

*And you know, ndiswrapper isn't the end of the world. That it is available as an option is better than no option at all. But we'd all rather have *real* drivers, right? :)

---

