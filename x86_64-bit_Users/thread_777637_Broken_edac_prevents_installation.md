---
title: "Broken edac prevents installation"
date: 2008-05-01
forum: x86 64-bit Users
---

### Post by thowland on 2008-05-01
Looks like there's something wrong with the EDAC module in 2.6.24 and later; when modprobe loads it, my machine instantly hangs.

I've been able to get around this by blacklisting mc_edac and i5000_edac under fedora, but I can't boot Ubuntu 8.0.4 as a live CD or installer.

(I added modprobedebug to the grub options, and the system hangs immediately after "EDAC MC: Ver: 2.1.0 Apr 10 2008"

The only option I can see is to go back to 7 and do a distribution upgrade through synaptic, then blacklisting the module prior to restarting.

Is there a way to tell the kernel not to load a particular module from grub? Since it's a CD I don't see any other way to prevent this from happening...

My system is running on a supermicro x7daL-e motherboard, bios version 2.0b. There doesn't seem to be any way to disable ECC from the bios that I could see.

Any thoughts would be appreciated-

Tim

---

### Post by thowland on 2008-05-01
I've tried passing edac_mc.blacklist=yes on the kernel arguments line in grub, but the installer still loads EDAC and crashes.

---

