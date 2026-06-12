---
title: "Q6600 showing freq values way too low"
date: 2008-04-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by androticus on 2008-04-09
I recently installed Kubuntu 64 on my Q6600 desktop. I just OC'ed it to 3.0GHz using 333 FSB (from stock 2.4 GHz @ 266 FSB)

At this point

/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
shows
900000 600000

Of course these are WAY too low! All the other related files have similar values (either of those).

Any idea what gives? 

thanks for any tips

---

### Post by tamoneya on 2008-04-09
I have a pretty much identical setup.  I have mine OCed to 9x336 and i am still going up.
here is the output of cat /proc/cpuinfo```
tamoneya@ubuntu0:~$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Quad CPU           @ 2.40GHz
stepping	: 7
cpu MHz		: 3024.002
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 6051.75
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Quad CPU           @ 2.40GHz
stepping	: 7
cpu MHz		: 3024.002
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 6048.00
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Quad CPU           @ 2.40GHz
stepping	: 7
cpu MHz		: 3024.002
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 6048.01
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Quad CPU           @ 2.40GHz
stepping	: 7
cpu MHz		: 3024.002
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 3
cpu cores	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 6048.01
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

```
You will notice that while it says "Intel(R) Core(TM)2 Quad CPU           @ 2.40GHz"  This is just the model name.  Later on it says:"cpu MHz		: 3024.002"  This is the measured speed and this is what it is actually running at.

---

### Post by androticus on 2008-04-09
Mine just all say:
cpu MHz: 600.000

---

### Post by tamoneya on 2008-04-09
Is that from /proc/cpuinfo or available frequencies as you posted above.  Can you confirm this in windows?  What motherboard are you using?  How long have you had it clocked this high?

---

### Post by GTengineer on 2008-04-09
This is due to a feature called SpeedStep in the BIOS. It lowers the CPU multiplier to reduce the clock speed, power consumption and heat output. If you disable it, it will show the correct clock speed with cat /proc/cpuinfo but it is better to leave it on. For example my Q6600 is running at 3.8GHz (9x423) but it shows up as 2538MHz (6x423) because the multiplier is dropped to 6 automatically when the machine is idle or under very small load. Having SpeedStep enabled does not affect performance at all nor does it affect overclocking stability despite popular belief.

---

### Post by androticus on 2008-04-09
But why is my system showing either 600MHz or 900MHz? 

avail_frequencies lists this:
600000 900000

---

### Post by fjgaude on 2008-04-09
> **GTengineer said:**
> This is due to a feature called SpeedStep in the BIOS. It lowers the CPU multiplier to reduce the clock speed, power consumption and heat output. If you disable it, it will show the correct clock speed with cat /proc/cpuinfo but it is better to leave it on. For example my Q6600 is running at 3.8GHz (9x423) but it shows up as 2538MHz (6x423) because the multiplier is dropped to 6 automatically when the machine is idle or under very small load. Having SpeedStep enabled does not affect performance at all nor does it affect overclocking stability despite popular belief.

Very interesting. The Intel SpeedStep is not handled too well yet by Ubuntu's kernel. It works as it should, I think, if you don't overclock and leave the CPU at stock values. Even then only two speeds are available with my E8400 Core 2 Duo, 2000 and 3000. When I overclock the CPUFreq Scalling stops working, period. I have a late model Gigabyte MB, ga-p35-ds4. Works great and quick as I overclock it with raid5 array for data:

With Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz), fan at 908 RPM; no-load, temp=24C; under max load, temp=41C, fan=1167 RPM; VCore=1.39/1.38v:

```
root@sunshine:/home/frank# hdparm -tT /dev/md32
 Timing cached reads:   18948 MB in  2.00 seconds = 9487.52 MB/sec
 Timing buffered disk reads:  644 MB in  3.00 seconds = 214.42 MB/sec
```

The idea of saving power and being green doesn't go with overclocking, eh? Pray tell, what CPU cooler are you using?

---

### Post by alecmg on 2008-06-02
> **fjgaude said:**
>  Even then only two speeds are available with my E8400 Core 2 Duo, 2000 and 3000. When I overclock the CPUFreq Scalling stops working, period. I have a late model Gigabyte MB, ga-p35-ds4. 

The idea of saving power and being green doesn't go with overclocking, eh? 
I have e8200 and too Gigabyte EX38. Same thing - if I overclock, cpufreq stops working.
People at phoronix guessed that gigabyte mobo is to blame.
(yet in Windows SpeedStep works without a glitch, even lowering the voltage)

---

