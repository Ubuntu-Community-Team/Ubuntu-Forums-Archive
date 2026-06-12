---
title: "Compaq v2000z ACPI/fan problem"
date: 2006-07-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by tr1cky on 2006-07-22
I have been running ubuntu on my compaq v2000z without many problems for some time now. After installing ubuntu dapper, I had a kernel panic that I could only resolve by turning off ACPI (adding noacpi and acpi=off) to the boot line in GRUB. Since this is a laptop though, it's not really acceptable to have ACPI off. The result has been that the fan for my video card NEVER runs and no matter what level of activity I'm engaged in, the laptop gets fairly hot after only a few minutes. It also can't shut itself down... that's just obnoxious. In short I really need to figure out what is wrong with ACPI (or my kernel or whatever) that prevents me from booting with ACPI on.

If someone could tell me where the log file is, I'll find and post it, here's the last line though:

[10.990615]<0>Kernel panic - not syncing: Attempted to kill init!

Thanks for any help! :]

---

### Post by cnlohfin3109 on 2006-07-25
i actually had the same problem with gateway m275, the noapci works great thanks!

---

