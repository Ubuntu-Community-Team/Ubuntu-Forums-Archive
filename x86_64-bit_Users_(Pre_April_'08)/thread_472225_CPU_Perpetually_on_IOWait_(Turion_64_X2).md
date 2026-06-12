---
title: "CPU Perpetually on IOWait (Turion 64 X2)"
date: 2007-06-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by ve4cib on 2007-06-12
Hello, everyone.  I just bought an HP Pavillion dv6000-series laptop with a dual-core AMD Turion 64 X2 CPU, and am having a minor problem with it.  I don't know if this is a CPU problem, a graphics problem (see below), or something else entirely, so any help would be greatly appreciated.

When idle the CPU runs at 100%, and according to my System Monitor panel applet the CPU is in IOWait mode.  When doing very heavy calculations the CPU runs at 50% (give or take); one core is going full-out, and the other is idle.  But once the heavy calculations stop both cores go into IOWait mode, working at 100%.

When I run top Xorg comes out on top, which leads me to suspect it may be a graphics problem.  I am using the proprietary nVidia beta driver.  However, when I get rid of the

Driver    "nvidia"

line in /etc/X11/xorg.conf and replace it with

Driver    "nv"

and reboot the same problem occurs.  Thus it might not be a graphics problem at all, but I don't know.

I am currently running Ubuntu 7.04, with kernel 1.6.20-16-generic

The reason I want this solved is because the CPU running at 100% all the time seems to be messing up my CPU scaling (and thus killing my battery life).  I've attached a few files* that should hopefully contain some useful information.  If you need anything else please let me know.

Thanks a lot for the help!


*I've included xorg.conf and the nvidia bug report in case it turns out that this is a graphics problem and the thread gets moved.
cpu_info contains the output from
$cpufreq-info
$cat /proc/acpi/processor/CPU0/throttling
$cat /proc/acpi/processor/CPU0/info

---

### Post by RagingOcelot on 2007-08-27
I'd like to know the cause of this as well.  My cpus are AMD Turions as well.  This high iowait issue doesn't seem to bog the machine down in the slightest.  I'd like to get conky displaying the correct cpu usage.  Instead, it notes the usage as pretty much always very high (90-97% range).

---

