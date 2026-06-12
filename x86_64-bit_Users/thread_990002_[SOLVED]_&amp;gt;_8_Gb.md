---
title: "[SOLVED] &amp;gt; 8 Gb"
date: 2008-11-22
forum: x86 64-bit Users
---

### Post by Xeon_st on 2008-11-22
Hi there,

Just wondering if it is possible to break the 8Gb RAM limit in the 64 bit Ubuntu OS: setting up a virtal domain on the physical machine for the QA purposes.

Any comments, relevant links, suggestions are much appreciated.

---

### Post by Arup on 2008-11-22
I had no idea that x64 Intrepid is limited to 8GB ram when the Linux Kernel itself can hold more RAM than Windows x64 Kernel. In Windows x64, the limit is 128GB so I doubt that Ubuntu x64 will have less than Windows.

---

### Post by Idefix82 on 2008-11-22
There is no 8GB limit. The limit is what you can address with 64 bits, which is way more than you or your grandchildren will ever see in a computer.
Short explanation: 2³²= 4294967296 so with 32 bit you can express addresses of up to 4GB. On the other hand 2^64 is that squared, which is 18446744073709551616.

---

### Post by amauk on 2008-11-22
Theoretically, 64bit operating systems can support 16 Exabytes (that's approx 17 billion GB)

however, there are other limitations (OS, processor & motherboard each have limitations on max memory)

Current x86-64 processors have a limit of 256TB
and most consumer motherboards have far lower limits than that

Really cheap motherboards may well only support 8GB max
to be honest, you get what you pay for

But if you have the hardware, there's no reason 64bit Linux cannot support the full 16 Exabytes

It's down to the hardware

---

### Post by randiroo76073 on 2008-11-23
So far most consumer motherboards will,for the most part, max out at 16gb ram, after that you have to go with specialty boards. I know some gamers running 32gb high end Linux machines, but that's the exception rather than rule.

---

