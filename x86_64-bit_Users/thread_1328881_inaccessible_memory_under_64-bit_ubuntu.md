---
title: "inaccessible memory under 64-bit ubuntu"
date: 2009-11-16
forum: x86 64-bit Users
---

### Post by musicologyman on 2009-11-16
Grrrrrrrrrrrrr.

I installed the 64-bit ubuntu 9.10 on my system (AMD 64 with 4 GB RAM). Unfortunately, it's acting as if I'm running the 32-bit version. Thus, when I run free -m, I get the following:

```

             total       used       free     shared    buffers     cached
Mem:          3270        800       2470          0         16        321
-/+ buffers/cache:        462       2808
Swap:           31          0         31

```

What can I do about this? I really need to use all the RAM I have.

And, for kicks, here's the output of uname -a:

```

Linux m7330n 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
```



Thanks in advance.

musicologyman

---

### Post by 3Miro on 2009-11-16
There is a BIOS remaping issue that causes 64-bit kernels to misread the amount of RAM. Many people have complained about this before, you will have to check your BIOS settings.

---

