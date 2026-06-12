---
title: "Compiling boost from source and -fPIC"
date: 2008-08-16
forum: x86 64-bit Users
---

### Post by sipickles on 2008-08-16
Hi,

I am struggling with x64.

I am trying to programming using boost.python, but when I compile the c++ modules with bjam I get errors like this:

```

gcc.link.dll HybridBulletObject.so
/usr/bin/ld: HybridModule.o: relocation R_X86_64_PC32 against `(anonymous namespace)::CHybridBulletObject::Init()' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: final link failed: Bad value
collect2: ld returned 1 exit status
```

I heard somewhere that I need to recompile all my dependencies with -fPIC.

I don't know how to do this, being relatively new to Ubuntu (from Windows).

Boost compiles with bjam, so how do I specify to use the compile-flag -fPIC?

Any with other libs that use the configure/make/make install approach, what is the way to specify the -fPIC flag?

I am not calling g++ from the command line myself, but through bjam or make.

Thanks, before I revert to 32 bit!

Si

---

### Post by Yellow Pasque on 2008-08-16
Usually, you can set environment variables such as GPPFLAGS. Look in the make file for details.

---

