---
title: "8 FPS in diablo 3 with ubuntu 14.04 (64 bit)"
date: 2014-04-19
forum: Wine
---

### Post by shawn-corliss on 2014-04-19
Hi All,
I have just installed Ubuntu 14.04 (64 Bit).
I am trying to run D3 with PlayOnLinux(4.2.2) with Wine(x86) version 1.7.15 (default).
I have done zero config changes to the game and I am getting 8 FPS in Diablo3.
For all of you running Diablo3 what changes have you made to either Wine or PlayOnLinux to get better frame rates?

System Info for Graphics Card:
```
kas@Sentinal67:~$ lspci -nnk | grep VGA -A1
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Cypress LE [Radeon HD 5830] [1002:689e]
    Subsystem: PC Partner Limited / Sapphire Technology Device [174b:e140]
```

System Inform for CPU*4:
```
kas@Sentinal67:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 4
model name    : AMD Phenom(tm) II X4 965 Processor
stepping    : 3
microcode    : 0x10000c8
cpu MHz        : 800.000
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 4
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt nodeid_msr hw_pstate npt lbrv svm_lock nrip_save
bogomips    : 6830.61
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

```

Thanks for sharing your config.
cheers,
SCORLISS

---

