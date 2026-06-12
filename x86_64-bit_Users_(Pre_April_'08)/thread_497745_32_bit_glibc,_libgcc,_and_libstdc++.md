---
title: "32 bit glibc, libgcc, and libstdc++"
date: 2007-07-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by theycallhimtom on 2007-07-10
I need 32 bit versions of glibc, libgcc, and libstdc++ to install a program (intel compilier). I'm running the AMD64 version of Ubuntu 7.04. Is there an easy way to get the 32 bit versions?

---

### Post by Cappy on 2007-07-10
```

sudo apt-get install ia32-libs libc6-i386 libc6-dev-i386 lib32gcc1
```
may contain some or all of those.

Maybe this too::
lib32stdc++6
(ia32-libs above comes with 5)

You can run ldd on a binary (if it is that) and it will show what files are missing:
```
ldd /path/to/binary | grep need
```

---

### Post by MrWookie on 2007-07-31
I'm having this same problem with the intel Fortran 10 compiler, and I was glad I found this thread.  However, I installed the specified packages in the reply, but the installer for the compiler gave the same error about needing the 3 packages.  Has anyone gotten the intel fortran compiler to work on 64bit Ubuntu 7.04?

---

