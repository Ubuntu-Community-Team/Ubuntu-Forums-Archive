---
title: "kernel for 32-bit Opteron"
date: 2007-05-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by pbeeson on 2007-05-05
We are running Opteron machines that must be in 32-bit mode.  these are also multiprocessor machines.

I've searched everywhere to try to find out if there is an advantage to using linux-image-686-smp over linux-image-k7-smp when using an Opteron in 32-bit mode.  I get conflicting and vague info from all searches I've tried.

---

### Post by cmost on 2007-05-05
Though I cannot speak to your specific processors, I do know that it's always better to run a kernel image that is the most tailored to your processor.  Therefore, it follows that the K7 kernel image would be more optimized on your system than the more generic 686.  You should be aware that in Feisty, there is only one kernel and that's generic.  It is suitable for all processor variants without having to maintain specific kernels for specific processor types.  Hope this helps.

---

### Post by pbeeson on 2007-05-05
For other reasons, we are running Dapper, so there is no generic kernel package.

57 is optimzied for 32-bit AMD Athlon processors.  What little I did read seemed to indicated that code optimzed for the k7 kernels might not be optimzed for the k8 processors running in 32-bit mode.

But, this information is untrustworthy, which is why I posted this thread.

---

