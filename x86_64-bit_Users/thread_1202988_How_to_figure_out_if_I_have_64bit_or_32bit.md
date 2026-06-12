---
title: "How to figure out if I have 64bit or 32bit"
date: 2009-07-02
forum: x86 64-bit Users
---

### Post by Sims12345 on 2009-07-02
Hi,

I was wondering if there was a way to figure out which version of Ubuntu I was running (32bit or 64bit)?

Thanks

---

### Post by merlinus on 2009-07-02
```
uname -a
```

---

### Post by philcamlin on 2009-07-02
uname -a

edit: bah you beat be to it :P

---

### Post by AcousticRand on 2009-07-02
Some posts said to use the command: arch, but I guess that is deprecated, they now say to use the command: uname -m, and that should give you the architecture type.  I believe if you don't see x86_64 or the number 64 in the output, you are most likely running 32bit.

---

### Post by Sims12345 on 2009-07-02
Thanks very much!

---

