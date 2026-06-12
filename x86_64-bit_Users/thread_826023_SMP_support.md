---
title: "SMP support"
date: 2008-06-11
forum: x86 64-bit Users
---

### Post by birdsong on 2008-06-11
Is SMP (pentium-D, dual-core, quad-core, etc.) only supported in 64-bit Ubuntu? or does it work on i386 installs also?

---

### Post by aaron.d on 2008-06-11
both.

you can check your kernel by issuing the command:

```
uname -a
```

---

### Post by Yellow Pasque on 2008-06-11
All of those chips support amd64/emt64 (save for the Pentium D 805 & 820) and you should use the 64-bit version if possible.

---

