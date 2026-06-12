---
title: "Processor stepping in /proc/cpuinfo"
date: 2006-11-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by tszanon on 2006-11-26
Hi,

I have a AMD Athlon64 X2 3800+. When I type
```
cat /proc/cpuinfo
```
that's what is shown:
```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 2
cpu MHz         : 1005.166
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy
bogomips        : 2012.39
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 2
cpu MHz         : 1005.166
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy
bogomips        : 2012.39
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc
```

The stepping of this processor is "F2". As you can see, the stepping in /proc/cpuinfo is just "2". Is it correct? How should this information be interpreted?

---

