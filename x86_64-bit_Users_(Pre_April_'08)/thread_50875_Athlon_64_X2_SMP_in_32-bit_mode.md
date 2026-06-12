---
title: "Athlon 64 X2 SMP in 32-bit mode?"
date: 2005-07-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by dustyculler on 2005-07-21
I've just put a system together with an Athlon 64 X2 4200+ and am having to use 32-bit Ubuntu as there doesn't seem to be a 64 bit driver for my Adaptec ATA Raid 2400A card, and the installer is unable to find any drives to install to in 64-bit mode.

My question is are there smp kernels that I can use with this cpu in 32-bit mode?  Will the K7 smp kernels or the i686 smp kernels work ok, or do you really need to be running in 64-bit mode and use a k8 smp kernel?

Thanks in advance.

(Or if anyone knows how to install to a raid array on an adaptec 2400A, that would be great as well)

---

### Post by dustyculler on 2005-07-21
Maybe another question needs to be asked here as well.
Do the X2 processors handle smp internally, or do you still need an smp kernel to take advantage of the second core?

---

### Post by joekr on 2005-07-21
[QUOTE=dustyculler]Maybe another question needs to be asked here as well.
Do the X2 processors handle smp internally, or do you still need an smp kernel to take advantage of the second core?[/QUOTE]

SMP must be used else only one of your cores will work... **OR** you can post me your X2 and I'll post you back a 4000+ single core ;)

---

### Post by dustyculler on 2005-07-22
Thanks for the reply.  I think I'll hang on to the X2 for now.

So does anyone know if a K7 or i686 smp kernel would work with an X2 in 32-bit mode so I can at least use both cores?

---

### Post by Forge on 2005-09-01
Yes, both will work. The k7-smp should get you just a tad more functionality than i686-smp, though.

i686 = MMX
K7 = MMX, MMXext, 3Dnow!

K8 = MMX, MMXext, 3Dnow!, 3Dnow! Pro aka SSE1, SSE2.

---

