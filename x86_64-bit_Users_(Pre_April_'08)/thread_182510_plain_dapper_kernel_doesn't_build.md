---
title: "plain dapper kernel doesn't build?"
date: 2006-05-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by robsta on 2006-05-26
Hi, 

i tried to rebuild the dapper kernel from the original ubuntu sources for later modification, but even a plain rebuild bailed:

  LD      .tmp_vmlinux1
drivers/built-in.o: In function `pmac_wakeup_devices':via-pmu.c:(.text+0x8b320): undefined reference to `pmac_pfunc_base_resume'
drivers/built-in.o: In function `pmac_suspend_devices':via-pmu.c:(.text+0x8bf28): undefined reference to `pmac_pfunc_base_suspend'

Followed [https://wiki.ubuntu.com/KernelBuildPPCHowTo](https://wiki.ubuntu.com/KernelBuildPPCHowTo) to the point but to no avail. Thanks for any advice.

Best, 
Rob

---

### Post by robsta on 2006-05-28
For some reason downloading the dsc, orig tarball, diff and bulding that doesn't show that problem. If anyone's interested in a dapper kernel with atyfixes[1] let me know.

[http://stampflee.com/kernel/index.shtml](http://stampflee.com/kernel/index.shtml)

---

