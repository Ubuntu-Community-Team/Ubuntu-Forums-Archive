---
title: "Is my hardware compatible with 64bit"
date: 2009-06-05
forum: x86 64-bit Users
---

### Post by janeks on 2009-06-05
Hi!

I have system with:
Pentium(R) 4 CPU 2.40GHz, number of CPUs: 2
Look attached file for data from sysinfo.

Is it worth to install 64bit?
Is the motherboard components compatible?

brgds and 
Thanks in advance!

Janeks

---

### Post by steeleyuk on 2009-06-05
Your best bet is to try the Live CD, thats one of the reasons its there.

---

### Post by janeks on 2009-06-05
The available ISO is for AMD, but it does not like that I have AMD...

---

### Post by John.Michael.Kane on 2009-06-05
> **janeks said:**
> The available ISO is for AMD, but it does not like that I have AMD...

The 64 bit iso, are for both Intel, and AMD.

That said your Pentium 4 is not 64 bit compatible.

---

### Post by sanderj on 2009-06-05
```
CPU INFORMATION
        GenuineIntel, Intel(R) Pentium(R) 4 CPU 2.40GHz
        Number of CPUs: 2
        CPU clock currently at 2400.451 MHz with 512 KB cache
        Numbering: family(15) model(2) stepping(9)
        Bogomips: 4805.11
        Flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr

```

Your "Flags" does not contain " lm " (Long Mode), is thus not 64-bit, but plain 32-bit. You cannot run a 64-bit OS.

---

### Post by jespdj on 2009-06-06
Do you know what the processor number is for your Pentium 4? See [this chart](http://www.intel.com/products/processor_number/chart/pentium4.htm). I'm not sure if all Pentium 4 processors have the 64-bit extensions - the ones in that table all do. But the table doesn't seem to include the 2.4 GHz Pentium 4.

Try to find out exactly what model of Pentium 4 processor it is and use Intel's [Processorfinder](http://processorfinder.intel.com/) to check what features it supports. If it supports "EM64T" or "Intel 64", then you can run a 64-bit OS on it.

---

### Post by sanderj on 2009-06-06
> **janeks said:**
> 
Is it worth to install 64bit?


PS: apart from the fact that you **can't** install a 64-bit OS because your processor is 32-bit (see my earlier post about the missing "lm" flag), it would not be worth it as you have less than 3.5 GB RAM ("Total memory: 1265 MB").

---

