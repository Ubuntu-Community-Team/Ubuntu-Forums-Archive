---
title: "[SOLVED] Xenomai - kernel problem Urgent"
date: 2008-02-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by zanak on 2008-02-12
Hello world,

I'm trying to compile the kernel with xenomai (RT) patch, i'v done this several time, but meritoriously whene I try to configure the patched Kernel (v2.6.24) using make xconfig (or menuconfig), in the Real-time subsection, I just found nothing to cinfigure the Xenomai core
all I found is that :

WARNING! You enabled APM, CPU Frequency scaling or ACPI 'processor'
NOTE: Xenomai conflicts with PC speaker support.

I disabled those warnings but I cant get the real-time sub-menu !
in the xconfig menu whene I (Options->Show all options ) I get the Xenomai tree but its diabled !!?

Any Idea !

tks a lot

p.s: sorry for the english :p

---

### Post by zanak on 2008-02-17
ok itès quiet easy, it seems that I have to verify all warnings in the xenomai sub-section to be able to see the Xenomai tree.

Solved

---

