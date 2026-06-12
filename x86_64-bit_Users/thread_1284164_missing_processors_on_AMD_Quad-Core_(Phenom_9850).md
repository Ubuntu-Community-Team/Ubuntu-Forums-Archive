---
title: "missing processors on AMD Quad-Core (Phenom 9850)"
date: 2009-10-06
forum: x86 64-bit Users
---

### Post by texas2stepper on 2009-10-06
Seems Jaunty is only seeing one processor...

Sorry if this has been addressed, but the only thing I found was this command and it gave me this:

me@mycomputer:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 9850 Quad-Core Processor
stepping    : 3
cpu MHz        : 2511.404
cache size    : 512 KB
physical id    : 0
siblings    : 1
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good pni monitor cx16 lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips    : 5022.80
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate


Thanks in advance!
Loving Linux (windeers user since WFW 3.1)

---

### Post by NoaHall on 2009-10-06
Try this "cat /proc/cpuinfo | grep processor". What kernel are you using?

---

### Post by Arup on 2009-10-06
Also make sure that single core CPU mode isn't selected in the BIOS.

---

### Post by texas2stepper on 2009-10-07
Thanks for the replies!

me@linux1:~$ cat /proc/cpuinfo | grep processor
processor    : 0
me@linux1:~$ uname -r
2.6.28-15-generic
me@linux1:~$ 

BIOS is set for multi processor

VISTA sees the 4 processors with no problems

---

### Post by timgood on 2009-10-07
I have the same processor and get this:

tim@tim-desktop:~$ cat /proc/cpuinfo | grep processor
processor	: 0
processor	: 1
processor	: 2
processor	: 3

and with:

cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 2
model name	: AMD Phenom(tm) 9850 Quad-Core Processor
stepping	: 3
cpu MHz		: 1250.000
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 4
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good pni monitor cx16 lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips	: 5021.43
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 2
model name	: AMD Phenom(tm) 9850 Quad-Core Processor
stepping	: 3
cpu MHz		: 1250.000
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 4
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good pni monitor cx16 lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips	: 5023.06
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 2
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 2
model name	: AMD Phenom(tm) 9850 Quad-Core Processor
stepping	: 3
cpu MHz		: 1250.000
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 4
apicid		: 2
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good pni monitor cx16 lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips	: 5022.93
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 3
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 2
model name	: AMD Phenom(tm) 9850 Quad-Core Processor
stepping	: 3
cpu MHz		: 1250.000
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 3
cpu cores	: 4
apicid		: 3
initial apicid	: 3
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good pni monitor cx16 lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips	: 5022.90
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate


So I would guess it has to be something in your BIOS or Motherboard setting which is causing Ubuntu not to see all processors. Which motherboard are you running?

---

### Post by texas2stepper on 2009-10-07
I'm using an ASUS M2N32-SLI Deluxe. I just flashed the BIOS to the latest version (2209) with no change. Any ideas? My web searches haven't produced much info...

---

### Post by NoaHall on 2009-10-07
Try booting into a older kernel . See if "cat /proc/cpuinfo | grep processor" comes up with anything different.

---

### Post by texas2stepper on 2009-10-07
> **NoaHall said:**
> Try booting into a older kernel . See if "cat /proc/cpuinfo | grep processor" comes up with anything different.

No change from my original output earlier after the BIOS upgrade..

Do you have a kernel you recommend? 

This is my first Linux go round so I only have

Ubuntu 9.04, kernel 2.6.28-15-generic
Ubuntu 9.04, kernel 2.6.28-11-generic

available in GRUB

---

### Post by NoaHall on 2009-10-07
Try the 2.6.28.11 one. If it's not that, then  maybe it'll be fixed in Karmic.

---

### Post by texas2stepper on 2009-10-07
> **NoaHall said:**
> Try the 2.6.28.11 one. If it's not that, then  maybe it'll be fixed in Karmic.

After booting into Ultimate Edition 2.3 LiveCD, I get this:

ubuntu@ubuntu:~$ cat /proc/cpuinfo | grep processor
processor    : 0
processor    : 1
processor    : 2
processor    : 3


AND this

ubuntu@ubuntu:~$ cat /proc/cpuinfo 
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 9850 Quad-Core Processor
stepping    : 3
cpu MHz        : 1250.000
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
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good pni monitor cx16 lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips    : 5022.81
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 9850 Quad-Core Processor
stepping    : 3
cpu MHz        : 1250.000
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
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good pni monitor cx16 lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips    : 5022.03
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 2
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 9850 Quad-Core Processor
stepping    : 3
cpu MHz        : 1250.000
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
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good pni monitor cx16 lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips    : 5023.29
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 3
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 9850 Quad-Core Processor
stepping    : 3
cpu MHz        : 1250.000
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
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good pni monitor cx16 lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips    : 5024.59
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate



Any ideas?
Thanks

---

### Post by NoaHall on 2009-10-07
Hm, that's good, it means the kernel supports it. You could reinstall, while I try to think of something :)

---

### Post by texas2stepper on 2009-10-07
> **NoaHall said:**
> Hm, that's good, it means the kernel supports it. You could reinstall, while I try to think of something :)

My third go around! I did have to set NOAPIC to get Ubuntu to load, but my reading tells me this has no effect...

---

### Post by NoaHall on 2009-10-07
Ah, try "pci=nommconf" instead, and report back.

---

### Post by texas2stepper on 2009-10-07
> **NoaHall said:**
> Ah, try "pci=nommconf" instead, and report back.

Worked like a charm!
THANKS! now why did it work? What did this little change do? More beans in your cup!:)

michael@linux1:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 9850 Quad-Core Processor
stepping    : 3
cpu MHz        : 1250.000
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
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good pni monitor cx16 lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips    : 5022.89
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 9850 Quad-Core Processor
stepping    : 3
cpu MHz        : 1250.000
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
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good pni monitor cx16 lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips    : 5024.44
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 2
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 9850 Quad-Core Processor
stepping    : 3
cpu MHz        : 1250.000
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
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good pni monitor cx16 lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips    : 5024.20
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 3
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 9850 Quad-Core Processor
stepping    : 3
cpu MHz        : 1250.000
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
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good pni monitor cx16 lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips    : 5024.20
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

---

### Post by NoaHall on 2009-10-07
I believe, not sure though, that helps your system to override any BIOS problems with addressing.

---

### Post by texas2stepper on 2009-10-07
Thanks again for your help. 

VirtualBox is next!

---

