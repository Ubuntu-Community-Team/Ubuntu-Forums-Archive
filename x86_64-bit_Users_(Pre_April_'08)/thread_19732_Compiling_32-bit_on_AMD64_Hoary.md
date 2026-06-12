---
title: "Compiling 32-bit on AMD64 Hoary"
date: 2005-03-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by wmcbrine on 2005-03-13
After the most recent updates to ia32-libs, I finally* was able to compile 32-bit executables via "gcc-3.4 -m32 -static". But I didn't want static... Well, I figured out I could get a dynamic compile working by creating a symbolic link from /lib32/libgcc_s_32.so to /lib32/libgcc_s.so.1. (Actually I linked from libgcc_s_32.so.1 to libgcc_s.so.1, and then from libgcc_s_32.so to libgcc_s_32.so.1. But you get the idea.)

I still find it strange that this doesn't work out of the box, considering that OpenOffice is 32-bit. Did they not actually build it on amd64 hoary, or what?

But anyway, it works great now, and I'm happy. Still missing some 32-bit libs of course.

* I say "finally", but I only installed Ubuntu three days ago. :)

---

