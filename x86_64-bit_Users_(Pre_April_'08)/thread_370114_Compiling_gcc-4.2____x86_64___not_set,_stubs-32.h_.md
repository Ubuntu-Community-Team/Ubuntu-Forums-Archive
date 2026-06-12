---
title: "Compiling gcc-4.2:  __x86_64__ not set, stubs-32.h not found"
date: 2007-02-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Dr Eigen on 2007-02-25
Hi folks

I'm trying to build gcc-4.2 (I want the latest gfortran).  In the middle of the build it borks when including gnu/stubs.h, as this tries to include gnu/stubs-32.h which doesn't exist.  Looking at stubs.h, it seems gnu/stubs-64.h (which does exist) would be included were __x86_64__ defined.  I've tried playing with the lib/lib32/lib64 logic in gcc/config/i386/t-linux64, and --disable-multilibs, to no avail.

Any clues as to how to convince configure to set the appropriate defines?

---

### Post by kuja on 2007-02-25
```
sudo apt-get install libc6-dev-i386
```

---

### Post by Dr Eigen on 2007-02-26
Thanks for that reply kuja, but that doesn't really help.  libc6-dev-i386 is already installed, but puts stubs-32.h in /usr/include/i486-linux-gnu/gnu.  The stubs.h being referenced resides in /usr/include/gnu, and looks for stubs-32.h there.

But that's really an aside.  I don't want to find stubs-32.h.  I want __WORDSIZE to be 64.  What's the point of having 64 bit CPUs and OS and running 32 bit apps?  Anyone know how I convince configure that it's on a 64 bit arch?

---

### Post by Dr Eigen on 2007-02-27
OK, I'm going to crosspost this to the programming forum... and maybe the gcc-help list.

---

### Post by Dr Eigen on 2007-03-01
After no useful help here, the programming forum or gcc-help, I worked it out.

Solution was simple:  set CFLAGS to -m64 before configure.

Strange, as the previously installed gcc produced 64 bit execs by default.

---

### Post by hellospencer on 2007-04-11
For me, installing the package  libc6-dev-i386 worked fine for copmpiling nspluginwrapper-0.9.91.2.

But I just tried, i did not look for an explanation...

---

### Post by boogachamp on 2007-05-26
> **Dr Eigen said:**
> After no useful help here, the programming forum or gcc-help, I worked it out.

Solution was simple:  set CFLAGS to -m64 before configure.

Strange, as the previously installed gcc produced 64 bit execs by default.


Thanks....almost.

I tried "CFLAGS=-m64 ./configure"  then a "make"  I still got that error:
In file included from /usr/include/features.h:346,
                 from /usr/include/stdio.h:28,
                 from ../.././gcc/tsystem.h:90,
                 from ../.././gcc/crtstuff.c:68:
/usr/include/gnu/stubs.h:7:27: error: gnu/stubs-32.h: No such file or directory


Anyone else having trouble with this?

---

### Post by boogachamp on 2007-05-30
I finally got GCC to compile turning off the multilib stuff.  I will post here later the actual compile time flags I used.

---

### Post by boogachamp on 2007-06-02
ok

so if I configure with --disable-multilib , then I can complile gcc fine, my worry is that will limit me to not be able to build 32 bit apps if for some reason I would need to in the future.  

does anybody else have a better solution?  or can anyone else shed some more insight as to the effects of disabling multilib?


per: Installing GCC: Configuration
--disable-multilib
    Specify that multiple target libraries to support different target variants, calling conventions, etc. should not be built. The default is to build a predefined set of them.

    Some targets provide finer-grained control over which multilibs are built (e.g., --disable-softfloat):

    arc-*-elf*
        biendian.
    arm-*-*
        fpu, 26bit, underscore, interwork, biendian, nofmult.
    m68*-*-*
        softfloat, m68881, m68000, m68020.
    mips*-*-*
        single-float, biendian, softfloat.
    powerpc*-*-*, rs6000*-*-*
        aix64, pthread, softfloat, powercpu, powerpccpu, powerpcos, biendian, sysv, aix.

---

### Post by Dr Eigen on 2007-06-05
Only just seen this again.

I set the **environment veriable** CFLAGS, a la

setenv CFLAGS -m64

(adapt as appropriate for sh-derivatives).  My configure was:

./configure --disable-multilib --enable-languages=fortran

I don't care that I can't make 32 bit objects.  That's why I have a 64 bit machine/OS.  ;)

---

