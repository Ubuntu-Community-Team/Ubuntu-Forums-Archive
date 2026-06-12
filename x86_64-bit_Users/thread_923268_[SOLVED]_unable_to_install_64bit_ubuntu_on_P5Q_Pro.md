---
title: "[SOLVED] unable to install 64bit ubuntu on P5Q Pro Motherboard"
date: 2008-09-18
forum: x86 64-bit Users
---

### Post by baserunner_ams on 2008-09-18
Hi Forum,

I recently bought the P5Q Pro with a Intel Q6600 CPU.
2*2 GB DDR2-800 RAM,
3* 500 GB SATA HD
Samsung SATA DVD burner

My problem is that I can not install 64-Bit Linux (ubuntu 8.04 hardy).

I have updated the BIOS to 1306.
I have set the HD's to AHCI instead of RAID which i wanted to use.

When booting from the 64bit ubuntu CD (8.04.1 64bit desktop) and  trying to install, system hangs after successfully connecting to usb devices.

Quote:
"Starting Caldera DR-DOS...
EMM386 3.27 ..." 
then messages for the CD-ROM driver which dont find a cd rom drive as i use a SATA Drive instead of IDE,

then a list of found USB Hosts
last 3 lines be4 systems freezes:
"
USB device attached to host 04 Port 01
USB device attached to host 04 Port 02
USB Driver [09/29/04 12:55:14] loaded successfully.
"

then systems stops doing anything (as far as i can see)


I can however install 32bit OS without any issues.
( i tested with windows server 2003 and Ubuntu 8.04 32bit)

I could also successfully install MS Vista 64bit business (although vista was not able to use the onboard networkcard).

Do i miss something?
Do i need to enable or disable something to get this working?

I am new to ubunto and linux, so if more info is required pls tell me how to optain it and i will add it.

---

### Post by cariboo on 2008-09-18
I assume you are trying to do a wubi install, in other words setting up Ubuntu inside of windows. I don't know if this will work, but in the install window press F4 and chose noapic, then hit enter to see if that will work. IF that doesn't help you might be better off asking your question in the wubi forum.

Jim

---

### Post by baserunner_ams on 2008-09-19
sorry i was not clear enough.

I am doing a clean install of ubuntu 64bit.
I have downlaoded the following files:

- ubuntu-8.04.1-desktop-amd64.iso
- ubuntu-8.04.1-alternate-amd64.iso

I burned both files to a bootaable CD (2 CDs in total)

Boot behaviour is identical with both CDs

To see if my hardware supports 64bit OSes i tested a clean install of Windows Vista 64bit and windows Server 2003 64bit.
Both windows systems installed without a problem on my hardware.

Ubuntu 32bit also instaled and is running without any issues (i had to configure the driver for the network card manually)

thansk for the help

---

### Post by Kilz on 2008-09-19
> **baserunner_ams said:**
> sorry i was not clear enough.

I am doing a clean install of ubuntu 64bit.
I have downlaoded the following files:

- ubuntu-8.04.1-desktop-amd64.iso
- ubuntu-8.04.1-alternate-amd64.iso

I burned both files to a bootaable CD (2 CDs in total)

Boot behaviour is identical with both CDs

To see if my hardware supports 64bit OSes i tested a clean install of Windows Vista 64bit and windows Server 2003 64bit.
Both windows systems installed without a problem on my hardware.

Ubuntu 32bit also instaled and is running without any issues (i had to configure the driver for the network card manually)

thansk for the help

While its nice that you are asking Users for help. Have you asked the Developers for help? The forums are not regularly visited by the Developers (if at all). Why not [file a bug report on launchpad]("https://launchpad.net/ubuntu/+filebug") to see if they can fix the issue? This will help everyone who may buy the same hardware.

---

### Post by wallyberk on 2008-09-19
may this will help:
[http://ubuntuforums.org/showthread.php?t=890604](http://ubuntuforums.org/showthread.php?t=890604)

---

### Post by PranaNZ on 2008-09-21
Unlike the poor frustrated people on the link above I had no problems loading onto a setup almost exactly the same as yours (I only have 2 HD ).
This was my first foray into Linux and apart from frustration loading video drivers I have been very happy.  
This may be very obvious and sorry if it is ( I've seen more than a few cases of this looking through the forums), but did you "unpack" the .iso while burning it to your bootable CD.  There should be quite a few different files on the disc, not just a .iso copy.
Hope you get it up and running,

---

### Post by Sef on 2008-09-22
> This may be very obvious and sorry if it is ( I've seen more than a few cases of this looking through the forums), but did you "unpack" the .iso while burning it to your bootable CD. There should be quite a few different files on the disc, not just a .iso copy.

By unpack, I believe the op means extract the files.   Once you download an iso, just burn it as is to a cd.

---

### Post by baserunner_ams on 2008-09-23
yes i burned the iso files right to CD on my windows box using nero burning software.

Idid nothing different with the 64bit ubuntu CD than i did with the 32bit version (which works fine)

---

### Post by baserunner_ams on 2008-09-27
I have burned a new DVD from:
[http://cdimage.ubuntu.com]("http://cdimage.ubuntu.com")

and this solved my install issue.
However i played around a bit and found out that if i burned the same iso with my windows box i got the same error with the dvd image.
My DVD that solved the issue was burned with the 32bit ubuntu.

Cheers

---

