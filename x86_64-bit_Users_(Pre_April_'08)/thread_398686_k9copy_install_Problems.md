---
title: "k9copy install Problems"
date: 2007-04-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by tom35i on 2007-04-01
Hey i am a bit new to this but need some help installing the lastest version of k9copy as the one in the respories does not copy the new dvds i hav bought.
this is the output after i run ./configure
```
tom@tom-desktop:~$ cd k9copy-1.1.1
tom@tom-desktop:~/k9copy-1.1.1$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether g++ supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... yes
checking whether g++ supports -Wno-long-long... yes
checking whether g++ supports -Wnon-virtual-dtor... yes
checking whether g++ supports -fno-exceptions... yes
checking whether g++ supports -fno-check-new... yes
checking whether g++ supports -fno-common... yes
checking whether g++ supports -fexceptions... yes
checking how to run the C++ preprocessor... g++ -E
checking whether g++ supports -O0... yes
checking whether g++ supports -Wl,--no-undefined... yes
checking whether g++ supports -Wl,--allow-shlib-undefined... yes
not using lib directory suffix
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... yes
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
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking whether a program can dlopen itself... (cached) yes
checking whether a statically linked program can dlopen itself... (cached) yes
appending configuration tag "F77" to libtool
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking if C++ programs can be compiled... yes
checking for strlcat... no
checking if strlcat needs custom prototype... yes - in libkdefakes
checking for strlcpy... no
checking if strlcpy needs custom prototype... yes - in libkdefakes
checking for main in -lutil... yes
checking for main in -lcompat... no
checking for crypt in -lcrypt... yes
checking for socklen_t... socklen_t
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for inet_ntoa... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for sys/types.h... (cached) yes
checking for stdint.h... (cached) yes
checking for poll in -lpoll... no
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking if res_init needs -lresolv... yes
checking if res_init is available... yes
checking for killpg in -lucb... no
checking for int... yes
checking size of int... 4
checking for short... yes
checking size of short... 2
checking for long... yes
checking size of long... 8
checking for char *... yes
checking size of char *... 8
checking for dlopen in -ldl... (cached) yes
checking for shl_unload in -ldld... no
checking for size_t... yes
checking size of size_t... 8
checking for unsigned long... yes
checking size of unsigned long... 8
checking sizeof size_t == sizeof unsigned long... yes
checking crt_externs.h usability... no
checking crt_externs.h presence... no
checking for crt_externs.h... no
checking for _NSGetEnviron... no
checking for vsnprintf... yes
checking for snprintf... yes
checking for X... libraries /usr/X11R6/lib, headers .
checking for IceConnectionNumber in -lICE... yes
checking for libXext... yes
checking for pthread_create in -lpthread... yes
checking for extra includes... no
checking for extra libs... no
checking for libz... -lz
checking for libpng... -lpng -lz -lm
checking for libjpeg6b... no
checking for libjpeg... -ljpeg
checking for perl... /usr/bin/perl
checking for Qt... libraries /usr/share/qt3/lib, headers /usr/share/qt3/include using -mt
checking for moc... /usr/share/qt3/bin/moc
checking for uic... /usr/share/qt3/bin/uic
checking whether uic supports -L ... yes
checking whether uic supports -nounload ... yes
checking if Qt needs -ljpeg... no
checking for rpath... yes
checking for KDE... libraries /usr/lib, headers /usr/include/kde
checking if UIC has KDE plugins available... yes
checking for KDE paths... defaults
checking for dcopidl... /usr/bin/dcopidl
checking for dcopidl2cpp... /usr/bin/dcopidl2cpp
checking for mcopidl... /usr/bin/mcopidl
checking for artsc-config... /usr/bin/artsc-config
checking for kde-config... /usr/bin/kde-config
checking for meinproc... /usr/bin/meinproc
checking for xmllint... /usr/bin/xmllint
checking whether byte ordering is bigendian... no
checking for MAXPATHLEN... 4096
checking for X86 architecture... no
checking for 386 architecture... no
checking for X86_64 architecture... yes
checking GL/gl.h usability... yes
checking GL/gl.h presence... yes
checking for GL/gl.h... yes
checking dvdread/dvd_reader.h usability... yes
checking dvdread/dvd_reader.h presence... yes
checking for dvdread/dvd_reader.h... yes
checking for the HAL... headers /usr/include/hal  libraries /usr/lib
checking for DBus... headers /usr/include/dbus-1.0 /usr/lib64/dbus-1.0/include libraries /usr/lib
checking if doc should be compiled... yes
checking if k9Mplayer should be compiled... yes
checking if k9decmpeg should be compiled... yes
checking if k9devices should be compiled... yes
checking if k9vamps should be compiled... yes
checking if libdvdnav should be compiled... yes
checking if libk9copy should be compiled... yes
checking if po should be compiled... yes
checking if src should be compiled... yes
configure: creating ./config.status
wrong input (flag != 4) at admin/conf.change.pl line 117, <> line 1223.
config.status: creating Makefile
config.status: creating doc/Makefile
config.status: creating doc/k9copy/Makefile
config.status: creating k9decmpeg/Makefile
config.status: creating k9devices/Makefile
config.status: creating k9Mplayer/Makefile
config.status: creating k9vamps/Makefile
config.status: creating libdvdnav/Makefile
config.status: creating libk9copy/Makefile
config.status: creating po/Makefile
config.status: creating src/Makefile
config.status: creating src/icons/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

Good - your configure finished. Start make now

```
then MAKE
```
tom@tom-desktop:~/k9copy-1.1.1$ make
make  all-recursive
make[1]: Entering directory `/home/tom/k9copy-1.1.1'
Making all in k9vamps
make[2]: Entering directory `/home/tom/k9copy-1.1.1/k9vamps'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/tom/k9copy-1.1.1/k9vamps'
Making all in libdvdnav
make[2]: Entering directory `/home/tom/k9copy-1.1.1/libdvdnav'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/tom/k9copy-1.1.1/libdvdnav'
Making all in k9Mplayer
make[2]: Entering directory `/home/tom/k9copy-1.1.1/k9Mplayer'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/tom/k9copy-1.1.1/k9Mplayer'
Making all in k9decmpeg
make[2]: Entering directory `/home/tom/k9copy-1.1.1/k9decmpeg'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/tom/k9copy-1.1.1/k9decmpeg'
Making all in libk9copy
make[2]: Entering directory `/home/tom/k9copy-1.1.1/libk9copy'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/tom/k9copy-1.1.1/libk9copy'
Making all in k9devices
make[2]: Entering directory `/home/tom/k9copy-1.1.1/k9devices'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/tom/k9copy-1.1.1/k9devices'
Making all in src
make[2]: Entering directory `/home/tom/k9copy-1.1.1/src'
Making all in icons
make[3]: Entering directory `/home/tom/k9copy-1.1.1/src/icons'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/tom/k9copy-1.1.1/src/icons'
make[3]: Entering directory `/home/tom/k9copy-1.1.1/src'
/bin/sh ../libtool --silent --tag=CXX --mode=link g++ -O3 -g3 -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common    -o k9copy -R /usr/lib -R /usr/share/qt3/lib -R /usr/X11R6/lib -L/usr/X11R6/lib -L/usr/share/qt3/lib -L/usr/lib  kviewmpeg2.o main.o kconfigdlg.o k9copy.o k9main.o k9play.o k9settings.o k9prefmpeg4.o k9prefdvd.o k9prefmencoder.o k9playbackoptions.o k9langselect.o k9glwidget.o k9prefpreview.o k9titlefactor.o k9updatefactor.o viewmpeg2.o configDlg.o k9mainw.o prefDVD.o prefMPEG4.o prefMencoder.o playbackoptionsw.o langselectw.o prefpreview.o titlefactor.o kviewmpeg2.moc.o k9copy.moc.o  ../k9Mplayer/libk9mplayer.la ../libdvdnav/libk9dvdnav.la ../libk9copy/libk9copy.la ../k9decmpeg/libk9decmpeg.la ../k9vamps/libk9vamps.la ../k9devices/libk9devices.la -lkmdi -lkdeui
k9main.o: In function `k9Main::Open()':/home/tom/k9copy-1.1.1/src/k9main.cpp:518: undefined reference to `k9HalDevice::mountPoint()'
../k9devices/.libs/libk9devices.a(k9halconnection.o): In function `k9HalConnection::addDevice(char const*)':k9halconnection.cpp:(.text+0x5a2): undefined reference to `k9HalDevice::k9HalDevice(QObject*, char const*)'
../k9devices/.libs/libk9devices.a(k9halconnection.o): In function `k9HalConnection::testVolumeChanged(char const*)':k9halconnection.cpp:(.text+0x7df): undefined reference to `k9HalDevice::updateVolumeName()'
:k9halconnection.cpp:(.text+0x84b): undefined reference to `k9HalDevice::updateVolumeName()'
collect2: ld returned 1 exit status
make[3]: *** [k9copy] Error 1
make[3]: Leaving directory `/home/tom/k9copy-1.1.1/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/tom/k9copy-1.1.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tom/k9copy-1.1.1'
make: *** [all] Error 2
tom@tom-desktop:~/k9copy-1.1.1$

```

don't have a clue what these errors r if any1 could help me out please

---

### Post by Kilz on 2007-04-01
I never have had luck compiling k9copy. But its my favorite dvd application. [You might want to look here if you cant compile.]("http://packages.czessi.org/en/") The repo has the 1.1.0 version. Its even available for Dapper. 
But I will also tell you that some DVD's , Especially Disney DvD's have some copy protection that is almost imposable to beat.

---

