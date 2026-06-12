---
title: "Wireless not working on Feisty/Gutsy"
date: 2007-10-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by stevechaloner on 2007-10-22
Hi,

I installed Feisty a while back, and more recently Gutsy, and neither of them seem to support my wireless network interface.  The interface just refuses to show up in the network manager, and isn't listed by iwconfig/ifconfig.

Hardware:
Medion MD96327 laptop
AMD Turion 64 X2
Atheros AR5007UG Wireless Network Adapter (internal USB)

I've also tried using ndiswrapper and the Vista 64 bit driver - it reports the hardware as present and the driver installed, but still no action.

I've tried using the Mandriva 2008 live CD and that picks up the network card fine, identifying it as a ZyDAS USB device using module zd1211rw.

Any help on this would be much appreciated!

Thanks,
Steve

---

### Post by kuja on 2007-11-01
I think the drivers for the Atheros cards are in the linux-restricted-modules-`uname -r`-generic package. Do you have it installed?

---

