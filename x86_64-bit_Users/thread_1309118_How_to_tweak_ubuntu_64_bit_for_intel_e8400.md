---
title: "How to tweak ubuntu 64 bit for intel e8400"
date: 2009-11-01
forum: x86 64-bit Users
---

### Post by uitra on 2009-11-01
Is the stander ubuntu 9.10 desktop kernel optimized for intel dual core processors? or does the stock kernel have to sacrifice some performance tweaks for the sake of compatibility with older cpus?

Can on build a new kernel with better optimization for e8400?
Can on build packages from source with optimization for e8400?
(Or would that break the compatibility with the ubuntu 64 bit?)

I tried out gentoo, and wonder how much of those perforamce tweaks are possible within ubuntu. (optimization does work, just lock at the differences between i386 ubuntu 32 vs i586? ubuntu 64)

---

### Post by Yellow Pasque on 2009-11-01
> Can one build a new kernel with better optimization for e8400?
The generic 64-bit Ubuntu kernel is configured for a generic x86-64 CPU. The option is there in the kernel configuration to optimize for a specific CPU family (like Athlon/Opteron or Core2), but I'm not sure how much difference it would make. I personally would not bother rolling a kernel just to make that change.

> Can one build packages from source with optimization for e8400?
By default, Ubuntu64 packages are built with -O2 flag. Tweaking further probably won't yield significat gains, and may even slow you down in some cases.

---

### Post by uitra on 2009-11-01
Thank you for answering.

"By default, Ubuntu64 packages are built with -O2 flag."

But in gentoo you could also set in make.conf -march=native or something like that. When ubuntu packages are build with -02 flag they are also using generic amd64? and not using the full functionality of the specific processor like intel e8400?

I have build my first coustum kernel for ubuntu : ) 
Following the helpful documentation at : 

[https://help.ubuntu.com/community/CustomRestrictedModules](https://help.ubuntu.com/community/CustomRestrictedModules)

---

