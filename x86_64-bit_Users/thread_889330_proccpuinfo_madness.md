---
title: "/proc/cpuinfo madness"
date: 2008-08-14
forum: x86 64-bit Users
---

### Post by ohnoes on 2008-08-14
I have a q6600 (intel quad core) running at stock speed (2.4 ghz) loaded with ubuntu 8.04 64 bit. Dmesg correctly identifies the cpu:  

time.c: Detected 2399.972 MHz processor

However /proc/cpuinfo does not:

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping	: 11
[COLOR="Red"]cpu MHz		: 396.000[/COLOR]
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 4804.13
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:


This difference is quite a bit more than can be explained by cpu frequency scaling. Scaling can't account for a 2 ghz difference in reported speeds. Anyone have any idea what is going on here?

---

### Post by ilrudie on 2008-08-14
It shows the speed your cpu is *currently *operating at.  Your quad core simply wasnt busy when you looked at /proc/cpuinfo.

```
cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 9
model name    : Intel(R) Pentium(R) M processor 1400MHz
stepping    : 5
cpu MHz        : [COLOR=Red]**600.000**[/COLOR]
cache size    : 1024 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 tm pbe up bts est tm2
bogomips    : 1197.07
clflush size    : 64

```

I ran this when my cpu was mostly idle and it reports less than half speed.  You cpu is newer and has better stepping.  Start a processor intensive process (or a couple for your quad core) and look at it again.

---

### Post by ohnoes on 2008-08-14
Don't think so. I cranked up a folding@home smp run which is hitting all 4 cores hard and it still shows 396mhz. I fired up the frequency scaling meter and when it thinks the cpu is at 100%, it shows 594mhz. Both dmesg and the bios report everything correctly.

---

### Post by ohnoes on 2008-08-14
Ok, not that I know why it would do this, or even that it is doing this, but if you take the measured speed from dmesg (2399.972) and divide it by 4 (the number of cores) you get the number being reported by /proc/cpuinfo as 100% frequency. If you further multiply that by .66 (66% or what it runs at when scaled) you get 395.99 (rounded to 396) which is what cpuinfo is reporting for the "scaled" speed. So, to my eyes it sure looks like something in the kernel is taking the total mhz reported and dividing it by the number of cores reported.
Also please note that I had 7.10 x86_64 running on this hardware and did not experience this issue. I did a clean install of 8.04 on a new drive and this is the first oddity I noticed.

---

### Post by ilrudie on 2008-08-14
Not sure man.  I can look at my quad Phenom when I get home and see if it is doing anything weird like that.  I seem to recall it shows each core separately on my Phenom though.  Have you checked to see if there is a bug report about this?  Other than the annoyance of seeing low speeds is this causing problems?  What version of Ubuntu are you running?  Also I'm assuming you are running 64-bit Ubuntu since its in the x86_64 forum.  Is that correct?

---

### Post by viciouslime on 2008-08-16
Sounds like it's just a bug in the way it's calculating it then... Perhaps you should report it on launchpad. Are you noticing a massive performance decrease?

---

### Post by ian dobson on 2008-08-16
Hi,

My Q6600 shows the correct value in /proc/cpuinfo.

What motherboard are you using? It could be that a BIOS update could solve your problem.

Regards
Ian Dobson

---

