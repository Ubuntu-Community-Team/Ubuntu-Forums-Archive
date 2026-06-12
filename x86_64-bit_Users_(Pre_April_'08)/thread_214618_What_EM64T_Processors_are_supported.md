---
title: "What EM64T Processors are supported?"
date: 2006-07-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by blananar on 2006-07-12
I was thinking, since my Pentium 4 has EM64T, it might work with 64 bit Ubuntu.  But, I have my doubts, after not seeing my cpu in the examples list for 64 Bit (I only saw Xeon).  Does the EM64T mean all processors with it?

---

### Post by RAOF on 2006-07-12
Yes.

---

### Post by JoWilly on 2006-07-14
... and with an EM64T cpu you will want to install the amd64-xeon kernel (to enable full kernel em64t support).

---

### Post by res1oz9a on 2006-07-15
I can vouch that it does work here, system specs below:


Asus P5GD1
Pentium 4 630 (3.0ghz)
2GB Wintech PC3200 (512mb x 4)
2 x 250Gb SATA Seagates
Leadtek 6800GS 256MB video card

uname -a
Linux res1oz9a-desktop 2.6.15-26-amd64-xeon #1 SMP PREEMPT Fri Jul 7 20:21:29 UT C 2006 x86_64 GNU/Linux

```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      :               Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 3
cpu MHz         : 3010.793
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall lm constant_tsc pni monitor ds_cpl est cid cx16 xtpr
bogomips        : 6030.78
clflush size    : 64
cache_alignment : 128
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      :               Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 3
cpu MHz         : 3010.793
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall lm constant_tsc pni monitor ds_cpl est cid cx16 xtpr
bogomips        : 6021.76
clflush size    : 64
cache_alignment : 128
address sizes   : 36 bits physical, 48 bits virtual
power management:
 
```

---

### Post by blananar on 2008-01-21
Ack.  I wish I had seen this sooner, otherwise I would have installed 64 bit OSes instead of the 32 bit ones I have been using.  Would I be able to update from 32 bit to 64 bit with command line?

---

### Post by LeAstrale on 2008-01-21
> **blananar said:**
> Ack.  I wish I had seen this sooner, otherwise I would have installed 64 bit OSes instead of the 32 bit ones I have been using.  Would I be able to update from 32 bit to 64 bit with command line?

i have talked to some people on IRC who have actually done it. 
Ill just need to check if i can find some sites about how to do it.

Be back Later

---

### Post by blananar on 2008-01-21
Sweet.  Could I possibly this way do it for an OS that uses the Ubuntu Kernel, but doesn't generally offer 64 bit?  Such as gOS?

---

### Post by LeAstrale on 2008-01-21
you might, but i dont know.. you have to get the 64bit kernel and install it. and make entries in grub for it too.. but i dont know how yet..

try searching the forums for 32bit upgrade to 64bit ;)

---

### Post by blananar on 2008-01-21
Ah, okay.  Well, if I can, I'll try it.

---

### Post by Kilz on 2008-01-21
There is really no way to upgrade a 32bit install to 64bit. But if you have a separate home partition you can use it in the 64bit install to save you some time setting up applications.

---

### Post by blananar on 2008-01-21
Ah.  Thanks.  I actually do have a separate Home Partition.  :D

---

