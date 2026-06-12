---
title: "AMD Athlon-64 X2 6000+ crippled"
date: 2007-04-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by iMav on 2007-04-17
Under 64-bit Edgy, my new 3.0Ghz dual core AMD CPU is detected as 1Ghz per core.

```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 67
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
stepping        : 3
cpu MHz         : 1000.000
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni cx16 lahf_lm cmp_legacy svm cr8_legacy
bogomips        : 2001.06
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 67
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
stepping        : 3
cpu MHz         : 1000.000
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni cx16 lahf_lm cmp_legacy svm cr8_legacy
bogomips        : 2001.06
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

```
Under the 32-bit version [of Edgy], both cores show 3Ghz.  Default desktop install with all updates applied.

Any clue what the deal is?  I specifically bought this CPU to run the 64-bit SMP folding@home client...so I really want to get this figured out.

---

### Post by iMav on 2007-04-17
Never mind.  I'm an idiot.  I see that freq scaling is in full affect and working wonderfully.  Taxed the CPU's and they cranked up to 3.0Ghz without issue.

---

### Post by phossal on 2007-04-17
Isn't that AMD's premier engine currently?

---

### Post by iMav on 2007-04-18
> **phossal said:**
> Isn't that AMD's premier engine currently?
My primary folding@home machine needed a shot in the arm.  :)

CPU was only $240 from newegg.  In fact, CPU, 2GB of ram, and the motherboard total were right around $400.  Not a bad upgrade.

---

### Post by MiD-AwE on 2007-04-18
Hi all,

I have somthing to add, I'm also noticing actual performance loss under 64bit AMD dual core 4600+ Ubuntu 7.04 beta.  Either my nvidia 7600GS 512mb PCIe is not as powerful as the old 6600GT 8XAGP 128mb; or Ubuntu 7.04 64bit + AMD64 4600+X2 is not taking full advantage of my system even in a way that it's predecssor did. I've read and read the lecture, so I know not to expect the future today; but I also know, that in the attempt to improve my system with upgrades, now I'll have to downgrade to experience better performance from Ubuntu. 

Before I switched to 64bit, I was running DooM3 with every setting on Ultimate 1600x1200 getting perfect frame rates. Now, DooM3 is hell-a-chop-py . . .

Have you tried to performance test your gear? Or, is it just me? . . .

:-k

 Just for those curious:  vista64 premium is not any better on this same system. In fact, i'm experiencing awful visual flaws in DooM3's rendering "light & shadows".  Feisty 64bit is slow but the images are perfectly & beautifully rendered to the screen on full blast. Only, I wish that the 64bit was as good or even better than Feisty 32bit.

---

### Post by flapane on 2007-04-19
[ot]
are you a mil. in Iraq? I knew that newegg shippwed also to military, because years ago I saw that it couldn't ship here in Italy.

---

### Post by jaimz on 2007-04-19
hi AMD cool n quiet?

---

