---
title: "asterisk complilation problem"
date: 2008-03-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Varadhan on 2008-03-01
am compiling asterisk(soft PBX) in static mode in ubuntu 7.10 server edition, i got the following error:

everything goes through fine, problem comes at last when it does linking

```

/usr/lib/gcc/x86_64-linux-gnu/4.1.3/../../../../lib/libpthread.a(lowlevellock.o): In function `__lll_mutex_lock_wait':
(.text+0x0): multiple definition of `__lll_mutex_lock_wait'
/usr/lib/gcc/x86_64-linux-gnu/4.1.3/../../../../lib/libc.a(libc-lowlevellock.o):(.text+0x0): first defined here
/usr/lib/gcc/x86_64-linux-gnu/4.1.3/../../../../lib/libpthread.a(lowlevellock.o): In function `__lll_mutex_unlock_wake':
(.text+0x110): multiple definition of `__lll_mutex_unlock_wake'
/usr/lib/gcc/x86_64-linux-gnu/4.1.3/../../../../lib/libc.a(libc-lowlevellock.o):(.text+0x30): first defined here

```

it seems to be ubuntu libc.a and libpthread.a library has same function name ?
can anyone help me out of this ? any suggestion ?

---

