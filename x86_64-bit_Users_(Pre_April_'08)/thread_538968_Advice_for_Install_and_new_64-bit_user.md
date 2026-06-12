---
title: "Advice for Install and new 64-bit user"
date: 2007-08-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by pnotequalsnp on 2007-08-30
I have been using a 32-bit version of Ubuntu for a few years now and I have ordered new hardware (see below).  I was wondering if anyone had advice or experience on setting up the 64-bit version of Ubuntu.  I am looking for help (guides/how to's) installing Ubuntu as well as configuring RAID 1 for my four 500GB drives.  Thanks!  

set up:

XFX GeForce 8500 GT 512MB DDR2
Abit AB9 QuadGT Motherboard - Intel Socket 775, RAID ready
CP2-DUO-Q6600 - Intel Core 2 Quad Q6600 Processor - 2.40GHz
500GB Seagate Barracuda SATA - 4 of these in total
300GB Seagate Barracuda - 1 of these total (OS drive)
OCZ Dual Channel 4096MB PC6400 DDR2 800MHz Memory (2 x 2048MB) - for a total of 8GB of memory

---

### Post by John.Michael.Kane on 2007-08-30
> **pnotequalsnp said:**
> I have been using a 32-bit version of Ubuntu for a few years now and I have ordered new hardware (see below).  I was wondering if anyone had advice or experience on setting up the 64-bit version of Ubuntu.  I am looking for help (guides/how to's) installing Ubuntu as well as configuring RAID 1 for my four 500GB drives.  Thanks!  

set up:

XFX GeForce 8500 GT 512MB DDR2
Abit AB9 QuadGT Motherboard - Intel Socket 775, RAID ready
CP2-DUO-Q6600 - Intel Core 2 Quad Q6600 Processor - 2.40GHz
500GB Seagate Barracuda SATA - 4 of these in total
300GB Seagate Barracuda - 1 of these total (OS drive)
OCZ Dual Channel 4096MB PC6400 DDR2 800MHz Memory (2 x 2048MB) - for a total of 8GB of memory

Taking your setup part by part.

1) XFX GeForce 8500 GT 512MB DDR2
Should be supported by the nvidia-glx-new driver included with ubuntu. Should that not work there's other method to obtain a driver that will,however. It's usually best to try the ubuntu driver first.

2) Abit AB9 QuadGT Motherboard - Intel Socket 775, RAID ready
Looking over the specs of this board it would seem that it is supported. note: that you 'might' have to load in some extra modules for the jmicron sata to ide chipset.

3) CP2-DUO-Q6600 - Intel Core 2 Quad Q6600 Processor - 2.40GHz
Is supported by the kernel.

5) 500GB Seagate Barracuda SATA - 4 of these in total
300GB Seagate Barracuda - 1 of these total (OS drive)

Supported, As for setting up raid you can look into one of the guides below.
[RAID]("https://wiki.ubuntu.com/Raid?highlight=%28raid%29")
[Installation/RAID1]("https://help.ubuntu.com/community/Installation/RAID1")
[HOWTO: Linux Software Raid using mdadm]("http://ubuntuforums.org/showthread.php?t=408461&highlight=raid")
[Howto: Create RAID]("http://ubuntuforums.org/showthread.php?t=517282&highlight=raid")

OCZ Dual Channel 4096MB PC6400 DDR2 800MHz Memory (2 x 2048MB) - for a total of 8GB of memory
Supported under 64bit ubuntu.

For installing other items eg codec's/flash. see the below sticky thread.
[Please Read First Advantages and Disadvantages of 64bit. (Plus install Guides)]("http://ubuntuforums.org/showthread.php?t=368607")

---

### Post by Jouke74 on 2007-08-30
Nice computer!!! Mine is running Ubuntu 64bit already and it's working fine, shall we exchange??
(AMD 4200 X2, ATI X1600 Pro, 2 GB Twinmos 4 x 512, 74 WD Raptor, 250 GB WD Caviar, Soundblaster Audigy 4).

I am sure this forum can help you out. 

:lolflag:

---

