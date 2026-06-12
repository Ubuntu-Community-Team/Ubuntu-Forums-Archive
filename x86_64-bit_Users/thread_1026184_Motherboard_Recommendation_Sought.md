---
title: "Motherboard Recommendation Sought"
date: 2008-12-30
forum: x86 64-bit Users
---

### Post by vgrisham on 2008-12-30
My motherboard is coming on 5 years old, and I think I'd like to upgrade it and get a new 64-bit processor. 

Would someone please recommend a good, new-ish 64-bit motherboard and processor? Which motherboard manufacturer is the most linux friendly? Does any manufacturer offer a Linux based tool with which to upgrade the bios? 

By the way, this is for a full-sized ATX tower.

---

### Post by stchman on 2008-12-31
> **vgrisham said:**
> My motherboard is coming on 5 years old, and I think I'd like to upgrade it and get a new 64-bit processor. 

Would someone please recommend a good, new-ish 64-bit motherboard and processor? Which motherboard manufacturer is the most linux friendly? Does any manufacturer offer a Linux based tool with which to upgrade the bios? 

By the way, this is for a full-sized ATX tower.

I have an Asus P5K with a Core 2 Quad and everything works OOB.  I do not know if my mobo is made anymore, but a mobo with a P35 chipset will work well.  Steer clear of the newer Marvell ethernet cards.

---

### Post by John.Michael.Kane on 2008-12-31
> **vgrisham said:**
> My motherboard is coming on 5 years old, and I think I'd like to upgrade it and get a new 64-bit processor. 

Would someone please recommend a good, new-ish 64-bit motherboard and processor? Which motherboard manufacturer is the most linux friendly? Does any manufacturer offer a Linux based tool with which to upgrade the bios? 

By the way, this is for a full-sized ATX tower.

Here are the parts that were used in the workstation I am using.

CPU= Intel E8400
Main board= GA-P35-DS3L (rev. 2.0) or you could also use one of the newer P45 base boards.
Ram= G.SKILL F2-6400CL5D-4GBPQ

As for upgrading the bios the guide below is still supported, and has been tested.
[HOWTO: Flash BIOS, The Ubuntu Way]("http://ubuntuforums.org/showthread.php?t=318789")

---

### Post by vgrisham on 2008-12-31
Thank you both for your suggestions. 

Happy New Year.

---

### Post by OmnyDevi on 2008-12-31
i updagrade my computer about once a month. for ages i couldn't get any linux distro to install accept ubuntu. i tried kubuntu, sabayon, gentoo, they "all" failed. 

now i am using a egea 680i lt mobo and thus far, everything i have tried to install works oob. it was about 100 bucks or so, but well worth the 6 sata ports for raid and sli graphics cards :D

i have a intel quad core cpu, but a dual core would be fine for most. i am just very into virtual machines and need all i can get. being broke doesn't help :D

---

### Post by tech9 on 2008-12-31
> **vgrisham said:**
> My motherboard is coming on 5 years old, and I think I'd like to upgrade it and get a new 64-bit processor. 

Would someone please recommend a good, new-ish 64-bit motherboard and processor? Which motherboard manufacturer is the most linux friendly? Does any manufacturer offer a Linux based tool with which to upgrade the bios? 

By the way, this is for a full-sized ATX tower.

gigabyte motherboards are great. I have an AMD 64 CPU gigabyte

---

### Post by vgrisham on 2008-12-31
Has anyone gotten motherboard RAID to work? Ubuntu would never seem my ASUS mobo's onboard RAID configuration.

---

### Post by norwoods on 2008-12-31
i have put together a few GIGABYTE GA-EP45-DS3R LGA 775 Intel P45 ATX Intel Motherboard with G.SKILL 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 667 (PC2 5300) Dual Channel Kit Desktop Memory and Intel Q9550 processors and have been very happy with the results.  the GIGABYTE boards are very picky about memory; i am sticking to G.SKILL.  the BIOS can upgrade from a file on a usb flash drive without any operating system.

---

### Post by Kilz on 2008-12-31
> **norwoods said:**
> the BIOS can upgrade from a file on a usb flash drive without any operating system.

The ASUS M3A I have has the same thing. It has this [small error about 64mb of ram]("http://ubuntuforums.org/showthread.php?t=1018854"), but with 4gb 64mb isnt worth the worry. I like it a lot and it supports AMD+ chip's.

---

### Post by vgrisham on 2008-12-31
I've been on AMD64 for a long time. I didn't even know that Intel had 64-bit until recently. 

Are there advantages/disadvantages to AMD vs. Intel? Please educate me. (Don't go all KDE vs. Gnome though.)

---

### Post by Kilz on 2008-12-31
> **vgrisham said:**
> I've been on AMD64 for a long time. I didn't even know that Intel had 64-bit until recently. 

Are there advantages/disadvantages to AMD vs. Intel? Please educate me. (Don't go all KDE vs. Gnome though.)

Same here, I haave been using amd since my first 64bit and never went back to intel. The factor that got me was price, a 9950 phenom x4 was only $189. a comparable intel chip was $250-$300. Google also has a wealth of comparison info.

---

### Post by norwoods on 2008-12-31
the reason i chose intel was they manufacture with 45nm technology so they have less power dissipation at any performance level.  i want less power for easier cooling with fewer fans and less fan noise. 
i like the scythe s-flex fans for low noise and long life.
i like ECS N9600GT-512MX-P graphics cards with no fan.
i like XIGMATEK HDT-S1284EE cpu heat sinks.  i bolt the heat sink to the mobo with 3/4 inch 8-32 nylon machine screws rather than the pins which i am not adept at.  i bolt a fan to the rear of the case with a duct from the case toward the heat sink to remove the hot air from the case.
i would buy G.SKILL PI Black 4GB (2 x 2GB) 240-Pin DDR2 800 Dual Channel F2-6400CL4D-4GBPI-B today because they run at 1.8 volts, run at cas4 and have cooling fins.

---

### Post by dcstar on 2009-01-01
> **vgrisham said:**
> My motherboard is coming on 5 years old, and I think I'd like to upgrade it and get a new 64-bit processor. 

Would someone please recommend a good, new-ish 64-bit motherboard and processor? Which motherboard manufacturer is the most linux friendly? Does any manufacturer offer a Linux based tool with which to upgrade the bios? 

By the way, this is for a full-sized ATX tower.

If you want a cheaper option, go for something with an inbuilt Nvidia video chipset (which Linux supports well). Also make sure you have enough RAM slots for paired DDR2/3 modules as you get better data throughput with (identical) paired modules rather than single ones with AMD CPUs.

Other than that, don't go for any "bleeding edge" hardware as the Linux kernel may not yet support it and you may have to wait a few months for things to catch up.

---

### Post by dcstar on 2009-01-01
> **vgrisham said:**
> I've been on AMD64 for a long time. I didn't even know that Intel had 64-bit until recently. 

Are there advantages/disadvantages to AMD vs. Intel? Please educate me. (Don't go all KDE vs. Gnome though.)

AMD is not Intel - competition is good.......   :P

Seriously, if you want maximum performance just see what gives you the current best "bang for you buck" with CPU and motherboard costs.

AMD and Intel constantly leap-frog each other with CPU releases that offer better performance/cost benefits, so you may want to select whoever is in front of this race at the moment - or wait 6 months until the tables turn and go that way.

I have been using AMD stuff for many years now as they generally seem to offer better value and I have had no problems with reliability.

---

### Post by Kilz on 2009-01-01
> **dcstar said:**
> AMD is not Intel - competition is good.......   :P

excellent point

---

### Post by CJ56 on 2009-01-01
I've just built myself a new system using a Gigabyte mobo, I think it was a GA-M68SM-S2L - cost about £40, anyway - with an AMD Athlon 64x2 5400, 4Gb RAM from Crucial, plus an Nvidia 7300GT graphics card. It's running Ubuntu 8.04.1 64-bit

This is a fairly middle-of-the-road piece of kit, but it works really nicely for my (middle-of-the-road) purposes & was a breeze to set up. Ubuntu installed without any hiccups at all & is a pleasure to use. 

I don't know how much it helps that the mobo uses an Nvidia chipset, along with the Nvidia card, but it doesn't seem to have done any harm...

---

### Post by SkankinRatFink on 2009-01-02
> **tech9 said:**
> gigabyte motherboards are great. I have an AMD 64 CPU gigabyte
What model of Gigabyte motherboard do you have? I, too, am planning on jumping to 64-bit and I already have the AMD processor. If there was anything in particular you had to do to make the install go smoothly, I would love to hear that as well. Thanks!!

---

### Post by Kilz on 2009-01-02
I think this might be helpful. [I tried this board]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3939759&Sku=P450-9120") when building my brothers computer. I thought the onboard graphics would be a good thing and save a little cash that could be put to other things like a better processor.
The absolute worst mistake. The XFX GeForce 8200 Motherboard ranks in my mind a close second to a lexmark printer in things never to buy while running linux. after 2 days of head bashing I took it back and got an ASUS.

---

### Post by NewDisciple on 2009-01-07
Currently running Gigabyte EP45 UD3P motherboard
Wolfdale E8500 (Intel) processor
DuOrb CPU fan (hold down bracket-shortened to fit).
Geil Black Dragon (4x1GB) ram
Radeon HD3850 video card

Everything 64-bit runs great on this setup.

---

### Post by vgrisham on 2009-01-07
> **NewDisciple said:**
> Currently running Gigabyte EP45 UD3P motherboard
Wolfdale E8500 (Intel) processor
DuOrb CPU fan (hold down bracket-shortened to fit).
Geil Black Dragon (4x1GB) ram
Radeon HD3850 video card

Everything 64-bit runs great on this setup.

Thanks. It sounds like Gigabyte is becoming the defacto linux 64 motherboard manufacturer.

---

### Post by fanders on 2009-01-07
I am using an EVGA 750iFTW motherboard with an Intel quad 6600 and 8gb of Patriot Viper Extreme 1066 memory.  My video is an EVGA dual slot 8800gt. Works fine with 64bit Ubuntu.

Regards,

Frank

---

