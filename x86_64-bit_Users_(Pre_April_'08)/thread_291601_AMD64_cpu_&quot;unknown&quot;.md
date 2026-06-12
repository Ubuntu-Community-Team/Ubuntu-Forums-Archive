---
title: "AMD64 cpu &quot;unknown&quot;"
date: 2006-11-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by cogitordi on 2006-11-02
Here's what uname in Edgy Eft shows me:

2.6.17-10-generic #2 SMP Fri Oct 13 15:34:39 UTC 2006 x86_64 GNU/Linux

ubuntu:~$ uname -p
unknown

Under Dapper, the kernel was shown as AMD64.

Does this indicate a problem with my Edgy installation?

---

### Post by kam0t3 on 2006-11-02
i got the same result from "unmane -p". im using a sempron 2600+ run Ubuntu 6.10 64bit. i thing ubuntu cd installed the generic version of the kernel. also i'm havinf problem with splash screen but othern than that, everything AOK.

---

### Post by magick.crow on 2006-11-02
Look at the kernel options you have!! Edgy does not have an amd64 or smp kernel to pick from!! It is all one kernel. I don't know why but would love to know what is going on and how much speed we are loosing because of this!
Douglas

---

### Post by kuja on 2006-11-02
Shouldn't be a problem. Most of the uname things show as unknown for me and everything works just fine.

---

### Post by kuja on 2006-11-02
> **magick.crow said:**
> Look at the kernel options you have!! Edgy does not have an amd64 or smp kernel to pick from!! It is all one kernel. I don't know why but would love to know what is going on and how much speed we are loosing because of this!
Douglas

Ubuntu has dropped from supporting 10+ kernels, to half that or less. There is now 1 kernel per architecture with the exception of the x86, which has two (an i386 kernel(provided for maximum compatibility), and a generic kernel). Reducing the amount of kernels Ubuntu has to build and support reduces compatibility problems, and gives the Ubuntu devs more time to work on other stuff.

The generic kernels include SMP support, and performance loss by using the generic kernel (as opposed to say, a k8 kernel) is negligible.

---

### Post by photorealistic beaver on 2006-11-02
> **cogitordi said:**
> Here's what uname in Edgy Eft shows me:

2.6.17-10-generic #2 SMP Fri Oct 13 15:34:39 UTC 2006 x86_64 GNU/Linux

ubuntu:~$ uname -p
unknown

Under Dapper, the kernel was shown as AMD64.

Does this indicate a problem with my Edgy installation?

i have a pentium d930 with EMT64 and is the same.

---

### Post by almalaci on 2006-11-04
I use edgy on a Presario M2000Z with a turion CPU. I'm afraid that not having an amd64-specific kernel can not only result in a CPU speed issue but there can be many other possible bugs than that, for instance a buggy power-management I have with edgy that I didn't have with dapper. Could someone confirm if I'm right?

---

### Post by kuja on 2006-11-05
almalaci, I'm _quite_ sure that the problem is related to something other than the tiny optimizations that the kernel was (or was not) built with. I however, have heard that the power management in Ubuntu needs work. I have also heard that the power management in Kubuntu works well. That should give you somewhere to look for the real source of your problem.

---

### Post by almalaci on 2006-11-05
My special laptop control buttons haven't yet worked under kde (kubuntu, suse)and I much prefer ubuntu's gnome design. I will try kubuntu though and also a 32-bit install.
Thanks a lot for the info!

---

