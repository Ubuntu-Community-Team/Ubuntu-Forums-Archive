---
title: "A rather stupid mistake"
date: 2007-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by RemmyLee on 2007-10-26
While trying to install a 32bit application, I ran in to difficulties while compiling and found a supposed solution.

Said solution:

> 
export CFLAGS="-m32"
export CXXFLAGS="-m32"
./configure --enable-release --disable-cpucheck force_arch=athlon64
make


After applying the export commands, the compiler will no longer compile.

```

checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

```

Can anyone shed some light on this?

EDIT:
Disregard I simply installed the latest versions gcc and g++. Everything is fine now.

---

