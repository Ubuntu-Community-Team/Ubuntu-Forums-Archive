---
title: "Hardware and x86 64-bit compatibility"
date: 2008-04-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Seankel on 2008-04-04
I am a very recent convert to Linux from XP.  Ubuntu 7.10 on my old Dell 8100 has inspired me to attempt my first complete build.  I've spent the last few days doing a lot of research and put together what I hope will be a good system.  I would really appreciate any comments and recommendations any of you 64-bit users have, especially in the area of component/x86 64-bit compatibility.  In other words, I would like to avoid buying hardware that has known compatibility issues with Ubuntu and Linux in general.  
Example: I currently have a DLink Wireless PCI card with driver difficulties. 
Here are the specs:
 AMD Athlon 64 X2 5000+ Brisbane 2.6GHz Black Edition
 DFI LANPARTY DK 790FX-M2RS Mother Board
 SAPPHIRE 100227L Radeon HD 3850 1GB Video Card
 2 Seagate Barracuda 250GB Hard Drives in RAID
 LG GGW-H20L Blu-ray, DVD Burner, & HD DVD-ROM drive
 OCZ GameXStream OCZ600GXSSLI ATX12V 600W Power Supply
 Team Elite 4GB (4 x 1GB) 240-Pin SDRAM DDR2 800
 ENCORE ENLWI-N IEEE 802.11b/g, IEEE 802.11n Wireless PCI Card
This will be hooked up to a HD LCD TV and used mostly for multimedia and occasional gaming.  My intention is to build a fast, highly efficient (energy consumption, bang for buck) system that can be upgraded when the need arises. Like I stated above this will be my first build so any advice is welcome. Thanks.

---

### Post by jespdj on 2008-04-04
I see you have an ATI graphics card in your list. ATI graphics cards in general are more problematic than nVidia graphics cards. AMD/ATI has promised to make their Linux drivers better, but to date their drivers are still not great. So I'd look for an nVidia card instead.

For the wireless card, find out what wireless chipset it uses. Some wireless chipsets don't work well with Linux because the manufacturer doesn't bother to make drivers / help open source developers make drivers for their chips. As far as I know Broadcom is a brand to avoid with regard to wireless chipsets. Intel WiFi works well.

I don't know how well Blu-ray / HD-DVD is supported on Linux yet.

---

### Post by Seankel on 2008-04-04
jespdj- Thanks for the input. I was leaning towards an ATI card because I like to root for the underdog but if there is a significant performance difference or driver compatibility issue than I'll definitely go with nVidia.  I am considering cutting costs by down grading the mother board to one that doesn't support SLI or Crossfire as I doubt I will ever have the need for multiple graphics cards. I may even look for a MoBo that has decent on-board graphics card that I can later upgrade to lower the initial coast of the system so I can get it sooner.  Would there be any draw backs to ditching LSI/Crossfire compatibility and going with an on-board graphics card that I am missing?

---

