---
title: "Pentium Dual Core and Frequency Scaling"
date: 2008-04-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Outworlder on 2008-04-03
I cannot enable Frequency Scaling in my Pentium Dual Core E2160. Please note that this is the desktop version (Core2Duo with less cache and no VT) and not the notebook version.

```

sudo modprobe -v acpi_cpufreq
insmod /lib/modules/2.6.24-14-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko 
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.24-14-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device

```

```
stephen@Elderbrain:~$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Pentium(R) Dual  CPU  E2160  @ 1.80GHz
stepping	: 13
cpu MHz		: 2520.001
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 5043.39
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Pentium(R) Dual  CPU  E2160  @ 1.80GHz
stepping	: 13
cpu MHz		: 2520.001
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 5040.05
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

```

Trying to compile a new kernel with speedstep-centrino doesn't work either. 

Motherboard is a Gigabyte Ga-P35-DS3.

Anyone had luck with this processor?

---

### Post by ryanhaigh on 2008-04-03
You might want to try different 'drivers' for the scaling. Maybe checkout this guide:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features)

---

### Post by Outworlder on 2008-04-03
Speedstep-centrino isn't even available on Gutsy or Hardy.

According to that link, there's only acpi_cpufreq, speedstep_centrino and p4_clockmod. None of those work.

---

### Post by crwl on 2008-04-04
I'm having exactly the same problem (though my CPU is Pentium Dual Core E2180 with 2,0 GHz clock speed). Frequency scaling works neither with Gutsy or Hardy. My motherboard is an Asrock 775dual-vsta. 

Looks like omeone over at the Gentoo forums has had the same problem:
[http://forums.gentoo.org/viewtopic-t-626243.html](http://forums.gentoo.org/viewtopic-t-626243.html)

Supporting these CPU's probably needs a fix to the acpi-cpufreq module (which I assume is the one that should be used with current processors), no?

edit: I just noticed this thread is in a 64-bit forum, so just to make everything clear  I'm running 32-bit Ubuntu. I suspect it doesn't matter in this case though...

---

### Post by Outworlder on 2008-04-04
> **crwl said:**
> I'm having exactly the same problem (though my CPU is Pentium Dual Core E2180 with 2,0 GHz clock speed). Frequency scaling works neither with Gutsy or Hardy. My motherboard is an Asrock 775dual-vsta. 

Looks like omeone over at the Gentoo forums has had the same problem:
[http://forums.gentoo.org/viewtopic-t-626243.html](http://forums.gentoo.org/viewtopic-t-626243.html)

Supporting these CPU's probably needs a fix to the acpi-cpufreq module (which I assume is the one that should be used with current processors), no?

edit: I just noticed this thread is in a 64-bit forum, so just to make everything clear  I'm running 32-bit Ubuntu. I suspect it doesn't matter in this case though...

Time to create a bug report, then?

---

### Post by ori_ab on 2008-04-07
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/213119](https://bugs.launchpad.net/bugs/213119) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm having the same problem on feisty/gutsy/hardy beta.
I have a E2200 dual core cpu.

Opened a bug at: [https://bugs.launchpad.net/bugs/213119](https://bugs.launchpad.net/bugs/213119)

please add your info/remarks there.

thanks

---

