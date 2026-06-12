---
title: "Gigabyte M61VME-S2 motherboard + Athlon64 dual core + Geforce 7300GT + 2 GB DDR2"
date: 2007-06-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by trancephorm on 2007-06-23
Using newest Ubuntu 7.04 desktop AMD64. It freezes while loading kernel. Xubuntu freezes too, but it loads kernel.

Any hint?

---

### Post by dabang on 2007-07-01
I had a similar problem with my Gigabyte board before I updated the BIOS to version F6. Try booting with extra kernel parameter "noapic":
To pass any extra options to the kernel press “F6&#8243; at the start screen and add them to the line of options, which would be “noapic” (of course without the quotation marks). Then press “Enter”. If that doesn't work you may alternatively try "acpi=off". With this option Linux won't shut your computer down automatically, you'll have to press the power button after Linux has halted (just like in the old days... ;) )

---

