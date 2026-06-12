---
title: "I cant make a make xP"
date: 2005-10-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by T31 on 2005-10-24
This happened to me trying to compile phonegaim but has been happening several times with other programs, after i got the configure to go correctly I do make and....

(and yeah I have build-essential and autoconf)

:confused: 

make  all-recursive
make[1]: Entering directory `/home/t31/marlin_build_phonegaim-1.0.2'
Making all in doc
make[2]: Entering directory `/home/t31/marlin_build_phonegaim-1.0.2/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/t31/marlin_build_phonegaim-1.0.2/doc'
Making all in intl
make[2]: Entering directory `/home/t31/marlin_build_phonegaim-1.0.2/intl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/t31/marlin_build_phonegaim-1.0.2/intl'
Making all in pixmaps
make[2]: Entering directory `/home/t31/marlin_build_phonegaim-1.0.2/pixmaps'
make[3]: Entering directory `/home/t31/marlin_build_phonegaim-1.0.2'
make[3]: *** No rule to make target `am--refresh'.  Stop.
make[3]: Leaving directory `/home/t31/marlin_build_phonegaim-1.0.2'
make[2]: *** [Makefile] Error 2
make[2]: Leaving directory `/home/t31/marlin_build_phonegaim-1.0.2/pixmaps'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/t31/marlin_build_phonegaim-1.0.2'
make: *** [all] Error 2


thx in advance

---

