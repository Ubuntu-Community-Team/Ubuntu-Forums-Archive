---
title: "difference between amd64-generic and amd64-k8?"
date: 2005-12-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by darkpark on 2005-12-09
Ubuntu 5.10 AMD64 by default install the amd64-generic kernel but there is also an amd64-k8 kernel on the CD.   What is the difference between those two, if any?

---

### Post by arjaybe on 2005-12-10
[QUOTE=darkpark]Ubuntu 5.10 AMD64 by default install the amd64-generic kernel but there is also an amd64-k8 kernel on the CD.   What is the difference between those two, if any?[/QUOTE]

I have both Ubuntu and Kubuntu Breezy.  Ubuntu has the generic kernel and Kubuntu has the k8 kernel.  Could it be that simple?

---

### Post by rplantz on 2005-12-10
I found
> 
The generic one should run on any amd64/x86_64 cpu, including
those from intel.  It's mainly used by the installer.

There are several different kernels:
kernel-image-2.6-amd64-generic
kernel-image-2.6-amd64-k8
kernel-image-2.6-amd64-k8-smp
kernel-image-2.6-em64t-p4
kernel-image-2.6-em64t-p4-smp

K8* are for special for chips from amd, em64t* are for those
from intel.  The smp versions are in case you have multiple CPUs.

at [http://www.x86-64.org/lists/discuss/msg07547.html](http://www.x86-64.org/lists/discuss/msg07547.html)

I'm running
```

bob@robert:~$ uname -r
2.6.12-10-amd64-k8
bob@robert:~$

```
and it works fine with both gnome and xfce. (Haven't tried kde.)

---

### Post by darkpark on 2005-12-10
[QUOTE=arjaybe]I have both Ubuntu and Kubuntu Breezy.  Ubuntu has the generic kernel and Kubuntu has the k8 kernel.  Could it be that simple?[/QUOTE]

that isn't true.  ubuntu breezy has the amd64-k8 driver too but the generic one is installed by default.

what i was wondering is whether the k8 kernel offers any additional benefits over the generic kernel when running an AMD 64bit processor.  

i have an AMD Athlon 64bit 3500+ processor.

---

### Post by Ribs on 2005-12-10
[QUOTE=darkpark]what i was wondering is whether the k8 kernel offers any additional benefits over the generic kernel when running an AMD 64bit processor.  

i have an AMD Athlon 64bit 3500+ processor.[/QUOTE]

Yes, the whole system should feel a bit quicker. Install the k8 version if you can...

---

### Post by MighMoS on 2005-12-10
I thought the k8 was special for amd64, while -generic would be for any 64 bit processor?  The difference between a 686 (generic) and an athlon-xp (-k7) I think.

---

### Post by rplantz on 2005-12-10
[QUOTE=MighMoS]I thought the k8 was special for amd64, while -generic would be for any 64 bit processor?  The difference between a 686 (generic) and an athlon-xp (-k7) I think.[/QUOTE]

Not quite "any." For example, there must be a different kernel for PowerPC.

I think that the generic will run on either an AMD or an Intel processor that supports the amd64 (or Intel x86-64) instruction set architecture (ISA). Note that the Itanium uses ia64, which is quite different.

I assume that the k8 kernel is compiled with the -mtune=k8 option. The gcc man page says ```

     k8, opteron, athlon64, athlon-fx
          AMD K8 core based CPUs with x86-64 instruction set support.
          (This supersets MMX, SSE, SSE2, 3dNOW!, enhanced 3dNOW!
          and 64-bit instruction set extensions.)

```

The internal Intel implementation of the x86-64 ISA differs from AMD's. Presumably, the k8 tuning causes the compiler to generate code that runs faster on the AMD implementation.

Whether you would see any difference in your everyday usage depends on what you are doing. I'm pretty sure that I've more time writing this response than I am saving by running k8.  :-)

---

### Post by scruffy on 2005-12-12
[QUOTE=Ribs]Yes, the whole system should feel a bit quicker. Install the k8 version if you can...[/QUOTE]

Could you tell me please how to go about installing the k8 kernel, I am also on a amd64 machine.

All the best..scruffy :D

---

### Post by Suger on 2005-12-12
Open Synaptic. Search for linux. There you are.

---

### Post by nalmeth on 2005-12-12
K8* are for special for chips from amd, em64t* are for those
from intel. The smp versions are in case you have multiple CPUs.

I have an em64t processor from intel :o. Perhaps this kernel will help me with my graphics card problems (i810 is installed and does nothing).

And if it runs a little faster than all the better, no complaints to offer though.

---

### Post by RAOF on 2005-12-12
Sorry to crush your hope, but it is **extremely** unlikely that the em64t* kernel will solve your graphics problem. :(

---

