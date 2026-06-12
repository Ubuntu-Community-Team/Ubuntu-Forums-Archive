---
title: "Preventing kernel update"
date: 2007-01-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by loftwyr on 2007-01-06
I have a new install of Edgy on an Acer Aspire 5050.  With the installation, it works fine but when the kernel security update (10.34) gets installed, it no longer boots.  Kernel panic from the ide driver.

I have figured out how to back out the update but how do I prevent it from being installed again?  As soon as I back it out and reboot, it shows up as an update in the update manager.

I'd like to prevent this update from being applied but I don't know how to blacklist it.

Help?

---

### Post by xopher on 2007-01-06
You could use synaptic and the feature 'force version'. Right click on the package you want not to update, then press force version, if I recall correctly that is.. There you can choose which version you want to keep.

---

### Post by loftwyr on 2007-01-06
That helped but didn't remove the security update from the list.  Is there anyway to tell synaptic (or apt) to ignore it altogether?

---

