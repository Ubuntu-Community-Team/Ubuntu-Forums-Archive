---
title: "BIOS says 2.66GHz - meminfo says 1.6GHz"
date: 2009-04-29
forum: x86 64-bit Users
---

### Post by whaler1 on 2009-04-29
Ok, so I have pretty much gotten comfortable with my recent jump to Ubuntu 8.10 on my Dell XPS 435 and have decided to check out what the OS sees in the CPU which has an Intel i7 920 - 8 thread processor.  Although the BIOS says the processor is clocked at 2.66GHz the Ubuntu cpuinfo command reveals that the CPU is thinking at 1.6GHz on all 8 threads. Below is an output example from 1 thread. I wondered if someone could explain this since obviously I want the CPU speed maximized.

processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 26
model name    : Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz
stepping    : 4
cpu MHz        : 1600.000
cache size    : 8192 KB
physical id    : 0
siblings    : 8
core id        : 0
cpu cores    : 4
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr sse4_1 sse4_2 popcnt lahf_lm ida
bogomips    : 5319.97
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

---

### Post by 3Miro on 2009-04-29
The actual speed varies depending on the load. This is done to minimize heath output and power usage. It should be OK. get the cpuinfo again when the system is running on high load.

There re ways to manually adjust the cpu speed, if you want to.

---

### Post by malaprohibita on 2009-04-30
Seconded.  I have the same machine as you, with the same results.  It's just your CPU running at lower clock speeds until it needs to flex its muscles.  :P

---

