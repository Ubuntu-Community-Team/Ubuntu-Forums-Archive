---
title: "Openoffice on Breezy freezes the desktop"
date: 2006-04-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by hardhu on 2006-04-21
Hello everybody,
I am running Kubuntu AMD64 on an Acer Aspire 5024 with a Turion64 Amd processor  and an Ati Radeon X700 as a grphic card. I have installed latest ati driver (8.24.8) using the howto at [http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide) and they seem to work correctly with other applications, and 3d acceleration is enabled.
However I have a problem when using Openoffice (the 1.9.129 version available in breezy amd64): after a random period of time it crashes freezing all the desktop, and I am forced to switch to the console to kill it from a shell to obtain again control on my x session.
After that, I can read this line in /var/log/Xorg.0.log:
EE) fglrx(0): === [R200DALSetControllerConfigForRemap] === CWDDC ControllerSetConfig failed: 6 - 0

I have googled a while but found no suggestions to solve this issue,  can anybody help me?
Or is it better to use the 32 bit version in a dapper chroot?

---

