---
title: "Compiling 32bit apps on AMD64"
date: 2006-01-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by dabang on 2006-01-11
Hi!

I'm using Ubuntu 5.10 amd64 and now I'd like to know if it's possible to compile an application as 32bit application? It's because I'd like to compile gnupg with 32bit. Any suggestions? What packages would I need?
Thanks a lot!

---

### Post by koverg on 2006-01-11
Hi!

Both gcc 4.0 and 3.4 supports the -m32 option. (E.g. gcc -m32 test.c). If it complains about missing libraries during the linking you should optionally give the -L option specifying the directories containing the 32 libraries.

You may ensure that the compiled binary is 32 bit by using the "readelf -h ./a.out" command. If it says ELF32 it is a 32 bit program.

Cheers,

Gabor

---

### Post by dabang on 2006-01-12
Thanks Gabor! Is there a way of using the configure script (with make, make install)? Or does that depend on the configure script? Do I have to invoke gcc directly?

---

### Post by Suger on 2006-01-12
```
 export CC="gcc -m32"
./configure
make
sudo make install
```

---

### Post by dabang on 2006-01-13
Thanks guys! Now I'm facing another problem: the configure script stops saying, that executables cannot be compiled. I found some threads here and using google concerning this problem, but nothing helped. I tried gcc-4.0 and gcc-3.4. Any suggestions?

---

### Post by koverg on 2006-01-13
Need to look into the configure script to tell you what the problem is.
May be the program is platform specific so the configure check for a platform, and x86_64 is not supported.

Gabor

---

