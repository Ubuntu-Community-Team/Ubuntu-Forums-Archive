---
title: "Ubuntu not reporting correct CPU speed"
date: 2005-12-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by bhilton on 2005-12-05
I definately have a iBook 500, but Ubuntu is reporting it as a 400.  Does this matter?  Is it just reporting it wrong or am I really running slower.  Is there a way to tweak it to 500?

Thanks.

 cat /proc/cpuinfo
processor       : 0
cpu             : 745/755
temperature     : 10-14 C (uncalibrated)
clock           : 400MHz
revision        : 51.17 (pvr 0008 3311)
bogomips        : 797.35
machine         : PowerBook4,1
motherboard     : PowerBook4,1 MacRISC2 MacRISC Power Macintosh
detected as     : 257 (iBook 2)
pmac flags      : 0000001b
L2 cache        : 256K unified
memory          : 640MB
pmac-generation : NewWorld

---

### Post by bhilton on 2005-12-05
Ok, I followed the directions in another post and executed "watch -n 1 cat /proc/cpuinfo", and it reported 600 mhz when starting Gimp.  

Not that I couldn't use the extra boost, but how accurate is this?

---

### Post by ssam on 2005-12-05
thats a bit odd, i am not sure if there is a lower level way measuring the speed.

you could have a look around in /sys/devices/system/cpu/cpu0/cpufreq

perhaps file a bug about it.

---

