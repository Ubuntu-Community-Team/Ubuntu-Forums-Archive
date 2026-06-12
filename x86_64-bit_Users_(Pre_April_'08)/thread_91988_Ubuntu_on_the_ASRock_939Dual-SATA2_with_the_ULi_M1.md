---
title: "Ubuntu on the ASRock 939Dual-SATA2 with the ULi M1695 chipset?"
date: 2005-11-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Hercynium on 2005-11-18
I'm ready to finally upgrade my aging 5-year-old system and go with a shiny new AMD Athlon 64 (Probably a 3200+ Venice E6 -- cheap, low heat, low power, great overclocking potiential)

However, I don't want to get stuck with a socket 939 if the socket M2 becomes the best upgrade option. (And I'm not waiting another year for an M2 system...)

So, as you can see, the ASRock 939Dual-SATA2 with it's processor-slot upgrade socket seems like the perfect match! However, I can't find any other info on Linux compatibility with this or any other board with the ULi M1695 chipset.

:razz: My question is: What is everybody's general opinion on this board, regarding usability w/ linux. I don't care about performance, just compatibility and stability. My initial scans of the forums here make me optimistic, I guess I just want one last reassurance before I buy.

:KS BTW, If it requires some patching or custom config... I can do that, and even package it for others... but it *MUST* be stable!!!

---

### Post by casper_2095 on 2005-11-19
If it *must* be stable... seems like a no-brainer to resist that must-have-latest-and-greatest urge and settle for something less bleeding edge and... more stable :-) 

You just needed someone to help fight that urge out loud, right?  939 will be around for a while.

---

### Post by Hercynium on 2005-11-22
Thanks Casper, that was like getting a bucket of iced water dumped on my head. (I agree: bleeding edge usually causes, um, bleeding)

BUT... I went ahead and bought the parts anyway. Since this system will be primarily for a DVD conversion/production business I'm starting, I'll probably be forced to use Windows, at least until I find some really good linux-based video clean-up and authoring software. All the stuff I've read shows no stability problems w/windows (even when overclocking!)

Uli used to be Ali - remember them? They had some great AMD K6 and K7 chipsets back in the day.

Of course, I'll post a full update on how well this system works in Linux. (Specs, performance, stability, the works)

---

### Post by bioorganic on 2005-11-22
I've been using the ASRock 939Dual w/ Ubuntu 5.10 x86_64 and haven't run into any problems or lockups yet.  Everything seems to be recognized and working properly.  The setup is as follows:

ASRock 939Dual
AthlonX2 3800+
6800GT AGP version
WDRaptor SATA I hard-drive

I haven't tried the setup w/ a PCI-E graphics card or a SATA-II hard-drive so I can't comment on their compatability/stability.

---

### Post by crypto178 on 2005-11-22
The only "problem" for me was the integrated network thing not working out of the box (I didn't bother tweaking it, I had some unused network cards laying around).

---

### Post by RayG on 2005-11-23
I am using the same board with an Athlon 64 3000+ processor, ATI radeon 7000 video card, and 80GB Western Digital hard drive with an existing Hoary install on it. 

On booting for the first time, the boot process stuck at "Loading Stage 1.5   Please wait".  This looks like the LBA bug that I hit when installing Hoary. I solved that last time by setting the drive's Block Mode entry in the BIOS from Auto to LBA. Unfortunately the ASRock 939Dual motherboard has a BIOS that has only Auto and Disabled settings for block mode. I booted the system from another distro's install disk and tried reinstalling GRUB to the MBR of hda, to no avail. 

I installed Breezy over top of Hoary, but Breezy would not boot to complete the install because it could not reboot. I rebooted from a different disk, specifying the Breezy partition as root. The install completed, but the GRUB problem remains. Reinstalling GRUB from the command line under Breeze changed nothing.

This problem may be due to my combination of hardware, not the ASRock board in general, but buyer beware anyway.

RayG

---

### Post by vansouza on 2005-11-23
I can not get Ubuntu to see my SATA hard drive on my HP a1250n.  Any suggestions would be most welcomed.

---

### Post by psusi on 2005-11-24
If you are going to be setting up a sata raid and want to dual boot with windows, then you should read my fakeraid howto:

[https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)

---

