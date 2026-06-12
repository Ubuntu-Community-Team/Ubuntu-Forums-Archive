---
title: "wrong cpu  frequency on HP nx6125??"
date: 2006-03-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by bato on 2006-03-10
Hi everybody,
I have a HP compaq nx6125 laptop with an AMD64 Turion and I have installed ubuntu amd64. Now, all work great, but if I type

```
cat /proc/cpuinfo
```
```

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 36
model name      : AMD Turion(tm) 64 Mobile ML-34
stepping        : 2
cpu MHz         : 800.048
cache size      : 1024 KB
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm
bogomips        : 1554.65
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

```

The cpu frequency is 1.8 GHz, but it shows

```
cpu MHz         : 800.048
```

Why??  What is it mean? Is my CPU working at lower frequency than it wolud be?

[Sorry for my poor english]

---

### Post by el3ktro on 2006-03-10
Simple answer: Power saving. When your notebook isn't doing anything, the CPU freq is lowered. If you do something (watch a video, encode an MP3 etc.) the CPU freq rises.

Tom

---

### Post by bato on 2006-03-10
Thanks a lot!!

Now I am less ignorant! :D 

I try to start glxgears and cat /proc/cpuinfo looks

```
cpu MHz         : 1600.096
```

I like to learn new things.

---

