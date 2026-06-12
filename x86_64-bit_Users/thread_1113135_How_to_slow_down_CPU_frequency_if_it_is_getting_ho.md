---
title: "How to slow down CPU frequency if it is getting hot?"
date: 2009-04-01
forum: x86 64-bit Users
---

### Post by danielkoch on 2009-04-01
Hi,

I've a trouble with my cpu on my HP Pavilion Notebook (dv5-1160).

When I'm doing hardcore work using the two cores (eg: compiling 2 programs at same time, listening music and moving files) my CPU gets hot and my laptop halts.

Before it occurs, the fan works well but I get some delay with mouse/X and mp3 decoding. I can't listen music while I'm compiling software.

I dont think it is a hardware problem, once it never happen when I'm using Vista.

My CPU is AMD Turion(tm) X2 Dual-Core Mobile RM-70 (2x).

I'm using Ubuntu 8.10 with kernel 2.6.27-11-generic (x86_64).

I've tried to put these modules in my /etc/modules, as suggested in some thread in this forum, but it doesn't work properly:

battery
ac
thermal
processor
acpi-cpufreq
cpufreq-userspace

How can I fix it?

Thank you.

---

### Post by enzomatrix on 2009-04-01
You need the powernowd package.
There's also a gnome applet to show the real CPU clock speed, where you can select the mode and/or the speed.

---

### Post by danielkoch on 2009-04-02
Hi,

I'm using the cpufreq-set to set Ghz value when it's running as 'powersave' governator.

But I can only set these steps:
available frequency steps: 2.00 GHz, 1000 MHz, 500 MHz

I can't set 1.99Ghz or 1.90Ghz.

---

### Post by Yellow Pasque on 2009-04-02
Your CPU should never overheat under normal use, even during extended periods where it's under full load. Common causes:
- Inadequate cooling (poor design, dust clogged, loose heatsink)
- The acpi module not controlling the fan properly
- Blocking the vents (sometimes happens inadvertently when you sit a laptop on something like a bed)

If you continue to overheat your CPU, you are risking physical damage to it. I'd recommend looking in the BIOS to see if there's an automatic temperature-based shutdown. I'd also recommend using a temperature monitor applet in your panel and keep an eye on the temp when you're doing CPU-intensive stuff.

> I dont think it is a hardware problem, once it never happen when I'm using Vista.
If the fan is running correctly in Ubuntu, then you could probably overheat your CPU in Vista by running two instances of something like CPUBurn or Prime95. (Don't try that experiment unless you don't care if your CPU fries.)

> I can't set 1.99Ghz or 1.90Ghz.
You won't be able to pick any speed unless you use a program that gives you full control of the p-states (like cpupowerd). Even then, your CPU is probably only scalable in 100MHz increments.

> I can't listen music while I'm compiling software.
I've had this problem (music skipping, worse under load) before too. It has to do with the kernel latency. Unfortunately, Ubuntu's kernel isn't configured optimally for desktop users.

---

