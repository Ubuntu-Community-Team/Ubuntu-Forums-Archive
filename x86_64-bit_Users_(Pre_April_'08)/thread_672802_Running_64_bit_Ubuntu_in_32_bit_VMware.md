---
title: "Running 64 bit Ubuntu in 32 bit VMware"
date: 2008-01-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by ColonelSartoris on 2008-01-20
I have a 64 bit processor and I'm successfully running 64-bit Ubuntu in VMWare in 32 bit Windows Vista.
Why is this possible?

---

### Post by Kilz on 2008-01-20
> **ColonelSartoris said:**
> I have a 64 bit processor and I'm successfully running 64-bit Ubuntu in VMWare in 32 bit Windows Vista.
Why is this possible?

I bet its because its emulating a virtual 64bit processor. But I am almost certain you will get none of the performance improvements you would get running vmware on a 64bit os. Speed wise it will be like running a 32bit os at best.

---

### Post by bhaverkamp on 2008-01-20
The processor is not being emulated. The host OS is only used for IO. The memory and processor are used directly by your guest OS. Since your processor supports 64 bit OSs all is well. If you tried to run this on a 32 bit OS you would get failures during the installation of the guest OS.

---

### Post by bhaverkamp on 2008-01-20
I meant to say if you tried this on a 32 bit only processor you had have gotten failures during the install of the 64 bit guest.

---

