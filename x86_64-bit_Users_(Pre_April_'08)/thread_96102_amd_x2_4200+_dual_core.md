---
title: "amd x2 4200+ dual core?"
date: 2005-11-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by kntzeng on 2005-11-28
I have installed 2.6.12-10-amd64-k8-smp
but I type **cat /proc/cpuinfo**
I just found one processor? 
Is this normal?

=============================================================
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping        : 1
cpu MHz         : 2211.339
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 4374.52
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp
=============================================================

Mother Board: gigabyte K8NXP-SLI
                    BIOS version:F10 (the newest one)

Thanks~~~

---

### Post by Sutekh on 2005-11-28
[QUOTE=kntzeng]...
core id         : 0
**cpu cores       : 2**
fpu             : yes...
[/QUOTE]

That would suggest yes  I'm probably not the best to answer since I use 32 bit Ubuntu!  However I **do** have a X2 3800 and a SMP kernel (k7 - on 32bit). 
On my box cat /proc/cpuinfo spits out information for two separate processors, whereas your output has one processor, two cores.  

Same thing? 32 v 64 bit anomaly?  Need a 64 bit SMP user too relate their setup.

---

### Post by stimpie on 2005-11-30
I have an AMD X2 3800+ working with a 64bit smp kernel.

When just installed the second core didn't work because of an old bios firmware (asus).  This could be your problem as well.

---

### Post by AndersAA on 2005-11-30
you should get both a processor:0 and a processor:1, make sure your running a smp kernel, and that your bios has the neccesary updates.

---

### Post by Casey on 2005-11-30
With 64 bit ubuntu, the correct output is:
processor: 1
cpu cores: 2

(I also have an X2 and have confirmed that I can use both cores).

---

### Post by AndersAA on 2005-11-30
[QUOTE=Casey]With 64 bit ubuntu, the correct output is:
processor: 1
cpu cores: 2

(I also have an X2 and have confirmed that I can use both cores).[/QUOTE]

no it's not, the correct output is two seperate entries.  One for processor0 and processor1.

example:
```

#cat /proc/cpuinfo  | egrep 'processor|core'
processor       : 0
core id         : 0
cpu cores       : 2

processor       : 1
core id         : 1
cpu cores       : 2

```

---

### Post by Casey on 2005-11-30
Whoops, you're right -- this is what I have:

```
cat /proc/cpuinfo  | egrep 'processor|core'
processor       : 0
core id         : 0
cpu cores       : 2
processor       : 1
core id         : 1
cpu cores       : 2

```

I am incorrect, sorry about that.

---

