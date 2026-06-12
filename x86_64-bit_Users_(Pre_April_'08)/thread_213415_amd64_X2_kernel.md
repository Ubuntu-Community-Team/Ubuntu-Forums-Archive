---
title: "amd64 X2 kernel"
date: 2006-07-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by martux on 2006-07-11
Is there a supported SMP amd64 kernel image available anywhere? I can't find one in the standard repositories (supposing linux-image-2.6.15-26-amd64-server is not SMP?!).
Could someone please enlighten me?

---

### Post by RAOF on 2006-07-11
**All** the AMD64 kernels are SMP :)

---

### Post by martux on 2006-07-11
Thanks, that makes sense.
Nevertheless do I have an Athlon 64 X2 and
martux@hilbert:~$ uname -r
2.6.15-23-amd64-k8
martux@hilbert:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : AMD Hammer Family processor - Model Unknown
stepping        : 2
cpu MHz         : 2210.214
cache size      : 1024 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm
bogomips        : 4423.27
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

Can this be a processor fault? Any other way of testing if two cores are available?

---

### Post by hajk on 2006-07-11
You might also check the output of "dmesg". Another possibility: does your motherboard require a setting for dual cores? The output of "cat /proc/cpuinfo" for a dual-core processor should be more or less as indicated below. I notice that you're running behind as to the kernel version, it's version 2.6.15-26-amd64-k8 by now...


Output of my "cat /proc/cpuinfo"

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : Dual Core AMD Opteron(tm) Processor 165
stepping        : 2
cpu MHz         : 1004.635
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 2012.16
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : Dual Core AMD Opteron(tm) Processor 165
stepping        : 2
cpu MHz         : 1004.635
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 2012.16
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

---

