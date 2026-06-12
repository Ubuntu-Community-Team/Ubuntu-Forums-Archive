---
title: "Athlon64 X2 3800+ Problem - Single Core Recognized instead of Dual"
date: 2007-05-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Twintop on 2007-05-26
I recently (today) upgraded my desktop computer from an Athlon64 3000+ to an Athlon64 X2 3800+. I did a fresh install of Ubuntu on a new HD I installed also, and when I boot up only one processor is being recognized and my CPU type isn't being seen properly.

```
david@alethea:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : AMD Hammer Family processor - Model Unknown
stepping        : 2
cpu MHz         : 2009.291
cache size      : 512 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm
bogomips        : 4021.00
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

david@alethea:~$ 
```

```
david@alethea:~$ uname -a
Linux alethea 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux
david@alethea:~$ 
```

The biggest issue with this is that my processor is an Athlon64 X2 3800+ Toledo, NOT a Hammer (Windows' built in system info reads it the same, but CPU-Z shows it as a Toledo). System monitor only shows one processor also.

Does anyone have any advice or help with getting this processor to play nicely?

Thanks!

---

### Post by MetalMusicAddict on 2007-05-26
That is odd. Heres my 4600+:

```
[SIZE="1"]user@pc:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4600+
stepping        : 2
cpu MHz         : 1000.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc
bogomips        : 2011.54
clflush size    : 64

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4600+
stepping        : 2
cpu MHz         : 1000.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc
bogomips        : 2011.54
clflush size    : 64

user@pc:~$ uname -a
Linux dash 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux[/SIZE]
```

It does look like some or your values are combined though. If you look at mine, they're split over the 2 CPUs. Only difference looks to be I'm using the 32bit kernel.

---

### Post by Kilz on 2007-05-26
> **Twintop said:**
> I recently (today) upgraded my desktop computer from an Athlon64 3000+ to an Athlon64 X2 3800+. I did a fresh install of Ubuntu on a new HD I installed also, and when I boot up only one processor is being recognized and my CPU type isn't being seen properly.

```
david@alethea:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : AMD Hammer Family processor - Model Unknown
stepping        : 2
cpu MHz         : 2009.291
cache size      : 512 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm
bogomips        : 4021.00
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

david@alethea:~$ 
```

```
david@alethea:~$ uname -a
Linux alethea 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux
david@alethea:~$ 
```

The biggest issue with this is that my processor is an Athlon64 X2 3800+ Toledo, NOT a Hammer (**Windows' built in system info reads it the same**, but CPU-Z shows it as a Toledo). System monitor only shows one processor also.

Does anyone have any advice or help with getting this processor to play nicely?

Thanks!

Ok, So windows says its the same. Thats 2 different operating systems saying the same thing. Are you sure the motherboard you installed the x2 on supports the chip?

---

### Post by Twintop on 2007-05-26
> **Kilz said:**
> Are you sure the motherboard you installed the x2 on supports the chip?

I'm honestly not certain if that's the issue or not. I have a[ Foxconn NF4UK8AA-8EKRS Socket 939 NVIDIA nForce4 Ultra ATX AMD Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813186037") that I purchased about 2 years ago, and AMD didn't start releasing their dual core processors until the month *after* I purchased the motherboard. I was under the impression that it didn't matter/didn't have any effect since they were both Socket 939s and none of the motherboards I had looked at specified 'dual core capable'. Thoughts? :)

---

### Post by starsphereaz on 2007-05-26
**[SIZE="4"]The new  Athlon64 X2 CPUs requires a motherboard with AM2 sockets to use as dual core the 939 socket motherboards will do that too but only if you have a newer model within the past 6 months.  The older 939 socket motherboards may have slightly different voltages to the CPU socket that would only show it as a single core CPU.  You can get a great deal on a new AM2 socket motherboard at Newegg.com or your favorite place to shop.  I just build a totally new computer from scratch for under $325.00 USD (The  Athlon64 X2 3800+. MSI AM2 Motherboard, 2Gigs of ddr2 240 pin memory, the box with 400 watt power supply with 5 bays and a front panel access bay with usb-2 and sound ports).  I re-installed X86 Ubuntu 6.01 everything showed up as a dual core processor onboard. [/SIZE]**

---

### Post by Hershey on 2007-05-26
Have you tried updating your BIOS?  My A8N-SLI Deluxe is old as dirt and I upgraded to a X2 3800+ last weekend and it picked it up fine.  Looking at the specs, your motherboard should support dual core: [Supported CPUs]("http://www.foxconnchannel.com/EN-US/upload/Compatibility/200603210954407167NF4UK8AA-8EKRS.htm").

Looking at this [thread]("http://www.ocworkbench.com/ocwbcgi/ultimatebb.cgi?ubb=get_topic;f=1;t=011057;p=29"), you need to have atleast BIOS revision P39 for dual core.  Which you can get [here]("http://www.foxconnchannel.com/service/downloads.aspx").

---

### Post by Twintop on 2007-05-26
Thanks for the thoughts and input, guys. I just flashed my motherboard's BIOS on Hershey's recommendation and both cores are being recognized successfully now:

```
david@alethea:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 2
cpu MHz         : 2009.282
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
bogomips        : 4021.03
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 2
cpu MHz         : 2009.282
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
bogomips        : 4018.80
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

david@alethea:~$ 
```

```
david@alethea:~$ uname -a
Linux alethea 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux
david@alethea:~$ 

```

Is there anything special i need to do to get SMP running, or is it already working? uname -a returns the same information as before, and in Synaptic it says that linux-amd64-k8-smp (installed version 2.6.20.15.14) has been obsoleted by linux-generic (installed version 2.6.20.15.14). Should I remove the generic kernel, manually compile and install a vanilla kernel, or go another route? Thanks again!

---

### Post by dabl on 2007-05-26
It is already running both cores.  If you want to prove it, open System>Administration>System Monitor, and then you're going to have to figure out how lay a heavy processing load on it.  My example -- capture a vinyl record album as a .wav file, and then run the Gnome Wave Cleaner (gwc in the repositories) and run Edit>Declick to remove the clicks.  That is a very CPU-intensive task that will run for some minutes, I imagine, and you will be able to observe the CPU cores trading off tasks.  But even so, on my Intel Core 2 Extreme, usually one will approach 100% and the other will not get above 50% -- I don't think Linux wants them both totally saturated at the same time.

:D

---

### Post by Twintop on 2007-05-26
> **dabl said:**
> It is already running both cores.  If you want to prove it, open System>Administration>System Monitor, and then you're going to have to figure out how lay a heavy processing load on it.  My example -- capture a vinyl record album as a .wav file, and then run the Gnome Wave Cleaner (gwc in the repositories) and run Edit>Declick to remove the clicks.  That is a very CPU-intensive task that will run for some minutes, I imagine, and you will be able to observe the CPU cores trading off tasks.  But even so, on my Intel Core 2 Extreme, usually one will approach 100% and the other will not get above 50% -- I don't think Linux wants them both totally saturated at the same time.

:D

I thought it was running both but wasn't 100% sure. :) Thanks for all of the help on this guys, I really do appreciate it. :-D

The only issue I'm running in to now (that is tangentially related) is that there isn't any CPU Scaling support for the X2 3800+ Socket 939. All the searching I've done on it shows that no one under Ubuntu has been able to get it up and running at all. Oh well, that's a more minor thing anyway. :-D

---

### Post by Kilz on 2007-05-26
I was going to suggest to flash the bios, to late.

---

### Post by Hershey on 2007-05-27
Awesome!  Glad to hear flashing got it working for you!

---

