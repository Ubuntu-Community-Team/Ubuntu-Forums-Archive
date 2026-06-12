---
title: "latest ker nel update = no throttling??"
date: 2006-09-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Lonthong on 2006-09-22
Is it just me or does anyone else feel it as well??
After latest kernel update, my laptop fan seems to spin louder.
Checked system monitor & one of the core (Turion X2) is always running 100% eventhough I did not do anything (just idle).
Rebooted to previous kernel & laptop is dead silent. each core is running about 5-10% only.

---

### Post by Lonthong on 2006-10-03
Update:
After recompiling the ATI kernel module, I have no more issue with one of the core always running at full load

In the past I also had similar issue, i.e. one of the core always running at 100% load when using amd64-k8-smp kernel.
Just now, I tried again installing latest amd64-k8-smp kernel. After rebooting one of the core was always running 100% load. 
Recompiled ATI kernel module and now both core are throttling correctly.
For now, I am going to use this kernel

---

