---
title: "nvidia-glx broken again?"
date: 2007-04-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by kuja on 2007-04-17
Feisty is slated for release on thursday, and it seems the latest kernel update from yesterday or the day before or some such, has broken nvidia-glx yet again. Bummer!!

Backtrace:
0: /usr/bin/X11/X(xf86SigHandler+0x6d) [0x48282d]
1: /lib/libc.so.6 [0x2ba611a3ed40]

Fatal server error:
Caught signal 11.  Server aborting

---

### Post by RealityMaster on 2007-04-17
Try nvidia-glx-new, worked for me.

---

### Post by kuja on 2007-04-17
Didn't for me ....

---

