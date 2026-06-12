---
title: "Enable DMA on x86_64 Real Time Kernel"
date: 2008-01-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by lexum on 2008-01-17
I tried to enable DMA on hdb using the command:

**hdparm -d1 /dev/hdb**

i get:

[B]/dev/hdb:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma     =  0 (off)[/B]

i do:

[B]cd /usr/src/linux
make xconfig[/B]

and check:

**Enable DMA only for disks**

and save.  then I do:

[B]make clean
make dep
make bzImage[/B]

and get:

[B]make[1]: *** No rule to make target `arch/x86_64/kernel/asm-offsets.c', needed by `arch/x86_64/kernel/asm-offsets.s'.  Stop.
make: *** [prepare0] Error 2[/B]

why?  please help.

---

