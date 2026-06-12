---
title: "AMD Phenom processor: The triple-core 2.1GHz Phenom 8400 processor"
date: 2008-08-31
forum: x86 64-bit Users
---

### Post by morgandeath on 2008-08-31
I am thinking about getting this Gateway GT5670.

1,  Will Ubuntu use all 3 cores or just one?  and/or are the Ubuntu programs that will take advantage of them?


Thanks,

Morgan

---

### Post by jespdj on 2008-08-31
Like with any other multi-core processor, Ubuntu will use all cores. Software has to be written specifically to make full use of more than one core (this is true not only on Ubuntu, but on any operating system).

---

### Post by lavinog on 2008-08-31
> **jespdj said:**
>  Software has to be written specifically to make full use of more than one core (this is true not only on Ubuntu, but on any operating system).
You can still benefit with single threaded apps if you are multitasking.
For instance sometimes I render blender files with one thread so I can use my computer for other things (I only have 2 cores).
I have also found that I can encode two files simultaneously in about the same time it takes to encode 1. (I know that many codecs are multi-threaded now, but some still claim to have issues with multi-threaded encoding)

Many games are not multi-threaded so don't expect a big gain there.

Multi-core processors really show their potential with complicated mathematical operations...such as encoding/decoding, compression/decompression.

---

### Post by felker2 on 2008-08-31
> **morgandeath said:**
> 
1,  Will Ubuntu use all 3 cores or just one?  and/or are the Ubuntu programs that will take advantage of them?




Ubuntu will use all 3 cores.

Ubuntu will "spread" the different running processes and programs across those cores, so that all cores are "working"

You can see CPU usage via "System Monitor" (GUI) and/or "htop" (CLI).

HTH

---

### Post by insane_alien on 2008-08-31
linux will work on anything from 1-255 cores depending on how you compile the kernel.

although i do believe it would be trivial to mod the kernel source so it could use any arbitrary number of cores.

---

### Post by fjgaude on 2008-08-31
The last time I checked the standard kernel is set to eight (8) cores. It can be compiled for lots more, like 255.

---

### Post by autumnraine on 2009-11-05
Hi, I'm thinking about buying a computer with this processor - does anyone know whether it runs well with the latest (k)ubuntu? I know it should. 

Thanks,
Autumn

---

### Post by autumnraine on 2009-11-05
Nevermind, bought something else.

---

