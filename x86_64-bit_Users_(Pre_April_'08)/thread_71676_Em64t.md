---
title: "Em64t"
date: 2005-10-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by kb00heda on 2005-10-04
Hi,

Which kernel would you say works better om a Intel Pentium 4 660 EM64T? Is it the AMD64-generic, k8-SMP or -XEON?

I cannot see two CPU:s listed in /proc/cpuinfo, but I believe I should, since this CPU has Hyperthreading.

I'm confused! :(

Regards,
David

P.S. I posted a similar thread a couple of days ago, but probably in the wrong section. Sorry about that! D.S.

---

### Post by DancingSun on 2005-10-04
Hyperthreading is not dual core, so I don't think you should be seeing two CPUs. Hyperthreading only works when the software supports it.

That said, on the list you provided, I think AMD64-generic works best, unless you can find a EM64T optimized kernel somewhere. K8-smp and Xeon are for multi-processor systems so those shouldn't be used in your case.

---

### Post by flurdy on 2005-10-05
Hyperthreaded cpus shows up as multiple cpus. Well my xeons servers did anyway.

Ive install amd64 on celeron d emt64 enabled cpu, which means it is dual cored.
However I can't find anything to indicate the system is using this ability.

I am supprised there is no x86_64 smp kernel with ununtu , 
the x86_32 smp version has been around for ages.

Does anyone know if there is any inline for breezy or dapper?

Or do we need to kick Torvalds in the right direction for the kernel in general?

---

