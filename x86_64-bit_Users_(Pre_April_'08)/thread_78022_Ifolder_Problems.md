---
title: "Ifolder Problems"
date: 2005-10-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by deusinvictus on 2005-10-17
I am trying in install Ifolder on my laptop, I'm running Ubuntu Breezy on a Powerbook G4.  The first time I tried I used the instructions Seb Payne had on his blog and it didn't work.  Recently I tried again using the instructions on the Ubuntu wiki that were linked to by the ifolder website (it looks the exact same as Seb Payne's if I remember correctly).  Each time I have gotten the same error:

if /bin/sh ../../../libtool --tag=CXX --mode=compile g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"simias\" -DVERSION=\"1.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -I. -I.    -I "../../../external/flaim/include" -fshort-wchar -DFLAIMWRAPPER_EXPORTS -DUNIX -D_REENTRANT -c -g -O2 -MT libFlaimWrapper_la-FlaimWrapper.lo -MD -MP -MF ".deps/libFlaimWrapper_la-FlaimWrapper.Tpo" -c -o libFlaimWrapper_la-FlaimWrapper.lo `test -f 'FlaimWrapper.cpp' || echo './'`FlaimWrapper.cpp; \
then mv -f ".deps/libFlaimWrapper_la-FlaimWrapper.Tpo" ".deps/libFlaimWrapper_la-FlaimWrapper.Plo"; else rm -f ".deps/libFlaimWrapper_la-FlaimWrapper.Tpo"; exit 1; fi
 g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"simias\" -DVERSION=\"1.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -I. -I. -I ../../../external/flaim/include -fshort-wchar -DFLAIMWRAPPER_EXPORTS -DUNIX -D_REENTRANT -c -g -O2 -MT libFlaimWrapper_la-FlaimWrapper.lo -MD -MP -MF .deps/libFlaimWrapper_la-FlaimWrapper.Tpo -c FlaimWrapper.cpp  -fPIC -DPIC -o .libs/libFlaimWrapper_la-FlaimWrapper.o
 g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"simias\" -DVERSION=\"1.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -I. -I. -I ../../../external/flaim/include -fshort-wchar -DFLAIMWRAPPER_EXPORTS -DUNIX -D_REENTRANT -c -g -O2 -MT libFlaimWrapper_la-FlaimWrapper.lo -MD -MP -MF .deps/libFlaimWrapper_la-FlaimWrapper.Tpo -c FlaimWrapper.cpp -o libFlaimWrapper_la-FlaimWrapper.o >/dev/null 2>&1
/bin/sh ../../../libtool --tag=CXX --mode=link g++  -g -O2   -o libFlaimWrapper.la -rpath /usr/lib -L"../../../external/flaim/lxx86/gcc3/release" -lflm libFlaimWrapper_la-CSPObjectIterator.lo libFlaimWrapper_la-CSPropertyIterator.lo libFlaimWrapper_la-CSPStore.lo libFlaimWrapper_la-CSPStoreObject.lo libFlaimWrapper_la-FlaimWrapper.lo
g++ -shared -nostdlib /usr/lib/gcc/powerpc-linux-gnu/4.0.2/../../../../lib/crti.o /usr/lib/gcc/powerpc-linux-gnu/4.0.2/crtbeginS.o  .libs/libFlaimWrapper_la-CSPObjectIterator.o .libs/libFlaimWrapper_la-CSPropertyIterator.o .libs/libFlaimWrapper_la-CSPStore.o .libs/libFlaimWrapper_la-CSPStoreObject.o .libs/libFlaimWrapper_la-FlaimWrapper.o  -L/home/deus/ifolder/simias/external/flaim/lxx86/gcc3/release -lflm -L/usr/lib/gcc/powerpc-linux-gnu/4.0.2 -L/usr/lib/gcc/powerpc-linux-gnu/4.0.2/../../../../lib -L/usr/lib/gcc/powerpc-linux-gnu/4.0.2/../../.. -L/lib/../lib -L/usr/lib/../lib -lstdc++ -lm -lc -lgcc_s /usr/lib/gcc/powerpc-linux-gnu/4.0.2/crtsavres.o /usr/lib/gcc/powerpc-linux-gnu/4.0.2/crtendS.o /usr/lib/gcc/powerpc-linux-gnu/4.0.2/../../../../lib/crtn.o  -Wl,-soname -Wl,libFlaimWrapper.so.0 -o .libs/libFlaimWrapper.so.0.0.0
/usr/bin/ld: skipping incompatible /home/deus/ifolder/simias/external/flaim/lxx86/gcc3/release/libflm.a when searching for -lflm
/usr/bin/ld: cannot find -lflm
collect2: ld returned 1 exit status
make[3]: *** [libFlaimWrapper.la] Error 1
make[3]: Leaving directory `/home/deus/ifolder/simias/src/FlaimProvider/FlaimWrapper'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/deus/ifolder/simias/src/FlaimProvider'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/deus/ifolder/simias/src'
make: *** [all-recursive] Error 1


I don't know if their is a solution to this error, I was reading something in one of the other threads about licensing issues with the libflaim.

---

### Post by castrojo on 2005-10-17
I'm pretty sure that ifolder doesn't build on ppc yet. File a bug perhaps?

---

### Post by poofyhairguy on 2005-10-17
This forum is for guides, not problems or questions. So I moved the thread.

---

### Post by deusinvictus on 2005-10-17
Sorry for posting in the wrong forum.  I wasn't sure if iFolder was building in Linux on PPC yet.  But obviously the backend code must be compatible with PPC otherwise it wouldn't work under OSX of course the frontend code would probably be a bit different, but I didnt' think that would be affected by the proccessor.

---

