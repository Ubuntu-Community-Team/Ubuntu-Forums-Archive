---
title: "Sucess with AMD Athlon64 X2 4800+ ...sort of"
date: 2005-12-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by nothreat33 on 2005-12-30
I just installed ubuntu 64-bit and then the smp kernel.
I looked at the system monitor and i see two cpu's.
The 4800+ is clocked at 2.4Ghz. which is why when i checked /proc/cpuinfo
i saw something odd.
```
mike@titan:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4800+
stepping        : 2
cpu MHz         : 1005.154
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 1993.38
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4800+
stepping        : 2
cpu MHz         : 1005.154
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 1993.38
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

mike@titan:~$

```

notice this section:
```

model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4800+
stepping        : 2
cpu MHz         : 1005.154
cache size      : 1024 KB

```

It says my cpu is running at 1005.154 mhz just over 1 ghz which is less than half of what the cpu can do.
I'm not sure what to do. 
I checked my BIOS and there is no advanced configuration for the cpu to set the clock. However, the BIOS does recognize that its a 2.4Ghz processor.

Does anybody know whats going on?

```
Linux titan 2.6.12-10-amd64-k8-smp #1 SMP Thu Dec 22 11:27:46 UTC 2005 x86_64 GNU/Linux
```

---

### Post by Sutekh on 2005-12-30
Sounds like normal to me.  Ubuntu has a power management daemon called powernowd, which scales back your CPU freq when not under load, to save power and wear and tear.  

Try this command
```
watch -n 0 cat /proc/cpuinfo
```
And open some windows, play some mp3s and generally give your PC some work to do, and the frequency should go the the full 2.4GHz

This will tell you the available PCU frequencies that your Processor is capable of
```
 cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
```

There is an applet that can control the frequency of your CPU.  Right click on a panel and add the 'CPU Frequency Scaling Monitor' (actually add two, one for each core of your X2 4800), then you can control the CPU speed.

---

### Post by Mikael on 2005-12-30
Sounds like Cool 'n Quiet to me. It's a feature to reduce the clock frequency when the CPU is idling. Try checking the CPU info when the CPU is working or try to disable Cool 'n Quiet in BIOS.

Now, I don't know if Ubuntu really supports Cool 'n Quiet, but it seems as if it's the most reasonable explanation.

EDIT: Bah... I'm too slow. :)

---

### Post by nothreat33 on 2005-12-30
Disabling Cool 'n Quiet did the trick!
my cpu is now running at: 2412.374 mhz
sweeet.

Sutekh: I had a screen saver running and john the ripper and when watching the cpu frequency didn't change. i guess ubuntu doesn't support that? I dont know.



off topic: i installed ubuntu 64-bit on an alienware with the x2 4800+, its got a 256mb geforce 7800 GT card with DVI output and 5.1 suround sound.

Installing ubuntu went without a hitch, X server is working without having to mess with Xorg, and all my speakers are working. Installing the smp kernel was a breeze as well. No problems at all so far, just this one which wasn't as much a problem as it was a configuration error.

definatly A LOT easier than i had expected.

---

### Post by Sutekh on 2005-12-30
[QUOTE=nothreat33]
Sutekh: I had a screen saver running and john the ripper and when watching the cpu frequency didn't change. i guess ubuntu doesn't support that? I dont know.
[/QUOTE]

That's probably becuase the X2 4800 would kick sweet ass to the bank.  There are also 'modes' of frequency scaling called governers.

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governorscat 
/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors 
```

Will tell you the ones you have.  They all follow set parameters to determine the frequency at any one time.  I choose 'performance' when gaming, and 'conservative' for normal activity.  Then there's 'userspace' where you can choose the actual frequency.

I have a X2 3800 and I can assure you Ubuntu supports it, I think it's a great feature, but each to his own.

Yes turn of 'Cool N Quiet' in BIOS to get rid of this, or remove the powernowd daemon from startup.

---

