---
title: "AMD TL-58 1.9GHz shows 1600 bogomips, is it right?"
date: 2009-03-08
forum: x86 64-bit Users
---

### Post by IQRules on 2009-03-08
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 104
model name      : AMD Turion(tm) 64 X2 Mobile Technology TL-58
stepping        : 1
cpu MHz         : 800.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
apicid          : 0
initial apicid  : mip0
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good nopl pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips        : 1600.16

---

### Post by Yellow Pasque on 2009-03-09
Since your CPU is only running at 800MHz in your example (because it's idle), and the calculation for bogomips on an Athlon K8 CPU is clock * 2, then yes, it is correct as shown.
[http://www.clifton.nl/index.html?bogomips.html](http://www.clifton.nl/index.html?bogomips.html)

If you look at the cpuinfo when the CPU is running at full tilt, bogomips should be ~3800.

EDIT: Sorry, my initial post was misleading.

---

### Post by IQRules on 2009-03-09
The funny things for Intel CPUs, the bogomips calculation are not using Idle speed, so it shows much correct values on Intel Systems.

---

