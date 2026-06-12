---
title: "Vodafone 3G data card - HOWTO needed please"
date: 2007-02-10
forum: Za Team - South Africa
---

### Post by umuntu_ngabantu on 2007-02-10
Hello Zuid Afrika!

I am a new linux user and I need help with most things. I have successfully done quite a lot on my own and I feel good about the whole thing. At this point in time though, I am sort of stuck.

I need to use my Vodafone 3G data card with ubuntu edgy 6.10. When I insert the card, it is not recognised by ubuntu, so suppose will have to start there. Don't know how to do it.[http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)

Can I please have a HOWTO on how to eventually get the card working. I'm currently dual boothing and relying on  Winxp for my wireless connection. Not ideal.

Has anyone successfully set up their card?

My PC: Acer Aspire 1410

PS: I have made another post re: mounting my Ipod nano, which I have been failing at, despite the numerous posts made on the main forum. Perhaps if anyone can offer help, they can visit my post (?)

Dankie almal.

---

### Post by diepruis on 2007-02-11
Hi, welcome to Ubuntu.

I don't know how to fix your card, but you might try typing ```
lspci -v
``` and see if you can find any information on the hardware that will help you search for more info about it.

Regarding your iPod, have you looked at this page: [https://help.ubuntu.com/community/IPodHowto](https://help.ubuntu.com/community/IPodHowto) ?

Good luck and have fun :)

---

### Post by umuntu_ngabantu on 2007-02-12
@ Diepruis

Thank you for the response.

I tried your suggestion, with the 3G card inserted and I the got the following output:

 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, fast devsel, latency 0
        Memory at <unassigned> (32-bit, prefetchable)
        Capabilities: <access denied>

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, fast devsel, latency 0

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) (prog-if 00 [VGA])
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, fast devsel, latency 0, IRQ 6
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, fast devsel, latency 0
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Memory at e0080000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, medium devsel, latency 0, IRQ 6
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, medium devsel, latency 0, IRQ 6
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, medium devsel, latency 0, IRQ 6
        I/O ports at 1860 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, medium devsel, latency 0, IRQ 10
        Memory at e0100000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=06, sec-latency=64
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: e0200000-e05fffff
        Prefetchable memory behind bridge: 30000000-32ffffff

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, medium devsel, latency 0, IRQ 6
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 1810 [size=16]
        Memory at 33000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: medium devsel, IRQ 10
        I/O ports at 1880 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
        Memory at e0100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: medium devsel, IRQ 10
        I/O ports at 2400 [size=256]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>

02:02.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, fast devsel, latency 64, IRQ 6
        Memory at e0204000 (32-bit, non-prefetchable) [size=8K]
        [virtual] Expansion ROM at 32000000 [disabled] [size=16K]
        Capabilities: <access denied>

02:04.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
        Subsystem: AMBIT Microsystem Corp. Unknown device 0305
        Flags: bus master, medium devsel, latency 64, IRQ 10
        I/O ports at 3800 [size=32]
        Memory at e020a000 (32-bit, non-prefetchable) [size=32]
        Memory at e0209000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, medium devsel, latency 168, IRQ 10
        Memory at e0208000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 30000000-31fff000 (prefetchable)
        Memory window 1: 34000000-35fff000
        I/O window 0: 00003000-000030ff
        I/O window 1: 00003400-000034ff
        16-bit legacy interface ports at 0001

02:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at e0209800 (32-bit, non-prefetchable) [size=2K]
        Memory at e0200000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

02:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at e0206000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

03:00.0 Network controller: Option N.V. Unknown device 000c
        Flags: medium devsel, IRQ 10
        Memory at 34000000 (32-bit, non-prefetchable) [disabled] [size=2K]
_____

I supposeHost bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, fast devsel, latency 0
        Memory at <unassigned> (32-bit, prefetchable)
        Capabilities: <access denied>

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, fast devsel, latency 0

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) (prog-if 00 [VGA])
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, fast devsel, latency 0, IRQ 6
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, fast devsel, latency 0
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Memory at e0080000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, medium devsel, latency 0, IRQ 6
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, medium devsel, latency 0, IRQ 6
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, medium devsel, latency 0, IRQ 6
        I/O ports at 1860 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, medium devsel, latency 0, IRQ 10
        Memory at e0100000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=06, sec-latency=64
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: e0200000-e05fffff
        Prefetchable memory behind bridge: 30000000-32ffffff

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, medium devsel, latency 0, IRQ 6
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 1810 [size=16]

        Memory at 33000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: medium devsel, IRQ 10
        I/O ports at 1880 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
        Memory at e0100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: medium devsel, IRQ 10
        I/O ports at 2400 [size=256]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>

02:02.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, fast devsel, latency 64, IRQ 6
        Memory at e0204000 (32-bit, non-prefetchable) [size=8K]
        [virtual] Expansion ROM at 32000000 [disabled] [size=16K]
        Capabilities: <access denied>

02:04.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
        Subsystem: AMBIT Microsystem Corp. Unknown device 0305
        Flags: bus master, medium devsel, latency 64, IRQ 10
        I/O ports at 3800 [size=32]
        Memory at e020a000 (32-bit, non-prefetchable) [size=32]
        Memory at e0209000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, medium devsel, latency 168, IRQ 10
        Memory at e0208000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 30000000-31fff000 (prefetchable)
        Memory window 1: 34000000-35fff000
        I/O window 0: 00003000-000030ff
        I/O window 1: 00003400-000034ff
        16-bit legacy interface ports at 0001

02:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at e0209800 (32-bit, non-prefetchable) [size=2K]
        Memory at e0200000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

02:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at e0206000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

03:00.0 Network controller: Option N.V. Unknown device 000c
        Flags: medium devsel, IRQ 10
        Memory at 34000000 (32-bit, non-prefetchable) [disabled] [size=2K]


I suppose I'll have to keep at it.

___

Regarding the ipod, yes I did visit the link you have suggested. It basically seems to assume the ipod has already been mounted to the system. My ipod is not mounted & that's what I'm struggling with at the moment.

---

### Post by nullpex on 2007-02-12
Hi, try this:

[http://www.smachado.com/sergio/28.0.html](http://www.smachado.com/sergio/28.0.html)

---

### Post by RudolfMDLT on 2007-02-24
Hi there.

I've worked with 3G cards before on a RouterBoard RouterOS system. There a different makes of 3G cards out there - the one that we found to work best was the Novatel Merlin 70 series. The Hawaii make didn't want to work.

---

