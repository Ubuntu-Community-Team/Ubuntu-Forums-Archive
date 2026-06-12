---
title: "Breezy Badger 64-bit"
date: 2005-09-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by arlie on 2005-09-27
Breezy Badger supports up to 4 gigabytes of RAM by default on 32-bit
architectures. How about 64-bit? How much memory can it support?

---

### Post by Teren on 2005-09-27
Theoretically, 17179869184 GB :D

---

### Post by kahping on 2005-09-27
use a calculator and see what 2^64 gives you. that should be how much RAM it can address in bits. divide by 8 to convert to bytes :-P

kahping

EDIT:

looks like somebody beat me to the reply :-D

---

### Post by wmcbrine on 2005-09-27
[QUOTE=kahping]use a calculator and see what 2^64 gives you. that should be how much RAM it can address in bits. divide by 8 to convert to bytes :-P[/QUOTE]Actually RAM is already addressed per byte, not bit. 64 bits of address space = 2^64 bytes of RAM.

---

### Post by Kuolio on 2005-09-28
I think most motherboards limit ram to 8gigs, even for amd64.

---

### Post by arlie on 2005-09-28
Thanks.

---

### Post by Etnu on 2005-10-02
RAM limits are pretty much entirely dependent on what your mobo will cap out at.

My Turion-based laptop will only go up to 2 GB (I think), but I run 5 dual opteron servers that each have 8 DIMM sockets (4 per CPU) that can each hold 2GB sticks, so 16GB total there.

Of course, the price point on 2GB sticks is still ridiculous, and probably will be for at least the next year or two. I suspect we won't really see systems with > 4GB of RAM in desktop / laptop systems on a regular basis for at least another 2 years. This will be especially true as long as the big PC vendors (Dell, etc.) stick with Intel, as Intel seems to be really keen on sticking in 32 bit land for most of their stuff, whereas AMD is pretty much all 64-bit across the board (Opteron, Athlon, Turion, and Sempron).

---

### Post by GuyveR800 on 2005-10-03
Besides, current AMD64 processors have a 40 bit addressing space, and a 48 bit virtual addressing space. So that's 256 TB at best :)

---

