---
title: "cpu frequency scaling no longer works"
date: 2009-04-30
forum: x86 64-bit Users
---

### Post by ufnoise on 2009-04-30
I am using 8.04 and due to a recent upgrade, my cpu frequency scaling no longer works.

I have an Asus A8N-SLI motherboard with an nVidia nForce 4 chipset with an AMD 4200+.

This didn't seem to be an issue before, and I think it has something to do with my upgrade to kernel 2.6.24-16-generic.  Now my cpu fan is running at full speed and I can't control it.

These are the errors:
FATAL: Error inserting powernow_k8 (/lib/modules/2.6.24-16-generic/kernel/arch/x86/kernel/cpu/cpufreq/powernow-k8.ko): No such device

FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.24-16-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device

tail -f /var/log/syslog
Apr 30 03:08:58 machine kernel: [ 1739.931401] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ processors (2 cpu cores) (version 2.20.00)
Apr 30 03:08:58 machine kernel: [ 1739.932256] powernow-k8: MP systems not supported by PSB BIOS structure
Apr 30 03:08:58 machine kernel: [ 1739.932412] powernow-k8: MP systems not supported by PSB BIOS structure

Thanks for any help or suggestions you are able to give me.

Juan

---

### Post by ufnoise on 2009-04-30
Please excuse the original post.  I had two issues:
I had some "kept back" kernel packages that needed to be manually upgraded.

The frequency scaling had gotten disabled in bios.  My bios settings tend to get screwed up every time I reboot (Perhaps a bad battery.)

---

