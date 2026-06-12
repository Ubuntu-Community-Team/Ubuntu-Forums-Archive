---
title: "Intel E4500 2 core with SMP kernel but only 1 CPU active"
date: 2008-03-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by jimhall on 2008-03-25
I'm running an Intel E4500 duo core with Hardy server 64. Kernel is SMP, and /proc/cpuinfo shows 2 CPU but only 1 CPU appears to be running.

top only shows 1 process running instead of 2:

Tasks:  86 total,   1 running,  85 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.0%sy,  0.0%ni, 96.2%id,  3.6%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   1018380k total,  1009172k used,     9208k free,    44096k buffers

does anyone know what's going on here ? how can I get the 2nd cpu going ?

any help or suggestions appreciated. further sys info below.

rgds,
james

The kernel is SMP as shown below:
Linux prinsep 2.6.24-12-server #1 SMP Wed Mar 12 22:58:36 UTC 2008 x86_64 GNU/Linux

The output of /proc/cpuinfo shows there are 2 CPUs as shown below:
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz
stepping	: 13
cpu MHz		: 2199.999
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 4402.56
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz
stepping	: 13
cpu MHz		: 2199.999
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 4400.01
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

---

### Post by dcstar on 2008-03-26
> **jimhall said:**
> I'm running an Intel E4500 duo core with Hardy server 64. Kernel is SMP, and /proc/cpuinfo shows 2 CPU but only 1 CPU appears to be running.

top only shows 1 process running instead of 2:

Tasks:  86 total,   1 running,  85 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.0%sy,  0.0%ni, 96.2%id,  3.6%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   1018380k total,  1009172k used,     9208k free,    44096k buffers
........

You are misinterpreting top, it shows running** processes** whether they run in one CPU or 100 CPUs.

You have a dual CPU system and if you give it enough work, the processes will be shared between the available CPUs.

---

### Post by Kevin Funnell on 2008-03-26
G'Day from the Top End,
I agree with David but if you are still not convinced then look at:  System / Adminstration / System Monitor / Resources and the top graph (CPU History) should show you both CPU1 and CPU 2.  
Old Kevin

---

### Post by CyrusTR on 2008-03-26
when you run top .. press "1" and it should show you the individual cores

before pressing "1":
```
Cpu(s): 17.2%us,  1.6%sy,  0.0%ni, 78.9%id,  2.2%wa,  0.1%hi,  0.0%si,  0.0%st

```

after pressing "1":
```
Cpu0  :  7.1%us,  1.2%sy,  0.0%ni, 91.5%id,  0.2%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu1  : 15.7%us,  1.3%sy,  0.0%ni, 79.5%id,  3.1%wa,  0.1%hi,  0.2%si,  0.0%st

```

---

