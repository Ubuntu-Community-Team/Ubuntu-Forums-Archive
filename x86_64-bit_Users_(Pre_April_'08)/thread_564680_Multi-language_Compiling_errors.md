---
title: "Multi-language Compiling errors"
date: 2007-10-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by NFITC1 on 2007-10-01
I've asked this on the related program's forum, but no one seems to have much experience with this so I'll ask it here too.
I've been posting before about not getting OpenGL to work and I realized my problem was that I was using Mesa and not the actual accelerating drivers. So now my system reports that it's using ati's drivers and that OpenGL should work on 2D and 3D apps. I thought that would solve the problem but it did not. So I wonder if it might be some of these other errors that I'm getting. It's a 32-bit app that uses gcc, g++ and nasm to compile (zsnes 1.51 if that makes a difference, which it might):
 
```
/usr/bin/ld: skipping incompatible /usr/lib/libpthread.so when searching for -lpthread
/usr/bin/ld: skipping incompatible /usr/lib/libpthread.a when searching for -lpthread
/usr/bin/ld: skipping incompatible /usr/lib/libpthread.so when searching for -lpthread
/usr/bin/ld: skipping incompatible /usr/lib/libpthread.a when searching for -lpthread
/usr/bin/ld: skipping incompatible /usr/lib/libncurses.so when searching for -lncurses
/usr/bin/ld: skipping incompatible /usr/lib/libncurses.a when searching for -lncurses
/usr/bin/ld: skipping incompatible /usr/lib/libncurses.so when searching for -lncurses
/usr/bin/ld: skipping incompatible /usr/lib/libncurses.a when searching for -lncurses
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib32/libncurses.so when searching for -lncurses
/usr/bin/ld: skipping incompatible /usr/lib/libGL.so when searching for -lGL
/usr/bin/ld: skipping incompatible /usr/lib/libGL.so when searching for -lGL
/usr/bin/ld: skipping incompatible /usr/lib/libm.so when searching for -lm
/usr/bin/ld: skipping incompatible /usr/lib/libm.a when searching for -lm
/usr/bin/ld: skipping incompatible /usr/lib/libm.so when searching for -lm
/usr/bin/ld: skipping incompatible /usr/lib/libm.a when searching for -lm
/usr/bin/ld: skipping incompatible /usr/lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.a when searching for -lc
```


The libm is the math libraries and I've installed them all for this distro. I'm not sure what the lc is or why lGL, lpthread, and lncurses are giving errors even though the config tells me that they're all there. What am I missing?

---

### Post by mjwood0 on 2007-10-01
Sounds like you have library files compiled for a different version of GCC.  That, or they were compiled for 32-bit and you're running 64-bit.  Either way, if you can re-compile the libraries using the same environment you are trying to build in, I'll bet it will work.

---

### Post by NFITC1 on 2007-10-01
> **mjwood0 said:**
> Sounds like you have library files compiled for a different version of GCC.  That, or they were compiled for 32-bit and you're running 64-bit.  Either way, if you can re-compile the libraries using the same environment you are trying to build in, I'll bet it will work.

This is what I thought. If I do this, will this mess up anything else I want to compile with these? How DO I compile them in 32-bit. I know of the -m32 switch, but I don't know where the source of any of them are. I'm just downloading the packages through the Synaptic Package Manager.

---

