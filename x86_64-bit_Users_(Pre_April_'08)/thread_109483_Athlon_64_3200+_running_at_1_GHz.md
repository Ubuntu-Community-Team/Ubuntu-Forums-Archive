---
title: "Athlon 64 3200+ running at 1 GHz"
date: 2005-12-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bachstelze on 2005-12-28
here is my /proc/cpuinfo

```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 47
model name      : AMD Athlon(tm) 64 Processor 3200+
stepping        : 2
cpu MHz         : 994.932
cache size      : 512 KB
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm
bogomips        : 1957.88
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

```

Any ideas ? I don't think it could be a BIOS issue, in XP it runs as it should (2 GHz)

---

### Post by rottame on 2005-12-28
powernowd is running?
on Athlon64 is a feature called Cool'N'Quiet
it should raise the frequency when the box needs full power

---

### Post by Bachstelze on 2005-12-28
[QUOTE=rottame]powernowd is running? it slows the cpu down to save power
on Athlon64 is a feature called Cool'N'Quiet[/QUOTE]

how can I check this out ?

EDIT : How silly of me, system monitor... I killed the process and my CPU runs at 2 GHz, thanks for the info :)

EDIT II : But it lauches automatically at every startup. How could I disable it ?

---

### Post by turbonium on 2005-12-28
theres no need to. unless you want to pay more for your electricity...

the cpu will clock at 2ghz instantly when it needs to with NO performace loss or lag. its a great feature, keep it.

---

### Post by rottame on 2005-12-29
remove powernowd with synaptic

keep it.... lower speed = less heat = the fan slows down = less noise :)

---

### Post by void_false on 2005-12-29
Yeah. It's great feature when CPU suits its freq for computer's need. Better keep it as it is.

---

### Post by nothreat33 on 2005-12-31
seems like many people have this issue, i just posted about this problem on my 4800+ amd64. it turned out it was cool'n'quiet in bios. it didn't seem to increase the frequency from 1 to 2.4ghz. but when idisabled it it works fine.

---

### Post by Atreju on 2005-12-31
the best way to load a system at it's maximum is to launch the "yes" command

it's an infinite loop, cpu climps for sure at 100% and my cpu does get to 2Ghz when I use it...

also, take a look at the cpufreq applet could give you a hint... and also it _does_ load the cpufreq kernel modules.... this could be useful

---

