---
title: "3 GHz Xeon runs at 900 MHz"
date: 2009-02-28
forum: x86 64-bit Users
---

### Post by clarge2 on 2009-02-28
I just pulled my 8.04 server install from my closet and upgraded it to 8.10 desktop. After I upgraded and rebooted, I was amazed to find that my cpu running at only 900 MHz on "Performance." Here's what I know so far.

cat /proc/cpuinfo:
```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Xeon(R) CPU           E3110  @ 3.00GHz
stepping	: 6
cpu MHz		: 900.000
cache size	: 6144 KB
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 5984.90
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Xeon(R) CPU           E3110  @ 3.00GHz
stepping	: 6
cpu MHz		: 900.000
cache size	: 6144 KB
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 5984.94
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:
```
cpufreq-info:
```
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 600 MHz - 900 MHz
  available frequency steps: 900 MHz, 600 MHz
  available cpufreq governors: ondemand, powersave, userspace, conservative, performance
  current policy: frequency should be within 600 MHz and 900 MHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 900 MHz (asserted by call to hardware).
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 600 MHz - 900 MHz
  available frequency steps: 900 MHz, 600 MHz
  available cpufreq governors: ondemand, powersave, userspace, conservative, performance
  current policy: frequency should be within 600 MHz and 900 MHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 900 MHz (asserted by call to hardware).
```
I did quite a bit of searching through the forums and Google, but found that most of the related problems revolved around the CPU Frequency Monitor. My monitor works just fine, it's the acpi (maybe?) that's not.

---

### Post by bford16 on 2009-02-28
It looks like your computer thinks this is a Pentium iii Xeon, which did in fact run at 900Mhz.  Wouldn't that be funnny?

---

### Post by amauk on 2009-02-28
This is completely normal

This is caused by an Intel power saving system, called StepSpeed

when your CPU is idle, the [multiplier]("http://en.wikipedia.org/wiki/CPU_multiplier") will be reduced

this reduces the clock speed when idle (Ie. not needed), reducing power consumption and heat generated
The multiplier is raised in increments, to compensate for higher loads

As I said, this is completely normal, and these types of power saving mechanisms have been on Intel & AMD chips for a while

---

### Post by clarge2 on 2009-03-01
Correct me if I'm wrong, but shouldn't it run at something higher than 900 MHz if it's being taxed? I guess I should encode a video and run top at the same time to see what the result is. My suspicion is that the system really does think that the cpu max is 900.

---

### Post by lswb on 2009-03-01
> **clarge2 said:**
> Correct me if I'm wrong, but shouldn't it run at something higher than 900 MHz if it's being taxed? I guess I should encode a video and run top at the same time to see what the result is. My suspicion is that the system really does think that the cpu max is 900.

My older laptop has a 1.4Ghz Pentium M. It "idles" at 600Mhz. With a web browser and audio playing it still stays at 600. but if I play a video at the same time it bumps it up to max. This is according to the same /proc/cpuinfo info you are using. 

Your system being dual core and a more advanced processor, it might require more of a load before the processor speed is increased.

---

### Post by amauk on 2009-03-01
if you do
```
watch -n 1 cat /proc/cpuinfo
```
you can see what happens when you load up the machine

---

### Post by clarge2 on 2009-03-01
I'll try that and post the results, provided there is still an issue.

Update: When I turned the machine on to test this out, the CPU showed 1.6 GHz as the ondemand speed. It jumped to 2.4 GHz when I ran ffmpeg on a short avi-mpg conversion. I don't know what caused the change, but we should consider the problem solved.

Thanks all for the help!

---

### Post by jespdj on 2009-03-01
> **amauk said:**
> This is completely normal

This is caused by an Intel power saving system, called StepSpeed
It's normal that an idle processor runs at a low clock speed. And Intel's technology is called SpeedStep (not StepSpeed).

However, it looks like the OP really has a problem, because cpufreq-info only reports two available speeds: 600 and 900 MHz. That's definitely not as it should be.

On my Core 2 Duo T9300 (max. speed 2.5 GHz), it says:
```

jesper@jesper-laptop:~$ cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 2.50 GHz
  available frequency steps: 2.50 GHz, 2.50 GHz, 2.00 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: powersave, userspace, ondemand, conservative, performance
  current policy: frequency should be within 800 MHz and 2.50 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 2.50 GHz
  available frequency steps: 2.50 GHz, 2.50 GHz, 2.00 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: powersave, userspace, ondemand, conservative, performance
  current policy: frequency should be within 800 MHz and 2.50 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.

```

---

### Post by bford16 on 2009-03-01
> **amauk said:**
> if you do
```
watch -n 1 cat /proc/cpuinfo
```
you can see what happens when you load up the machineA good program for testing is "glxgears". You can open up a Terminal and run the 'watch' command, then open a new Terminal and run this code.```
glxgears
```Use Ctrl+c to stop the program.

---

