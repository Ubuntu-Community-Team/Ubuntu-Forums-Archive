---
title: "Broke links on kernel source directory"
date: 2007-02-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Saubazi on 2007-02-08
I just noticed that I have some broken links on kernel source?

under /usr/src/linux 

it links to linux-headers-2.6.17-10-generic and this in turn links:

lrwxrwxrwx 1 root root     35 2007-02-08 20:28 firmware -> ../linux-headers-2.6.17-10/firmware

lrwxrwxrwx 1 root root     34 2007-02-08 20:28 modules -> ../linux-headers-2.6.17-10/modules

These directories firmware and modules do not exist under linux-headers-2.6.17-10

Is there something that is not quite in order?

I am wondering since make does not work???

In /usr/src/linux

$ sudo make
  CHK     include/linux/version.h
  SPLIT   include/linux/autoconf.h -> include/config/*
  HOSTCC  scripts/genksyms/genksyms.o
  HOSTCC  scripts/genksyms/lex.o
  HOSTCC  scripts/genksyms/parse.o
  HOSTLD  scripts/genksyms/genksyms
  HOSTCC  scripts/mod/mk_elfconfig
  MKELF   scripts/mod/elfconfig.h
  HOSTCC  scripts/mod/file2alias.o
  HOSTCC  scripts/mod/modpost.o
  HOSTCC  scripts/mod/sumversion.o
  HOSTLD  scripts/mod/modpost
  HOSTCC  scripts/kallsyms
  HOSTCC  scripts/conmakehash
make[1]: *** No rule to make target `init/main.o', needed by `init/built-in.o'.  Stop.
make: *** [init] Error 2

---

### Post by Saubazi on 2007-02-09
Well obviously the kernel compilation isn't done in gentoo way so perhaps scratch the question about the make problems. However, the question about the broken links remain - is this normal?

---

### Post by Kilz on 2007-02-09
> **Saubazi said:**
> Well obviously the kernel compilation isn't done in gentoo way so perhaps scratch the question about the make problems. However, the question about the broken links remain - is this normal?

You might want to look at the front page of the forum. There are problems with the release of the last kernel and support files.

---

