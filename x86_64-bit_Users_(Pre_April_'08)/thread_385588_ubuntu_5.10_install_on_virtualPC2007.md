---
title: "ubuntu 5.10 install on virtualPC2007"
date: 2007-03-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by shreesh on 2007-03-15
I tries running ubuntu 5.10 ( 64 bit ) on my acer5101 laptop running vista ultimate using microsoft virtual pc 2007.

After i start the installation process, i always get this sceen . i am clueless as to what is happening wrong here.

---------------------------------------------

AMIBIOS 2001 American Megatrends , Inc,
Bios date: 02/22/06 20:54:49 ver:08.00.02

Press DEL to run Setup
checking NVRAM

251MB OK
Auto-detecting Pri Channel (0)...IDE Hard Disk
Auto-DEtecting Pri Channel (1)
Auto-Detecting Sec Channel 90)...CDROM
Auto-Detecting Sec Channel (1)...


Argon PXE Boot Agent v2.00(BIOS Integrated)
All rights reserved , w.ArgonTechnology.com

client MAC ADDR:00 03 FF 5C 27 B3 GUID:9EBFF569-38F0-384B-9A64-45BE564401AD
dhcp..

------------------------------------------------
at this stage, it searches for DHCP and returns the message
NO DHCP OR DHCP PROXY OFFERS WERE RECEIVED
reboot and select proper boot device
or insert boot media in selected boot device.


what could be going wrong here?

---

### Post by Kilz on 2007-03-16
> **shreesh said:**
> I tries running ubuntu 5.10 ( 64 bit ) on my acer5101 laptop running vista ultimate using microsoft virtual pc 2007.

After i start the installation process, i always get this sceen . i am clueless as to what is happening wrong here.

---------------------------------------------

AMIBIOS 2001 American Megatrends , Inc,
Bios date: 02/22/06 20:54:49 ver:08.00.02

Press DEL to run Setup
checking NVRAM

251MB OK
Auto-detecting Pri Channel (0)...IDE Hard Disk
Auto-DEtecting Pri Channel (1)
Auto-Detecting Sec Channel 90)...CDROM
Auto-Detecting Sec Channel (1)...


Argon PXE Boot Agent v2.00(BIOS Integrated)
All rights reserved , w.ArgonTechnology.com

client MAC ADDR:00 03 FF 5C 27 B3 GUID:9EBFF569-38F0-384B-9A64-45BE564401AD
dhcp..

------------------------------------------------
at this stage, it searches for DHCP and returns the message
NO DHCP OR DHCP PROXY OFFERS WERE RECEIVED
reboot and select proper boot device
or insert boot media in selected boot device.


what could be going wrong here?

Its looking for the bootable drive, or a network boot to install the operating system. Odds are it isnt seeing the cd or cd drive.

---

