---
title: "installation hangs during creation of / partiion"
date: 2006-08-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by tardis1984 on 2006-08-12
I am trying to install linux on my Compaq desk top: 
AMD Sampron Processor 3400+ (64 bit)
256MB DDR-400 RAM; 
100GB 7,200RPM Serial ATA Hard Drive;

During the installation I have selected to erase entire disk:
The reference to the disk, that shows on the monitor is
SCSI1 (0,0,0) - 100 Gb ATA Maxtor 6L100M0

The installation invariably hangs during the creation of:
ext 3 file system for /in partition #1 of SCSI1 (0,0,0) sda.
This happened couple of times, once at 11% and second time at 15% of progress.

The disk drive, I think, is SATA drive, is there a problem with SATA in this version of Linux, UBUNTU 6.06 - 64 bit version.

Why is the referrence to disk specify SCSI1 type of disk?

Any help would be greatly appriciated, I am stuck!!!!!!!!! ](*,)**[COLOR="Red"][COLOR="Red"][COLOR="Black"][COLOR="Black"][B][B][B][B][B]**[/B][/B][/B][/B][/COLOR][/COLOR][/COLOR][/COLOR][/B]

---

### Post by Anduu on 2006-08-12
A new version of the Dapper Cd has been released...6.06.1.

There were some issues with installing on certain system configurations...not sure if yours falls in there but it couldn't hurt to try.

Also formatting of large drives can take quite some time...I remember mine did.I would let it sit for *at least* 30 minutes before assuming it is hung up.

---

### Post by mikeescott on 2006-08-12
This happened to me with the 6.06 cd at 15%. I reformatted with the live cd and install went fine after that. Now, if I could just figure out how to install modem drivers, I could get on the net and out of Windoze.

---

### Post by Kilz on 2006-08-12
> **mikeescott said:**
> This happened to me with the 6.06 cd at 15%. I reformatted with the live cd and install went fine after that. Now, if I could just figure out how to install modem drivers, I could get on the net and out of Windoze.

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

