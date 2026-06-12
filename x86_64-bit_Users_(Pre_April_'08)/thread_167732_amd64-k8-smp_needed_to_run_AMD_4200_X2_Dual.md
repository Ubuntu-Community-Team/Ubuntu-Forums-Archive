---
title: "amd64-k8-smp needed to run AMD 4200 X2 Dual ?"
date: 2006-04-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by TitanKing on 2006-04-29
Am I right in assuming that I need the amd64-k8-smp kernel to run the AMD 4200 X2 correctly ? I noticed that the X86_64 kernel only runs one CPU.

Thanks for any replies.

---

### Post by Sutekh on 2006-04-29
Yes thats correct, you will need the SMP kernel.  The default kernel does not support an AMD X2.

I think in Dapper (if you ever use it), that the AMD-K8 kernel is SMP enabled by default.

---

### Post by tseliot on 2006-04-30
[QUOTE=Sutekh]I think in Dapper (if you ever use it), that the AMD-K8 kernel is SMP enabled by default.[/QUOTE]
You're right:

```
 uname -a
Linux dapper 2.6.15-21-k7 #1 SMP PREEMPT Fri Apr 21 17:10:51 UTC 2006 i686 GNU/Linux
```

---

### Post by kaffeine on 2006-04-30
that is so good to know - now i see why there's no explicit SMP kernel in the Ubuntu repos! thanks sutekh and tseliot!

---

### Post by Sutekh on 2006-05-01
There is an explicit SMP kernel for Breezy, but not for Dapper. 

 - For Breezy;

[Ubuntu Packages - Breezy - linux-amd64-k8-smp](http://packages.ubuntu.com/breezy/base/linux-amd64-k8-smp)

 - This package installs the latest **linux-image-amd64-k8-smp** package, which is a different kernel image to the non SMP one.  One kernel for non SMP K8 processors, one for SMP K8 processors.


 - For Dapper;

[Ubuntu Packages - Dapper - linux-amd64-k8smp](http://packages.ubuntu.com/dapper/base/linux-amd64-k8-smp)

 - This package installs the latest **linux-image-amd64-k8** package, which is SMP enabled, so one kernel for all AMD64-K8's.

---

### Post by kaffeine on 2006-05-01
ah-ha...so that's why i had the amd64-k8-smp kernel when i was running breezy and was desperately looking for the same on Dapper. yet another confusion demystified - thanks again sutekh!

---

