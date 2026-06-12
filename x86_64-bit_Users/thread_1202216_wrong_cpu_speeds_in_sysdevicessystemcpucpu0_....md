---
title: "wrong cpu speeds in /sys/devices/system/cpu/cpu0/ ..."
date: 2009-07-02
forum: x86 64-bit Users
---

### Post by davygravy on 2009-07-02
I need some help getting my missing  .2GHz in Ubuntu - I don't see this problem in Leopard, only here...

I have an Intel Core 2 Duo OC'd to 3.8GHz.  It runs that speed in OS X/Leopard.  It also runs fine @4HGz (have a great cooler on it - never exceeds 42deg Celsius).

But in Ubuntu, it won't show up at 3.8GHz - it maxes out at 3.6 and won't let me go beyond that.

Also, dmesg yields
```
davygravy@DuoBuntu:~$ dmesg | grep processor
[    0.000000] Detected 3798.070 MHz processor.

```

but ```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
3600000 2400000 
```

Speed stepping works in terms of bouncing back and forth  between 2.4GHz and 3.6GHz, but I would rather set these two speeds at 3.0 and3.8.

Ideas?

I tried changing values (as root) in /sys/devices/system/cpu/cpu0/cpufreq, but this had no effect.

Is there some way to reset this?

---

### Post by ronaldprettyman on 2009-07-02
```
cat /proc/cpuinfo
```

> **davygravy said:**
> 
Is there some way to reset this?
No, I'm fairly sure those are live numbers. At least the /proc/cpuinfo is.

---

### Post by davygravy on 2009-07-02
Well, stepping works, either by setting it in userspace, or with the ondemand/performance/powersaver/whatever settings... as evidenced by :
```
davygravy@DuoBuntu:~/Desktop$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
stepping	: 10
cpu MHz		: 2400.000            <++++++++++++++++++++++++++++++++
cache size	: 6144 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 7596.14
clflush size	: 64
power management:



processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
stepping	: 10
cpu MHz		: 3600.000          <++++++++++++++++++++++++++++++++++++
cache size	: 6144 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 7596.61
clflush size	: 64
power management:


```

But what I'm looking for is to get it to recognize the remaing .2 or .4 GHz...'

```
[    0.000000] Detected 3798.070 MHz processor.
```  (from dmesg)

---

### Post by davygravy on 2009-07-02
I have confirmed that I can "force" it to recognized all 3.8GHz if I turn off E1C and EIST in BIOS - this produces an expected "... Processor Scaling is not supported..." warning at the desktop as login completes.   But at least all the processors "umpphh" is honored.

**I was hoping that turning these two features off, and then on again would "reset" it to the correct values.**  This was not the case.

I had the proc OC'ed to 3.6 when I installed Ubuntu.

Somebody, please don't tell me that I have to reinstall  while it is overclocked at my new/higher rate to get it to honor it all...  ;)

---

### Post by davygravy on 2009-07-04
bump & other thoughts...
===============


I am going to try to reinstall ubuntu this weekend on a fresh hdd, while it is OC'ed to 4.0GHz...


A question:  Does anyone know if the cpu limits are based on some policy that Ubuntu adheres to?

---

