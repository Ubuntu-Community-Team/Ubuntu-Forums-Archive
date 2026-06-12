---
title: "C compiler can't create executables"
date: 2007-06-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by enderandrew on 2007-06-30
I am running Kubuntu Feisty 7.04 x86_64 with the stock toolchain.  I tried compiling a few KDE addons, such as the latest version of Yakuake, except I can't compile anything.  So I removed binutils, glibc and gcc and reinstalled them.  No joy.  Here is a sample config.log to show the error I'm getting.

```
configure:3417: gcc --version >&5
gcc (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:3420: $? = 0
configure:3427: gcc -v >&5
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release x86_64-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
configure:3430: $? = 0
configure:3437: gcc -V >&5
gcc: '-V' option must have argument
configure:3440: $? = 1
configure:3463: checking for C compiler default output file name
configure:3490: gcc     conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:3493: $? = 1
configure:3531: result: 
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "yakuake-2.8-beta1"
| #define VERSION "3.5.6"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:3538: error: C compiler cannot create executables
See `config.log' for more details.

```

---

### Post by PaulFr on 2007-06-30
**sudo apt-get install build-essential** should help.

---

