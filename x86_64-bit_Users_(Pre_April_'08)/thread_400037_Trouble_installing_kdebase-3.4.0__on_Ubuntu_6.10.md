---
title: "Trouble installing kdebase-3.4.0  on Ubuntu 6.10"
date: 2007-04-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Vrzcqv on 2007-04-03
I am a newbie to Linux.

When I try to configure kdebase 3.4.0 on my Ubuntu 6.10 (Edgy fit) OS
I get the error

checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

Does anyone know how to resolve this problem?

---

### Post by Yfrwlf on 2007-04-06
Just so ya know, posting the same thread twice within a day is bound to be annoying :)

The solution is to install the package "build-essential".

---

