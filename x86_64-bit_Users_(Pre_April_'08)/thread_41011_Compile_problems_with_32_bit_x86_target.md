---
title: "Compile problems with 32 bit x86 target"
date: 2005-06-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by drach on 2005-06-11
I seem to be missing some critical library for compiling 32 bit programs:

$ gcc -m32 -c hello.c
$ file hello.o
hello.o: ELF 32-bit LSB relocatable, Intel 80386, version 1 (SYSV), not stripped
$ gcc -m32 -o hello hello.o
/usr/bin/ld: skipping incompatible /usr/lib/gcc-lib/x86_64-linux/3.3.5/./libgcc.a when searching for -lgcc
/usr/bin/ld: skipping incompatible /usr/lib/gcc-lib/x86_64-linux/3.3.5/libgcc.a when searching for -lgcc
/usr/bin/ld: cannot find -lgcc
collect2: ld returned 1 exit status
$ locate libgcc.a
/usr/lib/gcc-lib/x86_64-linux/3.3.5/libgcc.alo

---

### Post by drach on 2005-06-12
further discussion is in

[http://www.ubuntuforums.org/showthread.php?t=9957&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=9957&page=1&pp=10)

---

