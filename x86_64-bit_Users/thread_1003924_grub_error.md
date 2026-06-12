---
title: "grub error"
date: 2008-12-06
forum: x86 64-bit Users
---

### Post by Richard-g8jvm on 2008-12-06
Hi All
being the approaching silly season , I decided to build a machine for a member of the family.
Celeron 1200, Abit A-N68SV mobo, using an IDE Maxtor 160GB HD.

I know the HD is OK I've checked on my main machine.
Every time I try to load 8.10 It goes all the way through the full install,
then fails to boot with a Grub error, doesnt say which one either.
I know the load is OK as I disconnected the IDE DVD drives off this machine 
and connected the HD just loaded for about the upmteenth time on the new machine, and it boots up without any problem

The Abit mobo has facilities for only one IDE master and slave and 4 SATA drives, before I go and buy a SATA HD , any ideas what I can try.

I'm using the advance option when I askes where to put the boot loader, the default is Hd0,0. not much good when it get treat as a scsi and given sd1.. 


any ideas please


thanks 

Richard

---

### Post by caljohnsmith on 2008-12-06
If you use the advanced button and have Grub installed to (hd0,0), that is the boot sector of the sda1 partition; if you want to boot the drive with Grub, you should install Grub to the MBR (Master Boot Record) by using /dev/sda or whichever is the drive you are installing Ubuntu to. Can you set your BIOS to boot the Ubuntu drive directly on start up, or do you have to boot another drive? If you can boot the Ubuntu drive, just have the installer put Grub in the MBR of the Ubuntu drive, and you should be all set. How about trying that and let me know how it goes.

---

### Post by Richard-g8jvm on 2008-12-06
Well as I pointed out for some reason the default is hd0,0, I've tied both
sd1 and the logical first drive which should be the same.
If I unplug the SATA drive from this machine it boots that up OK, and if I take the IDE drive from the new machine and plug it in here it boots up OK.

That ABIT Mobo is getting returned to the dealer on Monday as as far as I'm concerned its not fit for purpose especially as the onboard graphics is restricted to 800 x 600 .
I suspect whats happening with the IDE drive is its being treated as a RAID device, that mobo has the capability of using 4 x SATA and as a RAID controller it wont look at the mbr.


That Mobo is real cheap and nasty

---

### Post by John Jason Jordan on 2008-12-06
> **Richard-g8jvm said:**
> That Mobo is real cheap and nasty

About a year and a half ago I built myself a new desktop computer with an Abit motherboard. It sort of worked and I could install Ubuntu, but I wanted a RAID1 setup with mdadm. Nothing but errors. I struggled for weeks blaming madadm and everything under the sun. Finally a local Linux guru who works for a large local company and maintains/builds their computers for them told me "Abit motherboards are evil."

I took it back to the dealer and paid a few bucks more for an Asus. The Asus is worth the extra money just because it has extra SATA connectors, an e-SATA connector, and lots more goodies. It has been flawless.

So I have to say that your decision to return the Abit is probably a good one.

---

