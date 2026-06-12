---
title: "Compilation problem"
date: 2005-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by sulobanks on 2005-10-20
Not sure if this is specific to ubuntu ppc or if all platforms are affected. When I try to compile anything written in c, the compiler can't find the standard libraries. I've tried to compile libdvdcss from source and it errors out with "c compiler cannot create executables".  So then I tried a simple hello world program in c and gcc can't find stdio.h.  I'm assuming this means the compiler can't find any of the standard libraries.  Any idea how I get my system to recognize where the c libraries are? I've got libc6, g++, gcc, binutils and several other development packages installed.

---

### Post by sulobanks on 2005-10-20
ldconfig -v fixed it. I wish I knew which package didn't run that as part of its install so I could report it. :/

---

