---
title: "theme engine problem"
date: 2006-09-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Perfex on 2006-09-17
Hello I receently decided to install te 64bit version of ubuntu, been going pretty good, except I not able to use diffrent theme engines for some reason, I install them see below but when I go into theme prefrences and select them with one of their corisponding themes, its like they do not exist

example of one install:
```
robert@robert-desktop:~$ cd /home/robert/Desktop/murrine-0.12.tar.bz2_FILES
robert@robert-desktop:~/Desktop/murrine-0.12.tar.bz2_FILES$ ./configure bash: ./configure: No such file or directory
robert@robert-desktop:~/Desktop/murrine-0.12.tar.bz2_FILES$ cd /home/robert/Desktop/murrine-0.12.tar.bz2_FILES/murrine-0.12
robert@robert-desktop:~/Desktop/murrine-0.12.tar.bz2_FILES/murrine-0.12$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTK... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating murrine.pc
config.status: creating src/config.h
config.status: executing depfiles commands
Now run make.
robert@robert-desktop:~/Desktop/murrine-0.12.tar.bz2_FILES/murrine-0.12$ make
if /bin/sh ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I./src -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -MT murrine_rc_style.lo -MD -MP -MF ".deps/murrine_rc_style.Tpo" -c -o murrine_rc_style.lo `test -f './src/murrine_rc_style.c' || echo './'`./src/murrine_rc_style.c; \
        then mv -f ".deps/murrine_rc_style.Tpo" ".deps/murrine_rc_style.Plo"; else rm -f ".deps/murrine_rc_style.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I./src -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT murrine_rc_style.lo -MD -MP -MF .deps/murrine_rc_style.Tpo -c ./src/murrine_rc_style.c  -fPIC -DPIC -o .libs/murrine_rc_style.o
if /bin/sh ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I./src -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -MT murrine_style.lo -MD -MP -MF ".deps/murrine_style.Tpo" -c -o murrine_style.lo `test -f './src/murrine_style.c' || echo './'`./src/murrine_style.c; \
        then mv -f ".deps/murrine_style.Tpo" ".deps/murrine_style.Plo"; else rm -f ".deps/murrine_style.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I./src -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT murrine_style.lo -MD -MP -MF .deps/murrine_style.Tpo -c ./src/murrine_style.c  -fPIC -DPIC -o .libs/murrine_style.o
./src/murrine_style.c: In function 'draw_focus':
./src/murrine_style.c:1353: warning: pointer targets in initialization differ in signedness
./src/murrine_style.c:1370: warning: pointer targets in assignment differ in signedness
./src/murrine_style.c:1390: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness
if /bin/sh ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I./src -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -MT murrine_theme_main.lo -MD -MP -MF ".deps/murrine_theme_main.Tpo" -c -o murrine_theme_main.lo `test -f './src/murrine_theme_main.c' || echo './'`./src/murrine_theme_main.c; \
        then mv -f ".deps/murrine_theme_main.Tpo" ".deps/murrine_theme_main.Plo"; else rm -f ".deps/murrine_theme_main.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I./src -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT murrine_theme_main.lo -MD -MP -MF .deps/murrine_theme_main.Tpo -c ./src/murrine_theme_main.c  -fPIC -DPIC -o .libs/murrine_theme_main.o
if /bin/sh ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I./src -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -MT support.lo -MD -MP -MF ".deps/support.Tpo" -c -o support.lo `test -f './src/support.c' || echo './'`./src/support.c; \
        then mv -f ".deps/support.Tpo" ".deps/support.Plo"; else rm -f ".deps/support.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I./src -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT support.lo -MD -MP -MF .deps/support.Tpo -c ./src/support.c  -fPIC -DPIC -o .libs/support.o
if /bin/sh ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I./src -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -MT animation.lo -MD -MP -MF ".deps/animation.Tpo" -c -o animation.lo `test -f './src/animation.c' || echo './'`./src/animation.c; \
        then mv -f ".deps/animation.Tpo" ".deps/animation.Plo"; else rm -f ".deps/animation.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I./src -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT animation.lo -MD -MP -MF .deps/animation.Tpo -c ./src/animation.c  -fPIC -DPIC -o .libs/animation.o
if /bin/sh ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I./src -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -MT murrine_draw.lo -MD -MP -MF ".deps/murrine_draw.Tpo" -c -o murrine_draw.lo `test -f './src/murrine_draw.c' || echo './'`./src/murrine_draw.c; \
        then mv -f ".deps/murrine_draw.Tpo" ".deps/murrine_draw.Plo"; else rm -f ".deps/murrine_draw.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I./src -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT murrine_draw.lo -MD -MP -MF .deps/murrine_draw.Tpo -c ./src/murrine_draw.c  -fPIC -DPIC -o .libs/murrine_draw.o
/bin/sh ./libtool --tag=CC --mode=link gcc  -g -O2   -o libmurrine.la -rpath /usr/local/lib/gtk-2.0/2.4.0/engines -module -avoid-version -no-undefined murrine_rc_style.lo murrine_style.lo murrine_theme_main.lo support.lo animation.lo murrine_draw.lo -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
gcc -shared  .libs/murrine_rc_style.o .libs/murrine_style.o .libs/murrine_theme_main.o .libs/support.o .libs/animation.o .libs/murrine_draw.o  /usr/lib/libgtk-x11-2.0.so -L/usr/lib /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libpangocairo-1.0.so -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes /usr/lib/libpango-1.0.so /usr/lib/libcairo.so -lX11 /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so  -Wl,-soname -Wl,libmurrine.so -o .libs/libmurrine.so
creating libmurrine.la
(cd .libs && rm -f libmurrine.la && ln -s ../libmurrine.la libmurrine.la)
robert@robert-desktop:~/Desktop/murrine-0.12.tar.bz2_FILES/murrine-0.12$ sudo make install
Password:
make[1]: Entering directory `/home/robert/Desktop/murrine-0.12.tar.bz2_FILES/murrine-0.12'
make[1]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/gtk-2.0/2.4.0/engines" || mkdir -p -- "/usr/local/lib/gtk-2.0/2.4.0/engines"
 /bin/sh ./libtool --mode=install /usr/bin/install -c  'libmurrine.la' '/usr/local/lib/gtk-2.0/2.4.0/engines/libmurrine.la'
/usr/bin/install -c .libs/libmurrine.so /usr/local/lib/gtk-2.0/2.4.0/engines/libmurrine.so
/usr/bin/install -c .libs/libmurrine.lai /usr/local/lib/gtk-2.0/2.4.0/engines/libmurrine.la
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib/gtk-2.0/2.4.0/engines
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/gtk-2.0/2.4.0/engines

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[1]: Leaving directory `/home/robert/Desktop/murrine-0.12.tar.bz2_FILES/murrine-0.12'
robert@robert-desktop:~/Desktop/murrine-0.12.tar.bz2_FILES/murrine-0.12$

```

and they are in the directory as seen in attached image.
Anyone know whats going on?

---

### Post by Kilz on 2006-09-17
Are they 32 or 64bit packages?

---

### Post by Perfex on 2006-09-17
their the source packages, the i386 .debs wont work, where can one specific 64 bit source packages or .debs?

---

### Post by Kilz on 2006-09-17
> **Perfex said:**
> their the source packages, the i386 .debs wont work, where can one specific 64 bit source packages or .debs?

](*,) sorry I should have looked at the compile to see they are compilations. I dont know whay they are not working.

---

### Post by Perfex on 2006-09-17
solved : needed to ./configure --prefix=/usr instead of just ./configure

---

