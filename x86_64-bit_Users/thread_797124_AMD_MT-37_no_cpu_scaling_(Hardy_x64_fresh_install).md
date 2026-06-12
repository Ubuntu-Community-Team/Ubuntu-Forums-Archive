---
title: "AMD MT-37 no cpu scaling (Hardy x64 fresh install)"
date: 2008-05-17
forum: x86 64-bit Users
---

### Post by clickwir on 2008-05-17
```
clickwir@lappy:~$ sudo modprobe powernow-k8
FATAL: Error inserting powernow_k8 (/lib/modules/2.6.24-16-generic/kernel/arch/x86/kernel/cpu/cpufreq/powernow-k8.ko): No such device

clickwir@lappy:~$ sudo modprobe acpi-cpufreq
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.24-16-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device

clickwir@lappy:~$ uname -a
Linux lappy 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux
```

Dir /sys/devices/system/cpu/cpu0 has no cpufreq dir in it, I don't know if it should, but several other threads have indicated that it probably should. Powernowd says it should be there.

```
clickwir@lappy:~$ sudo powernowd
powernowd: PowerNow Daemon v0.97, (c) 2003-2006 John Clemens
powernowd: Found 1 scalable unit:  -- 1 'CPU' per scalable unit
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq: No such file or directory

```
Works fine in XP Pro and on previous versions of Kubuntu. I just reinstalled fresh Kubuntu 8.04 hardy x64 tonight.

top shows nothing taking cpu time and Ksensors shows full speed on the cpu.
```

clickwir@lappy:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 36
model name      : AMD Turion(tm) 64 Mobile Technology MT-37
stepping        : 2
cpu MHz         : 2000.064
cache size      : 1024 KB
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up rep_good pni lahf_lm
bogomips        : 4002.15
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc
```

I have to find what's missing. Fan is going all the time and it makes it impossible to hold this on my lap for more than 10 seconds. I can't go portable with this like this.

I've spent several hours over 3 days reading threads and trying things. So far it's not working in Hardy, at all. Yet, again, if I reboot into XP, works perfectly fine. What else can I supply or do to get this going?

---

### Post by clickwir on 2008-05-17
What else can I supply to help trouble shoot this?

---

### Post by Kilz on 2008-05-18
> **clickwir said:**
> What else can I supply to help trouble shoot this?

[File a bug report]("https://launchpad.net/ubuntu/+filebug") to let the developers (who seldom if ever look at the forums) know about the issue.

---

### Post by clickwir on 2008-05-18
OK, I'll go start that now. I'll link the bug report and this thread.

If there's anything anyone else can think of, lemme know and I'll try it.

I just wanted to make sure I wasn't missing something obvious.


linked: [https://bugs.launchpad.net/ubuntu/+source/powernowd/+bug/231534](https://bugs.launchpad.net/ubuntu/+source/powernowd/+bug/231534)

---

### Post by clickwir on 2008-06-11
Anyone have any idea's on this? It's still melting my lap.

---

