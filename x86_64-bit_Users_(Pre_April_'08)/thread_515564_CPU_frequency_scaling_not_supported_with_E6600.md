---
title: "CPU frequency scaling not supported with E6600"
date: 2007-08-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by litemotiv on 2007-08-02
hi all,

i'm trying to get cpu scaling working with my core2duo e6600, kernel 2.6.20-16-generic (kubuntu feisty). during boot i always get a powernowd message saying "cpu frequency scaling not supported". scaling is working properly on my side winxp install.

any ideas? is scaling support for my processor absent in the kernel, or am i doing something wrong?

lsmod | grep cpu
```

cpufreq_userspace       6176  0
cpufreq_conservative     9736  0
cpufreq_ondemand       10640  0
cpufreq_powersave       3072  0
cpufreq_stats           8416  0
freq_table              6336  2 cpufreq_ondemand,cpufreq_stats

```

lsmod | grep acpi
```

dev_acpi               17028  0
sony_acpi               7064  0
pcc_acpi               15616  0
asus_acpi              19756  0
backlight               8448  1 asus_acpi

```

sudo modprobe acpi-cpufreq
*FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.20-16-generic/kernel/arch/x86_64/kernel/cpufreq/acpi-cpufreq.ko): No such device*


with cpufreqd:
*No cpufreq interface found, not starting cpufreqd.*

with cpufreq-info:
*no or unknown cpufreq driver is active on this CPU*

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies:
*No such file or directory*

---

### Post by bollix47 on 2007-08-02
Could it be related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89927")?

---

### Post by zero-9376 on 2007-08-02
dont know if this will work as there is nothing specific about the core 2

[http://doc.gwos.org/index.php/CPUFreq](http://doc.gwos.org/index.php/CPUFreq)

---

### Post by litemotiv on 2007-08-02
> **bollix47 said:**
> Could it be related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89927")?

that sounds feasible, **sudo modprobe speedstep-centrino** gives back:

FATAL: Module speedstep_centrino not found

so i guess i would need a custom kernel then right..?

---

### Post by bollix47 on 2007-08-02
> **litemotiv said:**
> that sounds feasible, **sudo modprobe speedstep-centrino** gives back:

FATAL: Module speedstep_centrino not found

so i guess i would need a custom kernel then right..?

Or maybe upgrade to Gutsy if that is an option for you.  The longer you can wait the better chance that it will be stable, but, realistically, anything could break between now and it's October release date.

Might want to create a test partition for it and see if it solves your problem.

---

### Post by litemotiv on 2007-08-09
now testing in Gutsy, same problem unfortunately (tried both powernowd & kernel module)..

**fixed:**

recovered lost speedstep setting in bios

---

