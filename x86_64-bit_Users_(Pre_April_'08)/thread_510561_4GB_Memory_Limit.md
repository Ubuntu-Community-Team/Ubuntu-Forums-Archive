---
title: "4GB Memory Limit?"
date: 2007-07-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Luminosity on 2007-07-26
I've decided to make the switch from Windows to Ubuntu. Currently I run Windows X64 for the sole reason that I have 4gb of memory and 32-bit windows will not address the full amount of memory. I was wondering if 32-bit Ubuntu had the same limitation. I have never noticed a speed difference between 32/64-bit Windows and therefore the only reason I am considering 64-bit Ubuntu is for the 4gb memory limit that exists in Windows. Is this a problem? Is this even a Linux problem in general or simply specific to windows? Any help would be appreciated. Thanks in advance.

---

### Post by John.Michael.Kane on 2007-07-26
32bit ubunt will not address the full amount of ram. The amount addressed could be anywhere between 3.2-3.3gb.

Ubuntu64 should address your 4gb or more of memory without issue.

You can read here on the [Advantages and Disadvantages of 64bit.]("http://ubuntuforums.org/showthread.php?t=368607")

---

### Post by Steveway on 2007-07-26
Afaik there are patches that allow Linux to access more than thos 3.5 Gig of Ram on x86.
Ah, yes. On Startcom.org they have such a kernel.
> #

kernel-hugemem &#8212; (nur für i686-Systeme) Zusätzlich zu den für das kernel-Paket aktivierten Optionen. Die Schlüssel-Konfigurationsoptionen sind wie Folgt:

    *

      Support für mehr als 4 GB RAM (bis zu 16 GB für x86)
    *

      PAE (Physical Address Extension), oder 3-Stufen-Paging auf x86-Prozessoren die PAE unterstützen
    *

      Support für mehrere Prozessoren
    *

      4GB/4GB Split &#8212; 4GB virtueller Adressraum für den Kernel und nahezu 4GB für jeden Benutzerprozess auf x86 Systemen 

---

### Post by lisati on 2007-07-26
> **Luminosity said:**
> I've decided to make the switch from Windows to Ubuntu. Currently I run Windows X64 for the sole reason that I have 4gb of memory and 32-bit windows will not address the full amount of memory. I was wondering if 32-bit Ubuntu had the same limitation. I have never noticed a speed difference between 32/64-bit Windows and therefore the only reason I am considering 64-bit Ubuntu is for the 4gb memory limit that exists in Windows. Is this a problem? Is this even a Linux problem in general or simply specific to windows? Any help would be appreciated. Thanks in advance.

Part of it could be a hardware thing too. I recently installed some extra RAM in my desktop, and when I was doing my homework on what sort to get, the instructions I found for my particular machine said that it could only take up to 4Gb.

---

### Post by dabl on 2007-07-26
> **Luminosity said:**
> 
I am considering 64-bit Ubuntu is for the 4gb memory limit that exists in Windows. Is this a problem? Is this even a Linux problem in general or simply specific to windows? Any help would be appreciated. Thanks in advance.

I'd say it's a non-issue at this date. I have 4GB of RAM installed, and I've been running Ubuntu 64-bit for about 4 months (since Feisty), doing audio recording and running Audacity and Gnome Wave Cleaner (32-bit apps).  I've loaded up my dual CPU cores to 100% for 5 minutes at a stretch, and never seen RAM utilization above 500MB.  Yesterday I got Avidemux working on a 20GB video file, and was exercising that, but RAM never went over 500MB.  So, yeah, you'll see your 4GB of RAM with your Ubuntu 64-bit, but no, you won't be using it....  :)

Maybe there'll be some whizzy 64-bit packages one of these days, with which to exercise this baby .... :)

---

### Post by aldenhg on 2007-12-02
Try computing some Rainbow Tables and you'll be really glad you have all that memory. 
Also, is there a Ubuntu-sanctioned/provided kernel pre-patched with hugemem? I'd sure love to load up my laptop with it's maximum memory, but I don't particularly want to switch to 64 bit just yet and I'm done with the days of hacking my own kernel. 
In other words, I'm lazy and I want someone to give me a .deb that's in the repos so I don't even have to check for updates myself.

---

### Post by sethvath on 2007-12-02
There are plenty of precomputed rainbow tables for use with ophcrack but this is besides the point. I've never used more than 2.5gb of ram at any one time, even with ophcrack. My 2gb swap never seems to get utilised more than 5% either.

---

### Post by Jouke74 on 2007-12-03
Unfortunately, not only your Operating System needs to see the full 4 GB. Your motherboard also needs to be able to handle it. Often certain settings in the BIOS need to be made. And yes, I have 2 or 3 programs for my work that easily eat up 4+ GB is I don't restrain the analyses.

---

