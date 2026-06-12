---
title: "64 bit intel core2duo??"
date: 2007-04-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by natman on 2007-04-23
I am running feisty on my laptop and its kinda slow ( slower than vista!!) just want to know if i have the right kernel and whatever to take full advantage of the intel core2duo 64bit

I think im using kernel 2.6.20-15generic

---

### Post by Sockerdrickan on 2007-04-23
How do you compare the speed between Windows Vista and Ubuntu?

---

### Post by Kilz on 2007-04-23
> **natman said:**
> I am running feisty on my laptop and its kinda slow ( slower than vista!!) just want to know if i have the right kernel and whatever to take full advantage of the intel core2duo 64bit

I think im using kernel 2.6.20-15generic

All 64bit kernels support smp , or the ability to use duel core processors. The amd64 version also supports the emt64 intel chips like the core2duo. Are you sure you installed the 64bit version?

---

### Post by Enverex on 2007-04-25
If you're using 64bit Gentoo then your kernel should read "Linux whatever 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux". It also sounds like you don't have your graphics drivers loaded.

---

