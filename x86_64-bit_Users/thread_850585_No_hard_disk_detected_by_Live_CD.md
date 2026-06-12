---
title: "No hard disk detected by Live CD"
date: 2008-07-05
forum: x86 64-bit Users
---

### Post by CJScully on 2008-07-05
I downloaded the ISO for the Live CD of the AMD 64 version of Hardy and checked it for errors before burning the CD.  When I boot the CD everything seems to be fine until I look for my hard disk.  It's not there!

I had a the x86 version of Gutsy installed on my system for some time on a separate partition and was intending to do a fresh install from the Live CD.  My disk is a pretty vanilla (and not that old) Western Digital IDE drive - model WD2500JB.  It works for everything else, Windows, Gutsy, just not the Live CD.

Chris

---

### Post by Yellow Pasque on 2008-07-05
What tools/commands have you used to make this assertion?
Try these:
```
sudo fdisk -l
sudo lshw -C disk
ls -la /dev/disk/by-uuid
gksudo gparted
```

EDIT: Does the BIOS recognize the hard disk? Are you using a (non-rounded) 80-pin IDE cable without any sharp bends in it? Do you have the disk jumpered for Master (in case the cable doesn't support Cable Select?)

---

### Post by soxs on 2008-07-06
maybe download the alternate hard AMD64 cd and try ttaht one?

---

### Post by CJScully on 2008-07-13
> **Temüjin said:**
> What tools/commands have you used to make this assertion?


Well, excuse me for thinking that it should actually work when you pop the CD in the tray and boot it up!  Gutsy did.  Seems like Hardy should too.  But maybe I'm just such a tyro that I'm making an unreasonable assumption.

The disk is visible in the bios.  Windows boots fine from that disk.  Gutsy used to boot from that disk until the upgrade to hardy failed.  I then downloaded the live CD to attempt a fresh in stall and when I boot to the CD there are no hard disks detected or available.

I have since downloaded the alternate CD and had the same problem with that.  Only at least with that CD it gives me an option to choose disk drivers for my system.  I have not gone through and tried all of them but I did add the boot option all_generic_ide.  That did not work either.  

I am running an Intel 6420 CPU on a ECS PT690T-A motherboard with 2GB of RAM.  As I said this config worked fine with the previous version of Ubuntu and still works fine with Windows XP.  Therefore logic would dictate that the problem does not lie with my system or its configuration but with this release of Ubuntu and its installation routines.

---

### Post by Neo0351 on 2008-07-13
its probably something in the kernel was marked or not marked.  in my case the default kernel has the PCI_MSI option marked and it wouldn't route my IRQ properly and none of my SATA drives were recognized.  so i recompiled the kernel and now it works.  unfortunately i dont think u can do this until after u have installed.  but u might want to try all three for ur boot options.
```
all_generic_ide floppy=off irqpoll
```

---

### Post by charlesbw on 2008-07-14
i am facing this same problem.  except that i don't have a very intimate understanding of hardware kernels like most linux users.

---

### Post by Neo0351 on 2008-07-14
yeah, i understand, did u try all three boot options i gave u?  if they work, you can add them to ur grub and u dont have to rebuild ur kernel.  i did cause i was bored.

---

### Post by CJScully on 2008-08-20
I finally got around to trying the boot options given above.  They didn't work.  I downloaded the alternate CD and tried to do the install from that.  The nice thing about that CD is it gives more information and options to try to troubleshoot the problem.  When no disks were detected it gave a rather long list of drivers and asked me to select the appropriate driver for my system.  I didn't know which driver was appropriate so I decided to try each one until I found one that worked.  Unfortunately none of them did.
My system has a Via chipset with a PT890 northbridge and a VT8237A southbridge.  It seems that suppport for this chipset was dropped with this release even though it was included in the previous release.  Is there a way to use the driver from 7.10 or am I just out of luck?

---

### Post by philinux on 2008-08-20
I'd give the intrepid alpha 4 live cd a go.

[http://cdimage.ubuntu.com/releases/intrepid/alpha-4/](http://cdimage.ubuntu.com/releases/intrepid/alpha-4/)

Or the gutsy live cd.

---

### Post by CJScully on 2008-08-20
Intrepid live CD wouldn't run at all on my system.  I guess it's back to Gutsy or forget about Ubuntu broader driver support is available.

---

