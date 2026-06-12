---
title: "No K8 in kernel"
date: 2007-06-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by marios_geo on 2007-06-26
Hi, i have installed the kubuntu 7.10 (64 bit) version.
Allthough i have installed linux-kenrel-image-k8 through synaptic, whereer i type uname -a i see that i have the generic kernel. What am i doing wrong?

P.S.
I have installed also module, headers etc for the k8 version.
Even grub during boot, shows generic kernel.

---

### Post by david_2001 on 2007-06-26
There is only one kernel nowadays (ignoring the low latency and server kernels, of course).  The linux-image-k8 package is "only for upgrades" and will install the linux-image-generic kernel.

---

