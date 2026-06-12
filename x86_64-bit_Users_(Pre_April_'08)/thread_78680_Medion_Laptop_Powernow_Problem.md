---
title: "Medion Laptop Powernow Problem"
date: 2005-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Markuz Nightwind on 2005-10-18
Hi, i've a problem with my girlfriend's amd64 laptop. It is a Medion WAD2000 with an hoary 64 bit kubuntu (AMD64 3000+). It has only 3 power states (800Mhz, 1500Mhz, 1800Mhz); i've tried all ways (powernowd, cpufreqd, cpudyn) but with all i can't keep the laptop running for more than some minutes.
Powernowd keep the computer at full frequency when I open an application and after two minutes the computer automatically shutdown for too much heat.
Cpufreqd cannot work correctly because the computer have acpi=off (cause else the kernel doesn't boot up...) so it doesn't scale anything.
Cpudyn don't work at all (I don't know why), and all the kernel governors doesn't work well (with ondemand module i'll get the cpu locked at 800Mhz but it doesn't seem to reduce voltage, so after some minutes lockup and shutdown).

I don't know what I can do, all acpi/cpufreq modules are compiled and ok (I've double checked everything), so if anyone can help me i'll thank him/her very much.

P.S. Sorry for my horrible english, i hope u can at least understand it.

---

