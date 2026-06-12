---
title: "AMD64 speedstep not working"
date: 2009-08-01
forum: x86 64-bit Users
---

### Post by diffy on 2009-08-01
Hello,

I've just buy a new netbook and try to figure out how to enable the speedstep on it.
The processor is an AMD and below is the cat /proc/cpuinfo 
```

processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 124
model name    : AMD Athlon(tm) Processor L110
stepping    : 2
cpu MHz        : 1197.081
cache size    : 512 KB
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow up rep_good pni cx16 lahf_lm svm extapic cr8_legacy 3dnowprefetch
bogomips    : 2394.16
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

```when i try to load the module powernow-k8 i have an error 
```

sudo modprobe powernow-k8
FATAL: Module powernow_k8 not found.

```normally this module is include since the version 2.6.7 right ? so i check my kernel version, i have this :
```

uname -a
Linux ptitpc 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 01:19:55 UTC 2009 x86_64 GNU/Linux

```it seems that this module is not included in my kernel, and i see that this module is not listed in the modules blacklist. what's going on please ? does anyone have an idea ?

sorry for the title i mean cool and quiet :) no speedstep techology, i have and amd :)

thanks a lot
David

---

### Post by insane_alien on 2009-08-01
AMD's version is Cool 'n' Quiet. SpeedStep is intel only.

---

