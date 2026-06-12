---
title: "Slow System"
date: 2007-09-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by coutts99 on 2007-09-30
My system seems to run very slowly. Seems to be when the system is doing anything the CPU spends a lot of time it the wait state.

See example top output below -:

[B]top - 14:31:34 up 28 min,  2 users,  load average: 1.78, 1.75, 1.34
Tasks:  86 total,   3 running,  83 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.8%us,  3.8%sy,  0.0%ni,  7.7%id, 80.8%wa,  0.0%hi,  3.8%si,  0.0%st[/B]

Currently running gutsy gibbon, but it did the same in feisty fawn as well.

Some info on the system -:

[B]processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 47
model name      : AMD Athlon(tm) 64 Processor 3000+
stepping        : 2
cpu MHz         : 1808.370
cache size      : 512 KB
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm
bogomips        : 3619.95
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc[/B]

Anyone any idea how I can start to debug this?

---

### Post by Mr_bleu on 2007-09-30
Why do you consider it slow?  What are you running?  If it's not cpu intensive, there won't be much usage.

---

### Post by Jouke74 on 2007-10-01
Yeah please give some info on which processes are runnning? Could be anything, from a beagle being installed to having a faulty harddrive.

---

### Post by mjwood0 on 2007-10-01
I think I'm running the exact same processor and everything seems well with my install. 

I'm guessing it's some program running that you don't know about.  I was actually quite surprised how well mine was running considering I've only got 512MB of RAM.

Post a full listing of what's currently taking processor cycles and perhaps we can figure out what it is.

---

### Post by Mr_bleu on 2007-10-01
Run the command: top
and see what's using all of the cpu's resources.

---

### Post by coutts99 on 2007-10-06
It's disk access, the machine is a server, no X etc.

When a I copy a large file to the system it becomes mostly unresponsive and the cpu is showing it is in the wait state.

---

