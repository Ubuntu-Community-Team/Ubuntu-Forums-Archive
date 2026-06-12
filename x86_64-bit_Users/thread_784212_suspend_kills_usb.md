---
title: "suspend kills usb"
date: 2008-05-06
forum: x86 64-bit Users
---

### Post by MartinG on 2008-05-06
Using Kubuntu 8.04 on an ASRock ALiveNF7G-HD720p R5.0 motherboard, my computer will suspend to RAM fine (I'm not bothered about hibernation).  However, on "wake up" I have no USB.

I've tried removing and reloading usblp, ehci_hcd, ohci_hcd, but to no avail.  I've tried including the same in MODULES and/or MODULES_WHITELIST in /etc/acpi-support, I've tried installing the hibernate and/or uswsusp packages.  None of it works, the only way to get USB working again is to reboot :(

I suspect this is not a 64-bit specific problem, nor a KDE one, but let's start here ...

---

### Post by Calmor on 2008-05-29
> **MartinG said:**
> 
I suspect this is not a 64-bit specific problem, nor a KDE one, but let's start here ...

I'll second that it's not a KDE-specific problem.  Have you had any luck resolving the issue?

I'm running Ubuntu 8.04 64-bit on an HP dv2745se laptop, and have the same issues.  I didn't find out until I was using the laptop as a desktop this past weekend and was surprised to find that the usb keyboard and mouse were not responding at all after starting back up.  The built-in keyboard and touchpad functioned normally, which is probably why I never noticed before.

I believe the issue was present in the .16 kernel but it is definitely present in the .17 version.

Trying to see what is plugged in to the USB via lsusb causes a long delay after which it spits out four lines of zeros (not at that computer now to give an actual output).  I haven't had the time to try any other fixes at this point.

---

