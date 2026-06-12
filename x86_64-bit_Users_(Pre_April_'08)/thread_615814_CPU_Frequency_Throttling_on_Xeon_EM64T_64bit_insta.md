---
title: "CPU Frequency Throttling on Xeon EM64T 64bit installation not working?"
date: 2007-11-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Master One on 2007-11-17
Fresh Edubuntu Gutsy 64bit installation on a dual Xeon 3.2 EM64T machine, the intended kernel module acpi_cpufreq is present, but can not be loaded.```
$ uname -a
Linux lanmaster 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux

$ cat /proc/cpuinfo
processor : 0
vendor_id : GenuineIntel
cpu family : 15
model : 4
model name : Intel(R) Xeon(TM) CPU 3.20GHz
stepping : 1
cpu MHz : 3200.210
cache size : 1024 KB
physical id : 0
siblings : 2
core id : 0
cpu cores : 1
fpu : yes
fpu_exception : yes
cpuid level : 5
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl cid cx16 xtpr
bogomips : 6404.88
clflush size : 64
cache_alignment : 128
address sizes : 36 bits physical, 48 bits virtual
power management:

processor : 1
vendor_id : GenuineIntel
cpu family : 15
model : 4
model name : Intel(R) Xeon(TM) CPU 3.20GHz
stepping : 1
cpu MHz : 3200.210
cache size : 1024 KB
physical id : 3
siblings : 2
core id : 0
cpu cores : 1
fpu : yes
fpu_exception : yes
cpuid level : 5
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl cid cx16 xtpr
bogomips : 6400.81
clflush size : 64
cache_alignment : 128
address sizes : 36 bits physical, 48 bits virtual
power management:

processor : 2
vendor_id : GenuineIntel
cpu family : 15
model : 4
model name : Intel(R) Xeon(TM) CPU 3.20GHz
stepping : 1
cpu MHz : 3200.210
cache size : 1024 KB
physical id : 0
siblings : 2
core id : 0
cpu cores : 1
fpu : yes
fpu_exception : yes
cpuid level : 5
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl cid cx16 xtpr
bogomips : 6400.78
clflush size : 64
cache_alignment : 128
address sizes : 36 bits physical, 48 bits virtual
power management:

processor : 3
vendor_id : GenuineIntel
cpu family : 15
model : 4
model name : Intel(R) Xeon(TM) CPU 3.20GHz
stepping : 1
cpu MHz : 3200.210
cache size : 1024 KB
physical id : 3
siblings : 2
core id : 0
cpu cores : 1
fpu : yes
fpu_exception : yes
cpuid level : 5
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl cid cx16 xtpr
bogomips : 6400.85
clflush size : 64
cache_alignment : 128
address sizes : 36 bits physical, 48 bits virtual
power management:

$ dmesg | grep -i throttling
[ 55.718656] ACPI: Processor [CPU0] (supports 8 throttling states)
[ 55.718683] ACPI: Processor [CPU1] (supports 8 throttling states)
[ 55.718704] ACPI: Processor [CPU2] (supports 8 throttling states)
[ 55.718725] ACPI: Processor [CPU3] (supports 8 throttling states)

$ lsmod | grep -i cpufreqcpufreq_stats 8160 0
cpufreq_conservative 9608 0
cpufreq_userspace 6048 0
cpufreq_powersave 3072 0
cpufreq_ondemand 10896 0
freq_table 6464 2 cpufreq_stats,cpufreq_ondemand

$ sudo modprobe acpi_cpufreq
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.22-14-generic/kernel/arch/x86_64/kernel/cpufreq/acpi-cpufreq.ko): No such device

$ sudo cpufreq-selector -g ondemand
No cpufreq support
```
That's the info I also already provided in ***[this](https://bugs.launchpad.net/ubuntu/+bug/163398)*** bugreport.

Does anybody here have more info on that issue?

---

### Post by s4w2099 on 2008-07-15
I have an HP xw6200 Workstation with two Intel Xeon (Nocona) 1MB cache with hyper threading enabled and I suffer from the same exact problem. I dont even bother to post the logs because they look exactly the same as yours.

---

