---
title: "Xeon without EM64T"
date: 2006-03-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by molnarj on 2006-03-14
Is the AMD64 CD image is right for a Xeon processor without EM64T feature?

---

### Post by fmo on 2006-03-14
if you Xeon doesn't have EM64T then it's a 100% 32bits processor which means that you need the normal x86 CD.

Cheers

---

### Post by molnarj on 2006-03-14
[QUOTE=fmo]if you Xeon doesn't have EM64T then it's a 100% 32bits processor which means that you need the normal x86 CD.

Cheers[/QUOTE]

Somewhere I read that if no "lm" in the flags of /proc/cpuinfo, it means that no EM64T feature is exists. Is it true? Or how can I fully recognise my cpu?

---

### Post by Stormbringer on 2006-03-14
[QUOTE=molnarj]Somewhere I read that if no "lm" in the flags of /proc/cpuinfo, it means that no EM64T feature is exists. Is it true? Or how can I fully recognise my cpu?[/QUOTE]

To put it simply: "lm" is short for "Long Mode" --- the native 64-Bit Mode of AMD64 / EM64T CPUs.

If your Xeon lacks EM64T-support then your processor is 32-Bit only. As fmo already pointed out: you need to install the i386 (aka x86) Version of Ubuntu.

If you have Windows installed on that machine download CPU-Z and run it ... it'll show you all the info about your CPU(s).

[CPU-Z Homepage]("http://www.cpuid.com/cpuz.php")
[Latest CPU-Z 1.32.1]("http://www.cpuid.com/download/cpu-z-132.zip")

Cheers,
Storm.

---

