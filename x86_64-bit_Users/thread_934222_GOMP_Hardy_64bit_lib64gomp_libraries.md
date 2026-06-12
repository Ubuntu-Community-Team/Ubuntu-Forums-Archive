---
title: "GOMP: Hardy 64bit lib64gomp libraries"
date: 2008-09-30
forum: x86 64-bit Users
---

### Post by jmb365 on 2008-09-30
Hello,

I am trying to install OpenMP libraries (GOMP) in an Intel quad-core PC for Hardy 64bit, but do not find the lib64gomp1 or lib64gomp1-dbg packages in Synaptic.  All repos have been enabled.  An aptitude search shows "lib64gomp1" but does not install it.  I have searched the Ubuntu website and find debs for i386, powerpc CPUs, but none for amd64. :(

Questions:
1. Where can I find amd64 lib64gomp1 and lib64gomp1-dbg packages
2. If amd64 packages are not available, when will they be available?
3. If amd64 packages are not available, will i386 packages work in the same machine, if I install using "dpkg -i lib64gomp1....deb".

Any insight will be welcome and useful. Thank you

---

### Post by Yellow Pasque on 2008-09-30
You want libgomp1(-dbg) for 64-bit programs, or lib32gomp1(-dbg) for 32-bit programs.

Since you're already using a 64-bit install, none of your packages will start with "lib64".

---

