---
title: "Imac 233, install problem."
date: 2006-03-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by namzuf9 on 2006-03-03
I've recently aqquired an old 233-32mb ram imac which I was planning to install ubuntu with fluxbox to use as a internet box for the kids. I've downloaded the ubuntu ppc install disc and verified the checksum but its giving me the following error messages when I try to install it.

error -3 while decompressing
kernel panic-not syncing- attempted to kill init!
rebooting in 180 seconds

I do use linux as my main os, so I'm not a complete newb but this is beyond my current capabilties!  I would be grateful for any help offered.

System specs:
Imac 233mhz (bondi blue?)
32MB RAM
Mac os 8.6 (seems to be working fine)
Mac os rom v1.0

Cheers

---

### Post by Ptero-4 on 2006-03-03
IIRC. That error means that your initial ram disk couldn't be decompressed b/c you don't have enough free RAM to decompress it on. Can you add some more RAM to that iMac. It would make it easier to install and use linux on.

---

### Post by deathshadow on 2006-03-03
Usually it hinges on WHEN in the boot process that error occurs - the second line is typical for panic shutdowns, so isn't really related to the issue.

Can you pull the five or six lines BEFORE the "error -3 while decompressing" as that would let me (and most others) figure out WHERE it failed, then we can point you the right direction (I hope). There can be many causes for decompression errors, from a bad disk, to bad ram, to linux not being able to even access the file it wants to decompress because it lacks the proper device drivers for the CD drive and/or interface (which given the first gen iMacs are SCSI...) 

To get to the error 3 point the kernel load worked, at which point the kernel starts and tries to load the root filesystem (in the case of a installation, a ramdisk decompress). When the kernel starts the computer stops relying on the legacy BIOS (or apple rom equivalents) and starts trying to use it's own device drivers instead - this could be your problem.

---

### Post by jdp on 2006-03-04
[QUOTE=deathshadow](which given the first gen iMacs are SCSI...)[/QUOTE]


Nope, they're 100% ATAPI drives. ;)  They just happen to use a custom Apple adapter card on the back of the drive to convert the laptop-style ATA plug into a normal header for a ribbon cable.  They DO use a 50-pin ribbon cable, because in the iMac that cable also carries drive power and audio wires.  I can see the confusion that they might be SCSI, but the HDD runs off the same cable in slot-load iMacs.  You can just use the first 40 pins of the 50-pin  cable and attach any ATA/IDE device...

---

### Post by deathshadow on 2006-03-05
Well, I'm glad you mentioned that 50 pin centronics D isn't SCSI before I went and risked burning out a device on it.

Oh yeah, that apple quality people are always talking about. RIGHT.

---

