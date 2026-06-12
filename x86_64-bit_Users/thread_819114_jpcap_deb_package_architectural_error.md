---
title: "jpcap deb package architectural error"
date: 2008-06-05
forum: x86 64-bit Users
---

### Post by rotacorona on 2008-06-05
hi
im having a bit of trouble getting a .deb package
to work on my computer when i try to install it
it comes up with a wrong architect error because its made for
the i386 platform. and im running 64bit version of ubuntu is there a way to get this package working on my computer.

also might be a bit off topic but what version of ubuntu should i run i have a vaio with intel t2500 dual core 1.88ghz does that count as a standard platform or the other one.

---

### Post by Kilz on 2008-06-05
> **rotacorona said:**
> hi
im having a bit of trouble getting a .deb package
to work on my computer when i try to install it
it comes up with a wrong architect error because its made for
the i386 platform. and im running 64bit version of ubuntu is there a way to get this package working on my computer.
[This should help for applications]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs"). But if the package is a library, dont force install it.

> **rotacorona said:**
> also might be a bit off topic but what version of ubuntu should i run i have a vaio with intel t2500 dual core 1.88ghz does that count as a standard platform or the other one.
If you installed the adm64 version you have the correct version for your hardware. The install disk checks your hardware and would not install unless you had a compatible 64bit processor.

---

