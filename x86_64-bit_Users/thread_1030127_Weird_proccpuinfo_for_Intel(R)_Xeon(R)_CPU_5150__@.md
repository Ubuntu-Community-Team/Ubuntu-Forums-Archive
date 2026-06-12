---
title: "Weird proc/cpuinfo for Intel(R) Xeon(R) CPU 5150  @ 2.66GHz"
date: 2009-01-04
forum: x86 64-bit Users
---

### Post by fab6 on 2009-01-04
Hi,

I just got a new hp xw6400 with two dual core xeon cpu 5150 2.66Ghz. The installation with kubuntu's alternative 64bit installation cd was straight forward. Though I wonder about the corresponding cat /proc/cpuinfo output (here just for the first core):

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Xeon(R) CPU            5150  @ 2.66GHz
stepping        : 6
cpu MHz         : 1998.000
cache size      : 4096 KB
physical id     : 3
siblings        : 2
core id         : 0
cpu cores       : 2
apicid          : 6
initial apicid  : 6
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov 
pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant
_tsc arch_perfmon pebs bts rep_good nopl pni monitor ds_cpl vmx est tm2 ssse3 cx
16 xtpr dca lahf_lm
bogomips        : 5320.09
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:



What looks so weird, it the number for 'cpu MHz : 1998.000'. How does it fit to the proposed 2.66GHz!? Does anyone have an explanation for this? 
Intel' page: [http://www.intel.com/cd/channel/reseller/asmo-na/eng/products/server/processors/5100/feature/index.htm](http://www.intel.com/cd/channel/reseller/asmo-na/eng/products/server/processors/5100/feature/index.htm)

Greetings!
Fabian

---

### Post by felker2 on 2009-01-04
> **fab6 said:**
> 

What looks so weird, it the number for 'cpu MHz : 1998.000'. How does it fit to the proposed 2.66GHz!? Does anyone have an explanation for this? 
Intel' page: [http://www.intel.com/cd/channel/reseller/asmo-na/eng/products/server/processors/5100/feature/index.htm](http://www.intel.com/cd/channel/reseller/asmo-na/eng/products/server/processors/5100/feature/index.htm)

Greetings!
Fabian

That's caused by this feature on that Intel-page you gave:

"Enhanced Intel® Speedstep™ Technology	Helps reduce average system power consumption and potentially improves system acoustics."

meaning: if the CPU is not under heavy load, it will reduce the frequency to save energy.

---

### Post by fab6 on 2009-01-04
Hi,

thanks for the explanation! So it will switch automatically to 2.66GHz as soon as I need it or do I have to adjust some kernel settings!?

Greetings!

---

### Post by felker2 on 2009-01-04
> **fab6 said:**
> 
thanks for the explanation! So it will switch automatically to 2.66GHz as soon as I need it or do I have to adjust some kernel settings!?



Under heavy load you will automagically get 2.66GHz. No kernel adjusting needed.

---

### Post by fab6 on 2009-01-04
Thanks for the help!

---

