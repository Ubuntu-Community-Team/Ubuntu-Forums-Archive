---
title: "The K8 Kernel"
date: 2006-05-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by R3linquish3r on 2006-05-30
I tried a search on this but I oculdnt find anything to answer my question :/

Whats the deal with this K8 kernel? Is it recommended for 64 users instead of the Generic? Incase you need to know to give the answer, my processor is an AMD 64 3200+

---

### Post by ispmarin on 2006-05-30
K8 is the name of the AMD architecture for the AMD64. The k8 Kernel is optimized for your processor/motherboard. You can check the amd page <a href=amd.com>AMD </a> and sees for yourserf.

---

### Post by R3linquish3r on 2006-05-30
Cool. Thanks for the quick reply. :)

---

### Post by rplantz on 2006-05-31
[QUOTE=R3linquish3r]
Whats the deal with this K8 kernel? Is it recommended for 64 users instead of the Generic? Incase you need to know to give the answer, my processor is an AMD 64 3200+[/QUOTE]

If you have gcc installed, the manpage for gcc shows for the -mtune=cpu-type option:
```

 k8, opteron, athlon64, athlon-fx
          AMD K8 core based CPUs with x86-64 instruction set support.  (This supersets MMX, SSE, SSE2, 3dNOW!, enhanced 3dNOW! and 64-bit instruction set extensions.)

```
and
```

 -m32
 -m64
           Generate code for a 32-bit or 64-bit environment.  The 32-bit environment sets int, long and pointer to 32 bit and generates code that runs on any i386 system.  The 64-bit environment sets int to 32 bits and long and pointer to 64 bits and generates code for AMD&#8217;s x86-64 architecture.

```

Although I have not compiled a kernel, I assume that the k8 kernels are compiled with both -mtune=k8 and -m64, while the generic (64-bit) kernels only have -m64.

---

