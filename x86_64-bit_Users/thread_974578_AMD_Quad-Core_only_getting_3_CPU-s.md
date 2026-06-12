---
title: "AMD Quad-Core only getting 3 CPU-s"
date: 2008-11-07
forum: x86 64-bit Users
---

### Post by johnsenf@gmail.com on 2008-11-07
Edit: **Solved**

Hi

I've noticed my system only shows 3 CPU-s (0 to 2). Anyone know whats wrong? Using freshly installed and up-to-date 8.10.

$ uname -a
Linux MYUBUNTUPC 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64 GNU/Linux

~$ cat /proc/cpuinfo 
**processor	: 0**
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 2
model name	: AMD Phenom(tm) 9850 **Quad-Core** Processor
stepping	: 3
cpu MHz		: 2500.000
cache size	: 512 KB
physical id	: 0
siblings	: 3
core id		: 0
**cpu cores	: 3**
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips	: 5015.19
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

**processor	: 1**
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 2
model name	: AMD Phenom(tm) 9850 Quad-Core Processor
stepping	: 3
cpu MHz		: 1250.000
cache size	: 512 KB
physical id	: 0
siblings	: 3
core id		: 1
cpu cores	: 3
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips	: 5015.26
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

**processor	: 2**
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 2
model name	: AMD Phenom(tm) 9850 Quad-Core Processor
stepping	: 3
cpu MHz		: 1250.000
cache size	: 512 KB
physical id	: 0
siblings	: 3
core id		: 2
cpu cores	: 3
apicid		: 2
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips	: 5015.27
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate


Can someone help me find my lost core? I miss it and want it back *playing 80-s lovesong*

/Finn

---

### Post by wfeltmate on 2008-11-08
Looking at what your core speeds are being reported as, it looks as though Ubuntu is seeing 2 of your cores as one. Core 0 is being reported at 2500MHz while the other two are only 1250.

---

### Post by soxs on 2008-11-08
Go into your bios, and check if downcore is set to anything below 4. If so, then only 3 or 2 or even only one will be used.

Edit: I've got a Phenom 9500 from stepping #2 and I get:
```
~$ cat /proc/cpuinfo 
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 9500 Quad-Core Processor
stepping    : 2
cpu MHz        : 1100.000
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 4
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips    : 4422.10
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 9500 Quad-Core Processor
stepping    : 2
cpu MHz        : 1100.000
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 4
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips    : 4422.40
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 2
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 9500 Quad-Core Processor
stepping    : 2
cpu MHz        : 1100.000
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 2
cpu cores    : 4
apicid        : 2
initial apicid    : 2
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips    : 4422.33
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 3
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 9500 Quad-Core Processor
stepping    : 2
cpu MHz        : 1100.000
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 3
cpu cores    : 4
apicid        : 3
initial apicid    : 3
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips    : 4422.32
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

```

---

### Post by johnsenf@gmail.com on 2008-11-08
> **soxs said:**
> Go into your bios, and check if downcore is set to anything below 4. If so, then only 3 or 2 or even only one will be used.


Yes, thank you Soxs. :D

My bios was indeed downcored to 3. Can't recall when or why I did that, but I may have.

/Finn

---

### Post by soxs on 2008-11-08
Presss the shiny medal in the right bottom of my post and mark this thread as solved. ;-)

---

