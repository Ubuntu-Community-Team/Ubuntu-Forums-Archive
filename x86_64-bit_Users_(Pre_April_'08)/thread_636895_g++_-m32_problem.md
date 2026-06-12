---
title: "g++ -m32 problem"
date: 2007-12-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by svadimr on 2007-12-10
Hello all,

When I add -m32 option to g++ I get:

/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.1.3/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.1.3/libstdc++.a when searching for -lstdc++

my machine:
$ uname -a
Linux laptop 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64

I have no idea how tell g++ to take .so from /usr/lib32 directory
I have libc6-dev-i386 installed in my system.

Please help,

---

