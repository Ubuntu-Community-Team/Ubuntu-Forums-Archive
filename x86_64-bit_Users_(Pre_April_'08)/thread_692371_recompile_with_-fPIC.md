---
title: "recompile with -fPIC"
date: 2008-02-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by ima998 on 2008-02-09
Dear all,

I'm very new to ubuntu ,
Im trying to install robocub in my ubuntu 7.10 in my intell dual core mechine (T2330 64 bit)

but i get this error when trying to 'make'

make[3]: Entering directory `/home/imantha/rcss3d/rcsoccersim/rcssserver3D/plugin/collisionperceptor'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/imantha/rcss3d/rcsoccersim/rcssserver3D/plugin/collisionperceptor'
Making all in sexpparser
make[3]: Entering directory `/home/imantha/rcss3d/rcsoccersim/rcssserver3D/plugin/sexpparser'
/bin/bash ../../libtool --tag=CXX --mode=link g++  -fPIC   -o sexpparser.la -rpath /usr/local/lib/rcssserver3d -module -version-info 0:0:0 -L../../utility/sfsexp/ export.lo sexpparser.lo sexpparser_c.lo -lsexp 
g++ -shared -nostdlib /usr/lib/gcc/x86_64-linux-gnu/4.1.3/../../../../lib/crti.o /usr/lib/gcc/x86_64-linux-gnu/4.1.3/crtbeginS.o  .libs/export.o .libs/sexpparser.o .libs/sexpparser_c.o  -L/home/imantha/rcss3d/rcsoccersim/rcssserver3D/utility/sfsexp -lsexp -L/usr/lib/gcc/x86_64-linux-gnu/4.1.3 -L/usr/lib/gcc/x86_64-linux-gnu/4.1.3/../../../../lib -L/lib/../lib -L/usr/lib/../lib -lstdc++ -lm -lc -lgcc_s /usr/lib/gcc/x86_64-linux-gnu/4.1.3/crtendS.o /usr/lib/gcc/x86_64-linux-gnu/4.1.3/../../../../lib/crtn.o  -Wl,-soname -Wl,sexpparser.so.0 -o .libs/sexpparser.so.0.0.0
/usr/bin/ld: /home/imantha/rcss3d/rcsoccersim/rcssserver3D/utility/sfsexp/libsexp.a(parser.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
/home/imantha/rcss3d/rcsoccersim/rcssserver3D/utility/sfsexp/libsexp.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[3]: *** [sexpparser.la] Error 1
make[3]: Leaving directory `/home/imantha/rcss3d/rcsoccersim/rcssserver3D/plugin/sexpparser'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/imantha/rcss3d/rcsoccersim/rcssserver3D/plugin'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/imantha/rcss3d/rcsoccersim/rcssserver3D'
make: *** [all] Error 2


What does 'recompile with fPIC' mean

any help is much appriciated,thanks in advance

-ima998

---

### Post by ima998 on 2008-02-09
I found the answer

./configure --enable-kerosin  CXXFLAGS=-fPIC CFLAGS=-fPIC CPPFLAGS=-fPIC 

didi the trick

cheers

---

