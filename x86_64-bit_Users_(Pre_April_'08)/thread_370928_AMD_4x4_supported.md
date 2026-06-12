---
title: "AMD 4x4 supported?"
date: 2007-02-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by lukej on 2007-02-26
Can anybody confirm or deny if Ubuntu supports the AMD 64 bit 4x4 (dual dual-cores) processor setup?

I am looking to purchase:
ASUS L1N64-SLI WS Dual Socket L
2x AMD Athlon 64 FX-74 Windsor 3.0GHz

I just want to make sure that any special drivers that this setup might require are supported by the kernel and/or Ubuntu.

---

### Post by John.Michael.Kane on 2007-02-26
The chips should show up as four cores.

You main research should be around the two item below as this board seems fairly new I'm not sure the support is there yet for these. 

NVIDIA nForce 680a

Silicon Image Sil3531

At the very least you "may" have to compile a kernel with support for these

---

### Post by lukej on 2007-02-27
Any ideas where I could look for support of those components?  If I'm not mistaken, that would be the motherboard chipset, and the external SATA controller.  I don't care as much about the external SATA controller, since there are 12 internal SATA ports.

However, I would say that support for the motherboard's chipset would be critical to proper operation, wouldn't it?  I've searched on quite a few Linux forums for anything concerning the 680a chipset, but no results.  I also set Asus an email, but I haven't got a response yet.

Thanks!
Luke

---

