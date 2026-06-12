---
title: "Intermittent boot up timing problem involving ATA hard drive"
date: 2009-01-29
forum: x86 64-bit Users
---

### Post by gallen53 on 2009-01-29
I've got a really tough kernel bootup bug that probably only an expert can solve.

System description:

Supermicro H8DA8 motherboard with a built in Adaptec AIC7902 Ultra320 SCSI adapter.
Dual AMD Opteron Processor 252
4 GBytes of RAM
e-GeFore 6200 graphics card
one / Western Digital WD1600 hard ATA drive
three / Hitachi IC35L036UWDY10-0 SCSI U-320 hard drives
Floppy drive
Matshita DVD-ROM SR-8588 DVD drive
Pioneer  DVD-RW  DVR-115D DVD drie
LG BDDVDRW GGC-H20L HD and BluRay DVD drive based on an SATA adapter card

Kernel:  2.6.24-16-generic SMP installed on one of the SCSI U-320 hard drives

Problem description:

Occurring about one out of three bootups, the system seems to take a little longer than usual at one of the "ACPI: PCI Interrupt" commands.  Then the system will go into recovery mode because it can not read the partition table on the Western Digital WD1600 ATA hard drive (no problems ever encountered with the three SCSI drives).  I have run the WD1600 ATA hard drive through the Western Digital diagnostic software and the diagnostic software did not register any hardware faults.  

I believe(?) the fault is due to a subtle PCI bus timing issue where something associated with the PCI bus times out.  I have attached the "dmesg" dumps for the case of a successful bootup and for the case of a failed boot attempt.  I performed a diff between the two dmesg dumps and they are full of false clues (I have no idea where to start).  Random plugging and unplugging of cables, etc. doesn't impact the fault.  I'm convinced this is a software problem.  Only a kernel guru could diagnose this problem.  I have attached the failed and successful dmesg dump files as gzipped text files.

Thanks!

Gary Allen

---

### Post by dcstar on 2009-01-31
> **gallen53 said:**
> 
........
Occurring about one out of three bootups, the system seems to take a little longer than usual at one of the "ACPI: PCI Interrupt" commands.  Then the system will go into recovery mode because it can not read the partition table on the Western Digital WD1600 ATA hard drive (no problems ever encountered with the three SCSI drives).  I have run the WD1600 ATA hard drive through the Western Digital diagnostic software and the diagnostic software did not register any hardware faults.  

I believe(?) the fault is due to a subtle PCI bus timing issue where something associated with the PCI bus times out.  I have attached the "dmesg" dumps for the case of a successful bootup and for the case of a failed boot attempt.  I performed a diff between the two dmesg dumps and they are full of false clues (I have no idea where to start).  Random plugging and unplugging of cables, etc. doesn't impact the fault.
.......

A lot of BIOSs have a setting for Hard Disk delay (to allow sufficient spin-up for some drives), I suggest you see if you can increase this value.

---

### Post by yyyc186 on 2009-01-31
You know, I've been using computers a long time.  The first PC I ever personally owned was an NCR PC4 with 2 360K floppies.  Yee-haw!

Over my lengthy career, I have seen no end of problems caused by Can't-Adapt-Cr*p controllers.  They are the bottom feeders of the industry.

If the previous suggestion of timing adjustments don't work for you, try the following things in the following order:

1)  firmware update on that crummy card
2)  BIOS update for your motherboard
3)  Replace that crummy Adaptec card with one from a reputable manufacturer.

Spastic problems with Adaptec is simply another day at the office.

---

