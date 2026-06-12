---
title: "Rigth Kernel for a Athlon64 dual core for Debian"
date: 2008-03-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by amrlima on 2008-03-16
Hi,

I have Lenny installed on my AMD Athlon 64 dual core.

vendor_id : AuthenticAMD
cpu family : 15
model : 107
model name : AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
stepping : 1
cpu MHz : 2109.545
cache size : 512 KB

my kernel is 2.6.22-3-486. I notice that system monitor only show one of the CPUs. Is this a big inconvenience? I'm wasting performance on my PC?

If so what is the best kernel for my processor? 2.6.22-3-amd64?
If I install a 64 bit kernel I will have to reinstall many 64 bit packages right?

Thanks!!
_________________
Omnia sunt communia

---

### Post by Yellow Pasque on 2008-03-16
Please run:
```
uname -a
```
I don't know if you're running an SMP kernel that can recognize both cores. You don't need a 64-bit kernel/system to see both cores,
> If I install a 64 bit kernel I will have to reinstall many 64 bit packages right?
Yes. If you've already put a lot of work into configuring your system, I would not recommend reinstalling with 64-bit.

---

