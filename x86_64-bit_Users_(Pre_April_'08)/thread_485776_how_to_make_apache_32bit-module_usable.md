---
title: "how to make apache 32bit-module usable?"
date: 2007-06-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by kzm. on 2007-06-27
can someone help me out may be?

i try to load an apache module (*.so) that is 32bit in my 64bit apache server.. obviously it fails. is there a chance to wrap it up or something? the source code is not available.. grmpf.
i know you can use ia32 to wrap applications, can the same be used for modules? if so, how should i do this?

any help is very much welcome, i couldnt find anything of value about this particular circumstance by googeling it...

---

### Post by kzm. on 2007-06-27
hmm.. i did the ldd and it says its all fine:
        linux-gate.so.1 =>  (0xffffe000)
        libc.so.6 => /lib32/libc.so.6 (0xf7e39000)
        /lib/ld-linux.so.2 (0x56555000)

so i guess, it could run in apache?

---

