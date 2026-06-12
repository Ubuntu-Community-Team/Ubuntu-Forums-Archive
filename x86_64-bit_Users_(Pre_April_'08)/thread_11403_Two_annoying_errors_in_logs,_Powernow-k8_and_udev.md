---
title: "Two annoying errors in logs, Powernow-k8 and udev"
date: 2005-01-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Eklöf on 2005-01-16
powernow-k8: transition frequency failed

localhost udev[3785]: creating device node '/dev/vcsa3'


I get those ALOT in my logs. Any ideas to why, and how to get it to work properly. 

/ jonas

---

### Post by jnoreiko on 2005-08-05
[QUOTE=Eklöf]powernow-k8: transition frequency failed[/QUOTE]

I'm seeing this one.
A trawl through a few Google results suggests it's to do with the linux kernel's lack of support for AMD's Cool n Quiet system.

I gather one solution is to turn it off in the BIOS. Another might be to update the kernel, but I have no idea how to do that.

---

### Post by hardw1re on 2005-08-20
i am getting the Powernow-k8 message too, i think the kernel to use is the one that ends in the amd64-k8, its quite easy to add a kernel to the system using the apt-get install feature.

in terms of the cool and quiet i have the completely disabled and still have these messages.

---

