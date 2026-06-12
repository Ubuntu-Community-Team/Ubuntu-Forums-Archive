---
title: "Building Mozilla Sunbird"
date: 2006-01-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by sdyson on 2006-01-10
Has anyone had any luck installing Sunbird? This is my first attempt at building anything and I'm gettting the following problem when I run sudo make -f client.mk build: 

checking for gcc... gcc
checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.
*** Fix above errors and then restart with "make -f client.mk build"
make[1]: *** [configure] Error 1
make[1]: Leaving directory `/home/simon/documents/Downloads/Linux/mozilla'
make: *** [/home/simon/documents/Downloads/Linux/mozilla/Makefile] Error 2


I have gcc (GCC) 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

Any tips would be much appreciated.

---

### Post by WhiteHorse on 2006-05-04
try this first:
sudo apt-get install build-essential

---

