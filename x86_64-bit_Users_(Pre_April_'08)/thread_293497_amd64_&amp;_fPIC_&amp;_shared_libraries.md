---
title: "amd64 &amp; fPIC &amp; shared libraries?"
date: 2006-11-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by alion on 2006-11-05
It's a fact, that on certain architectures (AMD64 among them), shared libraries must be PIC enabled.

But when I'm trying to link a library I get the following message:

libc.o: relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC libc.o: could not read symbols: Bad value

So I already recompiled a bunch of the libraries my app is dependent of.
But I did that using source checkout and ./configure && make.

Is there a good-looking way to compile the whole runtime (libc + libstdc++,etc) with fPIC flag on Ubuntu?

---

### Post by kuja on 2006-11-05
I've no idea. It might be better to ask this question in the Compiling/packaging subforum.

---

### Post by RAOF on 2006-11-05
I think you'll find that there's a **libc-pic** package (and libstdc++, too).  You may wish to install it :).

---

### Post by alion on 2006-11-06
I have installed libc-pic and libstdc++-pic packages, but get an error:

/usr/lib64/gcc/x86_64-linux-gnu/4.0.4/libstdc++_pic.a
/usr/lib/libc_pic.a(init-first.os): In function `_init': multiple definition of `_init'
/usr/lib/gcc/x86_64-linux-gnu/4.0.4/../../../../lib64/crti.o:/build/buildd/glibc-2.4/build-tree/amd64-libc/csu/crti.S:37: first defined here
/usr/lib/gcc/x86_64-linux-gnu/4.0.4/libgcc_eh.a(unwind-dw2.o): In function `_Unwind_Resume': multiple definition of `_Unwind_Resume'
/usr/lib/libc_pic.a(unwind-resume.os): first defined here
/usr/bin/ld: Warning: size of symbol `_Unwind_Resume' changed from 159 in /usr/lib/libc_pic.a(unwind-resume.os) to 245 in /usr/lib/gcc/x86_64-linux-gnu/4.0.4/libgcc_eh.a(unwind-dw2.o)
/usr/bin/ld: libframesprovider_ffmpeg_amd64.so: undefined versioned symbol name pthread_cond_wait@@GLIBC_2.3.2
/usr/bin/ld: failed to set dynamic section sizes: Bad value


Something wrong happened to glibc version, It looks like some library refers to old version of it(installed version is 2.4).

---

### Post by RAOF on 2006-11-06
Not really sure what's happening there.  Is there some of your previous attempt to get this to work getting in the way?

It's hard to say without knowing what your program is, or what libraries it is dependent upon, or what you've done in the past to try and fix it :)

---

