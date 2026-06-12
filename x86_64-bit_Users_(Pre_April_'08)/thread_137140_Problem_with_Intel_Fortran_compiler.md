---
title: "Problem with Intel Fortran compiler"
date: 2006-02-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by James Long on 2006-02-27
Im trying to compile some code written in fortran.
Using g77 works fine and  get an executable whch reports as ELF64

I downloaded and installed the intel fortran compiler without problems according to [http://www.ubuntuforums.org/showthread.php?t=89571&highlight=intel+compiler](http://www.ubuntuforums.org/showthread.php?t=89571&highlight=intel+compiler)

The problem is that when I run the complier it gives errors about incompatible libraries, e.g. 
ld: skipping incompatible /usr/lib/libm.so when searching for -lm

I've tried pointing it toward /usr/lib64 with no effect and /usr/lib32 where I get the following: 
ld: warning: i386:x86-64 architecture of input file `/usr/lib/crt1.o' is incompatible with i386 output

Ive got the latest versions of IA32-libs for development.

What am I missing?


System: Athlon 64 /  Breezy


Thanks
James

---

### Post by gappy on 2006-03-02
I have experienced problems with Intel Fortran 9.0 too, but at install time. Specifically, after I choose a typical install, I receive the following message:

[FONT="Courier New"][COLOR="Blue"]rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - No such file or directory (2)

The installation program was not able to detect the IA32 version of the following libraries installed   :
libstdc++
libgcc
glibc

Without these libraries, the compiler will not function properly.
These libraries, if not installed, can be installed from
the OS discs after finishing the compiler installation.
Please refer to Release Notes for more information.[/COLOR][/FONT]

any suggestion? I am using kubuntu breezy on an athlon 3000+.

---

### Post by apecar54 on 2008-01-23
I'm having a very similar problem, so I thought I'd bump this thread up to the top.

I'm running the 64-bit version of Ubuntu Gutsy 7.10, with an Athlon 64 chip.  I just installed the Intel Fortran compiler, version 10.1.008.  The install was without issue, although I had to apt-get a bunch of 32-bit libraries for it, even though it is the "Intel 64" version of the compiler.

Anyway.  So I have a basic "Hello World" program in Fortan 90 that I've successfully compiled using gfortran.  When I try to compile the same program using ifort, I get this mess:

```
ld: skipping incompatible /usr/lib/libm.so when searching for -lm
ld: skipping incompatible /usr/lib/libm.a when searching for -lm
ld: skipping incompatible /usr/bin/../lib/libm.so when searching for -lm
ld: skipping incompatible /usr/bin/../lib/libm.a when searching for -lm
ld: skipping incompatible /usr/lib/libc.so when searching for -lc
ld: skipping incompatible /usr/lib/libc.a when searching for -lc
ld: skipping incompatible /usr/bin/../lib/libc.so when searching for -lc
ld: skipping incompatible /usr/bin/../lib/libc.a when searching for -lc
ld: skipping incompatible /usr/lib/libdl.so when searching for -ldl
ld: skipping incompatible /usr/lib/libdl.a when searching for -ldl
ld: skipping incompatible /usr/bin/../lib/libdl.so when searching for -ldl
ld: skipping incompatible /usr/bin/../lib/libdl.a when searching for -ldl
ld: skipping incompatible /usr/lib/libc.so when searching for -lc
ld: skipping incompatible /usr/lib/libc.a when searching for -lc
ld: skipping incompatible /usr/bin/../lib/libc.so when searching for -lc
ld: skipping incompatible /usr/bin/../lib/libc.a when searching for -lc
ld: i386:x86-64 architecture of input file `/usr/lib/crt1.o' is incompatible with i386 output
ld: i386:x86-64 architecture of input file `/usr/lib/crti.o' is incompatible with i386 output
ld: i386:x86-64 architecture of input file `/usr/lib/crtn.o' is incompatible with i386 output
```

Any ideas?

---

### Post by apecar54 on 2008-01-23
I think I've got it figured out.  I went to uninstall the compiler.  The uninstall script gave me:
```
Which of the following would you like to uninstall?
1.    Intel(R) Fortran Compiler for applications running on IA-32, Version 10.1.008 (/opt/intel/fc/10.1.008)
2.    Intel(R) Fortran Compiler for applications running on Intel(R) 64, Version 10.1.008 (/opt/intel/fce/10.1.008)
3.    Intel(R) Debugger for applications running on Intel(R) 64, Version 10.1.008 (/opt/intel/idbe/10.1.008)
x.    Exit

```

So Intel's installer had put BOTH the 32-bit and 64-bit compilers on my machine.  I removed the 32-bit compiler, then updated my path to look in /opt/intel/fce/..., and my "hello.f90" compiled and linked without issue.

---

