---
title: "Kernel Problems With 7.10"
date: 2007-10-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mojosdad on 2007-10-27
Have upgraged to Gutsy and encountered several problems so far:
2.6.20.16 boots fine but will not use the restricted nvidia driver (X throws up error about modules not having matching version numbers).

2.6.22.14 failed to boot to desktop, which seemed to be an issue connected with how the swap partition was being referenced (changed FSTAB to use UUID, now seems to work). Nvidia restricted module seems to work. Unfortunately DMA cannot be turned on (get HDIO_SET_DMA failed: Operation not permitted message). Have tried to load AMD74xx  for NForce 3 chipset in /etc/modules, no difference.

Tried to recompile kernel with DMA support built-in. This will boot and DMA is set to 'on' by default. Unfortunately I obviously lose Nvidia support. Is it possible to recompile the restricted modules for custom kernel or will I have to install nVidia drivers from source.

Alternatively is it possible to recompile the Ubuntu kernel whilst maintaining the same version number in such a way that Ubuntu wouldn't realise it had been changed and would still pickup module from Synaptic? I notice that the version number of my custom kernel is 2.6.22.9, the source is 2.6.22, so why wasn't my kernel build 2.6.22.14-custom?

Have read the guides about kernel compilation (which is how I managed it in the first place) but I'm still umsure about how to proceed. Any help appreciated.

---

### Post by devzero on 2007-10-27
hi

you can forget the restriction-driversupport as I got told it here:
[http://ubuntuforums.org/showpost.php?p=3644569&postcount=94](http://ubuntuforums.org/showpost.php?p=3644569&postcount=94)

if you are lucky u might try envy and install the driver with it.
But as I tried to enable compiz and installed xgl, the xserver ate itself up
as u can read it here:
[http://ubuntuforums.org/showthread.php?t=593667](http://ubuntuforums.org/showthread.php?t=593667)

OK I got that thing run, read it here:
[http://ubuntuforums.org/showthread.php?t=594619](http://ubuntuforums.org/showthread.php?t=594619)

---

