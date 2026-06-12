---
title: "Pr-em64t kernel?"
date: 2006-03-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Robocoastie on 2006-03-24
Hi,

I have a Dell Dimension 5100 running U-5.10 64bit with a single 2.8GHz P4-em64t HT processor and an ATI Radeon X300 video card. I'm currently running the *-9-xeon kernel from the repositories which works and correctly shows dual procs (meaning it sees the HT when I do a cat /proc/cpuinfo well here it is:

```

rob@dell5100:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      :               Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping        : 1
cpu MHz         : 2793.106
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 3
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl cid cx16 xtpr
bogomips        : 5537.79
clflush size    : 64
cache_alignment : 128
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      :               Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping        : 1
cpu MHz         : 2793.106
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 3
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl cid cx16 xtpr
bogomips        : 5570.56
clflush size    : 64
cache_alignment : 128
address sizes   : 36 bits physical, 48 bits virtual
power management:

rob@dell5100:~$

```

But what kernel SHOULD I be using? I found one in the repository called P4em64t but that didn't work at all (said no linux found at mount point to be exact). I'd like to get the right one and eliminate all the others cluttering up my startup screen.

Thanks!

Rob

***Update*** Solved by using the amd64-k8-smp kernel instead. Thread can be blown away if moderator wishes.

---

