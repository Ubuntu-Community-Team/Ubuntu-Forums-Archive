---
title: "&quot;this is not an amd64 machine&quot; when trying to build kernel"
date: 2007-03-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by edyson on 2007-03-16
I'm running dapper on a dual opeteron 248 machine. I grabbed the latest kernel:
sudo apt-get install linux-source-2.6.15
and ran make menuconfig as usual. But when I go to pick the processor, i get this eerie message:

```

Processor family (AMD-Opteron/Athlon64)  --->
(This is not an amd64 machine. Please install the i386 distribution of Ubuntu.) Message for booting on non-x86_64 machine (32-bit) 
```

What gives?

---

### Post by vnbuddy2002 on 2007-03-17
That's weird, which release are you using ? i386 or amd64 ? if you are using amd64, remember to do the magic command "make oldconfig" before you try to do anything else.

---

