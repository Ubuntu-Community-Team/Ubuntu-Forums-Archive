---
title: "CPU 1 disabled"
date: 2006-04-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by gnumac on 2006-04-18
I recently installed Ubuntu breezy powerpc64 
```
uname -a
Linux Zeus 2.6.12-10-powerpc64-smp #1 SMP Sat Mar 11 17:03:13 UTC 2006 ppc64 GNU/Linux

```

When running lshw I was a bit chocked as I noticed that CPU1 was disabled. see link below. Both CPU 's are detected by the [COLOR="DarkGreen"]cat /proc/cpuinfo[/COLOR].

My question is if lshw is correct or doesn't  Ubuntu support dual CPU's for the powerpc line?
Any clues? 

After some investigation (like looking at the CPU statistics of System Monitor,m where both CPU's are registered and working) I have realized that lshw must have a bug

[http://www.itstud.chalmers.se/~it2bjar/ubuntu/hw.html]("http://www.itstud.chalmers.se/~it2bjar/ubuntu/hw.html")

```
  cat /proc/cpuinfo                           Tue Apr 18 10:45:33 2006
processor       : 0
cpu             : PPC970, altivec supported
clock           : 2000.000000MHz
revision        : 2.2

processor       : 1
cpu             : PPC970, altivec supported
clock           : 2000.000000MHz
revision        : 2.2

timebase        : 33333333
machine         : PowerMac7,2
motherboard     : PowerMac7,2 MacRISC4 Power Macintosh
detected as     : 336 (PowerMac G5)
pmac flags      : 00000000
pmac-generation : NewWorld

```

---

