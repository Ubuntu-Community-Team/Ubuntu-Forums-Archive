---
title: "Turion Dapper"
date: 2006-07-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Vlad Janicek on 2006-07-13
Hey there... I have a Compaq v2410US laptop with a turion processor. I've managed to install everything --i have to confess that the wifi card gave me some headaches-- but there's something I haven't found out and it's the CPU's speed. This processor is a 1.5ghz and somehow this is my /proc/cpuinfo:

root@moore:~# more /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 36
model name      : AMD Turion(tm) 64 Mobile Technology ML-30
stepping        : 2
cpu MHz         : 795.955
cache size      : 1024 KB
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm
bogomips        : 1594.29
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

This CPU is expected to have this speed running in battery power but it's now plugged. I disabled the energy saving feature in the bios and in windows I can see that is a 1.5 ghz and runs a LOT faster than this 795Mhz. 

Using eclipse in ubuntu with this processor --maybe missconfigured kernel-- it's sooo slooooooow and using 32bits windows its quite fast. I have recompiled the kernel many many many times with different options and I have never been able to get it to run at full speed ](*,) ](*,) 

Any ideas? any patches to install?? any hidden and strange option I should compile in the kernel?? I want to use ubuntu but it's too slow with this processor :( and BTW, i need to run 64bit mode because I need to compile into 64bit processors, thats why I chose this machine

Thanks a lot

---

### Post by RAOF on 2006-07-13
Powernowd is what's scaling your processor down.  If you add the "CPU frequency scaling monitor" to one of your gnome panels, you (should) see that the processor gets scaled back when idle, and up to full speed when there's some processor load.  This is probably a good idea :)

If you want to try full-speed-all-the-time, just run ```
sudo /etc/init.d/powernowd stop
``` in a terminal.  That'll disable the freq-scaling daemon.

---

### Post by Vlad Janicek on 2006-07-13
Thank you :D it works perfectly. Now i'll read about that 

:D

---

