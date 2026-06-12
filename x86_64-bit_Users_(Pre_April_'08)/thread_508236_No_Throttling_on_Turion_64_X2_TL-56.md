---
title: "No Throttling on Turion 64 X2 TL-56"
date: 2007-07-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by MrWonderful on 2007-07-24
I have an HP dv6449us and I cant get throttling to work on the processor. I've tried to modprobe powernow-k8 and i got:
```
FATAL: Error inserting powernow_k8 (/lib/modules/2.6.20-16-generic/kernel/arch/x86_64/kernel/cpufreq/powernow-k8.ko): No such device
```
I really want to get it going because the battery lasts only about an hour.

---

### Post by MrWonderful on 2007-07-24
I thought more information might be needed. I'm on feisty and here is my uname:
```
Linux NickLaptop 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64 GNU/Linux
```

---

### Post by varnav on 2007-08-04
Try installing "powernowd" package. Reboot after install.

---

