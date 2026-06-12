---
title: "Optimization for AMD64 for 32 Ubuntu?"
date: 2008-03-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by tseo on 2008-03-22
Hello

I am running 32bit Gutsy on my laptop which has AMD Turion64x2 CPU. The system as a whole seems to be not very fast and responsive. 

Do you think this has anything to do with the CPU and what can I do to fix it?

---

### Post by caver1 on 2008-03-22
which processor do you have and how much ram?
Generally speaking a 32bit Os cannot use all of the 64bit hardware.
Look at your system monitor and see if your Os even sees both cores. probably doesn't.
I would suggest dumping 32bit Gutsy and install 64bit Gutsy.
caver1

---

### Post by tseo on 2008-03-22
```
 *-cpu
          product: AMD Turion(tm) 64 X2 Mobile Technology TL-52
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.8.2
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxe
xt fxsr_opt rdtscp x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8legacy ts fid vid ttp tm stc cpufreq

```

2Gb of ram. System monitor sees both cores and there seems to be activity at both of them. But the system is not running normally.

---

### Post by Kilz on 2008-03-22
If you have room on the hard drive, install both versions in a duel boot. That way you can move over slowly while haveing the 32bit install available in case of issues.

---

