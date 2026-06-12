---
title: "Does this mean I need more memory/swap?"
date: 2008-08-29
forum: x86 64-bit Users
---

### Post by choey on 2008-08-29
This is my workstation, and it was working fine on XP, but I recently switched to Ubuntu 8.04 since I found myself using cygwin a lot with lots of frustrations.

Anyway, here is the top portion of my top report... no pun intended:
```
top - 21:47:30 up 11:10,  7 users,  load average: 0.58, 0.65, 0.48
Tasks: 168 total,   1 running, 167 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.3%us,  4.2%sy,  0.0%ni, 86.0%id,  0.4%wa,  0.1%hi,  0.1%si,  0.0%st
Mem:   2061132k total,  2037372k used,    23760k free,     8544k buffers
Swap:   996020k total,   995532k used,      488k free,   107440k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 9697 root      20   0  305m 119m  27m S   24  5.9  17:12.84 Xorg
 9816 scho      20   0  176m  19m 4440 S   23  1.0   3:17.12 vino-server
18993 scho      20   0 84156 5216 1584 S    2  0.3  13:35.99 npviewer.bin
10429 scho      20   0 1061m 121m 3128 S    1  6.0   8:27.17 java
26699 scho      20   0 1577m 690m  11m S    1 34.3  14:03.89 java
 9805 scho      20   0  131m 3864 2816 S    1  0.2   0:18.02 gnome-screensav
 9923 scho      20   0  192m 3356 2212 S    1  0.2   0:22.24 nm-applet
10330 scho      20   0  230m  10m 4992 S    1  0.5   1:56.51 gnome-terminal
 9900 scho      20   0  833m 513m 506m S    0 25.5   6:39.98 compiz.real
13867 scho      20   0 18992  832  528 R    0  0.0   1:20.22 top
23034 scho      20   0  278m 9752 4276 S    0  0.5   0:30.26 p4v.bin
    1 root      20   0  4020  336  256 S    0  0.0   0:02.68 init
```

I'm remoting in from home, so that's probably why we see ~25% on Xorg and vino-server... I don't think I saw this at work.

My meminfo:
```
MemTotal:      2061132 kB
MemFree:         21900 kB
Buffers:          9080 kB
Cached:         108148 kB
SwapCached:     144668 kB
Active:         891692 kB
Inactive:       528004 kB
SwapTotal:      996020 kB
SwapFree:          580 kB
Dirty:             804 kB
Writeback:           0 kB
AnonPages:     1160820 kB
Mapped:         557500 kB
Slab:            36488 kB
SReclaimable:    10932 kB
SUnreclaim:      25556 kB
PageTables:      26412 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   2026584 kB
Committed_AS:  3346816 kB
VmallocTotal: 34359738367 kB
VmallocUsed:     42960 kB
VmallocChunk: 34359694843 kB
```

My cpuinfo:
```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Xeon(R) CPU            5130  @ 2.00GHz
stepping	: 6
cpu MHz		: 1994.998
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx tm2 ssse3 cx16 xtpr dca lahf_lm
bogomips	: 3992.98
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Xeon(R) CPU            5130  @ 2.00GHz
stepping	: 6
cpu MHz		: 1994.998
cache size	: 4096 KB
physical id	: 3
siblings	: 2
core id		: 0
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx tm2 ssse3 cx16 xtpr dca lahf_lm
bogomips	: 3990.06
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Xeon(R) CPU            5130  @ 2.00GHz
stepping	: 6
cpu MHz		: 1994.998
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx tm2 ssse3 cx16 xtpr dca lahf_lm
bogomips	: 3990.06
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Xeon(R) CPU            5130  @ 2.00GHz
stepping	: 6
cpu MHz		: 1994.998
cache size	: 4096 KB
physical id	: 3
siblings	: 2
core id		: 1
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx tm2 ssse3 cx16 xtpr dca lahf_lm
bogomips	: 3990.05
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

```

Finally, my glxgears output:
```
8120 frames in 5.0 seconds = 1623.850 FPS
8456 frames in 5.0 seconds = 1690.937 FPS
8314 frames in 5.0 seconds = 1662.601 FPS
8366 frames in 5.0 seconds = 1673.034 FPS
8265 frames in 5.0 seconds = 1652.740 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 38 requests (38 known processed) with 0 events remaining.
```

I don't know what the last error message is. I haven't seen it before. But anyway, I've got the nvidia driver installed and beryl is very snappy... at first.

What happens is I run like 3 java server applications with 2~3 instances of IntelliJ IDEA (I've tried adjusting its vmoptions to some effect, but the lag persists). I've also got XP on vmware running... (closing this doesn't seem to help the lag) At boot beryl is very snappy and everything is very fast. But after running all my necessary apps, it frequently lags very badly--even my mouse! So, I'm wondering whether this was worth the switch to linux. It seems as though a coworker with debian (KDE) on same computer specs has no probs.

Do I need more memory? Swap? Or what am I doing wrong...? Do I need to recompile the kernel with only the necessary modules?

I even tried using gparted to resize the swap partition... but it won't let me resize ANY of my partitions: /, /boot, swap, and an ntfs partition. Sigh. Halp! :confused:

---

### Post by Temposs on 2008-08-29
hi choey. I'm glad you're trying ubuntu. Let's try to figure out what's slowing down your system.

It looks like your compiz.real process is using way too much, compared to what mine uses. My compiz.real process is only using 10mb of memory. Yours is using 25%, or 512mb, if you have 2gb total....

There are some compiz features that really take a ton of resources. Off the top of my head, two are Cube Reflection and 3D Windows. Make sure you have those disabled. 

If those are already disabled, try turning off compiz and see if your system runs better. If it does, try going to the "Normal" compiz setting and see if that works alright. If that works, go to "Extra". Then you can customize with extra features as you like. That should get you to a compiz level appropriate to your system's capacity.

I have 2gb of RAM and a 1.5ghz pentium m processor and my system runs fine with plenty of compiz features enabled.

---

### Post by Jouke74 on 2008-08-29
How much memory did you assign to VMware + XP? Because if you made it more than 1 Gb and you are running some other memory intensive programs you simply reached your max and your computer will start swapping resulting in serious slowness.

Make sure you have installed all updates, this might resolve some memory leaks. More memory and swap will never hurt. 

Plain Ubuntu on my PC will use about 380 mb of memory. Also still after 5 days of use.

---

### Post by choey on 2008-08-29
The thing I like the most about this community is that everyone's willing to help at anytime, with anything, unlike some boards where most of the times the reply is "there is a search function just for you." You guys :guitar: !

I didn't know the memory column was in percentage! That makes a huge difference! LOL I thought compiz is just taking 25MB of memory.. hehe. I tried enabling all pretty features. I guess I'll try disabling it.

As for vmware, I had assigned it 512MB of memory, but I brought it down to 256MB, I think. This made a difference. It even made vmware to run faster. lol

I'll try experimenting with these a bit and give you guys an update. Thanks, again!

---

### Post by choey on 2008-08-29
Here is after boot and two IDE instances running. Very snappy at this point:
```
top - 09:29:06 up 4 min,  2 users,  load average: 0.94, 0.52, 0.22
Tasks: 134 total,   2 running, 132 sleeping,   0 stopped,   0 zombie
Cpu(s): 16.6%us,  2.7%sy,  0.0%ni, 80.5%id,  0.1%wa,  0.1%hi,  0.1%si,  0.0%st
Mem:   2061132k total,  1329868k used,   731264k free,    21360k buffers
Swap:   996020k total,        0k used,   996020k free,   518012k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6325 scho      20   0 1531m 433m  38m S   68 21.5   0:39.04 java
 5598 root      20   0  192m  63m  13m S    2  3.1   0:05.68 Xorg
 6094 scho      20   0  275m  36m  11m S    1  1.8   0:03.56 compiz.real
 6228 scho      20   0  516m 103m  24m S    1  5.2   0:06.08 firefox
 6142 scho      20   0  134m 9280 7092 S    1  0.5   0:00.26 gtk-window-deco
 6206 scho      20   0  258m  22m  11m R    1  1.1   0:00.36 gnome-terminal
 6226 scho      20   0 18992 1272  932 R    1  0.1   0:00.30 top
```

This is after running three java services and building a project:
```
top - 09:37:22 up 12 min,  5 users,  load average: 0.33, 0.61, 0.44
Tasks: 143 total,   1 running, 142 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.6%us,  0.3%sy,  0.0%ni, 97.1%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2061132k total,  1940740k used,   120392k free,     5764k buffers
Swap:   996020k total,    54500k used,   941520k free,   275276k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 7157 scho      20   0  792m  89m  10m S    3  4.4   0:04.95 java
 6206 scho      20   0  263m  26m  11m S    1  1.3   0:02.60 gnome-terminal
 5598 root      20   0  219m  84m  14m S    1  4.2   0:17.02 Xorg
 6094 scho      20   0  286m  39m  12m S    1  2.0   0:07.90 compiz.real
 6228 scho      20   0  579m  93m  24m S    0  4.6   0:13.04 firefox
 7125 scho      20   0 1030m 450m  13m S    0 22.4   0:50.14 java
 7181 scho      20   0  443m 209m  10m S    0 10.4   0:16.96 java
```

And this is after running XP on vmware:

```
top - 09:40:50 up 15 min,  5 users,  load average: 1.34, 0.90, 0.57
Tasks: 148 total,   1 running, 147 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.8%us,  1.0%sy,  0.0%ni, 97.0%id,  1.2%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2061132k total,  2037452k used,    23680k free,      644k buffers
Swap:   996020k total,    54396k used,   941624k free,   312080k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 7552 root      10 -10  264m  43m  37m S    8  2.1   0:12.90 vmware-vmx
 7125 scho      20   0 1030m 450m  13m S    1 22.4   0:51.77 java
 5598 root      20   0  256m 109m  33m S    1  5.5   0:21.80 Xorg
 6206 scho      20   0  263m  26m  11m S    1  1.3   0:03.02 gnome-terminal
 7540 root      20   0 44404  29m  16m S    1  1.5   0:02.80 vmware
 6228 scho      20   0  586m  99m  24m S    0  4.9   0:14.48 firefox
 7157 scho      20   0  792m  92m  10m S    0  4.6   0:05.87 java
    1 root      20   0  4020  868  600 S    0  0.0   0:02.66 init
```
Still very snappy! It's very acceptable. I guess compiz was eating up a lot of memory... I knew the eye-candy wasn't for free :( I miss my wiggly windows, but good to have a snappy system back. :)

I'll bug you guys a bit more if I find the system slowing down later today. Thanks for the help guys!

---

