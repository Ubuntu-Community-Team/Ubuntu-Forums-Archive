---
title: "Qemu"
date: 2005-12-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by FluffyElmo on 2005-12-21
I'm trying to compile Qemu and not having much luck. I need vmdk format support, so the version in the repositories doesn't cut it. 

I've tried 0.7.2 and 0.8.0 with gcc-3.3 and gcc-3.4 but I always get the following error:
```

for d in x86_64-softmmu; do \
make -C $d all || exit 1 ; \
        done
make: *** x86_64-softmmu: No such file or directory.  Stop.
make: *** [all] Error 1
```

I use the configure parameters *./configure --target-list=x86_64-softmmu*.

Any help greatly appreciated.

---

### Post by daschl on 2005-12-22
the 0.7 version is in the apt-repository so if you install this i think you have all the dependencies you need

try this, and then you can upgrade (hopefully ;))

---

