---
title: "Nforce 4 Network Card"
date: 2007-03-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Eyasha on 2007-03-18
Hi all,

I was just installing the 64bit version of Ubuntu version 6.10, but it does not reconise my nforce network card could anyone tell me how to get my network card working?

My motherboard is a:
Asus K8N4E-Deluxe

It already didnt found a network card during installation.

Eya

---

### Post by ilbozo on 2007-03-19
You need to install a more recent kernel. I suggest you to follow the ubuntu [master kernel thread]("http://ubuntuforums.org/showthread.php?t=311158") and enable following modules:

Audio (AC97)    nForce-1 – nForce-4 	intel8x0.c
Audio (HDA) 	nForce-430 and later 	hda_intel.c
Storage 	   SATA 	                   sata_nv.c
ACHI 	                                                ahci.c
IDE 	                                                 amd74xx.c
Ethernet 	   All 	                             forcedeth.c

I did it and now i got everything working.

---

