---
title: "soundcard irq"
date: 2006-05-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by dafyddhughes on 2006-05-29
Hi Folks

Sorry if this question is a bit dumb, but I'm sorta new to the guts of linux and this is my first attempt at kernel-building.

I've built the 2.6.15 kernel in dapper with ingo molnar's realtime patch, but performance isn't significantly better.  A bit of research turns up that I can improve things by setting irq priorities - give the soundcard a higher priority than anything else.  Problem is, I don't know what my soundcard's irq is.  Here's the output of cat /proc/interrupts:

root@monster:~# cat /proc/interrupts
           CPU0
  1:        791   MPIC 1    Edge      PMac Output
  2:          0   MPIC 1    Edge      PMac Input
 24:     241200   MPIC 1    Level     ide1
 25:     599994   MPIC 1    Level     VIA-PMU
 26:        109   MPIC 1    Level     keywest i2c
 27:    2770705   MPIC 1    Level     ohci_hcd:usb1
 28:      99791   MPIC 1    Level     ohci_hcd:usb2
 29:          0   MPIC 1    Level     ohci_hcd:usb3
 39:     112144   MPIC 1    Level     ide0
 40:          2   MPIC 1    Level     ohci1394
 42:          0   MPIC 1    Level     keywest i2c
 47:      22401   MPIC 1    Level     GPIO1 ADB
 52:      97329   MPIC 1    Level     bcm43xx
 61:          0   MPIC 1    Edge      Sound Headphone Detection
BAD:          0

Can anybody tell me which of these is my soundcard?

This is a g4 powerbook 867.

Thanks for anny help.

cheers
dafydd

---

