---
title: "Athlon64 X2 Dual Core Enabling part 2"
date: 2007-06-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by kalcifer on 2007-06-14
Hi Joekr. I have this problem too, here is the output of:  cat /proc/cpuinfo, I wonder if you could help me to enable my dual core, tahnks in advance......(help me plz :( )

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
stepping        : 2
cpu MHz         : 2210.218
cache size      : 1024 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm cmp_legacy
bogomips        : 4423.12
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

---

### Post by tgm4883 on 2007-06-14
> **kalcifer said:**
> Hi Joekr. I have this problem too, here is the output of:  cat /proc/cpuinfo, I wonder if you could help me to enable my dual core, tahnks in advance......(help me plz :( )

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
stepping        : 2
cpu MHz         : 2210.218
cache size      : 1024 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm cmp_legacy
bogomips        : 4423.12
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

kalcifer,

Please start a new thread.  Also, in the future, please don't reopen a thread that is almost **_two years old_**

---

### Post by Cappy on 2007-06-14
Hey, on the bright side, at least we know he searched before posting!! =P

---

### Post by tgm4883 on 2007-06-14
Much better.

Whats the output of uname -r

---

### Post by Kilz on 2007-06-14
Just a question, Did you buy or make the computer with the x2 in it, or is it a processor upgrade on a machine that had a single core before?

---

### Post by kalcifer on 2007-06-14
Well, let me explain.  I bought this computer x2 originally. But, I made a backup and restore following instructions from a post, then I realized that just one core is working,...the thing is that I boot form ubuntu installation cd and there the two cores are running, but not when I boot from my harddisk. Is there a way to make the two cores running? I tried by installing smp packages using synaptic, but no succes, my system still uses one single core :(

---

### Post by Kilz on 2007-06-15
tgm4883 asked for 
```
uname -r
```
open a terminal and type it in, then copy and paste in the result to a post. Also please do 
```
uname -a
```

---

### Post by bigtom2 on 2007-06-15
make sure you have 2 memory sticks installed had the same problem installed 1 more
and it works fine amd 64 daul ddr is suposed to have 2 moduals.
they work good with one but ddr 2 support is with double mods.
     hope it helps bigtom2.

---

### Post by kalcifer on 2007-06-15
Hi Folks, here is the output of uname -a 

Linux noodle 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64 GNU/Linux

thank you for your help...

---

### Post by kalcifer on 2007-07-02
Is there anybody who is  able to help me please?  I posted my data, but no help. Please, don't leave alone...

---

### Post by Kilz on 2007-07-02
> **kalcifer said:**
> Is there anybody who is  able to help me please?  I posted my data, but no help. Please, don't leave alone...

Just a question, but have you thought about installing a fresh install to a different partition to see if the problem follows there?

---

### Post by MMoudry on 2007-07-24
Hi,
I have the same problem, I bought a ASUS M2N32 WS and Athlon 64 X2 4600+ EE (notice that this combo supports the AMD Cool 'n Quiet technology) and installed a clean install of Feisty Server on it (yes the uname reports a generic SMP kernel).
The /proc/cpuinfo reports also only one core.

I found this :
[http://www.ubuntu-es.org/index.php?q=node/52510](http://www.ubuntu-es.org/index.php?q=node/52510)

here is a link to a altavista translation :
[http://babelfish.altavista.com/babelfish/trurl_pagecontent?lp=es_en&url=http%3A%2F%2Fwww.ubuntu-es.org%2Findex.php%3Fq%3Dnode%2F52510](http://babelfish.altavista.com/babelfish/trurl_pagecontent?lp=es_en&url=http%3A%2F%2Fwww.ubuntu-es.org%2Findex.php%3Fq%3Dnode%2F52510)

I don't know if that works, will test it this evening,

After reading the post above I am wondering whether this is not caused by the powernow optimizations (ie. when idle one core gets switched off?), 

MM

---

### Post by John.Michael.Kane on 2007-07-24
Here's the out put of uname -a, and cat /proc/cpuinfo from the machine I'm on.
```
 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64 GNU/Linux
```

```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 1
cpu MHz         : 1000.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 2002.07
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 1
cpu MHz         : 1000.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 2002.07
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp
```

@MMoudry I find it hard to believe that powernowd is the culprit here, As I have it installed as do most users, and still garner the output above.

Also powernowd only controls CPU speed .and voltage eg: when the cpu's max speed, and max voltage is not needed it is dropped to a lower speed, and voltage. it does not as you say turn off idle cores.

With this said theres more to the issue that you, and the OP are having. 

What I would suggest is testing the older kernels in dapper/edgy that would allow you to find out if the issue is related to the kernel in feisty. Which could be a possible reason for the one core issue.

---

### Post by MMoudry on 2007-07-24
SD-Plissken, I agree with you entirely that powernow is not the culprit, I realized moments after posting the last post that the entire core switchoff will be a feature in barcelona and not in the current generations of chips. For me however the problem fixed itself somehow. I restarted my machine for a CD-ROM upgrade and suddentely the CPUINFO shows two processors :
```

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4600+
stepping        : 2
cpu MHz         : 2410.974
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8_legacy
bogomips        : 4827.75
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4600+
stepping        : 2
cpu MHz         : 2410.974
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8_legacy
bogomips        : 4821.88
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

```

Hmm... strange.

MM

---

### Post by John.Michael.Kane on 2007-07-24
MMoudry that is strange. it might have been a hardware conflict not sure. 

If you want to find out if it had anything to with the cdrom drive doubtful it did. You can try putting back in the old one, and see if the problem happens.

In any case I'm glad you got it sorted out.

---

