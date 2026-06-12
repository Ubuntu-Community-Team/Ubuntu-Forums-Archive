---
title: "Unable to run Doom3"
date: 2008-11-22
forum: x86 64-bit Users
---

### Post by widggman on 2008-11-22
Hi.. I'm new on Ubuntu with a new machine.

I have a quad-core 64bits with a GeForce 9800GTX. The driver for the video card is installed and everything looks fine.

I install doom 3 and I'm not able to run it. It fails at these place:
----- R_InitOpenGL -----
Setup X display connection
dlopen(libGL.so.1)
Segmentation fault

thank in advance

---

### Post by widggman on 2008-11-22
More information... I installed all the 32bits libraries needed.

---

### Post by soxs on 2008-11-23
output from (plx):
```
glxinfo|grep direct
```

---

### Post by widggman on 2008-11-23
it says "Yes"... and everything works now.

---

