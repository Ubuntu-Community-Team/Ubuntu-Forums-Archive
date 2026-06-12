---
title: "ati drivers on ppc"
date: 2006-03-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by qbic on 2006-03-09
how does one install the ati driver for ppc
```
sh ati-driver-installer-8.23.7-i386.run
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.23.7............................................. .............................................................................................. .............................................................................................. .............................................................................................. ..........................
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Detected configuration:
Architecture: ppc ()
X Server: Xorg 6.8.2
Architecture 'ppc' is not supported
Removing temporary directory: fglrx-install

```

---

### Post by calum on 2006-03-09
[QUOTE=qbic]how does one install the ati driver for ppc[/QUOTE]

Don't know what kind of card you're trying to install it for, but if it's a Radeon 9600 or newer I'm afraid you're out of luck... the only ATI drivers for those currently are binary-only, and they don't do a binary for PPC.  You'll have to make do with the generic "ati" driver, which works fine but doesn't support hardware acceleration.

---

### Post by ssam on 2006-03-09
the binary drivers from ati are x86 only. the opensource ati/radeon drivers are pretty good up to the r200 cards (graphics card version numbers confuse me).

what card do you have? what is currently to slow that you need the binary drivers?

---

### Post by amklinux on 2006-05-17
Hi. I'm not the same guy who made the first question :-), but I'm trying to solve a similar problem. I have a Rage 128 Pro in a G4-400 with 512MB of RAM, and video play is too slow. I'm using Breezy. Is there any option for me?

Thanks a lot.

amklinux

---

### Post by ssam on 2006-05-17
if you have a search through the forum i think there are some tricks for the rage 128. possibly enabling dri?

---

