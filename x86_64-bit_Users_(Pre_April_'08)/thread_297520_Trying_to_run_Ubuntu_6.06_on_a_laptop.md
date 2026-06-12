---
title: "Trying to run Ubuntu 6.06 on a laptop"
date: 2006-11-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Loopsurgeon on 2006-11-11
I got the live CD in the mail and I want to install on an 11GB partition I have on my HP Pavilion dv9000. It just freezes up at different places during the boot. One time it actually ran and then froze. I am including all the stats I think someone might need to help me figure this out. I am thinking there is a hardware conflict or two, but take a look please. I am pretty new to Linux but not a virgin so you don't have to dumb it down too much for me. 



AMD Turion 64 X2 Mobile TL-56
2GB DDR2 667Mhz
System Manufacturer	Hewlett-Packard
System Model	HP Pavilion dv9000 (EZ453UA#ABA)
System Type	X86-based PC
Processor	x86 Family 15 Model 72 Stepping 2 AuthenticAMD ~1808 Mhz
Processor	x86 Family 15 Model 72 Stepping 2 AuthenticAMD ~1808 Mhz
BIOS Version/Date	Hewlett-Packard F.17, 8/21/2006
SMBIOS Version	2.33
Hardware Abstraction Layer	Version = "5.1.2600.2765 (xpsp.050928-1517)"
Total Physical Memory	2,048.00 MB
Available Physical Memory	1.43 GB
Total Virtual Memory	2.00 GB
Available Virtual Memory	1.96 GB
Drive	E:
Description	CD-ROM Drive
Media Loaded	No
Media Type	CD-ROM
Name	HL-DT-ST DVDRAM GSA-4084N
Manufacturer	(Standard CD-ROM drives)
Status	OK
Transfer Rate	Not Available
SCSI Target ID	0
PNP Device ID	IDE\CDROMHL-DT-ST_DVDRAM_GSA-4084N_______________KQ09____\304B36334D373146303720362020202020202020
Name	Conexant High Definition Audio
Manufacturer	Conexant
Status	OK
PNP Device ID	HDAUDIO\FUNC_01&VEN_14F1&DEV_5045&SUBSYS_103C30B7&REV_1001\4&1FC54547&0&0001
Name	NVIDIA GeForce Go 6150
PNP Device ID	PCI\VEN_10DE&DEV_0244&SUBSYS_30B7103C&REV_A2\3&13C0B0C5&0&28
Adapter Type	GeForce Go 6150, NVIDIA compatible
Adapter Description	NVIDIA GeForce Go 6150
Adapter RAM	256.00 MB (268,435,456 bytes)
Installed Drivers	nv4_disp.dll
Driver Version	6.14.10.8638
Name	[00000001] Broadcom 802.11b/g WLAN
Adapter Type	Ethernet 802.3
Product Type	Broadcom 802.11b/g WLAN
Installed	Yes
PNP Device ID	PCI\VEN_14E4&DEV_4311&SUBSYS_1363103C&REV_01\4&14C5F9B7&0&0018
Last Reset	11/11/2006 8:09 AM
Index	1
Service Name	BCM43XX
HID-compliant consumer control device	HID\VID_045E&PID_00E1&COL01\6&37E83A0D&0&0000
HP Pavilion Webcam	USB\VID_0C45&PID_62C0&MI_00\6&6893C9F&0&0000
Microsoft USB Wireless Mouse (IntelliPoint)	HID\VID_045E&PID_00E1&COL02\6&37E83A0D&0&0001
Standard Enhanced PCI to USB Host Controller	PCI\VEN_10DE&DEV_026E&SUBSYS_30B7103C&REV_A3\3&13C0B0C5&0&59
Standard OpenHCD USB Host Controller	PCI\VEN_10DE&DEV_026D&SUBSYS_30B7103C&REV_A3\3&13C0B0C5&0&58
USB Composite Device	USB\VID_0C45&PID_62C0\SN0001
USB Human Interface Device	USB\VID_045E&PID_00E1\5&3558176A&0&6
USB Root Hub	USB\ROOT_HUB\4&6CD36D&0
USB Root Hub	USB\ROOT_HUB20\4&3753860B&0

---

### Post by Frak on 2006-11-11
I think your theory of a hardware conflict could be correct, no offence but try an alternate install CD that might rid you of your problems, but I can't see any conflicts, or not any major ones at least, the only computer I've seen thats better than this one is the "Wild Dog" from System76 fully upgraded. You have a beauty of a computer may I say.
EDIT
Hey you run 64 bit AMD proccessor you are sure that you are using a 64 bit disc, right? That Might sound like a n00b question but it does happen to alot of people
(It should work with the regular disc too, but I've heard of some incompatibility issues with that.)

---

### Post by Loopsurgeon on 2006-11-11
Thanx, so you think I should just try a completely different flavor, or just a new CD of Ubuntu?

---

### Post by s.grinovero on 2006-11-11
I'm having a similar setup here, with many problems.
HP DV9000, 2 GB ram, TurionX2 TL50, nvidia chipset.
To boot ANY Linux distro I need to change some kernel parameters..
First thing to try is > acpi=off, it should be enough to begin ubuntu installation.
After that I'm trying different mixes of parameters, as acpi=nopci , nolapic and nosmp (ubuntu kernel doesn't have smp support, but others have).

HP bios for Turion X2's is badly broken:( : try downloading the live cd at
[www.linuxfirmwarekit.org](www.linuxfirmwarekit.org) to test your bios.

I edited my ACPI table and got it working, but still many problems are getting my system very unstable, as I get some IRQ errors I don't understand.
Somebody told me to try disabling the second GB of ram.. didn't try it yet.

Let me know.. I want to fix it too.

---

### Post by Loopsurgeon on 2006-11-11
Thanks for those ideas. I will check that out as soon as I can. Work is crazy right now. Do you think trying to install Linux messed up your BIOS somehow? or were you having trouble with Windows too?

---

### Post by John Jason Jordan on 2006-11-12
> **Loopsurgeon said:**
> Thanks for those ideas. I will check that out as soon as I can. Work is crazy right now. Do you think trying to install Linux messed up your BIOS somehow? or were you having trouble with Windows too?
I don't think it's possible for Linux to mess up a BIOS. Operating systems get info from the BIOS, but writing to it can only be done at the very beginning of the boot process, long before any operating system starts to load.

---

### Post by s.grinovero on 2006-11-13
> **Loopsurgeon said:**
> Thanks for those ideas. I will check that out as soon as I can. Work is crazy right now. Do you think trying to install Linux messed up your BIOS somehow? or were you having trouble with Windows too?
No, I was saying that the BIOS could be wrong: the acpi table in my case is broken; linux expects a good table and uses this table to configure power schemes, battery status readings, to control fans and in many cases also to configure system timers and PCI devices.
Windows has a different design and knows some more workarounds, so some broken bioses work well with windows but not in linux.
Using acpi=off disables most trouble, but leaves you in a laptop without power management. acpi=nopci leaves the power management but disables the pci devices configuration by acpi...
So you should first try the safest mode
> acpi=off nosmp notsc nolapic pci=noacpi,route-irq
and then if it works try removing some paramters, narrowing down.

The big problem is that there are two different tools to compile ACPI tables: a very strict and good one from intel (works for amd too) and a microsoft one which supports some microsoft extensions and does NOT guarantee a good result except for windows. Of course most hardware producers don't worry about linux users and use the simplest/cheapest and fastest one.. as in many cases the microsoft tools are simpler to use but provide a buggy solution.

You can also try many linux workarounds.. as 
> noirq,noirqbalance,biosirq
but some don't work on all kernel, you should search about them.

Yust try the tool... very simple and gives you a good answer.

---

### Post by s.grinovero on 2006-12-04
I tried OpenSuSE 10.2 RC1 and all problems where solved!
Apparently the latest kernels (2.6.18.3 and newer) know some good workarounds. I have all acpi functions enabled, still no problems.
Now you just have to wait ubuntu gets an update to newer kernels; I'll stick with OpenSuSE.

---

### Post by BIGtrouble77 on 2006-12-04
Why didn't you try edgy first?  SuSE? To each his own.

---

### Post by richandcreamy on 2007-02-27
I can't get edgy to work either so I'm going to attempt SUSE myself. It locks up on detecting hardware.  

I just want linux for the video editing programs and the fact that its way more effiecent.  I was going with ubuntu just because I heard so much about it but linux is linux no?

The distros are more of a personal thing? I think?

There's almost 10 different threads with answers to problems I know that I will run into with Ubuntu for my laptop but this guy says everything is good with one install. 

If OpenSUSE dosen't work though, I'll come back.  You all seem like nice people =)

---

### Post by elizleisndahizle on 2007-03-16
just booting with noapic nolapic works for me, i have the same laptop.

---

