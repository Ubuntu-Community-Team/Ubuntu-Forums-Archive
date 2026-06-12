---
title: "VLC does HW-acceleration without NVIDIA-drivers?"
date: 2005-12-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by phibxr on 2005-12-12
I've noticed that VLC plays video exceptionally well even though NVIDIA refuses to compile their drivers for Linux/PPC, and that so on a 700MHz iMac. How is this implemented, and why isn't it implemented in X (or is it?)?.

---

### Post by Viro on 2005-12-12
The nVidia drivers are only for 3D acceleration. Most of the usual 2D stuff is supported directly by X. That, and the fact that VLC has some nifty altivec optimizations means that it should play most videos well.

---

