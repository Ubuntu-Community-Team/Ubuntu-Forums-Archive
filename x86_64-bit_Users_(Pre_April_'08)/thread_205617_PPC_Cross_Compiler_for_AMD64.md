---
title: "PPC Cross Compiler for AMD64"
date: 2006-06-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by superm1 on 2006-06-28
Hello, I Have been attempting to build a cross-compiler for AMD64-> PPC.

I have followed this howto: [http://people.debian.org/~debacle/cross/](http://people.debian.org/~debacle/cross/)

And managed to build binutils and libc6.  GCC seemed to have some troubles in finding some headers.  I resolved this by making a symlink from /usr/ppc-linux/include to ../powerpc-linux-gnu/include.

After resolving the header search, GCC still fails to build.

This was the last command it failed at:

```
make[5]: Leaving directory `/usr/src/gcc-ppc-linux-3.4.3/build/gcc'
/usr/src/gcc-ppc-linux-3.4.3/build/gcc/xgcc -B/usr/src/gcc-ppc-linux-3.4.3/build/gcc/ -B/usr/ppc-linux/bin/ -B/usr/ppc-linux/lib/ -isystem /usr/ppc-linux/include -isystem /usr/ppc-linux/sys-include -O2  -DIN_GCC -DCROSS_COMPILE   -W -Wall -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -Wold-style-definition  -isystem ./include  -fPIC -g -DHAVE_GTHR_DEFAULT -DIN_LIBGCC2 -D__GCC_FLOAT_NOT_NEEDED -Dinhibit_libc -shared -nodefaultlibs -Wl,--soname=libgcc_s.so.1 -Wl,--version-script=libgcc/./libgcc.map -Wl,-O1 -o libgcc_s.so.1.tmp  -fPIC -mstrict-align  libgcc/./_muldi3.o libgcc/./_negdi2.o libgcc/./_lshrdi3.o libgcc/./_ashldi3.o libgcc/./_ashrdi3.o libgcc/./_cmpdi2.o libgcc/./_ucmpdi2.o libgcc/./_floatdidf.o libgcc/./_floatdisf.o libgcc/./_fixunsdfsi.o libgcc/./_fixunssfsi.o libgcc/./_fixunsdfdi.o libgcc/./_fixdfdi.o libgcc/./_fixunssfdi.o libgcc/./_fixsfdi.o libgcc/./_fixxfdi.o libgcc/./_fixunsxfdi.o libgcc/./_floatdixf.o libgcc/./_fixunsxfsi.o libgcc/./_fixtfdi.o libgcc/./_fixunstfdi.o libgcc/./_floatditf.o libgcc/./_clear_cache.o libgcc/./_enable_execute_stack.o libgcc/./_trampoline.o libgcc/./__main.o libgcc/./_absvsi2.o libgcc/./_absvdi2.o libgcc/./_addvsi3.o libgcc/./_addvdi3.o libgcc/./_subvsi3.o libgcc/./_subvdi3.o libgcc/./_mulvsi3.o libgcc/./_mulvdi3.o libgcc/./_negvsi2.o libgcc/./_negvdi2.o libgcc/./_ctors.o libgcc/./_ffssi2.o libgcc/./_ffsdi2.o libgcc/./_clz.o libgcc/./_clzsi2.o libgcc/./_clzdi2.o libgcc/./_ctzsi2.o libgcc/./_ctzdi2.o libgcc/./_popcount_tab.o libgcc/./_popcountsi2.o libgcc/./_popcountdi2.o libgcc/./_paritysi2.o libgcc/./_paritydi2.o libgcc/./_divdi3.o libgcc/./_moddi3.o libgcc/./_udivdi3.o libgcc/./_umoddi3.o libgcc/./_udiv_w_sdiv.o libgcc/./_udivmoddi4.o libgcc/./_pack_sf.o libgcc/./_unpack_sf.o libgcc/./_addsub_sf.o libgcc/./_mul_sf.o libgcc/./_div_sf.o libgcc/./_fpcmp_parts_sf.o libgcc/./_compare_sf.o libgcc/./_eq_sf.o libgcc/./_ne_sf.o libgcc/./_gt_sf.o libgcc/./_ge_sf.o libgcc/./_lt_sf.o libgcc/./_le_sf.o libgcc/./_unord_sf.o libgcc/./_si_to_sf.o libgcc/./_sf_to_si.o libgcc/./_negate_sf.o libgcc/./_make_sf.o libgcc/./_sf_to_df.o libgcc/./_sf_to_tf.o libgcc/./_thenan_sf.o libgcc/./_sf_to_usi.o libgcc/./_usi_to_sf.o libgcc/./_pack_df.o libgcc/./_unpack_df.o libgcc/./_addsub_df.o libgcc/./_mul_df.o libgcc/./_div_df.o libgcc/./_fpcmp_parts_df.o libgcc/./_compare_df.o libgcc/./_eq_df.o libgcc/./_ne_df.o libgcc/./_gt_df.o libgcc/./_ge_df.o libgcc/./_lt_df.o libgcc/./_le_df.o libgcc/./_unord_df.o libgcc/./_si_to_df.o libgcc/./_df_to_si.o libgcc/./_negate_df.o libgcc/./_make_df.o libgcc/./_df_to_sf.o libgcc/./_df_to_tf.o libgcc/./_thenan_df.o libgcc/./_df_to_usi.o libgcc/./_usi_to_df.o libgcc/./tramp.o  libgcc/./unwind-dw2.o libgcc/./unwind-dw2-fde-glibc.o libgcc/./unwind-sjlj.o libgcc/./gthr-gnat.o libgcc/./unwind-c.o -lc && rm -f libgcc_s.so && if [ -f libgcc_s.so.1 ]; then mv -f libgcc_s.so.1 libgcc_s.so.1.backup; else true; fi && mv libgcc_s.so.1.tmp libgcc_s.so.1 && ln -s libgcc_s.so.1 libgcc_s.so
/usr/ppc-linux/bin/ld: crti.o: No such file: No such file or directory
collect2: ld returned 1 exit status
make[4]: *** [libgcc_s.so] Error 1
make[4]: Leaving directory `/usr/src/gcc-ppc-linux-3.4.3/build/gcc'
make[3]: *** [stmp-multilib] Error 2
make[3]: Leaving directory `/usr/src/gcc-ppc-linux-3.4.3/build/gcc'
make[2]: *** [all-gcc] Error 2
make[2]: Leaving directory `/usr/src/gcc-ppc-linux-3.4.3/build'
```

After looking around the directories, it appears crti should have been an assembly file.  I don't see one for amd64 (or x86 for that matter though)

```
supermario@supermario:/usr/src/gcc-ppc-linux-3.4.3$ find ./ -name crti*
./src/gcc/config/arm/crti.asm
./src/gcc/config/fr30/crti.asm
./src/gcc/config/h8300/crti.asm
./src/gcc/config/ia64/crti.asm
./src/gcc/config/m68k/crti.s
./src/gcc/config/mcore/crti.asm
./src/gcc/config/mips/crti.asm
./src/gcc/config/mmix/crti.asm
./src/gcc/config/sh/crti.asm
./src/gcc/config/xtensa/crti.asm
```

Has anyone had any luck building a cross compiler and could provide some more suggestions?

---

