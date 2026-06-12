---
title: "SMP is not working with 9.04"
date: 2009-08-05
forum: x86 64-bit Users
---

### Post by skibler on 2009-08-05
I have a quadcore intel q6600 cpu on an Asus P5K SE (p35 chipset) motherboard. I have xubuntu 9.04 installed, and the kernel right now is 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 x86_64.

Everything that reports cpu info is only reporting a single cpu/core. I have an error when I boot saying "Local APIC #0 not detected. Using dummy local APIC instead." If I try to remove the noapic and nolapic lines from my grub boot string the computer locks up while ubuntu is loading.

I had gentoo linux installed on this computer for years and smp/apic worked fine. What can I do to solve this problem with ubuntu?

---

