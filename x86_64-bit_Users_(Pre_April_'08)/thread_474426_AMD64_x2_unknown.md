---
title: "AMD64 x2 unknown"
date: 2007-06-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Herix on 2007-06-15
when I type uname -a no info is shown about the processor, when I type uname -p it says "unknown". I'm believe my processor isn't working as it should; I want to make sure my two cores work at full speed. Do I have to isntall additional drivers to for my AMD64 X2 4200 processor to work correctly??.....I've just installed ubuntu Edgy and still don't know much about Linux.

Thanks.

---

### Post by Kilz on 2007-06-15
> **Herix said:**
> when I type uname -a no info is shown about the processor, when I type uname -p it says "unknown". I'm believe my processor isn't working as it should; I want to make sure my two cores work at full speed. Do I have to isntall additional drivers to for my AMD64 X2 4200 processor to work correctly??.....I've just installed ubuntu Edgy and still don't know much about Linux.

Thanks.

I have a athlon x2 4600 Ubuntu should detect the processor without you doing anything. You dont need to install anything to enable mutiple processors because all 64bit kernels have that (SMP) already enabled.
Did you install from the live cd? If so boot from it and do uname -a

---

### Post by xzero1 on 2007-06-15
In a terminal type cat /proc/cpuinfo.
This will list info on both cores.

---

### Post by ©TriMoon® on 2007-06-15
> **Herix said:**
> when I type uname -a no info is shown about the processor, when I type uname -p it says "unknown". I'm believe my processor isn't working as it should; I want to make sure my two cores work at full speed. Do I have to isntall additional drivers to for my AMD64 X2 4200 processor to work correctly??.....I've just installed ubuntu Edgy and still don't know much about Linux.

Thanks.

I don't know how Edgy behaves but Feisty didn't need any extras.
I would recommend to use the DVD iso and boot from it to install, this iso will have all the bits you will need.
Also make sure you have ACPI/APIC enabled in your bios settings...
(I had to disable it when i wanted to try the 32bit fe&#305;sty, but am now using 64bit)

---

### Post by DaGGer on 2007-06-16
Hye  i was just looking through the different threads and I was curious to see if my Dual core was working and I got this when I typed in "cat /proc/cpuinfo"

> processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping        : 1
cpu MHz         : 2210.220
cache size      : 512 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm cmp_legacy
bogomips        : 4423.10
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp


---

### Post by Herix on 2007-06-16
that doesn't look good to me. This is my output:

```
uname -a
Linux heri-laptop 2.6.17-11-386 #2 Fri May 18 23:37:00 UTC 2007 i686 GNU/Linux
heri@heri-laptop:~$ 

```

And...


```
cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
stepping        : 2
cpu MHz         : 1000.000
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm cmp_legacy ts fid vid ttp
bogomips        : 4408.76

```


First it says there's only one core. On top of that, it says  cpu MHz : 1000.000, when it should be 2. something MHz. I upgraded from Dapper. Maybe it carries old configuration problems.

---

### Post by fabertawe on 2007-06-16
> **Herix said:**
> First it says there's only one core. On top of that, it says  cpu MHz : 1000.000, when it should be 2. something MHz. I upgraded from Dapper. Maybe it carries old configuration problems.

'cat /proc/cpuinfo' should show both cores, it does for me. Have a look in '/sys/devices/system/cpu', you should have 'cpu0' and 'cpu1'. 'cpu0/cpufreq' contains various info/settings.

As for the 'cpu MHz: 1000.000', that's because of the AMD "Cool'n'Quiet/Powernow" feature where the CPU's clock rate and voltage are lowered when idling.

Paul

---

### Post by DaGGer on 2007-06-16
no I only have cpu0??? I don't get it, It shows that it reads it as a dual core but it doesn't have both cores running?  I have the 64 bit version and everything.

---

### Post by Herix on 2007-06-16
I also get only cpu0.  And I also must add that sometimes my computer is not considered a 64bit when installing certain applications. Like when installing VMware I couldnt use the 64bit version, but the 32bit version ran just fine. Somebody please explain this.

---

### Post by Ocxic on 2007-06-17
> 
uname -a
Linux heri-laptop 2.6.17-11-386 #2 Fri May 18 23:37:00 UTC 2007 i686 GNU/Linux
heri@heri-laptop:~$


this tells me your running the 32-bit version and not the 64-bit version.. it should read something like this:

uname -a
Linux heri-laptop 2.6.17-11-x86_64 #2 SMP Fri May 18 23:37:00 UTC 2007 x86_64 GNU/Linux
heri@heri-laptop:~$

unless you installed the 32-bit edition on purpose

---

### Post by DaGGer on 2007-06-17
well I'm running 64 bit, but what about Linux seeing its a X2 Dual core but not showing me two cores?

---

### Post by Herix on 2007-06-22
You are right Ocxic. I had installed a 32bit version of Dapper before, and then upgrades to edgy, but it continued to be 32bit version.  I upgraded to the latest version -7.04 or whatever is called- and everything is smooth now.

---

### Post by Ocxic on 2007-06-22
thtas great, but you can;t upgrade from 32-bit to 64-bit, a re-install is required... I'm happy things are workin for you though, just wanted to make sure u knew that.

---

