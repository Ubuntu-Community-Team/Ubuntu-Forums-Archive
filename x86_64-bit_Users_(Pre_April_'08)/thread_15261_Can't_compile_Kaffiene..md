---
title: "Can't compile Kaffiene."
date: 2005-02-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Rock on 2005-02-13
root@linuxboard:/home/chris/kaffiene # ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
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
checking whether g++ supports -Wmissing-format-attribute... no
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... no
checking whether g++ supports -Wno-long-long... no
checking whether g++ supports -Wnon-virtual-dtor... no
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
root@linuxboard:/home/chris/kaffiene # 

Anyone have any idea on this? Btw I have KDE installed.

---

### Post by blinksilver on 2005-02-13
well, it is already in the resopositories, at least for me, just use synapitc, there is a section on KDE, sorry could not be more help

---

### Post by Rock on 2005-02-13
Already searched synaptic and not there.

---

### Post by blinksilver on 2005-02-13
it is in mine, make sure you have universe and multiverse on (using hoary 4)

---

### Post by Rock on 2005-02-13
I do, btw you got the AMD64 Ubuntu right?

---

### Post by Nadir on 2005-02-14
[QUOTE=Rock]I do, btw you got the AMD64 Ubuntu right?[/QUOTE]
 Kaffeine is in universe

---

### Post by blinksilver on 2005-02-14
yup and nadir is right it is in universe sadly alot of the dependencies for it are not, at least yesterday they were not, but all of KDE is actually in unverse installed for fun yesterday, and it broke gnome, on my XFCE now

---

