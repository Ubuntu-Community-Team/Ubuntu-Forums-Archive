---
title: "Linx32 Bit applications"
date: 2005-03-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by artimess on 2005-03-04
Mandarake has a command called linx32rpm which builds 32 bit applications for their x86_64 platform.
Can someone build a similair utility for ubuntu x86_64 user community?
It is a shame for such a wonderful distribution as ubuntu not to have an easy way of building and running 32bit application on x86_64.

Artimess

---

### Post by AndersAA on 2005-03-04
Well to build a 32bit application you need gcc 3.4 or higher, and compile with -m32.

I've been trying to do it with wine-cvs, failing, because ubuntu doesn't have as many 32bit libs as most other 64bit distro's yet.

---

