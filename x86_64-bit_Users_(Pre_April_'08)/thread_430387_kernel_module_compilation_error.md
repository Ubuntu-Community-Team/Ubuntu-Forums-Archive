---
title: "kernel module compilation error"
date: 2007-05-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by s13884 on 2007-05-02
Hi-

Whenever I tried to compile my sample test  module this error wil come so can anybody help me out to figure out this error.

it's architecture problem or what;-) 

make -C /lib/modules/2.6.15-26-amd64-generic/build SUBDIR=/home/vecima11/Desktop/module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-amd64-generic'
CHK include/linux/version.h
HOSTCC scripts/basic/fixdep
HOSTCC scripts/basic/split-include
HOSTCC scripts/basic/docproc
SPLIT include/linux/autoconf.h -> include/config/*
HOSTCC scripts/genksyms/genksyms.o
HOSTCC scripts/genksyms/lex.o
HOSTCC scripts/genksyms/parse.o
HOSTLD scripts/genksyms/genksyms
HOSTCC scripts/mod/mk_elfconfig
MKELF scripts/mod/elfconfig.h
HOSTCC scripts/mod/file2alias.o
HOSTCC scripts/mod/modpost.o
HOSTCC scripts/mod/sumversion.o
HOSTLD scripts/mod/modpost
HOSTCC scripts/kallsyms
HOSTCC scripts/conmakehash
make[2]: *** No rule to make target `arch/x86_64/kernel/../../i386/kernel/cpuid.o', needed by `arch/x86_64/kernel/msr.o'. Stop.
make[1]: *** [arch/x86_64/kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-amd64-generic'
make: *** [default] Error 2

can anybody tell me what's the problem with compilation?
is dat problem with architecture or what?

cheer,
S

---

### Post by barper on 2007-07-25
if you resolve it please reply

---

### Post by tabhappy on 2007-07-26
I don't believe it has anything to do with your architecture.  It looks like your makefile is missing the line telling the make program how to create the cpuid.o object.  If you know the name of the source file needed and know where it is located, then you should be able to add the line in yourself.  google for "makefile tutorial" for more help on how to do this.

-j

---

