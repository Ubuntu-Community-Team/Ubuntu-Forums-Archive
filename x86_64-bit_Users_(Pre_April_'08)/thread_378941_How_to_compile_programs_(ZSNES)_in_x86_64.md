---
title: "How to compile programs (ZSNES) in x86_64"
date: 2007-03-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by dfreer on 2007-03-07
Hi all,

  I have ZSNES installed by using dpkg --force-architecture, and it runs fine. But I'm just trying to understand why there isn't an AMD64 package available. According to [*_this thread_*]("http://www.ubuntuforums.org/showthread.php?t=368568") it seems like as long as I have the source code I should be able to compile anything. ZSNES according to the maintainers is not compilable in AMD64, for I assume the same reasons why wine needs to run in 32-bit mode. But wine has an AMD64 package... shouldn't I be able to build one for ZSNES?

 Here's what I have done so far:
[LIST]
[*]I have installed build-essential package
[*]I have installed 32-bit libraries (although I don't believe I should need these if I understand things correctly)
[*]I am running Edgy AMD64 with a Intel Core 2 Duo T7200
[/LIST]
  
Specific Problems:

[INDENT]  I have downloaded the [_*latest zsnes source files*_]("http://superb-west.dl.sourceforge.net/sourceforge/zsnes/zsnes151src.tar.bz2"), untarred them, and navigated to the src folder. I run as user and I get this error:
```
$ make
g++  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -D__OPENGL__ -march=pentium-m -O3 -fomit-frame-pointer -s -fno-rtti -o tools/fileutil.o -c tools/fileutil.cpp
tools/fileutil.cpp:1: error: CPU you selected does not support x86-64 instruction set
```
I assume this is refering to the -march flag, and after googling [_*this thread*_]("http://forums.gentoo.org/viewtopic-t-496285.html") it looks like I need to modify the makefile to change -march=pentium-m to either -march=nocona or athlon-xp. athlon-xp gives me the same errors as above, so I try nocona and it starts working... but then I get a bunch of these errors (without the asterisks):
```
/usr/bin/ld: warning: i386 architecture of input file _`*****.o'_ is incompatible with i386:x86-64 output

```
I'm guessing these are libraries unique to zsnes and they are of the wrong ELF class... so I'm at a bit of a loss on how to proceed with zsnes.
[/INDENT]

---

### Post by Kilz on 2007-03-08
> **dfreer said:**
> Hi all,

  I have ZSNES installed by using dpkg --force-architecture, and it runs fine. But I'm just trying to understand why there isn't an AMD64 package available. According to [*_this thread_*]("http://www.ubuntuforums.org/showthread.php?t=368568") it seems like as long as I have the source code I should be able to compile anything. ZSNES according to the maintainers is not compilable in AMD64, for I assume the same reasons why wine needs to run in 32-bit mode. But wine has an AMD64 package... shouldn't I be able to build one for ZSNES?


The thing is, that even the versions of wine that are amd64bit packages. They are only 32bit. This is a good thing, because 99.9% of all windows applications are 32bit.
If ZSNES is a 32bit emulator, you may end up bashing your head into a wall trying to make something that will give you 0% performance improvement. All it will do is make something that installs easier, but is still 32bit. Because it needs to be in order to run the executables.

---

### Post by dfreer on 2007-03-09
> The thing is, that even the versions of wine that are amd64bit packages. They are only 32bit. If ZSNES is a 32bit emulator, you may end up bashing your head into a wall trying to make something that will give you 0% performance improvement. All it will do is make something that installs easier, but is still 32bit.

I should have made things a little bit clearer. I realize that the wine packages are still 32-bit, but they are packaged for AMD64 to make it super easy to install in Ubuntu x86_64. THAT is what I want to do for ZSNES, to install the 32-bit version with an AMD64 .deb. That way I don't have to use the --force-archiecture command. Similiar to the way that I can install 32-bit libraries in x86_64 using AMD64 .debs.

In all honesty, I don't do anything in 64-bit that I even notice the performance boost, at most I *might* rip a DVD. I simply run 64-bit because I can, and I enjoy the challenge of learning how to do stuff.

---

### Post by Kilz on 2007-03-09
> **dfreer said:**
> I should have made things a little bit clearer. I realize that the wine packages are still 32-bit, but they are packaged for AMD64 to make it super easy to install in Ubuntu x86_64. THAT is what I want to do for ZSNES, to install the 32-bit version with an AMD64 .deb. That way I don't have to use the --force-archiecture command. Similiar to the way that I can install 32-bit libraries in x86_64 using AMD64 .debs.

In all honesty, I don't do anything in 64-bit that I even notice the performance boost, at most I *might* rip a DVD. I simply run 64-bit because I can, and I enjoy the challenge of learning how to do stuff.

What you could do , is take the 32bit deb, extract it, extract the control file, and extract the program or data. Place the control file in a folder named DEBIAN the rest of the files should go in folders matching thier location in the file system. [Then use the instructions to create a binary deb file]("http://linuxdevices.com/articles/AT8047723203.html"). You will of course have to edit the control file and in architecture replace i386 with amd64.
But all it will do is make it easier for you or others to install, it will be the same files in the same locations you would get forcing it in.

---

### Post by dfreer on 2007-03-09
Thanks! I will definitely check out the link, here I was thinking I would have to use flags in the compiler and checkinstall to tell it to make a x86 .deb.

---

### Post by Slammer64 on 2007-04-27
Just an FYI for those trying to compile ZSNES on 64 bit machines, (I read this on the ZSNES forums), try setting your CFLAGS="-m32" and your CXXFLAGS="-m32" I have successfully compiled ZSNES on several 64 bit Linux distros this way, openSUSE and Fedora Core 6.

---

### Post by dfreer on 2007-04-28
so, like this?
```
./configure CFLAGS="-m32" CXXFLAGS="-m32"
```
or do I need to edit the configure file somewhere?

---

### Post by Slammer64 on 2007-04-28
I just use the "export" command i.e. export CFLAGS="-m32" export CXXFLAGS="-m32"

---

### Post by argux on 2007-04-29
> **Slammer64 said:**
> I just use the "export" command i.e. export CFLAGS="-m32" export CXXFLAGS="-m32"

Actually, I think (as I remember from my old lfs days), you can just state the flags before the command, like so:

```
CFLAGS="-m32" CXXFLAGS="-m32" ./configure
```

or something like that. I'm not terribly sure about it, but I don't think I'm too mistaken either.

---

### Post by nekoyokoshima on 2007-06-11
I exported CFLAGS and CXXFLAGS. However ./configure returned this error

```
root@neteng-keith:/home/keith/temp/zsnes151src/zsnes_1_51/src# CFLAGS="-m32" CXXFLAGS="-m32" ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking for C compiler default output file name...
configure: error: C compiler cannot create executables
See `config.log' for more details.
```

This is a copy on the config.log

> This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by configure, which was
generated by GNU Autoconf 2.61.  Invocation command line was

  $ ./configure

## --------- ##
## Platform. ##
## --------- ##

hostname = neteng-keith
uname -m = x86_64
uname -r = 2.6.20-15-generic
uname -s = Linux
uname -v = #2 SMP Sun Apr 15 06:17:24 UTC 2007

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = x86_64
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
/usr/bin/hostinfo      = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/bin/X11


## ----------- ##
## Core tests. ##
## ----------- ##

configure:1806: checking build system type
configure:1824: result: x86_64-unknown-linux-gnu
configure:1846: checking host system type
configure:1861: result: x86_64-unknown-linux-gnu
configure:1883: checking target system type
configure:1898: result: x86_64-unknown-linux-gnu
configure:1939: checking for a BSD-compatible install
configure:1995: result: /usr/bin/install -c
configure:2054: checking for gcc
configure:2070: found /usr/bin/gcc
configure:2081: result: gcc
configure:2319: checking for C compiler version
configure:2326: gcc --version >&5
gcc (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2329: $? = 0
configure:2336: gcc -v >&5
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexe
cdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enabl
e-libstdcxx-debug --enable-mpfr --enable-checking=release x86_64-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
configure:2339: $? = 0
configure:2346: gcc -V >&5
gcc: '-V' option must have argument
configure:2349: $? = 1
configure:2372: checking for C compiler default output file name
configure:2399: gcc -m32 -pipe -I. -I/usr/local/include -I/usr/include   -L/usr/local/lib -L/usr/lib conftest.c  >&5
/usr/bin/ld: skipping incompatible /usr/lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.a when searching for -lc
/usr/bin/ld: cannot find -lc
collect2: ld returned 1 exit status
configure:2402: $? = 1
configure:2440: result:
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| /* end confdefs.h.  */
|
| int
| main ()
| {
|
|   ;
|   return 0;
| }
configure:2447: error: C compiler cannot create executables
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_build=x86_64-unknown-linux-gnu
ac_cv_env_CCC_set=
ac_cv_env_CCC_value=
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=set
ac_cv_env_CFLAGS_value=-m32
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_CXXFLAGS_set=set
ac_cv_env_CXXFLAGS_value=-m32
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_LIBS_set=
ac_cv_env_LIBS_value=
ac_cv_env_XMKMF_set=
ac_cv_env_XMKMF_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_force_arch_set=
ac_cv_env_force_arch_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_host=x86_64-unknown-linux-gnu
ac_cv_path_install='/usr/bin/install -c'
ac_cv_prog_ac_ct_CC=gcc
ac_cv_target=x86_64-unknown-linux-gnu

## ----------------- ##
## Output variables. ##
## ----------------- ##

ARCH_INFO=''
CC='gcc'
CFLAGS='-m32 -pipe -I. -I/usr/local/include -I/usr/include'
CPP=''
CPPFLAGS=''
CXX=''
CXXFLAGS='-m32'
DEBUGGER_FILES=''
DEFS=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP=''
EXEEXT=''
GL_DRAW=''
GREP=''
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
JMA_FILES=''
LDFLAGS=' -L/usr/local/lib -L/usr/lib'
LIBOBJS=''
LIBPNG_CFLAGS=''
LIBPNG_LIBS=''
LIBPNG_VERSION=''
LIBS=''
LTLIBOBJS=''
MMLIB_FILES=''
NASMPATH=''
NFLAGS=''
OBJEXT=''
PACKAGE_BUGREPORT=''
PACKAGE_NAME=''
PACKAGE_STRING=''
PACKAGE_TARNAME=''
PACKAGE_VERSION=''
PATH_SEPARATOR=':'
PSRFLAGS=''
PSR_TEMP=''
SDL_CFLAGS=''
SDL_CONFIG=''
SDL_LIBS=''
SHELL='/bin/bash'
VERSION='1.51'
XMKMF=''
ZC=''
ZCFLAGS=''
ZLIB_CFLAGS=''
ZLIB_LIBS=''
ZLIB_VERSION=''
ZSNESEXE=''
ac_ct_CC='gcc'
ac_ct_CXX=''
bindir='${exec_prefix}/bin'
build='x86_64-unknown-linux-gnu'
build_alias=''
build_cpu='x86_64'
build_os='linux-gnu'
build_vendor='unknown'
datadir='${datarootdir}'
datarootdir='${prefix}/share'
docdir='${datarootdir}/doc/${PACKAGE}'
dvidir='${docdir}'
exec_prefix='NONE'
force_arch=''
host='x86_64-unknown-linux-gnu'
host_alias=''
host_cpu='x86_64'
host_os='linux-gnu'
host_vendor='unknown'
htmldir='${docdir}'
includedir='${prefix}/include'
infodir='${datarootdir}/info'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localedir='${datarootdir}/locale'
localstatedir='${prefix}/var'
mandir='${datarootdir}/man'
oldincludedir='/usr/include'
pdfdir='${docdir}'
prefix='NONE'
program_transform_name='s,x,x,'
psdir='${docdir}'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target='x86_64-unknown-linux-gnu'
target_alias=''
target_cpu='x86_64'
target_os='linux-gnu'
target_vendor='unknown'

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define PACKAGE_NAME ""
#define PACKAGE_TARNAME ""
#define PACKAGE_VERSION ""
#define PACKAGE_STRING ""
#define PACKAGE_BUGREPORT ""

configure: exit 77

Do I need a 32 bit complier?

---

### Post by nekoyokoshima on 2007-06-11
>  Super Nintendo Emulator (ZSNES) 1.510 for i386/AMD64

    * Read #General Notes 

For support or questions please see this thread [http://ubuntuforums.org/showthread.php?t=432642](http://ubuntuforums.org/showthread.php?t=432642)

echo "deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main" | sudo tee -a /etc/apt/sources.list
wget [http://packages.dfreer.org/5A22BD68.gpg](http://packages.dfreer.org/5A22BD68.gpg) -O- | sudo apt-key add -
sudo apt-get update

sudo apt-get install zsnes32 #for amd64 users
sudo apt-get install zsnes   #for everyone else

    * Applications > Games > zsnes or zsnes32 

This solved my issue. I used a .deb file instead of sources

---

### Post by zsouthboy on 2007-06-11
IIRC, ZSNES had x86 ASM sprinkled in it in spots, the last I remember.

That might be changed now, though.

---

### Post by dfreer on 2007-06-11
> **nekoyokoshima said:**
> This solved my issue. I used a .deb file instead of sources

That's MY .deb you used lol. I never did compile a 32-bit zsnes in 64-bit enviroment, I actually compiled it in 32-bit and packaged it for 64-bit, if that makes sense.

---

### Post by nekoyokoshima on 2007-06-11
It does make sense...yes.

Thanks dfeer

---

### Post by dfreer on 2007-06-11
You're welcome!
How's that zsnes32 working for you, BTW? Any sound issues?

---

### Post by fakie_flip on 2007-09-13
Could you tell me how to compile and make a deb for 64 bit please? I am trying to get a specific version that will allow me to use network play.

---

### Post by dfreer on 2007-09-13
You gotta compile a binary for x86, and then create a x86_64 .deb package. The compile instructions are fairly straightforward, although I would make sure to at least build with --enable-release (you don't have to). I compiled mine on a x86 machine, so I can't really help if you want to build a x86 package on a x86_64 machine. Anything else if you have a specific problem in the build I can probably help some.

Then, to create the .deb *my* way (this isn't the proper debian way, FYI), create a new folder. In this folder, build your directory tree structure and place your zsnes binary inside (I create ./usr/local/games/zsnes32/ and put the binary in there). create another folder called DEBIAN, and place your control file in there. then:
```
sudo dpkg -b *your_zsnes_folder* *your_zsnes_package_name*.deb
```

Hope that makes some sense, I was in a hurry lol. Feel free to ask!

EDIT: I could do a step-by-step later if needed, although you'll probably have to keep bugging me about it

---

### Post by fakie_flip on 2007-09-14
> **dfreer said:**
> You gotta compile a binary for x86, and then create a x86_64 .deb package. The compile instructions are fairly straightforward, although I would make sure to at least build with --enable-release (you don't have to). I compiled mine on a x86 machine, so I can't really help if you want to build a x86 package on a x86_64 machine. Anything else if you have a specific problem in the build I can probably help some.

Then, to create the .deb *my* way (this isn't the proper debian way, FYI), create a new folder. In this folder, build your directory tree structure and place your zsnes binary inside (I create ./usr/local/games/zsnes32/ and put the binary in there). create another folder called DEBIAN, and place your control file in there. then:
```
sudo dpkg -b *your_zsnes_folder* *your_zsnes_package_name*.deb
```

Hope that makes some sense, I was in a hurry lol. Feel free to ask!

EDIT: I could do a step-by-step later if needed, although you'll probably have to keep bugging me about it

actually i can compile a 32 bit application on a 64 bit with the help of vmware :) its just a pain in the @#%@#$ to install 32 bit ubuntu in vmware, but im going to do that because i wanted practice with software raid in vmware using 32 bit ubuntu server anyways.

---

### Post by fakie_flip on 2007-09-15
I found a 32 bit deb. I used --force-architecture to install it. i used ldd and objdump -x to see what libraries are missing. According to those commands, none are missing. Zsnes produces a lot of errors. Here's what happens when I try to run it.


```
chris@ubuntu:~/Desktop/asdfadsf$ zsnes 

ZSNES v1.42 (c) 1997-2005, ZSNES Team

Be sure to check http://www.zsnes.com/ for the latest version.
Please report crashes to zsnes-devel@lists.sourceforge.net.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE' thoroughly before doing so.

Use ZSNES -? for command line definitions.

*** glibc detected *** zsnes: munmap_chunk(): invalid pointer: 0xffd32e92 ***
======= Backtrace: =========
/lib32/libc.so.6(cfree+0x1bb)[0xf7b71b7b]
zsnes[0x80de151]
/lib32/libc.so.6(__libc_start_main+0xdc)[0xf7b1bebc]
zsnes(__gxx_personality_v0+0xd1)[0x804ba31]
======= Memory map: ========
08048000-082f8000 r-xp 00000000 08:01 3394576                            /usr/bin/zsnes
082f8000-0834b000 rwxp 002b0000 08:01 3394576                            /usr/bin/zsnes
0834b000-085d8000 rwxp 0834b000 00:00 0                                  [heap]
f6ed1000-f6f2e000 rwxp f6ed1000 00:00 0 
f6f2e000-f6f32000 r-xp 00000000 08:01 3394320                            /usr/lib32/libXdmcp.so.6.0.0
f6f32000-f6f33000 rwxp 00003000 08:01 3394320                            /usr/lib32/libXdmcp.so.6.0.0
f6f33000-f6f34000 rwxp f6f33000 00:00 0 
f6f34000-f6f36000 r-xp 00000000 08:01 3394316                            /usr/lib32/libXau.so.6.0.0
f6f36000-f6f37000 rwxp 00001000 08:01 3394316                            /usr/lib32/libXau.so.6.0.0
f6f37000-f7024000 r-xp 00000000 08:01 3394315                            /usr/lib32/libX11.so.6.2.0
f7024000-f7028000 rwxp 000ed000 08:01 3394315                            /usr/lib32/libX11.so.6.2.0
f7028000-f7035000 r-xp 00000000 08:01 3394321                            /usr/lib32/libXext.so.6.4.0
f7035000-f7036000 rwxp 0000d000 08:01 3394321                            /usr/lib32/libXext.so.6.4.0
f7036000-f7037000 r-xp 00000000 08:01 3735922                            /usr/lib32/tls/libnvidia-tls.so.100.14.11
f7037000-f7038000 rwxp 00000000 08:01 3735922                            /usr/lib32/tls/libnvidia-tls.so.100.14.11
f7038000-f7994000 r-xp 00000000 08:01 3393857                            /usr/lib32/libGLcore.so.100.14.11
f7994000-f79cc000 rwxp 0095c000 08:01 3393857                            /usr/lib32/libGLcore.so.100.14.11
f79cc000-f79d1000 rwxp f79cc000 00:00 0 
f79d1000-f79df000 r-xp 00000000 08:01 3394843                            /usr/lib32/libdirect-0.9.so.25.0.0
f79df000-f79e0000 rwxp 0000e000 08:01 3394843                            /usr/lib32/libdirect-0.9.so.25.0.0
f79e0000-f79e5000 r-xp 00000000 08:01 3394845                            /usr/lib32/libfusion-0.9.so.25.0.0
f79e5000-f79e6000 rwxp 00004000 08:01 3394845                            /usr/lib32/libfusion-0.9.so.25.0.0
f79e6000-f7a3b000 r-xp 00000000 08:01 3394844                            /usr/lib32/libdirectfb-0.9.so.25.0.0
f7a3b000-f7a3d000 rwxp 00055000 08:01 3394844                            /usr/lib32/libdirectfb-0.9.so.25.0.0
f7a3d000-f7a3f000 r-xp 00000000 08:01 6750216                            /lib32/libdl-2.5.so
f7a3f000-f7a41000 rwxp 00001000 08:01 6750216                            /lib32/libdl-2.5.so
f7a41000-f7b01000 r-xp 00000000 08:01 3392179                            /usr/lib32/libasound.so.2.0.0
f7b01000-f7b06000 rwxp 000c0000 08:01 3392179                            /usr/lib32/libasound.so.2.0.0
f7b06000-f7c41000 r-xp 00000000 08:01 6750213                            /lib32/libc-2.5.so
f7c41000-f7c42000 r-xp 0013b000 08:01 6750213                            /lib32/libc-2.5.so
f7c42000-f7c44000 rwxp 0013c000 08:01 6750213                            /lib32/libc-2.5.so
f7c44000-f7c48000 rwxp f7c44000 00:00 0 
f7c48000-f7c53000 r-xp 00000000 08:01 3394285                            /usr/lib32/libgcc_s.so.1
f7c53000-f7c54000 rwxp 0000a000 08:01 3394285                            /usr/lib32/libgcc_s.so.1
f7c54000-f7c79000 r-xp 00000000 08:01 6750217                            /lib32/libm-2.5.so
f7c79000-f7c7b000 rwxp 00024000 08:01 6750217                            /lib32/libm-2.5.so
f7c7b000-f7d5a000 r-xp 00000000 08:01 3394286                            /usr/lib32/libstdc++.so.6.0.8
f7d5a000-f7d5d000 r-xp 000de000 08:01 3394286                            /usr/lib32/libstdc++.so.6.0.8
f7d5d000-f7d5f000 rwxp 000e1000 08:01 3394286                            /usr/lib32/libstdc++.so.6.0.8
f7d5f000-f7d65000 rwxp f7d5f000 00:00 0 
f7d65000-f7ddf000 r-xp 00000000 08:01 3393855                            /usr/lib32/libGL.so.100.14.11
f7ddf000-f7dfa000 rwxp 00079000 08:01 3393855                            /usr/lib32/libGL.so.100.14.11
f7dfa000-f7dfb000 rwxp f7dfa000 00:00 0 
f7dfb000-f7e1d000 r-xp 00000000 08:01 3394308                            /usr/lib32/libpng12.so.0.15.0
f7e1d000-f7e1e000 rwxp 00021000 08:01 3394308                            /usr/lib32/libpng12.so.0.15.0
f7e1e000-f7e31000 r-xp 00000000 08:01 6750227                            /lib32/libpthread-2.5.so
f7e31000-f7e33000 rwxp 00013000 08:01 6750227                            /lib32/libpthread-2.5.so
f7e33000-f7e36000 rwxp f7e33000 00:00 0 
f7e36000-f7e9b000 r-xp 00000000 08:01 3394852                            /usr/lib32/libSDL-1.2.so.0.11.0
f7e9b000-f7e9d000 rwxp 00065000 08:01 3394852                            /usr/lib32/libSDL-1.2.so.0.11.0
f7e9d000-f7ec5000 rwxp f7e9d000 00:00 0 
f7ec5000-f7ed8000 r-xp 00000000 08:01 3394288                            /usr/lib32/libz.so.1.2.3
f7ed8000-f7ed9000 rwxp 00012000 08:01 3394288                            /usr/lib32/libz.so.1.2.3
f7eec000-f7eed000 rwxp f7eec000 00:00 0 
f7eed000-f7eef000 rwxp 00000000 00:0d 3876                               /dev/zero
f7eef000-f7ef1000 rwxp f7eef000 00:00 0 
f7ef1000-f7f0d000 r-xp 00000000 08:01 6750210                            /lib32/ld-2.5.so
f7f0d000-f7f0f000 rwxp 0001b000 08:01 6750210                            /lib32/ld-2.5.so
ffd2f000-ffd33000 rwxp ffd2f000 00:00 0                                  [stack]
ffffe000-fffff000 r-xp ffffe000 00:00 0                                  [vdso]
Aborted
chris@ubuntu:~/Desktop/asdfadsf$ 
```

I am trying to get a specific version, so that I can have network play, but I am having the same problem compiling it as others mentioned in this thread.

```
chris@ubuntu:~/Desktop/asdfadsf$ export CFLAGS+="-m32" export CXXFLAGS+="-m32" ./configure 
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
chris@ubuntu:~/Desktop/asdfadsf$ 
```

The config.log looks like this.

```
This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by configure, which was
generated by GNU Autoconf 2.61.  Invocation command line was

  $ ./configure CFLAGS=-m32 CXXFLAGS=-m32

## --------- ##
## Platform. ##
## --------- ##

hostname = ubuntu
uname -m = x86_64
uname -r = 2.6.20-16-generic
uname -s = Linux
uname -v = #2 SMP Thu Aug 30 23:16:15 UTC 2007

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = x86_64
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
/usr/bin/hostinfo      = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /home/chris/bin
PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:1799: checking build system type
configure:1817: result: x86_64-unknown-linux-gnu
configure:1839: checking host system type
configure:1854: result: x86_64-unknown-linux-gnu
configure:1876: checking target system type
configure:1891: result: x86_64-unknown-linux-gnu
configure:1967: checking for gcc
configure:1983: found /usr/bin/gcc
configure:1994: result: gcc
configure:2232: checking for C compiler version
configure:2239: gcc --version >&5
gcc (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2242: $? = 0
configure:2249: gcc -v >&5
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release x86_64-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
configure:2252: $? = 0
configure:2259: gcc -V >&5
gcc: '-V' option must have argument
configure:2262: $? = 1
configure:2285: checking for C compiler default output file name
configure:2312: gcc -m32 -pipe -I. -Wall -I/usr/local/include -I/usr/include   -L/usr/local/lib -L/usr/lib conftest.c  >&5
/usr/bin/ld: skipping incompatible /usr/lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.a when searching for -lc
/usr/bin/ld: cannot find -lc
collect2: ld returned 1 exit status
configure:2315: $? = 1
configure:2353: result: 
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:2360: error: C compiler cannot create executables
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_build=x86_64-unknown-linux-gnu
ac_cv_env_CCC_set=
ac_cv_env_CCC_value=
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=set
ac_cv_env_CFLAGS_value=-m32
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_CXXFLAGS_set=set
ac_cv_env_CXXFLAGS_value=-m32
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_LIBS_set=
ac_cv_env_LIBS_value=
ac_cv_env_XMKMF_set=
ac_cv_env_XMKMF_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_host=x86_64-unknown-linux-gnu
ac_cv_prog_ac_ct_CC=gcc
ac_cv_target=x86_64-unknown-linux-gnu

## ----------------- ##
## Output variables. ##
## ----------------- ##

CC='gcc'
CFLAGS='-m32 -pipe -I. -Wall -I/usr/local/include -I/usr/include'
CPP=''
CPPFLAGS=''
CXX=''
CXXFLAGS='-m32'
DEFS=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP=''
EXEEXT=''
GL_DRAW=''
GREP=''
INSTALL_DATA=''
INSTALL_PROGRAM=''
INSTALL_SCRIPT=''
ISODATE='2007-09-15'
LDFLAGS=' -L/usr/local/lib -L/usr/lib'
LIBOBJS=''
LIBPNG_CFLAGS=''
LIBPNG_LIBS=''
LIBPNG_VERSION=''
LIBS=''
LTLIBOBJS=''
NASMPATH=''
NFLAGS=''
OBJEXT=''
PACKAGE_BUGREPORT=''
PACKAGE_NAME=''
PACKAGE_STRING=''
PACKAGE_TARNAME=''
PACKAGE_VERSION=''
PATH_SEPARATOR=':'
SDL_CFLAGS=''
SDL_CONFIG=''
SDL_LIBS=''
SHELL='/bin/bash'
VERSION='1.42'
XMKMF=''
ZLIB_CFLAGS=''
ZLIB_LIBS=''
ZLIB_VERSION=''
ZSNESEXE=''
ac_ct_CC='gcc'
ac_ct_CXX=''
bindir='${exec_prefix}/bin'
build='x86_64-unknown-linux-gnu'
build_alias=''
build_cpu='x86_64'
build_os='linux-gnu'
build_vendor='unknown'
datadir='${datarootdir}'
datarootdir='${prefix}/share'
docdir='${datarootdir}/doc/${PACKAGE}'
dvidir='${docdir}'
exec_prefix='NONE'
host='x86_64-unknown-linux-gnu'
host_alias=''
host_cpu='x86_64'
host_os='linux-gnu'
host_vendor='unknown'
htmldir='${docdir}'
includedir='${prefix}/include'
infodir='${datarootdir}/info'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localedir='${datarootdir}/locale'
localstatedir='${prefix}/var'
mandir='${datarootdir}/man'
oldincludedir='/usr/include'
pdfdir='${docdir}'
prefix='NONE'
program_transform_name='s,x,x,'
psdir='${docdir}'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target='x86_64-unknown-linux-gnu'
target_alias=''
target_cpu='x86_64'
target_os='linux-gnu'
target_vendor='unknown'

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define PACKAGE_NAME ""
#define PACKAGE_TARNAME ""
#define PACKAGE_VERSION ""
#define PACKAGE_STRING ""
#define PACKAGE_BUGREPORT ""

configure: exit 77
```

Help!

---

### Post by dfreer on 2007-09-16
Hmmm. Like I said, I haven't tried compiling a 32-bit binary from an 64-bit Host, I just build the 32-bit binary on a 32-bit machine, and then bring it over. 

So in my other thread, I see you wanted this specific version of zsnes: 
[http://nsrt.edgeemu.com/forum/viewtopic.php?t=448](http://nsrt.edgeemu.com/forum/viewtopic.php?t=448)

So I thought I could be helpful and just compile that version for you. Can you try this file, and see whether it works for you on your 64-bit machine?
[http://www.dfreer.org/~dfreer/zsnes/binaries/zsnes_1.42-wip](http://www.dfreer.org/~dfreer/zsnes/binaries/zsnes_1.42-wip)

I compiled it on a 32-bit machine like so:
```
sudo apt-get install nasm build-essential libsdl1.2-dev zlib1g-dev libpng12-dev
./configure --enable-release   ## See --help for useful info, not sure if 1.42-wip has a "release" option
make
```

EDIT:
Can you provide a link to that 32-bit deb you tried, so I can see whether I can replicate your error? In general, --force-architecture isn't a good idea, but in zsnes's case it shouldn't have been an issue IMO.

---

### Post by fakie_flip on 2007-09-18
> **dfreer said:**
> Hmmm. Like I said, I haven't tried compiling a 32-bit binary from an 64-bit Host, I just build the 32-bit binary on a 32-bit machine, and then bring it over. 

So in my other thread, I see you wanted this specific version of zsnes: 
[http://nsrt.edgeemu.com/forum/viewtopic.php?t=448](http://nsrt.edgeemu.com/forum/viewtopic.php?t=448)

So I thought I could be helpful and just compile that version for you. Can you try this file, and see whether it works for you on your 64-bit machine?
[http://www.dfreer.org/~dfreer/zsnes/binaries/zsnes_1.42-wip](http://www.dfreer.org/~dfreer/zsnes/binaries/zsnes_1.42-wip)

I compiled it on a 32-bit machine like so:
```
sudo apt-get install nasm build-essential libsdl1.2-dev zlib1g-dev libpng12-dev
./configure --enable-release   ## See --help for useful info, not sure if 1.42-wip has a "release" option
make
```

EDIT:
Can you provide a link to that 32-bit deb you tried, so I can see whether I can replicate your error? In general, --force-architecture isn't a good idea, but in zsnes's case it shouldn't have been an issue IMO.

Thank you very much. I have been struggling to get zsnes of that version working in Linux for a while. I read online that people were able to compile programs to be 32 bit in 64 bit Linux. I think most users had Fedora. Would you also compile this version for me?

[http://prdownloads.sourceforge.net/zsnes/zsnes142src.tar.gz](http://prdownloads.sourceforge.net/zsnes/zsnes142src.tar.gz)

And run configure with --with-x again please.

---

### Post by dfreer on 2007-09-18
I'm pretty sure you can, I know zsnes has the --host= and --build= options and I think those can be used to set the arch. Also, I think you can pass some flags directly to your compiler as well. I've never done this myself, cuz I think it's simply eaiser to build on my x86 machine instead.

Did the other version not work for you? It seems to work fine for me...

Alright, I'll compile the 1.42 source, and get back to you with a binary.

---

### Post by fakie_flip on 2007-09-18
> **dfreer said:**
> I'm pretty sure you can, I know zsnes has the --host= and --build= options and I think those can be used to set the arch. Also, I think you can pass some flags directly to your compiler as well. I've never done this myself, cuz I think it's simply eaiser to build on my x86 machine instead.

Did the other version not work for you? It seems to work fine for me...

Alright, I'll compile the 1.42 source, and get back to you with a binary.

It does work. Thank you. One of my friends uses the version 1.42. In order for me to use network play with him, I must have the exact same version. He thinks it's better, but I have not tried both long enough to say which is better. I did setup software raid for Ubuntu Server under vmware server like I said I would. It is 32 bit. The problem is networking that guest os with the host os. I've been able to accomplish the networking between the guest and host before when using damn small linux, so I do not understand why it is not working. nmap shows the ssh port of the guest opened. I need to be able to transfer files back and forth inorder to compile Zsnes on 32 bit Ubuntu Server running under vmware. I can try those options when I get back home. Right now I am at the school library. Please post a binary of version 1.42. Thanks. The source is here.

[http://www.zsnes.com/index.php?page=files](http://www.zsnes.com/index.php?page=files)

I have another question for you. Have you ever got Project 64 working under Linux through wine or some other windows compatible layer? I would use Muphen64 except that it does not have network play yet, and It crashes when opening a rom under 64 bit Ubuntu. I think I have it as a 32 bit program with all the 32 bit libs it needs. Since it does not have network play, I'm forced to use xp for Project 64k (the version of pj64 that has network play).

---

### Post by dfreer on 2007-09-18
Ok, I'm currently working on compiling the 1.42 version, although it is currently giving me a bit of trouble. 
BTW, just saw this thread on zsnes forums concerning compiling a 32-bit binary in an 64-bit enviroment:
[http://board.zsnes.com/phpBB2/viewtopic.php?t=10468](http://board.zsnes.com/phpBB2/viewtopic.php?t=10468)
Specifically this:
```
export CFLAGS="-m32"
export CXXFLAGS="-m32"
./configure --enable-release --disable-cpucheck force_arch=athlon64
make
```

As for the N64 emulator, unfortunately the only one I've played with is mupen64, and I think only on the x86 platform. Sorry :(

EDIT: screw it, I can't get the 1.42 version to compile. No need, really, since 1.42 is in the repos. I'm just gonna grab the binary from it :D
1.42
[http://www.dfreer.org/~dfreer/zsnes/binaries/zsnes1.42](http://www.dfreer.org/~dfreer/zsnes/binaries/zsnes1.42)
1.42n
[http://www.dfreer.org/~dfreer/zsnes/binaries/zsnes1.42n](http://www.dfreer.org/~dfreer/zsnes/binaries/zsnes1.42n)

---

### Post by fakie_flip on 2007-09-18
> **dfreer said:**
> Ok, I'm currently working on compiling the 1.42 version, although it is currently giving me a bit of trouble. 
BTW, just saw this thread on zsnes forums concerning compiling a 32-bit binary in an 64-bit enviroment:
[http://board.zsnes.com/phpBB2/viewtopic.php?t=10468](http://board.zsnes.com/phpBB2/viewtopic.php?t=10468)
Specifically this:
```
export CFLAGS="-m32"
export CXXFLAGS="-m32"
./configure --enable-release --disable-cpucheck force_arch=athlon64
make
```

As for the N64 emulator, unfortunately the only one I've played with is mupen64, and I think only on the x86 platform. Sorry :(

EDIT: screw it, I can't get the 1.42 version to compile. No need, really, since 1.42 is in the repos. I'm just gonna grab the binary from it :D
1.42
[http://www.dfreer.org/~dfreer/zsnes/binaries/zsnes1.42](http://www.dfreer.org/~dfreer/zsnes/binaries/zsnes1.42)
1.42n
[http://www.dfreer.org/~dfreer/zsnes/binaries/zsnes1.42n](http://www.dfreer.org/~dfreer/zsnes/binaries/zsnes1.42n)

I'll try those when I get home. I have seen that thread you mentioned before and I even spoke to the guy who made the last post on it in irc. His solution did not work. I think Zsnes both versions will work fine now. They must be in 32 bit because the roms are 32 bit (I think). Do any of the playstation emulators support network play. I think the ps2 emulator must have high system requirements, not sure, but I would like to try.

---

### Post by dfreer on 2007-09-18
Can't quite remember why zsnes was 32-bit only, something to do with it being written in assembly code I do believe. 

pSX does not support network play, I haven't used ePSXe or PCSX for awhile, so I can't speak for them (I do not believe either of them do).

PCSX2 is the only PS2 emulator that shows any promise, and it pretty much requires a dual-core processor to run. I got FFX to work *somewhat* on my 2.0 Dual core with a Nvidia Geforce 7400 awhile ago.

---

### Post by fakie_flip on 2007-09-18
> **dfreer said:**
> Can't quite remember why zsnes was 32-bit only, something to do with it being written in assembly code I do believe. 

pSX does not support network play, I haven't used ePSXe or PCSX for awhile, so I can't speak for them (I do not believe either of them do).

PCSX2 is the only PS2 emulator that shows any promise, and it pretty much requires a dual-core processor to run. I got FFX to work *somewhat* on my 2.0 Dual core with a Nvidia Geforce 7400 awhile ago.

Did you say dual core? :popcorn:

How's this?

```
chris@ubuntu:~$ grep -i "model name\|mhz" /proc/cpuinfo 
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
cpu MHz         : 2200.246
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
cpu MHz         : 2200.246
chris@ubuntu:~$ 
```

Video card?

```
chris@ubuntu:~$ sudo nvidia-installer -i
Password:

Welcome to the NVIDIA Software Installer for Unix/Linux


The currently installed driver is: 'NVIDIA Accelerated Graphics Driver for
Linux-x86_64' (version: 100.14.11).
chris@ubuntu:~$ grep -i geforce /etc/X11/xorg.conf
    BoardName      "GeForce 8800 GTS"
chris@ubuntu:~$ grep -i ram .doom3/base/DoomConfig.cfg 
seta com_videoRam "320"
seta sys_videoRam "0"
chris@ubuntu:~$ 


```

---

### Post by dfreer on 2007-09-20
Yeah, you should be able to run PCSX2. I wish my laptop came with an 8800 *sniff* of course, technically since you can edit the BoardName in xorg.conf with relative ease, you could be lying to me :P Just kidding!

How did those binaries work for you? I'm going to make a debian package to install them if they work ok.

---

### Post by dfreer on 2007-09-22
I just read this in the opengl.txt file contained with the 1.51 linux source files:

> KNOWN ISSUES (AND SOME WORK-AROUNDS)

...

- segfault after having compiled the source -- this might be due to an old
  **zguicfg.dat** file; delete this and see if the problem gets fixed

Just an FYI for those having issues compiling the source themselves, for that matter, why not just backup/delete the entire ~/.zsnes/ directory, just to make sure that it isn't a config file somewhere causing problems.

---

### Post by fakie_flip on 2007-09-23
> **dfreer said:**
> Yeah, you should be able to run PCSX2. I wish my laptop came with an 8800 *sniff* of course, technically since you can edit the BoardName in xorg.conf with relative ease, you could be lying to me :P Just kidding!

How did those binaries work for you? I'm going to make a debian package to install them if they work ok.

They work just fine. My friend is using 32 bit Ubuntu. We tried to play zsnes. It did not work because we had different versions. So, I used scp to get his binary. It is version 1.43. I thought 1.42n was the last version that supported network play. Does the PCSX2 have network play?

---

### Post by fakie_flip on 2007-09-23
I want to get an adapter that will let me use a ps2 controller on the computer. I saw one at walmart for very cheap, but I did not know if it is compatible with Linux. Do you know about those? The ps2 controller would be good for zsnes.

---

### Post by dfreer on 2007-09-23
> **fakie_flip said:**
> They work just fine. My friend is using 32 bit Ubuntu. We tried to play zsnes. It did not work because we had different versions. So, I used scp to get his binary. It is version 1.43. I thought 1.42n was the last version that supported network play. Does the PCSX2 have network play?

...

I want to get an adapter that will let me use a ps2 controller on the computer. I saw one at walmart for very cheap, but I did not know if it is compatible with Linux. Do you know about those? The ps2 controller would be good for zsnes.


I'm pretty sure 1.42n displays 1.43 as it's version # in it's Misc > About, I'm not on my linux machine ATM.

Check out PCSX2's website, they are currently working on netplay (although I think they are referring to the online feature of the original PS2, and not being able to play a multiplayer game across a LAN/internet with a friend).

I happen to really like this controller for playing console games:
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1085740&CatId=141](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1085740&CatId=141)

I've got 1 (got it from a Wal-mart a couple years ago I think), and just ordered 2 more from this site so my friends can play. Works perfectly in pSX and ZSNES, no calibration/drivers required (at least for me ;) ). It has all of the features of a standard Dual-Shock controller except vibration, including the L3/R3 under the joysticks. There's a similar model on Logitech's site that will do rumble, but that will almost certainly only work in Windows. I've never used a PS2 -> USB adapter myself, most of the ones I've seen cost roughly the same as this controller.

---

### Post by fakie_flip on 2007-09-23
What games do you play in zsnes? I'd like to play with you some time. You can contact me by IM.

---

### Post by arcticblue on 2007-10-23
I have that same controller. Works great!  Did you know you can also use it as a cheap PS3 controller?

---

### Post by dfreer on 2007-10-23
Hmm, that's interesting to know... wish I had money to spend on a PS3 (well, actually I'd probably get an XBOX 360).

EDIT: Until I can figure out how to make each version of zsnes use a separate config file, I'm not updating any zsnes-legacy packages.

---

### Post by go_beep_yourself on 2007-11-11
> **dfreer said:**
> I'm pretty sure 1.42n displays 1.43 as it's version # in it's Misc > About, I'm not on my linux machine ATM.

Check out PCSX2's website, they are currently working on netplay (although I think they are referring to the online feature of the original PS2, and not being able to play a multiplayer game across a LAN/internet with a friend).

I happen to really like this controller for playing console games:
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1085740&CatId=141](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1085740&CatId=141)

I've got 1 (got it from a Wal-mart a couple years ago I think), and just ordered 2 more from this site so my friends can play. Works perfectly in pSX and ZSNES, no calibration/drivers required (at least for me ;) ). It has all of the features of a standard Dual-Shock controller except vibration, including the L3/R3 under the joysticks. There's a similar model on Logitech's site that will do rumble, but that will almost certainly only work in Windows. I've never used a PS2 -> USB adapter myself, most of the ones I've seen cost roughly the same as this controller.

After trying the usb adapter for a ps2 controller, and it not working in Linux, I ordered two of the controllers and they are working great with zsnes. I tried them with Open Arena, and they weren't working, so I think I need to use jscalibrate. I'd like to do some gaming when you have some free time. :popcorn:

EDIT; I just used jscalibrator to attempt to get that gamepad working with Open Arena. The right joystick only worked but none of the buttons did or other joystick did. Why is that? It works in zsnes and with other emulators but not other games in Linux. How can this be fixed?

---

### Post by dfreer on 2007-11-12
I've never played Open Arena myself :( But so far, with the various emulators I've used with these controllers (fceu, zsnes, pSX, PCSX, ePSXe, mupen64), I haven't found the need to use jscalibrate (in fact, never installed it so I actually haven't used it).

I'm up for gaming, mostly I play CS:S and some Guild Wars (I have yet to get farther than lvl 14 with any of my chars, just don't play that much ). Other games, I'm willing to play ever once in a while, I'll send you a PM with my MSN IM and xfire name if you're looking for someone to game with ;)

---

### Post by go_beep_yourself on 2007-11-12
Does anyone know how to compile a program to be 32 bit when using a 64 bit linux kernel and without using a 32 bit chroot?

---

### Post by go_beep_yourself on 2007-11-12
> **dfreer said:**
> I've never played Open Arena myself :( But so far, with the various emulators I've used with these controllers (fceu, zsnes, pSX, PCSX, ePSXe, mupen64), I haven't found the need to use jscalibrate (in fact, never installed it so I actually haven't used it).

I'm up for gaming, mostly I play CS:S and some Guild Wars (I have yet to get farther than lvl 14 with any of my chars, just don't play that much ). Other games, I'm willing to play ever once in a while, I'll send you a PM with my MSN IM and xfire name if you're looking for someone to game with ;)

Do you play any FPS games? I already have your msn email lol. I've even gamed with you before. Now that I have the gamepads, it should be much easier to game with emulators. I haven't been able to get Mupen64 to work without crashing in 64 bit Gusty Goose and it doesn't have network support, so I'll be using Project 64 k when I have time to install Windows. I'm thinking these gamepads are going to be much better for games such as Dirt, Need For Speed, and other racing games. The keyboard sucks for those. Do you know of any computer games besides emulators that allow more than one person to play together on the same computer? That would be good sense I ordered two of those gamepads that you suggested.

---

### Post by go_beep_yourself on 2007-11-12
> **dfreer said:**
> I'll send you a PM with my MSN IM and xfire name if you're looking for someone to game with ;)

Have you got the xfire plugin to work in Linux with Pidgin?

---

### Post by dfreer on 2007-11-12
RE: xfire - Yes, I got a debian package for gutsy i386/amd64 from somewhere on the internet, I'll have to dig the link up again. I can put the .debs on the website (not the repository).
I also got xfire working with wine, but the names display all wrong.

Since most PC games use keyboard/mouse, most multiplayer PC games are designed to only have one player per PC. Beyond various console emulators, I don't know of any PC games that allow two players or more.

---

