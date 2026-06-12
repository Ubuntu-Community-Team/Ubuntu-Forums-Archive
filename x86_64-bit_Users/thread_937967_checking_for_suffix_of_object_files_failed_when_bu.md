---
title: "checking for suffix of object files failed when build gcc4.3.2 in ubuntu"
date: 2008-10-04
forum: x86 64-bit Users
---

### Post by simonwolf on 2008-10-04
checking for suffix of object files failed when build gcc4.3.2 in ubuntu

Hi, all.

I am a newbie to ubuntu and gcc.

When I tried to build gcc4.3.2, I encountered the following compilation error:
.....
Checking multilib configuration for libgcc...
Configuring stage 1 in i686-pc-linux-gnu/libgcc
configure: loading cache ./config.cache
checking for --enable-version-specific-runtime-libs... no
checking for a BSD-compatible install... /usr/bin/install -c
checking for gawk... gawk
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for i686-pc-linux-gnu-ar... ar
checking for i686-pc-linux-gnu-lipo... lipo
checking for i686-pc-linux-gnu-nm... /home/simon/gcc/gcc-4.3.2/objdir/./gcc/nm
checking for i686-pc-linux-gnu-ranlib... ranlib
checking for i686-pc-linux-gnu-strip... strip
checking whether ln -s works... yes
checking for i686-pc-linux-gnu-gcc... /home/simon/gcc/gcc-4.3.2/objdir/./gcc/xgcc -B/home/simon/gcc/gcc-4.3.2/objdir/./gcc/ -B/usr/local/gcc-4.3.2/i686-pc-linux-gnu/bin/ -B/usr/local/gcc-4.3.2/i686-pc-linux-gnu/lib/ -isystem /usr/local/gcc-4.3.2/i686-pc-linux-gnu/include -isystem /usr/local/gcc-4.3.2/i686-pc-linux-gnu/sys-include

**checking for suffix of object files... configure: error: cannot compute ****suffix of object files: cannot compile**

See `config.log' for more details.

make[2]: *** [configure-stage1-target-libgcc] Error 1
make[2]: Leaving directory `/home/simon/gcc/gcc-4.3.2/objdir'
make[1]: *** [stage1-bubble] Error 2
make[1]: Leaving directory `/home/simon/gcc/gcc-4.3.2/objdir'
make: *** [all] Error 2
-----------------

Is there anybody encountering the error too.

Any hint to solve this problem is appreciated.

---

### Post by cariboo on 2008-10-05
Have you installed build-essential?

Jim

---

### Post by simonwolf on 2008-10-05
Yes, I have installed build-essential before I tried to build gcc4.3.2.

---

### Post by cariboo on 2008-10-05
Is there a reson why you are building an older version of gcc than the one that is the default in Hardy?

> hardy (devel): The GNU C compiler
4:4.2.3-1ubuntu3: amd64 i386 

Jim

---

### Post by simonwolf on 2008-10-06
I have updated to gcc4.3.2. The previous version in my laptop was gcc4.2.2.

The reason why I try to build gcc4.3.2 is to learn.

---

