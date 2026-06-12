---
title: "Ubuntu - support for AMD64 hardware?"
date: 2004-12-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by stodge on 2004-12-02
I´m planning a major upgrade to my PC, and since I want to use Linux for development, I thought I´d post here and ask the experts! I´m worried about hardware support for modern graphics cards, motherboards and AMD64 processors in Linux, so if anyone has experience with this running under Ubuntu, please let me know how well it works for you.

I´m looking at:

MSI K8N NEO2 PLATINUM NFORCE3 ULTRA S939 AGP 5PCI SATA 1394 SOUND 1000LAN MOTHERBOARD
2-5 Business Days 12534 $189.24 $189.24

CORSAIR VALUE SELECT DUAL CHANNEL 1024MB KIT PC3200 DDR CAS2.5 2X512MB
In Stock 9821 $217.74 $217.74

XFX GEFORCE 6600 GT 128MB DDR3 AGP 8X DUAL DVI & TV OUT VIDEO CARD
In Stock 13402 $309.98 $309.98

AMD ATHLON 64 3200+ PROCESSOR S939 2.0GHZ 512KB L2 CACHE RETAIL BOX
In Stock 12843 $239.98 $239.98

ZALMAN CNPS7000A-CU AMD P4 S462 S478 S754 S939 S940 COPPER 1350-2400RPM 20-25DBA CPU HEATSINK FAN
This product can only be exchanged or replaced with the exact same item only.
In Stock 10100 $48.97 $48.97

All from [http://www.ncix.com](http://www.ncix.com) and these are pre-tax prices in CAN$.

Any suggestions greatly appreciated!

Thanks

---

### Post by jdong on 2004-12-02
I've set up the K8N for 32-bit Linux before (generic 2.6.6). Reporting 100% hardware support; ACPI button recognition; no ACPI sleep/hibernation support


Why get a heatsink/fan when it comes in the retail box? The stock cooling kit is quiet and efficient already!

Your video card is supported by Nvidia 1.0.6629 drivers (1 version above Warty's -- need kernel sources and such!) Thank god for Nvidia!


However, with only 1GB of RAM, I'd suggest that you use 32-bit Linux, as I find certain apps (notably games) have wacky performance under 64-bit... or maybe I'm simply too lazy to toy with 64-bit. As I've mentioned before, I have a very similar setup to yours (A64 3000+ Clawhammer; 1GB RAM), and I notice no speed difference between 64bit and 32-bit modes!

---

### Post by stodge on 2004-12-02
Thankyou! I suppose the alternative motherboard would be:

ASUS A8V DELUXE MOTHERBOARD ATHLON64 S939 K8T800PRO DUAL DDR AGP 5PCI SATA 1394 SOUND 1000LAN

Any comments on this?

Thanks again

---

### Post by dmallery on 2004-12-03
i'm running an a8v here with 1g of pc3500 (ocz).  cpu is 3400+
and the running so far is fine.

dave

---

### Post by jdong on 2004-12-03
Don't run the A8v here, but I do run the similar K8v. 100% hardware support, same ACPI support as mentioned above.

---

### Post by BoyOfDestiny on 2004-12-04
Well everything is working great on my rig:
ASUS Nforce3 SK8N, Opteron 144, 1 gig ram (2x 512 Corsair), Audigy 2 (surround working), Ati Radeon 9200, WinFast TV xp, maxtor 250 gig ata. I have 2x maxtor 150 sata... but have yet to attempt an install on the raid...

Has anyone had luck installing ubuntu on sata with this chipset (promise fast track). I would prefer to run with a linux based raid 0 if possible, but anything is fine... I'm ready to leave windows, and ubuntu is great (project utopia is great too!)

---

