---
title: "AMD 64 ACPI errors - Help"
date: 2006-08-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by linuxun on 2006-08-04
Hello everyone,

Built a barebones to use as a Ubuntu server:
MSI RX480 Neo2 K8 S939 AMD Athlon 64 mobo
CPU AMD Sempron 3000+ 1.8ghz socket 939

The errors that are occurring are the same for the following discs:
Ubuntu 6.06 Desktop
Ubuntu 6.06 Desktop 64
Ubuntu 6.06 Alternate 64
Ubuntu 5.1 and etc... so everything I've tried.
MD5's checked on all okay.

**In BIOS with ACPI turned OFF then booting from CD**:
Decompressing the kernel.
Booting the kernel.
[COLOR="DarkRed"][B]ACPI: Unable to locate RSDP
MP-BIOS bug: 8254 timer not connected to IO-APIC[/B][/COLOR]

**In BIOS with ACPI turned ON then booting from CD**:
Decompressing the kernel.
Booting the kernel.
[COLOR="DarkRed"]**ACPI: Unable to load the system description tables**[/COLOR]

And in both cases it freezes right there.
Just for grins I also tried swapping out the CD and HDD's.
Same errors.

I'm at a loss on what's going on here.  It seems it's with power management.

I haven't been able to find a list of CD boot codes, but through the forums I have tried all of the following.
**noacip, nolacip, noaicp, nolaicp, acip=off, aicp=off, noapm, apm=off**
Using them still results in the same two errors.

Also tried Mepis and Slack and they both freeze after they try to release unused kernel memory right after their boot cd's start their installs.

Not sure what else to try or exactly what these ACPI errors are complaining about.
Any help would be appreciated.  I sure don't want to have to use M$.

---

