---
title: "Ubuntu on Dual core G5 Powermac"
date: 2005-12-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by borbzz on 2005-12-14
Hello,
First off, I have used Ubuntu since the project started and loved it on x86 machines.  I finally made the switch to a Mac, buying a new PowerMac 2.3GHz Dual-core G5. 

I am trying to install Ubuntu, and I'm running into problems. I have the PowerPC pressed CDs from Canonical, and neither the Live CD nor the Install CD boot properly.  I get as far as the bootloader--it asks me which version to boot up.  Regardless of what I choose (powerpc or powerpc64), the system freezes and locks up in a white OpenFirmware screen.  This happens while the bootloader is loading the kernel.

I've looked around the message board before I posted, but I can't resolve the problem.  Many say to use the "powerpc64" option, but that does not work.  Are the new G5's (PCI Express, Dual Core) supported in 5.10?  Thanks!

-Eric

---

### Post by joshuapurcell on 2005-12-17
I haven't tried installing Ubuntu on one of these machines, but I think I've found some information on your problem:
[http://ozlabs.org/pipermail/linuxppc64-dev/2005-May/004140.html](http://ozlabs.org/pipermail/linuxppc64-dev/2005-May/004140.html)

The above link says there is a bug in the open firmware device tree on the G5s that requires a patch to be loaded. Here is a link to a message from someone describing the problem they are having (which sounds like what you may be having):
[http://lists.penguinppc.org/yaboot-users/2005/yaboot-users-200506/msg00005.html](http://lists.penguinppc.org/yaboot-users/2005/yaboot-users-200506/msg00005.html)

---

### Post by Midnightbrewer on 2006-01-27
I'm having this exact same problem.  It'd be nice if the patch could be incorporated in a user-friendly format, however, rather than as source that I can't use simply by booting off of the CD.  How soon can something like this be included in the installer?

---

### Post by deteringb on 2006-01-27
[QUOTE=Midnightbrewer]I'm having this exact same problem.  It'd be nice if the patch could be incorporated in a user-friendly format, however, rather than as source that I can't use simply by booting off of the CD.  How soon can something like this be included in the installer?[/QUOTE]

I too have a dual 2.3 and got the white screen, and then booted off my Pismo (in Target Disk Mode) and it worked (at least it booted into Ubuntu).  Barely runs on the G5, runs beautifully on the Pismo.. Although Ubuntu runs on the g5 under Virtual PC just fine...

---

