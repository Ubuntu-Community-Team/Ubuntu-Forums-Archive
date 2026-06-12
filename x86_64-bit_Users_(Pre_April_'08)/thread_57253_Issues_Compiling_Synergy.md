---
title: "Issues Compiling Synergy"
date: 2005-08-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by damonkohler on 2005-08-15
I'm having trouble compiling synergy for my AMD64 box.
```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... x86_64-unknown-linux
checking host system type... x86_64-unknown-linux
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for ranlib... ranlib
checking for dot... NO
checking dependency style of gcc... gcc3
checking if g++ defines correct C++ macro... no
checking for the pthreads library -lpthreads... no
checking whether pthreads work without any flags... no
checking whether pthreads work with -Kthread... no
checking whether pthreads work with -kthread... no
checking for the pthreads library -llthread... no
checking whether pthreads work with -pthread... no
checking whether pthreads work with -pthreads... no
checking whether pthreads work with -mthreads... no
checking for the pthreads library -lpthread... no
checking whether pthreads work with --thread-safe... no
checking whether pthreads work with -mt... no
configure: error: You must have pthreads to compile synergy
```

Anyone have any suggestions? Thanks!

---

### Post by damonkohler on 2005-08-18
This seems to have done the trick.

[http://ubuntuguide.org/#build-essential](http://ubuntuguide.org/#build-essential)

---

