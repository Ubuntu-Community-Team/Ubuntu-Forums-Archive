---
title: "Have I lost one CPU core?"
date: 2009-01-29
forum: x86 64-bit Users
---

### Post by mariusm on 2009-01-29
I have installed 32bit linux on a system with AMD Athlon 64 3500+. This may sound like a stupid question but does this mean that one of the CPU cores has been disables? 1000MGhz seems like too low as well. Any ideas?

I have inluded my info below.

I have cheked 
```
# dmes | grep cpu
bash: dmes: command not found
s15333927:/etc# dmesg | grep cpu
Initializing cgroup subsys cpuset
Initializing cgroup subsys cpu
PERCPU: Allocating 42396 bytes of per cpu data
NR_CPUS: 8, nr_cpu_ids: 1, nr_node_ids 1
Initializing cgroup subsys cpuacct
cpufreq: No nForce2 chipset.
powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3500+ processors **[COLOR="Red"](1 cpu cores)[/COLOR]** (version 2.20.00)
Marking TSC unstable due to cpufreq changes
```

And this:
# cat /proc/cpuinfo
```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 127
model name      : AMD Athlon(tm) 64 Processor 3500+
stepping        : 1
**[COLOR="Red"]cpu MHz         : 1000.000[/COLOR]**
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow up pni cx16 lahf_lm svm extapic cr8_legacy 3dnowprefetch
bogomips        : 2009.09
clflush size    : 64
power management: ts fid vid ttp tm stc 100mhzsteps
```

---

### Post by soxs on 2009-01-29
Are you sure you have an AMD Athlon**[COLOR=DarkRed] X2 [/COLOR]**3500+ ?

For stock speed: if powernow-k8 is active, it will downstep your core to what is needed in favour of powereffciency and usability. It will upstep the core as soon as you run some more taxing programs (games etc..).

To check that simply add the pending applet to your gnome panel (Don't know its original name, running a localized german box).

---

### Post by mariusm on 2009-01-29
It actually is not "X2" just like you said. Misread provider's specification.  :o

And powernow did slow it down. I believe it should increase under mor stress :popcorn:

Thanks for the help, I will try to 

```
# watch cat /proc/cpuinfo
```

```
# dmesg | grep powernow
powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3500+ processors (1 cpu cores) (version 2.20.00)
powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x8
powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xa
powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xc
powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
```

---

### Post by stchman on 2009-01-29
> **mariusm said:**
> I have installed 32bit linux on a system with AMD Athlon 64 3500+. This may sound like a stupid question but does this mean that one of the CPU cores has been disables? 1000MGhz seems like too low as well. Any ideas?

I have inluded my info below.

I have cheked 
```
# dmes | grep cpu
bash: dmes: command not found
s15333927:/etc# dmesg | grep cpu
Initializing cgroup subsys cpuset
Initializing cgroup subsys cpu
PERCPU: Allocating 42396 bytes of per cpu data
NR_CPUS: 8, nr_cpu_ids: 1, nr_node_ids 1
Initializing cgroup subsys cpuacct
cpufreq: No nForce2 chipset.
powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3500+ processors **[COLOR="Red"](1 cpu cores)[/COLOR]** (version 2.20.00)
Marking TSC unstable due to cpufreq changes
```

And this:
# cat /proc/cpuinfo
```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 127
model name      : AMD Athlon(tm) 64 Processor 3500+
stepping        : 1
**[COLOR="Red"]cpu MHz         : 1000.000[/COLOR]**
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow up pni cx16 lahf_lm svm extapic cr8_legacy 3dnowprefetch
bogomips        : 2009.09
clflush size    : 64
power management: ts fid vid ttp tm stc 100mhzsteps
```

The Athlon 64 3500+ is a single core CPU.  If was dual core is would have X2 in the string.  I have one as well in one of my PCs.  The reason you are getting 1000MHz instead f 2200HMz is Ubuntu does frequency scaling on AMD Athlon 64 CPUs with a BIOS that has Cool 'N' Quiet enabled.

This is completely normal.

---

