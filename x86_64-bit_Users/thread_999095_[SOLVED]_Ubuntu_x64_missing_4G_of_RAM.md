---
title: "[SOLVED] Ubuntu x64 missing 4G of RAM"
date: 2008-12-01
forum: x86 64-bit Users
---

### Post by unprinted on 2008-12-01
This Core Duo 2 PC has four 2Gb DIMMs fitted and the BIOS setup page reckons it can indeed see all 8Gb of RAM.

However, both memtest+ and Ubuntu x64 8.10 reckon they can only see about 3 1/4Gb, i.e. the usual amount for 4+Gb on a 32 bit OS.

```
me@CORE2:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3267       1352       1914          0         21        294
-/+ buffers/cache:       1036       2230
Swap:        10236          0      10236

```

```
me@CORE2:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz
stepping	: 11
cpu MHz		: 1992.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 5319.97
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz
stepping	: 11
cpu MHz		: 2656.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 5320.07
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

```

So how does it determine how much RAM it has?

---

### Post by unprinted on 2008-12-01
Oh, Windows XP x64 also reckons it can see 3 1/4Gb RAM...

... but [CPU-Z]("http://www.cpuid.com/cpuz.php") on Windows can see all 8Gb and happily reports on the details of the DIMMs, down to their serial numbers, in all four slots.

---

### Post by Yellow Pasque on 2008-12-01
- What motherboard do you have?
- Do you have the latest BIOS?

---

### Post by soxs on 2008-12-01
post the output of ```
uname -a
```

---

### Post by unprinted on 2008-12-01
```
me@CORE2:~$ uname -a
Linux CORE2 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux
```

... but the interesting news is

```
me@CORE2:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          7990       1403       6587          0         44        331
-/+ buffers/cache:       1027       6963
Swap:        10236          0      10236

```

:)

What seems to have done the trick was updating the BIOS, although the only official change in it was something related to the CPU fan speed.

I wonder if it was reseting the BIOS's CMOS that did it?

Now, how do I mark this as sorted?

---

### Post by Yellow Pasque on 2008-12-01
The "mark thread as solved" option is under the thread tools menu (towards the top).

> What seems to have done the trick was updating the BIOS, although the only official change in it was something related to the CPU fan speed.
I've run into this before too, where the BIOS update fixes or adds features, but they're not listed in the changelog. *shrug*

---

### Post by felker2 on 2008-12-02
> **Temüjin said:**
> 

I've run into this before too, where the BIOS update fixes or adds features, but they're not listed in the changelog. *shrug*

I find it puzzling to see that such high-tech hardware as mobo's is created by people who generate so little / incomplete documentation, like "Modify Crashfree function fail problem." which is reported for my BIOS: no idea what that means.

---

### Post by unprinted on 2008-12-02
Yep. This one doesn't seem to have a manual (although they made it, there's nothing at all on the MSI website about it) and it is aimed squarely at the 'don't you worry your pretty little head about it' market. 

There is nothing in the PC's manual about how to get into the BIOS setup, for example, never mind what the various settings mean.

Which is fine, until you do need to know.

---

