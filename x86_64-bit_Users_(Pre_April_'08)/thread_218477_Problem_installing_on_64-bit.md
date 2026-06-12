---
title: "Problem installing on 64-bit"
date: 2006-07-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by ToyMachine on 2006-07-18
Hi,
I'm trying to use the alternate (not Dapper Drake) method of install (install file ubuntu-6.06-alternate-amd64.iso).  I've never installed linux before.
When I hit enter on "Install in text mode", I get a bunch of gibberish, then at the bottom it says "Kernel Panic - not syncing - Attempted to kill init!"
The same thing happens when I hit "Check CD for defects".
I've burned the CD 3 times, once on 48x and twice on 2x after that didn't work, and they all do this.
What's going on?

---

### Post by TripleE on 2006-07-18
> **ToyMachine said:**
> Hi,
I'm trying to use the alternate (not Dapper Drake) method of install (install file ubuntu-6.06-alternate-amd64.iso).  I've never installed linux before.
When I hit enter on "Install in text mode", I get a bunch of gibberish, then at the bottom it says "Kernel Panic - not syncing - Attempted to kill init!"
The same thing happens when I hit "Check CD for defects".
I've burned the CD 3 times, once on 48x and twice on 2x after that didn't work, and they all do this.
What's going on?

Can you please let us know what your specs are?  Be as detailed as possible.

---

### Post by bonzodog on 2006-07-18
first things first - did you check that the downloaded ISO image is in fact intact?

You will notice on the site a file like yours, but with the bit '.md5' on the end.

Click on this, and it will take you to a page with just a couple of numbers on it, 16 digits long. 

These are called md5 checksums. copy this number into notepad, or write it down, digit for digit. 

You will then need to check the ISO image. 

I'm not sure how you run md5 checksums in windows, but there is something to check ISO image files with. 
When you run it, it will give a number that should be identical to the one off the site. If they are exactly the same, then your ISo image downloaded correctly. 

If they are not, _especially the first 6 digits_, you will need to re-download it.

come back to us if the ISO is intact

---

### Post by ToyMachine on 2006-07-18
Yep, already md5-checked it before.

---

### Post by fatsheep on 2006-07-18
Answering this,

> **TripleE said:**
> Can you please let us know what your specs are?  Be as detailed as possible.

Would help people understand and pinpoint your problem.

---

### Post by ToyMachine on 2006-07-18
According to Belarc...

Current OS= Win XP Media Center build 2600
_Proc_
2.4GHz Athlon 64 3400+
128 KB Primary Cache
512 KB Secondary Cache

_Drives_
_NEC DVD_RW ND-3540A
LITE-ON CD-ROM LTN-489S

Generic USB CF Reader USB Device [Hard drive] -- drive 2
Generic USB MS Reader USB Device [Hard drive] -- drive 4
Generic USB SD Reader USB Device [Hard drive] -- drive 1
Generic USB SM Reader USB Device [Hard drive] -- drive 3
ST3200021A [Hard drive] (200.05 GB) -- drive 0, s/n 4LJ1255W, rev 3.01,

_Controllers_
Standard floppy disk controller
ATI IDE Controller
Primary IDE Channel [Controller] (3x)
Secondary IDE Channel [Controller] (3x)
Standard Dual Channel PCI IDE Controller (2x)

_Bus Adapters_
Standard Enhanced PCI to USB Host Controller
Standard OpenHCD USB Host Controller (2x)

_Communications_
SoftV92 Data Fax Modem with SmartCP
	
1394 Net Adapter
Linksys Wireless-G PCI Adapter
	Physical Address: 	00:12:17:71:FD:2A
Realtek RTL8139/810x Family Fast Ethernet NIC
 primary  	Auto IP Address: 	192.168.0.102 / 24
	Gateway: 	192.168.0.1
	Dhcp Server: 	192.168.0.1
	Physical Address: 	00:13:D3:0A:1D:93
 
Networking Dns Server: 	192.168.0.1


Blah blah...assume you don't need this crap about AV, MS Hotfixes, and software licenses

_Main Circuit Board_
Board: MICRO-STAR MS-7145
Bus Clock: 199 megahertz
BIOS: Phoenix Technologies, LTD 6.00 PG 05/13/2005

_Memory Modules_
896 Megabytes Installed Memory

Slot 'A0' has 512 MB
Slot 'A1' has 512 MB

_Local Drive Volumes_
c: (NTFS on drive 0) 	195.53 GB 	127.35 GB free
d: (FAT32 on drive 0) 	4.51 GB 	1.07 GB free
(This d: drive came with the computer...supposedly its used for System Restore, a feature I've never taken the time to look into)

_Network Drives_
None Detected


Hope that helps...

---

