---
title: "Query bitness of library"
date: 2008-08-27
forum: x86 64-bit Users
---

### Post by ikus060 on 2008-08-27
Hi,

I'm running Ubuntu on a 64bits platfrom and I got some library (.so) compile and want to be sure it's compile as 64bits and not 34 bits. There is a command line to do such ?

Thanks for your help.

ikus060

---

### Post by jespdj on 2008-08-27
Yes, the command is named "file". For example:
```

$ cd /usr/lib
$ file libglib-2.0.so.0.1600.4
libglib-2.0.so.0.1600.4: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), stripped

$ cd /usr/lib32
$ file libexif.so.12.2.0
libexif.so.12.2.0: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), stripped
```

---

