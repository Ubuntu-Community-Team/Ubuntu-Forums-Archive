---
title: "Problem with shutdown and keyboard"
date: 2006-12-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by lusis89 on 2006-12-13
I have a problem shutting down my Ubuntu6.10 64bit edition
I have not special hardware, I tried to disable APIC (but not successfully), I have a "Pentium 4 3.0GHz HT" CPU,

Neither my ubuntu neither kubuntu shuts down (appears an X-like pattern on the screen, --not grey but yellow--), the keyboard freezes up about 2 minutes after login, unless I am root.

Also the monitor insists to stand-by if I don't move the mouse...

I have this problem with Ubuntu 6.10, KUbuntu 6.10 note that these are both x86_64 distros, since x386 distros does not install (the installer cannot locate the CD/DVD.... terrible...).

My motherboard, probably the cause of all problems, is an ASRock ... dual-VSTA. (VSTA sounds like "vista", maybe it contains a Chip-Fritz that confuses the Linux Kernel?)](*,) ](*,) ](*,)

---

### Post by lusis89 on 2006-12-13
Booting in safe mode works well.

APIC=off
IDE=nodma ([-( ... very slow...)
APPEND=showopts
EDD=off
VGAMODE=normal

also keyboard delay problem has been resolved....

---

