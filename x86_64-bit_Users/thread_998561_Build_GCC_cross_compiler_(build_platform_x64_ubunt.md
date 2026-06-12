---
title: "Build GCC cross compiler (build platform x64 ubuntu, target win32)"
date: 2008-11-30
forum: x86 64-bit Users
---

### Post by qwertymodo on 2008-11-30
I've looked high and low for information on this, but it seems to be sparse.  I want to build a GCC cross-compiler (including at least the C, C++, and Java compilers) on my Ubuntu x64 system to create Win32 binaries.  Before anyone suggests I simply get a JDK for compiling java into bytecode, yes I already have that.  I want the GCJ in order to compile the java bytecode into native binaries.  And please don't just tell me all the reasons that this is stupid... I'm just looking for HELP.

I've found several tutorials on building such a cross-compiler, but none of them seem to work on my x64 system.  Any ideas?

---

### Post by tomdkat on 2008-12-01
What instructions have you found and tried that didn't work?

It's been a while since I've built a cross compiler but "back in the day", I built a GCC cross compiler on Linux (32-bit) that targetted Win32.

Have you also built your Win32 targeted toolchain as well?

If I recall correctly, I believe the important part is getting --build, --host, and --target parameters correct.

So, to build the GNU assembler (gas) to generate Win32 targeted code, you could specify --target=mingw32 to gcc.  You could configure the binutils package like this:

$ cd binutils
$ ./configure --prefix=/usr/local/win32cross --target={Win32 target} [options]
$ make

As for getting the {Win32 target} right, do you want to link apps that will run on Windows "as is" on the Linux box or are you wanting to run these apps in a Cygwin environment on Windows?

Read up on Cygwin vs MinGW.   The cross compiler I built targeted mingw32 and worked well.  :)

Peace...

---

### Post by qwertymodo on 2008-12-01
I want to run my final products in Windows, or, for quick testing purposes, via Wine.  I run a dual-boot, but I like developing in Linux.  I already have my native Linux development environment set up, it would just be nice to be able to compile my Win32 binaries from the same place.  I am a TOTAL neophyte at compiling compilers and toolchains and all of that... so go ahead and assume I have no idea what you're talking about and I'm starting at square 1.  Maybe the information is out there and I just didn't realize I was reading the answer right in front of my face, who knows.  However, any help would be much appreciated, even if it's just a link to information elsewhere.

---

### Post by tomdkat on 2008-12-01
Ok.  You'll need the source for binutils, gcc, and some Win32 api libraries to make the magic happen.

Here is a link for you to study:

[http://gcc.gnu.org/ml/gcc-help/2003-01/msg00118.html](http://gcc.gnu.org/ml/gcc-help/2003-01/msg00118.html)

This one pretty much covers the process I used. What you'll need to find out are the proper --target, --build, and --host values for your Linux system and for the target Win32 system.  Here is a list of targets supported by gcc:

[http://gcc.gnu.org/install/specific.html](http://gcc.gnu.org/install/specific.html)

Which version of gcc are you going to use for the compiler?

You can probably use i686-pc-mingw32 as your target and x86_64-pc-linux as your build and host parameters.

This sounds like a fun project so I'm going to do the same on my 64-bit Ubuntu system at home. :)  We can work through this together, so to speak.  :)

For now, download the sources for:

binutils: [http://sources.redhat.com/binutils/](http://sources.redhat.com/binutils/)
gcc: [http://gcc.gnu.org/](http://gcc.gnu.org/) (I'm going to build a gcc-4.3.2 cross compiler)
win32api: [http://sourceforge.net/project/showfiles.php?group_id=2435](http://sourceforge.net/project/showfiles.php?group_id=2435)
mingw-runtime: [http://sourceforge.net/project/showfiles.php?group_id=2435](http://sourceforge.net/project/showfiles.php?group_id=2435)

And then report back here. I'll do the same and we'll build each package one at a time.  Also, pick a place where you will want to install your cross compiler.  I'm going to install mine in /usr/local/mingw32-cross.

Peace...

---

### Post by tomdkat on 2008-12-01
Ok, I've started working on this and I've built binutils-2.19 targeting MingW32 (i686-pc-mingw32 to be exact).

You will need to install the texinfo package:

$ sudo apt-get install texinfo

before you configure binutils.

Then, this is what I did to build it:

$ tar zxf binutils-2.19.tar.gz
$ cd binutils-2.19
$ mkdir objdir
$ cd objdir
$ ../configure --prefix=/usr/local/mingw32-cross --target=i686-pc-mingw32
(waited for a bit)
$ time make
(waited for a bit)

At this point, you'll hit this compile error:

[http://www.mail-archive.com/bug-binutils@gnu.org/msg06568.html](http://www.mail-archive.com/bug-binutils@gnu.org/msg06568.html)

I've patched the dlltool.c and windmc.c files as described in that bug report.  I'm also trying to build the binutils-2.19-51 snapshot to see if that builds without the compile error.  If it does, you should use that instead of the "stock" binutils-2.19 distribution.

If you prefer using the "stock" binutils distribution, I can e-mail you the patched files.

With the patched files in place, the "stock" binutils-2.19 tarball builds in 7 minutes on my system:

```

make[4]: Leaving directory `/mnt/data/build/binutils-2.19/objdir/ld'
make[3]: Leaving directory `/mnt/data/build/binutils-2.19/objdir/ld'
make[2]: Leaving directory `/mnt/data/build/binutils-2.19/objdir/ld'
make[1]: Nothing to be done for `all-target'.
make[1]: Leaving directory `/mnt/data/build/binutils-2.19/objdir'

real	7m34.304s
user	2m48.787s
sys	1m1.040s
tom@deathstar:~/build/binutils-2.19/objdir$ uname -a
Linux deathstar 2.6.27-10-generic #1 SMP Fri Nov 21 19:19:18 UTC 2008 x86_64 GNU/Linux
tom@deathstar:~/build/binutils-2.19/objdir$ 

```

Once it's built, you can install it:

$ sudo make install
(enter password and wait for a bit)
tom@deathstar:~/build/binutils-2.19/objdir$ dir /usr/local/mingw32-cross
bin  i686-pc-mingw32  info  lib  man  share
tom@deathstar:~/build/binutils-2.19/objdir$ dir /usr/local/mingw32-cross/bin
i686-pc-mingw32-addr2line  i686-pc-mingw32-dlltool  i686-pc-mingw32-nm	     i686-pc-mingw32-readelf  i686-pc-mingw32-windmc
i686-pc-mingw32-ar	   i686-pc-mingw32-dllwrap  i686-pc-mingw32-objcopy  i686-pc-mingw32-size     i686-pc-mingw32-windres
i686-pc-mingw32-as	   i686-pc-mingw32-gprof    i686-pc-mingw32-objdump  i686-pc-mingw32-strings
i686-pc-mingw32-c++filt    i686-pc-mingw32-ld	    i686-pc-mingw32-ranlib   i686-pc-mingw32-strip
tom@deathstar:~/build/binutils-2.19/objdir$ /usr/local/mingw32-cross/bin/i686-pc-mingw32-as --version
GNU assembler (GNU Binutils) 2.19
Copyright 2007 Free Software Foundation, Inc.
This program is free software; you may redistribute it under the terms of
the GNU General Public License version 3 or later.
This program has absolutely no warranty.
This assembler was configured for a target of `i686-pc-mingw32'.
tom@deathstar:~/build/binutils-2.19/objdir$ dir /usr/local/mingw32-cross/i686-pc-mingw32
bin  lib
tom@deathstar:~/build/binutils-2.19/objdir$ dir /usr/local/mingw32-cross/i686-pc-mingw32/bin
ar  as	dlltool  ld  nm  objcopy  objdump  ranlib  strip
tom@deathstar:~/build/binutils-2.19/objdir$ 

See how far you get with your mingw32 targeted binutils build.  It looks like binutils-2.19-51 builds cleanly and WITHOUT having to patch any files:

tom@deathstar:~/build/binutils-2.19/objdir$ /usr/local/mingw32-cross/bin/i686-pc-mingw32-as --version
GNU assembler (GNU Binutils) 2.19.51.20081201
Copyright 2008 Free Software Foundation, Inc.
This program is free software; you may redistribute it under the terms of
the GNU General Public License version 3 or later.
This program has absolutely no warranty.
This assembler was configured for a target of `i686-pc-mingw32'.
tom@deathstar:~/build/binutils-2.19/objdir$ 

So, you can decide if you want to use the "stock" binutils tarball or the snapshot of the next release of binutils.  You can get the binutils-2.19.51.tar.bz2 snapshot file here:

[ftp://sourceware.org/pub/binutils/snapshots/](ftp://sourceware.org/pub/binutils/snapshots/)

Good luck and report your progress here.  :)

Peace...

---

### Post by qwertymodo on 2008-12-02
Ok, so as I said, I am totally new to this, and it would seem all is not well.  First, off, from a fresh install it looks like I had a few more dependencies to meet (you probably already had them).  I don't know what of this is actually needed, but I pretty much tried to get everything that showed up as a "no" when I configured, so...

```
sudo apt-get install bison build-essential expect flex gnat texinfo
```

Now when I try to build it I get the same errors as I got the last time I tried with the other instructions (I don't remember where, I used google...)

```
qwertymodo@HAL9000:~/xgcctemp/binutils-2.19.51/objdir$ ../configure --prefix=/usr/local/xmingw32 --target=i386-pc-mingw32
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... i386-pc-mingw32
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln works... yes
checking whether ln -s works... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gnatbind... gnatbind
checking for gnatmake... gnatmake
checking whether compiler driver understands Ada... yes
checking how to compare bootstrapped objects... cmp --ignore-initial=16 $$f1 $$f2
checking for version 0.10 of PPL... no
checking for correct version of CLooG... no
*** removing intl/Makefile to force reconfigure
*** removing libiberty/Makefile to force reconfigure
*** removing opcodes/Makefile to force reconfigure
*** removing bfd/Makefile to force reconfigure
*** removing binutils/Makefile to force reconfigure
*** removing gas/Makefile to force reconfigure
*** removing ld/Makefile to force reconfigure
*** removing gprof/Makefile to force reconfigure
*** removing etc/Makefile to force reconfigure
checking for bison... bison -y
checking for bison... bison
checking for gm4... no
checking for gnum4... no
checking for m4... m4
checking for flex... flex
checking for flex... flex
checking for makeinfo... makeinfo
checking for expect... expect
checking for runtest... no
checking for ar... ar
checking for as... as
checking for dlltool... no
checking for ld... ld
checking for lipo... no
checking for nm... nm
checking for ranlib... ranlib
checking for strip... strip
checking for windres... no
checking for windmc... no
checking for objcopy... objcopy
checking for objdump... objdump
checking for i386-pc-mingw32-cc... no
checking for i386-pc-mingw32-gcc... no
checking for i386-pc-mingw32-c++... no
checking for i386-pc-mingw32-g++... no
checking for i386-pc-mingw32-cxx... no
checking for i386-pc-mingw32-gxx... no
checking for i386-pc-mingw32-gcc... no
checking for i386-pc-mingw32-gcj... no
checking for i386-pc-mingw32-gfortran... no
checking for i386-pc-mingw32-ar... no
checking for i386-pc-mingw32-as... no
checking for i386-pc-mingw32-dlltool... no
checking for i386-pc-mingw32-ld... no
checking for i386-pc-mingw32-lipo... no
checking for i386-pc-mingw32-nm... no
checking for i386-pc-mingw32-objdump... no
checking for i386-pc-mingw32-ranlib... no
checking for i386-pc-mingw32-strip... no
checking for i386-pc-mingw32-windres... no
checking for i386-pc-mingw32-windmc... no
checking where to find the target ar... just compiled
checking where to find the target as... just compiled
checking where to find the target cc... pre-installed
checking where to find the target c++... pre-installed
checking where to find the target c++ for libstdc++... pre-installed
checking where to find the target dlltool... just compiled
checking where to find the target gcc... pre-installed
checking where to find the target gcj... pre-installed
checking where to find the target gfortran... pre-installed
checking where to find the target ld... just compiled
checking where to find the target lipo... pre-installed
checking where to find the target nm... just compiled
checking where to find the target objdump... just compiled
checking where to find the target ranlib... just compiled
checking where to find the target strip... just compiled
checking where to find the target windres... just compiled
checking where to find the target windmc... just compiled
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether -fkeep-inline-functions is supported... yes
configure: creating ./config.status
config.status: creating Makefile

```

```
qwertymodo@HAL9000:~/xgcctemp/binutils-2.19.51/objdir$ time make
make[1]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir'
make[2]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/libiberty'
make[3]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/libiberty/testsuite'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/libiberty/testsuite'
make[2]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/libiberty'
make[2]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/intl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/intl'
make[2]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/bfd'
Making info in doc
make[3]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/bfd/doc'
make[3]: Nothing to be done for `info'.
make[3]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/bfd/doc'
Making info in po
make[3]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/bfd/po'
make[3]: Nothing to be done for `info'.
make[3]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/bfd/po'
make[3]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/bfd'
make[3]: Nothing to be done for `info-am'.
make[3]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/bfd'
make  all-recursive
make[3]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/bfd'
Making all in doc
make[4]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/bfd/doc'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/bfd/doc'
Making all in po
make[4]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/bfd/po'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/bfd/po'
make[4]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/bfd'
make[4]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/bfd'
make[3]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/bfd'
make[2]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/bfd'
make[2]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/opcodes'
make  all-recursive
make[3]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/opcodes'
Making all in po
make[4]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/opcodes/po'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/opcodes/po'
make[4]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/opcodes'
make[4]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/opcodes'
make[3]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/opcodes'
make[2]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/opcodes'
make[2]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/binutils'
Making info in doc
make[3]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/binutils/doc'
make[3]: Nothing to be done for `info'.
make[3]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/binutils/doc'
Making info in po
make[3]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/binutils/po'
make[3]: Nothing to be done for `info'.
make[3]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/binutils/po'
make[3]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/binutils'
make[3]: Nothing to be done for `info-am'.
make[3]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/binutils'
make  all-recursive
make[3]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/binutils'
Making all in doc
make[4]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/binutils/doc'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/binutils/doc'
Making all in po
make[4]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/binutils/po'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/binutils/po'
make[4]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/binutils'
make[4]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/binutils'
make[3]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/binutils'
make[2]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/binutils'
make[2]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/etc'
for f in standards.info configure.info; do \
	  if test -f ../../etc/`echo $f | sed -e 's/.info$/.texi/'`; then \
	    if make "MAKEINFO=makeinfo --split-size=5000000 --split-size=5000000" $f; then \
	      true; \
	    else \
	      exit 1; \
	    fi; \
	  fi; \
	done
make[3]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/etc'
make[3]: `../../etc/standards.info' is up to date.
make[3]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/etc'
make[3]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/etc'
make[3]: `../../etc/configure.info' is up to date.
make[3]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/etc'
make[2]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/etc'
make[2]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/gas'
Making info in doc
make[3]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/gas/doc'
make[3]: Nothing to be done for `info'.
make[3]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/gas/doc'
Making info in po
make[3]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/gas/po'
make[3]: Nothing to be done for `info'.
make[3]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/gas/po'
make[3]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/gas'
make[3]: Nothing to be done for `info-am'.
make[3]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/gas'
make  all-recursive
make[3]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/gas'
Making all in doc
make[4]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/gas/doc'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/gas/doc'
Making all in po
make[4]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/gas/po'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/gas/po'
make[4]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/gas'
make[4]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/gas'
make[3]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/gas'
make[2]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/gas'
make[2]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/gprof'
make  all-recursive
make[3]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/gprof'
Making all in po
make[4]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/gprof/po'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/gprof/po'
make[4]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/gprof'
make[4]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/gprof'
make[3]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/gprof'
make[2]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/gprof'
make[2]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/ld'
Making info in po
make[3]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/ld/po'
make[3]: Nothing to be done for `info'.
make[3]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/ld/po'
make[3]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/ld'
make[3]: Nothing to be done for `info-am'.
make[3]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/ld'
make  all-recursive
make[3]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/ld'
Making all in po
make[4]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/ld/po'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/ld/po'
make[4]: Entering directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/ld'
/bin/bash ./libtool --tag=CC --mode=link gcc -W -Wall -Wstrict-prototypes -Wmissing-prototypes -Werror -g -O2   -o ld-new  ldgram.o ldlex.o lexsup.o ldlang.o mri.o ldctor.o ldmain.o ldwrite.o ldexp.o ldemul.o ldver.o ldmisc.o ldfile.o ldcref.o ei386pe.o deffilep.o pe-dll.o ../bfd/libbfd.la ../libiberty/libiberty.a  
libtool: link: gcc -W -Wall -Wstrict-prototypes -Wmissing-prototypes -Werror -g -O2 -o ld-new ldgram.o ldlex.o lexsup.o ldlang.o mri.o ldctor.o ldmain.o ldwrite.o ldexp.o ldemul.o ldver.o ldmisc.o ldfile.o ldcref.o ei386pe.o deffilep.o pe-dll.o  ../bfd/.libs/libbfd.a ../libiberty/libiberty.a
deffilep.o: In function `main':
/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/ld/deffilep.c:1: multiple definition of `main'
ldmain.o:/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/ld/../../ld/ldmain.c:184: first defined here
ei386pe.o: In function `gld_i386pe_unrecognized_file':
/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/ld/ei386pe.c:1397: undefined reference to `def_file_parse'
pe-dll.o: In function `pe_implied_import_dll':
/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/ld/../../ld/pe-dll.c:2809: undefined reference to `def_get_module'
/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/ld/../../ld/pe-dll.c:2837: undefined reference to `def_file_add_import'
/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/ld/../../ld/pe-dll.c:2794: undefined reference to `def_file_empty'
pe-dll.o: In function `process_def_file':
/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/ld/../../ld/pe-dll.c:601: undefined reference to `def_file_add_directive'
/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/ld/../../ld/pe-dll.c:663: undefined reference to `def_file_add_export'
/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/ld/../../ld/pe-dll.c:713: undefined reference to `def_file_add_export'
/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/ld/../../ld/pe-dll.c:588: undefined reference to `def_file_empty'
collect2: ld returned 1 exit status
make[4]: *** [ld-new] Error 1
make[4]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/ld'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/ld'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir/ld'
make[1]: *** [all-ld] Error 2
make[1]: Leaving directory `/home/qwertymodo/xgcctemp/binutils-2.19.51/objdir'
make: *** [all] Error 2

real	0m1.174s
user	0m0.848s
sys	0m0.328s

```

Also, by mingw-runtime, do you mean mingwrt-3.15.1??

---

### Post by qwertymodo on 2008-12-02
Ok, so I moved my working directory out of the source directory (can't remember where, but I remember reading something about gcc not supporting build directories in the same directory or a subdirectory of the source or install directories).  Looks good now.  I used binutils 2.19-51, and will be building gcc 4.3.2.  No idea where to go from here tho...

---

### Post by qwertymodo on 2008-12-02
Ok, so I checked out that link you pointed to, and for the next step first off you need gmp and mpfr

```
sudo apt-get install libgmp3-dev libmpfr-dev
```

then create a new directory outside of your gcc source dir (I called it build-gcc)

```
mkdir build-gcc
cd build-gcc
../gcc-4.3.2/configure --prefix=/usr/local/xmingw32 --host=x86_64-pc-linux --build=x86_64-pc-linux --target=i386-pc-mingw32 --without-headers --with-newlib --disable-threads --enable-languages=c,c++,java
make

```

I'm going to bed now, it seems to be taking it's sweet time compiling so I'll check in the morning.

---

### Post by qwertymodo on 2008-12-02
grr... more errors...


```
../../../gcc-4.3.2/libgcc/../gcc/config/i386/cygming-crtbegin.c:43:21: error: windows.h: No such file or directory
../../../gcc-4.3.2/libgcc/../gcc/config/i386/cygming-crtbegin.c: In function ‘__gcc_register_frame’:
../../../gcc-4.3.2/libgcc/../gcc/config/i386/cygming-crtbegin.c:113: error: ‘HANDLE’ undeclared (first use in this function)
../../../gcc-4.3.2/libgcc/../gcc/config/i386/cygming-crtbegin.c:113: error: (Each undeclared identifier is reported only once
../../../gcc-4.3.2/libgcc/../gcc/config/i386/cygming-crtbegin.c:113: error: for each function it appears in.)
../../../gcc-4.3.2/libgcc/../gcc/config/i386/cygming-crtbegin.c:113: error: expected ‘;’ before ‘h’
../../../gcc-4.3.2/libgcc/../gcc/config/i386/cygming-crtbegin.c:114: error: ‘h’ undeclared (first use in this function)
../../../gcc-4.3.2/libgcc/../gcc/config/i386/cygming-crtbegin.c:116: warning: implicit declaration of function ‘GetProcAddress’
make[2]: *** [crtbegin.o] Error 1
make[2]: Leaving directory `/home/qwertymodo/xgcctemp/build-gcc/i386-pc-mingw32/libgcc'
make[1]: *** [all-target-libgcc] Error 2
make[1]: Leaving directory `/home/qwertymodo/xgcctemp/build-gcc'
make: *** [all] Error 2

```

---

### Post by bismark on 2008-12-02
> **qwertymodo said:**
> grr... more errors...

```
../../../gcc-4.3.2/libgcc/../gcc/config/i386/cygming-crtbegin.c:43:21: error: windows.h: No such file or directory

```

Do you have mingw32-runtime installed? That package provides windows.h

---

### Post by tomdkat on 2008-12-02
> **bismark said:**
> Do you have mingw32-runtime installed? That package provides windows.hI found, it doesn't.  win32api does and I learned that the hard way.  :)

@qwertymodo: You're making great progress!  I was going to mention the GMP and MPFR dependencies as well but I see you discovered that on your own.

I'm also at the stage of building gcc and I actually got a C cross compiler built.  Here is what I've done thus far:

[list][*]Built binutils-2.19-51 targeting i686-pc-mingw32[*]Copied the include and lib directories from the mingw-runtime and win32api tarballs into $PREFIX/i686-pc-mingw32[*]Built a C-only gcc 4.3.2 cross compiler targeting i686-pc-mingw32[/list]

The mingw-runtime tarball I used is mingwrt-3.15.1.
The win32api tarball I used is win32api-3.12.

I downloaded the source targballs of both but using the DEV tarballs might be what is actually needed.

I found after copying the headers from the win32api-3.12/include directory to my $PREFIX/i686-pc-mingw32/include directory provided the windows.h file needed to address the compile error you hit.

Once I got through the C-only cross compiler build, I nuked my build tree and started to build it again using --enable-languages=c,c++,java and ran into some C++ compilation issues.

So, my current plan is to go back to making the C-only compiler and see if I can get that to build cleanly. I'll report back my findings later on.

I also found another site where someone listed their process for building a MingW-targeted gcc-4 based cross compiler. If I can find that site again, I'll post a link here as well.

Peace...

---

### Post by qwertymodo on 2008-12-05
...still can't get gcc to compile... i'm gonna just start over... :(

---

### Post by tomdkat on 2008-12-12
Guess what?????  I've just built a 64-bit Linux hosted, Win32 targeted cross compiler!!!!

Here is what I did:

1) Downloaded the following tool chain:
binutils-2.19-51
gcc-4.2.4
mingwrt-3.15.1-src
w32api-3.13-src

2) Built binutils first:
$ tar zxf binutils-2.19-51.tar.gz
$ mkdir objdir
$ cd objdir
$ ../binutils-2.19.51/configure --target=i686-pc-mingw32 --prefix=/usr/local/mingw32
$ make
$ make install

3) Copy w32api headers to the install directory:
$ tar zxf w32api-3.13-mingw32-src.tar.gz
$ cp -r w32api-3.13-mingw32/include /usr/local/mingw32/i686-pc-mingw32
$ ln -s w32api-3.13-mingw32 w32api

4) Copy mingw runtime to the install directory:
$ tar zxf mingwrt-3.15.1-src.tar.gz
$ cp -r mingwrt-3.15.1-mingw32/include /usr/local/mingw32/i686-pc-mingw32

5) Build a C-only cross compiler:
$ tar zxf gcc-4.2.4.tar.gz
$ rm -fR objdir
$ mkdir objdir
$ cd objdir
$ ../gcc-4.2.4/configure --prefix=/usr/local/mingw32 --target=i686-pc-mingw32 --with-headers=/usr/local/mingw32/i686-pc-mingw32/include \
--enable-languages=c
$ make
$ make install

6) Add the Win32 targeted tool chain to your path:
$ export PATH=$PATH:/usr/local/mingw32/bin

7) Build the Win32 API libraries:
$ cd w32api-3.13-mingw32
$ ./configure --prefix=/usr/local/mingw32/i686-pc-mingw32 --target=i686-pc-mingw32
$ make
$ make install

8) Build the Win32 MingW runtime libraries
$ cd mingwrt-3.15.1-mingw32
$ ./configure --prefix=/usr/local/mingw32/i686-pc-mingw32 --target=i686-pc-mingw32
$ make
$ make install

9) Build a C,C++,Java Win32 targeted cross compiler:
$ rm -fR objdir   (This is the objdir built for the C-only compiler above)
$ mkdir objdir
$ cd objdir
$ ../gcc-4.2.4/configure --prefix=/usr/local/mingw32 --target=i686-pc-mingw32 --with-headers=/usr/local/mingw32/i686-pc-mingw32/include \
--enable-languages=c,c++,java
$ make
$ make install

If you make it this far, you should have a working C++ and Java Win32 targeting cross compiler built.  :)

tom@deathstar:~/build/cross/src$ i686-pc-mingw32-gcj --version
i686-pc-mingw32-gcj (GCC) 4.2.4
Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

tom@deathstar:~/build/cross/src$ i686-pc-mingw32-gcj -dumpmachine
i686-pc-mingw32
tom@deathstar:~/build/cross/src$ 

I started out using gcc-4.3.2 above but ran into problems that others have run into and the consensus seems to be using a gcc-4.2.x source tree instead of gcc-4.3.x.

Give it a try and post your results here.  :)

EDIT:  Well, the C++ cross compiler worked (it created an EXE for me that I have yet to test) but the Java compiler won't run due to a libgcj.spec file not being created for some reason. :(

Peace...

---

### Post by eman7613 on 2008-12-14
Hi there, i have been trying to do this exact same thing on ubuntu8.10 x64 and have been having trouble. I tried to do what you said, and got all of the same sources and I keep getting errors when building the Win32 API libraries.
ends like this
```
/usr/include/sys/select.h:78: error: conflicting types for ‘fd_set’
./../include/winsock2.h:64: error: previous declaration of ‘fd_set’ was here
/usr/include/sys/select.h:109: error: conflicting types for ‘select’
./../include/winsock2.h:632: error: previous declaration of ‘select’ was here
scrnsave.c:36: warning: ‘stdcall’ attribute ignored
scrnsave.c:37: warning: ‘stdcall’ attribute ignored
scrnsave.c:51: warning: ‘stdcall’ attribute ignored
scrnsave.c:79: warning: ‘stdcall’ attribute ignored
make[1]: *** [scrnsave.o] Error 1
make: *** [lib] Error 2

```

Did you experience this at all or have an idea? Also did you install anything else that might be a dependency (trying this with 4.2.4, as you noted. also tried with others and i cant get past this.)

---

### Post by tomdkat on 2008-12-15
I vaguely remember seeing those kinds of messsages while building the Win32 API libraries.  I believe I resolved that by updating my PATH environment variable to include the location of the i686-pc-mingw32-xxx files.

Could you post more of your compile output so we can see which compiler is being invoked?

Peace...

---

### Post by eman7613 on 2008-12-15
I did this with a script, and said CC=gcc-4.2 at the top of it, and edit the path later. I am guessing this is what is causing the problem, I will post once I find out (need to get back to my desktop).

EDIT:
Okay, i cet CC="" and then had to set path to $PREFIX/$TARGET/bin:$PATH inorder for Win32 API to compile, but i can not get the MinGW runtime to compile at all, using gcc-4.2 or the just compiled gcc

```
make: *** [dllcrt2.o] Error 1
In file included from ../mingwrt-3.15-mingw32/crt1.c:22:
../mingwrt-3.15-mingw32/include/signal.h:84: warning: &#8216;__cdecl__&#8217; attribute ignored
../mingwrt-3.15-mingw32/include/signal.h:89: warning: &#8216;__cdecl__&#8217; attribute ignored
../mingwrt-3.15-mingw32/crt1.c:45: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;void&#8217;
../mingwrt-3.15-mingw32/crt1.c:104: warning: &#8216;__stdcall__&#8217; attribute ignored
make: *** [crt2.o] Error 1
```

I would scroll back up to see how it was configured, but i can not error messages like this one show up EVERYWHERE, filling up ther terminal completly so there is nothing else till there error.

```
../mingwrt-3.15-mingw32/include/process.h:126: warning: &#8216;__cdecl__&#8217; attribute ignored
```

(this shows up several times for each file)

---

### Post by tomdkat on 2008-12-16
Again, please post more of the build output so we can see which compiler is being invoked,etc.

Also, if you can please post the script you're using to build this.

As for the libgcj.spec problem, I think I'm now closer to getting a gcc-4.3.2 based Mingw32-targeted cross compiler built with C++ and Java support.  :)

Peace...

---

### Post by eman7613 on 2008-12-16
Attached is the script I made, and the build log, and as much of the build output that I could grab.

---

### Post by tomdkat on 2008-12-17
Thanks! I'll take a peek. I'm in the process of rebuilding my cross compiler toolchain to get a working GCJ cross compiler so once I've got that finished, I'll report back here with what I ended up doing.

EDIT:  Ok, we seem to be miscommunicating. :)   What I want to see is ALL of build output, and not just the errors.  :)   I want to see the compiler invocation, command line args, etc.  I want to make sure the build is running the right compiler.  Also, I noticed this in your script:
```

echo "Build Win32 Mingw runtime libraries"
cd mingwrt-*-mingw32
#mkdir buildMINRT
#cd buildMINRT
**[color=red]ln -s ../w32api-*-mingw32 w32api[/color]**
#../mingwrt-*-mingw32/configure --prefix=$PREFIX/$TARGET --target=$TARGET
./configure --prefix=$PREFIX/$TARGET --target=$TARGET
make $FLAGS
echo "We just tried to build Win32 Mingw runtime"
read name
make install

```I'm not sure if that link is interfering or not.

Again, I'll post an update once I'm done rebuilding my cross compiler.  I'll also post build output from the w32api and mingwrt builds.

Peace...

---

### Post by tomdkat on 2008-12-18
Ok, I'm at the C/C++/Java cross compiler build phase (building right now).  I built EVERYTHING from scratch (again) and here is what I did:

First, I built my build and source directories as separate, "peer" level directories:
$ mkdir build
$ cd build
$ mkdir src
$ mkdir bld

Then, I unpacked all the source files in the source directory:
$ cd src
$ tar zxf ~/binutils-2.19.51.tar.gz
$ tar zxf ~/mingwrt-3.15.1-mingw32-src.tar.gz
$ tar zxf ~/w32api-3.13-mingw32-src.tar.gz
$ tar zxf ~/gcc-4.3.2.tar.gz

Then, I built the Win32 targeted binutils:
$ cd ../bld
$ mkdir objdir
$ cd objdir
$ ../../src/binutils-2.19.51/configure --prefix=/usr/local/mingw32 --target=i686-pc-mingw32
$ make
$ sudo make install

Then, I copied the Win32 API and Mingw runtime headers to the right spot:
$ cd ../../src
$ sudo cp -r w32api-3.13-mingw32/include /usr/local/mingw32/i686-pc-mingw32
$ ln -s w32api-3.13 w32api
$ sudo cp -r mingwrt-3.15.1-mingw32/include /usr/local/mingw32/i686-pc-mingw32

Then, I built the Win32 targeted C compiler that will be used to build the Win32 runtime:
$ cd ../../bld
$ rm -fR objdir
$ mkdir objdir
$ cd objdir
$ sudo ../../src/gcc-4.3.2/configure --prefix=/usr/local/mingw32 --target=i686-pc-mingw32 --with-headers=/usr/local/mingw32/i686-pc-mingw32/include --enable-languages=c
$ make
$ sudo make install

Then, I built the Win32 runtime:
$ cd ../../src/w32api-3.13-mingw32
$ ./configure --prefix=/usr/local/mingw32/i686-pc-mingw32 **--host=i686-pc-mingw32**
$ make
$ sudo make install
$ cd ../mingwrt-3.15.1-mingw32
$ ./configure --prefix=/usr/local/mingw32/i686-pc-mingw32 **--host=i686-pc-mingw32**
$ make
$ sudo make install

Then, I started building the C,C++,Java Mingw32 targeted cross compiler:
$ cd ../bld
$ rm -fR objdir
$ mkdir objdir
$ cd objdir
$ sudo ../../src/gcc-4.3.2/configure --prefix=/usr/local/mingw32 --target=i686-pc-mingw32 --with-headers=/usr/local/mingw32/i686-pc-mingw32/include --enable-languages=c,c++,java
$ make

The build is still running.

Now, I've been doing some more research on this since I first started it and found [this site](http://linux.50webs.org/compile/gcc-4.3.0-compilers.htm) which has GREAT instructions I've been following.

Some notes:
[list]
[*]I added my Mingw32 installation bin directory (/usr/local/mingw32/bin) to the system path so sudo could find the binaries as well as my account.  The Win32 runtime build will need to use the Mingw32 targeted cross compiler in order to build.  I'll attach my build output to this post.
[*]For the Java compiler to work, I had to specify "--enable-libgcj" on the C,C++,Java cross compiler configure command to make sure libgcj.spec got built and installed.  I THEN learned I needed to put ecj.jar into the gcc-4.3.2 source tree so the gcj compiler would be able to parse Java files.
[/list]

Attached is my w32api build output as well as the mingw runtime build output.

Peace...

---

### Post by eman7613 on 2008-12-18
I just finished making a cross compiler by skipping the build w32api and runtime, and just downloading the binaries from the mingw website - same thing almost though. 

Note though, if you make an executable from a Java source file, 2 things:
1) it will be large, run the strip program (the one you compiled on it) to make it MUCH smaller (went from ~30mb to 11mb for a hello world, but this is expected since it needs the GC and other JRE toys to run).
2) You cant/will have trouble running the program in wine, however they will work under windows (which is the ultimate goal) so its still good :)

ive tested c,c++,Java,Fortran and they all seem to work cross compiled from x64 linux to windows, haven't tested an obj-c or obj-c++ yet, and couldn't get ada to build.

---

### Post by tomdkat on 2008-12-19
Thanks for the update!  I just finished my cross compiler this morning and it actually generated a native Windows executable that I have yet to test.  :)

Here are some additional things I had to do:
[list]
[*]I had to get the native gcj compiler installed and I used the Synaptic Package Manager to install it.
[*]I had to create a symlink to gcj called "x86_64-unknown-linux-gnu-gcj" so the cross compiler build would work.
[*]When compiling Java source to a Windows native executable, I have to specify "--main={class with main defined}" to get around this link error:
```

tom@deathstar:~/build$ i686-pc-mingw32-gcj HelloWorld.java -o HelloWorldApp.exe
/usr/local/mingw32/lib/gcc/i686-pc-mingw32/4.3.2/../../../../i686-pc-mingw32/lib/libmingw32.a(main.o): In function `main':
/home/tom/build/cross/src/mingwrt-3.15.1-mingw32/main.c:73: undefined reference to `_WinMain@16'
collect2: ld returned 1 exit status
tom@deathstar:~/build$

```
[/list]Other than that, everything else seemed to run just fine.

Now that I've got it built and working, I'm going to nuke it all and re-build it from scratch to take timings.  On my AMD64 3200+ based machine, I'm thinking everything builds in about 3-4 hours or so.

Glad to hear you got yours working as well and thanks for the tip on running strip to reduce the file size.  :)

Peace...

---

### Post by eman7613 on 2008-12-19
> **tomdkat said:**
> I had to create a symlink to gcj called "x86_64-unknown-linux-gnu-gcj" so the cross compiler build would work.

This appears to be a strangeness with GCC 4.3.2, I compiled with 4.2.4 and everything works fine. Making a 4.3.2 version with the exact same process, i get the error that i think you had too, prompting the need for this symbolic link (It happens at [all-target-libjava] Error 2).


also, "When compiling Java source to a Windows native executable, I have to specify "--main={class with main defined}" to get around this link error:"

This is just how gcj works, that is not cross compiler specific.

---

### Post by tomdkat on 2008-12-19
> **eman7613 said:**
> This appears to be a strangeness with GCC 4.3.2, I compiled with 4.2.4 and everything works fine. Making a 4.3.2 version with the exact same process, i get the error that i think you had too, prompting the need for this symbolic link (It happens at [all-target-libjava] Error 2).Gotcha.

> also, "When compiling Java source to a Windows native executable, I have to specify "--main={class with main defined}" to get around this link error:"

This is just how gcj works, that is not cross compiler specific.Coolio.  :)

Peace...

---

### Post by eman7613 on 2008-12-20
Did some more testing, (have a nice fast computer that can do almost 2 full builds in an hour :) ), I was a little bit wrong.

The funny is actualy with gcc 4.2.4, in that it appears to be smarter when it comes to configuring :P All the other versions choke and need the symbolic link fix. However, specifying "**--build=x86_64-linux-gnu --host=x86_64-linux-gnu**" in the final build of gcc will make everything work, no hacks needed. :grin: However, this will build gcj correctly if ecj.jar is *in the source directory*, specifiying its location will not work. 

Note: mingw-gcj-4.3.2 produces even larger binaries, 44mb->striped dwon to->13.4mb, kinda strange - but it works.



Hmm, can get flawless cross copmilers for gcc versions 4.2.X and 4.3.X, but nothing from 4.0.X or 4.1.X, if anyone figures this out would love to know.

---

### Post by tomdkat on 2008-12-21
Here are my build timings on my AMD64 3200+:

binutils-2.19.51: 4m 44s
gcc (C-only):    15m 13s
w32api:           0m 22s
mingwrt:          0m 44s
gcc (C,C++,Java):74m 50s

What happens when you try build gcc-4.0.x or 4.1.x cross compilers?  Why are you trying to use those older compilers?

Peace...

---

### Post by eman7613 on 2008-12-21
Okay, was able to get 4.0.X to compile by just downloading the binaries again (or using the ones from a previous compile), 3.4.6 as well though i didnt try doing that one from complete source.. building from only sources,  4.0.X chokes on compiling w32api no matter what, and 4.1.X chokes on building the C cross compiler, which is duplicating binaries cant side step the problem. 

Sometimes its nice to have the other compiles at your disposal for various reason!

For example, ive found out that compiling java to native with 3.4.6 will result in a binary that wine can run! Additional the executable gets much small as you go back in versions, 3.4.6 produce a binary initially 6mb in size, then strip brought it down to a respectable 2 mb. Im guessing this is due to the growing size of the gnu class-path over the years, but im not sure why it seems to include so much of the class-path when making executables (though i could be wrong, this is just a guess). 

So, if one needs to, just about everything except the 4.1.X gcc can be compiled the instrunctions you posted, though sometimes you just need to duplicated the binaries for w32api and mingwruntime, in which case you just do binutils -> copy binaries -> entire compiler suite (which would save you some time on older systems!)

building everything from source (binutils, c cross, w32api, mingwruntime, gmp, mpfr, then cross c,c++,java,objc, obj-c++,fortran) took 48 minutes for gcc 4.3.2 (and i was watching stuff online and inter webing)

intel quad 6600 - using all 4 cores

---

### Post by tomdkat on 2008-12-24
> **eman7613 said:**
> For example, ive found out that compiling java to native with 3.4.6 will result in a binary that wine can run!Which version of wine are you running?

> building everything from source (binutils, c cross, w32api, mingwruntime, gmp, mpfr, then cross c,c++,java,objc, obj-c++,fortran) took 48 minutes for gcc 4.3.2 (and i was watching stuff online and inter webing)

intel quad 6600 - using all 4 cores:guitar:

EDIT:  Check out this [wine announcement](http://www.winehq.org/announce/1.1.11)!  I guess it's time to play with Mingw64 now.  :D

Peace...

---

### Post by eman7613 on 2008-12-24
don't remember what version of wine I was using, wont have access to the same computer that i originally used for another month :( 

MinGW64 is still beta to my understanding, its probably not worth the effort to try yet.

---

### Post by qwertymodo on 2009-01-26
Sorry I never got back to anyone on this, I had Christmas break and kinda left it alone.  I haven't yet gotten a single successful complete build... :(  Will try again and check back when I do.

---

### Post by eman7613 on 2009-01-26
Thats okay, it happens.

[http://www.edwardraff.com/index.php?target=crosscompiling](http://www.edwardraff.com/index.php?target=crosscompiling)

You can download the script I made to build a cross complier from there.

---

