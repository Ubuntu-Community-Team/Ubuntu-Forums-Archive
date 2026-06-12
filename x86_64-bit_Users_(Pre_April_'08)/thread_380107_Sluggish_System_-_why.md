---
title: "Sluggish System - why?"
date: 2007-03-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by dsegarra on 2007-03-09
I have a brand new system. AMD 64 X2 processor. For some reason it is sluggish to start things such as nautilus and such. I compiled the latest 2.6.20.1 kernel and still is sluggish.  Any help/how to optimize? Any leads as to why this is happening?. My 32Bit system is faster in that sense, shouldnt be like that.


Thanks in Advance

Dan

---

### Post by diesel1 on 2007-03-09
I am also experiencing a very sluggish 64bit system.

When using 32bit Ubuntu the system was very fast and responsive even with lots of apps open,

This 64bit install is very slow even with one or two apps open.

I am using AM2 AthlonX2643800+.

Diesel1.

---

### Post by ben.s on 2007-03-09
What does /proc/cpuinfo say?

---

### Post by diesel1 on 2007-03-09
This is what /proc/cpuinfo returns....

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 2
cpu MHz         : 1000.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni cx16 lahf_lm cmp_legacy svm cr8_legacy
bogomips        : 2011.35
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 2
cpu MHz         : 1000.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni cx16 lahf_lm cmp_legacy svm cr8_legacy
bogomips        : 2011.35
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

Diesel1.

---

### Post by chrism66 on 2007-03-09
Try entering the following commands to remove the governor off your CPU's

[HTML]```

$ sudo su
$ echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
$ echo performance > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
$ watch -n 1 cat /sys/devices/system/cpu/*/cpufreq/scaling_cur_freq

```[/HTML]

---

### Post by diesel1 on 2007-03-09
Ok, my cpu cores now show 2000.00m.

I guess I just told the cpu to open the throttle a bit(?)

Thanks, please elaborate.

Diesel1.

Edit: I found this info on the net...
[http://www.thinkwiki.org/wiki/How_to_make_use_of_Dynamic_Frequency_Scaling](http://www.thinkwiki.org/wiki/How_to_make_use_of_Dynamic_Frequency_Scaling)

---

### Post by dsegarra on 2007-03-10
I fixed my problem using Edubuntu. Go figure!. Kids got more energy. Since I couldnt wait to try something different, I went ahead and installed Edubuntu. It worked. Weird.


thanks
Dan

---

### Post by Pilot-Doofy on 2007-04-21
I think I have the same problem. But when I enter the code you told me to enter, it says the file or directory cannot be found. Why would that be?

---

### Post by xfile087 on 2007-04-21
> **Pilot-Doofy said:**
> I think I have the same problem. But when I enter the code you told me to enter, it says the file or directory cannot be found. Why would that be?

That is because it's not actually a command, it's a file (someone correct me if I am wrong) so instead of typing just /proc/cpuinfo you type cat /proc/cpuinfo...

---

### Post by Pilot-Doofy on 2007-04-21
Okay, I'm a complete noob at Linux. Could you show me exactly what I would need to type? I don't know jack about any of the most basic commands. The only thing I can do in console is move, copy, and delete files/dirs.

---

### Post by xfile087 on 2007-04-21
> **Pilot-Doofy said:**
> Okay, I'm a complete noob at Linux. Could you show me exactly what I would need to type? I don't know jack about any of the most basic commands. The only thing I can do in console is move, copy, and delete files/dirs.

Okay, no problem. To get your CPU information type the following into a console

> cat /proc/cpuinfo

---

### Post by madman91 on 2007-04-21
> **Pilot-Doofy said:**
> I think I have the same problem. But when I enter the code you told me to enter, it says the file or directory cannot be found. Why would that be?

Which code, the first of the second..

If the 2nd, it is because that file does not exist. I had the same issue because I do not have a 

/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

file on my computer.

```
greg@greg-ubuntu:~$ ls -al /sys/devices/system/cpu/cpu0/
total 0
drwxr-xr-x 4 root root    0 2007-04-21 17:49 .
drwxr-xr-x 3 root root    0 2007-04-21 13:45 ..
drwxr-xr-x 5 root root    0 2007-04-21 13:45 cache
-r-------- 1 root root 4096 2007-04-21 17:49 crash_notes
drwxr-xr-x 2 root root    0 2007-04-21 13:46 topology
greg@greg-ubuntu:~$ 

```

Unless that command (echo > ....) is supposed to create that file, I think I am not doing anything wrong.

---

### Post by ronacc on 2007-04-21
what version of ubuntu are you using ? I could never get freq scaling to work right in edgy. it seems ok in feisty. in edgy ti would throtle to 50% before you could read a web page and would not unthrotle automaticly each core had to be manualy unthrotled every 2 minutes.

---

### Post by Pilot-Doofy on 2007-04-22
Here are my stats:
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 1
cpu MHz         : 2015.162
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 4034.42


I had the 64bit of Ubuntu installed first, but it was retardedly slow, so I thought it was the operating system because I had seen other people report the same problem with that version. But it turns out that my computer would have been fine to run the 64bit version, it's just that my processor is governed (or so I'm told).

I was wondering what you all could suggest that I do to increase performance on this thing. Because I really want to make the switch permanant from Windows to Linux, but with performance like this, I can't afford it.

---

