---
title: "f77 and lg2c flag error"
date: 2006-09-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by kamikaze04 on 2006-09-29
Hi all,

I'm trying to compile an application of m work, that is written in c++ and fortran. It is compiling fine on 32 bits fedora and gentoo. Now we are giving a chance to ubuntu64. Everything compiles fine, until it says:

make[2]: Leaving directory `/home/km/project/build/myproj/Util'
make -C compiler
make[2]: Entering directory `/home/km/project/build/myproj/compiler'
make -C GCC
make[3]: Entering directory `/home/km/project/build/myproj/compiler/GCC'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/km/project/build/myproj/compiler/GCC'
make[2]: Leaving directory `/home/km/project/build/myproj/compiler'
rm -f myproj.a && ar r myproj.a `find . -name '*.o'`
ar: creating myproj.a
g++ -o fest-3.5.0 myproj.a
myproj.a(reduce.o): In function `fndiam_':reduce.f.text+0x8e9): undefined reference to `s_wsle'
:reduce.f: (.text+0x907): undefined reference to `do_lio'
:reduce.f: (.text+0x924): undefined reference to `do_lio'
:reduce.f: (.text+0x942): undefined reference to `do_lio'
:reduce.f: (.text+0x960): undefined reference to `do_lio'
:reduce.f: (.text+0x97e): undefined reference to `do_lio'
:reduce.f: (.text+0x98: undefined reference to `e_wsle'
:reduce.f: (.text+0x99c): undefined reference to `s_stop'
:reduce.f: (.text+0xa7f): undefined reference to `s_wsle'
:reduce.f: (.text+0xa9d): undefined reference to `do_lio'

And then an the error:
collect2: ld returned 1 exit status

I think actually that the error is when it tries to link,and something related with libg2c because the project is compiled with the "-lg2c" flag.

Why it is not recognizing nothing of fortran? It compiled fine, but here it seems to be missing something. 

.it's just a matter of packet...or maybe something unsupported in 64 bits? 
I have installed gcc,g++,g77 and make.

Any kind of idea? Every little comment will be very wellcome

Thanks forum!
Reply With Quote

---

