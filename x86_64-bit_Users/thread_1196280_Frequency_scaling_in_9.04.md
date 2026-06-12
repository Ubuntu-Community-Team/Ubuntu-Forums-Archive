---
title: "Frequency scaling in 9.04"
date: 2009-06-24
forum: x86 64-bit Users
---

### Post by linuxpenguin on 2009-06-24
I can't seem to get frequency scaling to work at all in Ubuntu 9.04 (x86-64).  I have installed cpufrequtils, sysfsutils, etc - but I still can't actually set my CPU frequency!

It seems that the AMD module is gone - what do I do now?
```
root@darkwing:~# modprobe powernow-k8
FATAL: Module powernow_k8 not found.
root@darkwing:~# modprobe powernow-k10
FATAL: Module powernow_k10 not found.

```
Is there another module I should be using instead?
*EDIT: D'oh!  Now I rebooted, and it's working.  Nevermind. . .*

---

