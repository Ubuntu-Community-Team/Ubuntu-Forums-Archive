---
title: "ATI progress?"
date: 2006-02-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Blairboy on 2006-02-20
Ok, followed this guide [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584).  Now x still won't start up with the new drivers, but I got much more info than before.  Here's part of my xorg.log:


(WW) Ignoring request to load module GLcore
(WW) fglrx: No matching Device section for instance (BusID PCI:5:0:1) found
(EE) fglrx(0): Chipset 0x71c0 is not recognized
(EE) fglrx(0): PreInitConfig failed
SetVBEMode failed
(EE) fglrx(0): R200PreInit failed
(II) fglrx(0): === [R200PreInit] === end
(II) UnloadModule: "fglrx"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/X11R6/lib/modules/libvgahw.a
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found


Any ideas on how to fix it?

---

