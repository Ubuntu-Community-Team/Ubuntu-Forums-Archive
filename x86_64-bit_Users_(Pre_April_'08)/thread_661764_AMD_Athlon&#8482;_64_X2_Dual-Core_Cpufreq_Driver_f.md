---
title: "AMD Athlon&#8482; 64 X2 Dual-Core Cpufreq Driver for Linux 2.10.00 in Gutsy?"
date: 2008-01-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Crinos512 on 2008-01-08
[http://www.amd.com/us-en/Processors/TechnicalResources/0,,30_182_871_13118,00.html]("http://www.amd.com/us-en/Processors/TechnicalResources/0,,30_182_871_13118,00.html")

Relese Date: September 2007

"Allows the system to automatically adjust the CPU frequency, voltage and power combination that match the instantaneous user performance need. Supports all AMD Turion&#8482; 64 Mobile Technology, AMD Opteron&#8482; Processors, and Athlon&#8482; 64 Processors released through 2007. Provides support for AMD PowerNow!&#8482; technology and, where appropriate, AMD&#8217;s Cool-n-Quiet&#8482; technology for Linux systems. Works with all kernels, version 2.6.10 or later. Requires the on demand kernel module or the cpufreq-1.20, cpuspeed-1.20.1, or powersaved-0.8.19 or later user programs to support SMP and multi-core systems. **This driver is already included in the 2.6.18 or later kernels and does not need to be downloaded again.**"

Also there are a few "AMD Power Monitor Linux Version" apps below... are these worth a look, or are there better alternatives?

---

### Post by njparton on 2008-01-08
The driver in the kernel and the powernowd daemon seem to do a good job on my NAS device.  It defaults to 1GHz and only jumps up on demand and when needed.

---

