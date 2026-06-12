---
title: "cross-compiling in 32 bit: any ideas?"
date: 2005-01-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tobu on 2005-01-03
I'm trying to cross-compile some apps in 32-bit mode, and this fails quite soon. My ultimate goal is to get winex - this is reported to work on other distros.
I try with any tarball:
export CC='ccache gcc-3.4 -m32'
export CXX='ccache g++-3.4 -m32'
./configure

...
checking for gcc... ccache gcc-3.4 -m32
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
...

config.log:
...configure:2545: checking for C compiler default output file name
configure:2548: gcc-3.4 -m32    conftest.c  >&5
/usr/bin/ld: cannot find -lgcc_s_32
collect2: ld returned 1 exit status
configure:2551: $? = 1
configure: failed program was:
| /* confdefs.h.  */
|
| #define PACKAGE_NAME "Wormux"
| #define PACKAGE_TARNAME "wormux"
| #define PACKAGE_VERSION "0.5.0"
| #define PACKAGE_STRING "Wormux 0.5.0"
| #define PACKAGE_BUGREPORT "wormux-dev@gna.org"
| #define PACKAGE "wormux"
| #define VERSION "0.5.0"
| /* end confdefs.h.  */
|
| int
| main ()
| {
|
|   ;
|   return 0;
| }
configure:2590: error: C compiler cannot create executables
See `config.log' for more details.
...

If I use the default gcc-3.3 instead (though 3.4 is recommended for 64-bit), I get a slightly different output:

...
configure:2548: ccache gcc-3.3 -m32    conftest.c  >&5
/usr/bin/ld: skipping incompatible /usr/lib/gcc-lib/x86_64-linux/3.3.5/./libgcc.a when searching for -lgcc
/usr/bin/ld: skipping incompatible /usr/lib/gcc-lib/x86_64-linux/3.3.5/libgcc.a when searching for -lgcc
/usr/bin/ld: cannot find -lgcc
collect2: ld returned 1 exit status
...

I've apt-file searched for libgcc{_s_32,}.* which says:
gcc-3.3: usr/lib/gcc-lib/x86_64-linux/3.3.4/32/libgcc.a
gcc-3.3: usr/lib/gcc-lib/x86_64-linux/3.3.4/libgcc.a
gcc-3.3: usr/lib/gcc-lib/x86_64-linux/3.3.4/libgcc_s_32.so
gcc-3.4: usr/lib/gcc/x86_64-linux/3.4.2/32/libgcc.a
gcc-3.4: usr/lib/gcc/x86_64-linux/3.4.2/libgcc.a
gcc-3.4: usr/lib/gcc/x86_64-linux/3.4.2/libgcc_s_32.so
gcc-avr: usr/lib/gcc/avr/3.4.0/avr3/libgcc.a
gcc-avr: usr/lib/gcc/avr/3.4.0/avr4/libgcc.a
gcc-avr: usr/lib/gcc/avr/3.4.0/avr5/libgcc.a
gcc-avr: usr/lib/gcc/avr/3.4.0/libgcc.a
mingw32: usr/lib/gcc-lib/i586-mingw32msvc/3.3.1/libgcc.a
And slocate found me:
/usr/lib/gcc/x86_64-linux/3.4.4/32/libgcc.a
Which contains 32 bit objects all right, but is not libgcc_s_32.

---

### Post by Tobu on 2005-01-03
Since I wouldn't be deterred so easily, I tried compiling gcc myself.
This is quite bad, because when building itself gcc runs into a similar problem:
make LANG='' profiledbootstrap
./xgcc -B./ -B/usr/local/x86_64-unknown-linux-gnu/bin/ -isystem /usr/local/x86_64-unknown-linux-gnu/include -isystem /usr/local/x86_64-unknown-linux-gnu/sys-include -L/home/g2p/Construction/gcc-3.4.3/gcc/../ld -O2  -DIN_GCC    -W -Wall -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -Wold-style-definition  -isystem ./include  -fPIC -g -DHAVE_GTHR_DEFAULT -DIN_LIBGCC2 -D__GCC_FLOAT_NOT_NEEDED  -shared -nodefaultlibs -Wl,--soname=libgcc_s.so.1 -Wl,--version-script=libgcc/32/libgcc.map -o 32/libgcc_s.so.1.tmp  -m32  libgcc/32/_muldi3.o libgcc/32/_negdi2.o libgcc/32/_lshrdi3.o libgcc/32/_ashldi3.o libgcc/32/_ashrdi3.o libgcc/32/_cmpdi2.o libgcc/32/_ucmpdi2.o libgcc/32/_floatdidf.o libgcc/32/_floatdisf.o libgcc/32/_fixunsdfsi.o libgcc/32/_fixunssfsi.o libgcc/32/_fixunsdfdi.o libgcc/32/_fixdfdi.o libgcc/32/_fixunssfdi.o libgcc/32/_fixsfdi.o libgcc/32/_fixxfdi.o libgcc/32/_fixunsxfdi.o libgcc/32/_floatdixf.o libgcc/32/_fixunsxfsi.o libgcc/32/_fixtfdi.o libgcc/32/_fixunstfdi.o libgcc/32/_floatditf.o libgcc/32/_clear_cache.o libgcc/32/_enable_execute_stack.o libgcc/32/_trampoline.o libgcc/32/__main.o libgcc/32/_absvsi2.o libgcc/32/_absvdi2.o libgcc/32/_addvsi3.o libgcc/32/_addvdi3.o libgcc/32/_subvsi3.o libgcc/32/_subvdi3.o libgcc/32/_mulvsi3.o libgcc/32/_mulvdi3.o libgcc/32/_negvsi2.o libgcc/32/_negvdi2.o libgcc/32/_ctors.o libgcc/32/_ffssi2.o libgcc/32/_ffsdi2.o libgcc/32/_clz.o libgcc/32/_clzsi2.o libgcc/32/_clzdi2.o libgcc/32/_ctzsi2.o libgcc/32/_ctzdi2.o libgcc/32/_popcount_tab.o libgcc/32/_popcountsi2.o libgcc/32/_popcountdi2.o libgcc/32/_paritysi2.o libgcc/32/_paritydi2.o libgcc/32/_divdi3.o libgcc/32/_moddi3.o libgcc/32/_udivdi3.o libgcc/32/_umoddi3.o libgcc/32/_udiv_w_sdiv.o libgcc/32/_udivmoddi4.o  libgcc/32/unwind-dw2.o libgcc/32/unwind-dw2-fde-glibc.o libgcc/32/unwind-sjlj.o libgcc/32/gthr-gnat.o libgcc/32/unwind-c.o -lc && rm -f libgcc_s_32.so && if [ -f 32/libgcc_s.so.1 ]; then mv -f 32/libgcc_s.so.1 32/libgcc_s.so.1.`basename `; else true; fi && mv 32/libgcc_s.so.1.tmp 32/libgcc_s.so.1 && ln -s 32/libgcc_s.so.1 libgcc_s_32.so
/usr/bin/ld: skipping incompatible /usr/lib/../lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/../lib/libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.a when searching for -lc
/usr/bin/ld: cannot find -lc
collect2: ld returned 1 exit status
make[3]: *** [32/libgcc_s_32.so] Error 1
make[3]: Leaving directory `/home/g2p/Construction/gcc-3.4.3/gcc'

Apparently I need a 32-bit glibc.

---

### Post by Dylanby on 2005-01-03
If you just want to install Cedega (WineX) then you could look into setting up a 32bit chroot.

I did it using this howto:
[http://digital-conquest.ath.cx/wiki/index.php/Ubuntu](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu)

Once it's set up you can install other i386/x86 packages too like Mplayer & Firefox w/Flash.

---

### Post by Tobu on 2005-01-04
That's right, but I'd rather go for the other solution: it should take less disk space & integrate better with the rest of the system without the need for bind mounts and other tricks.
Hopefully Ubuntu will upgrade its gcc so that every app can me compiled in 32-bit mode if necessary, just like in plain debian: [http://lists.debian.org/debian-amd64/2004/08/msg00084.html](http://lists.debian.org/debian-amd64/2004/08/msg00084.html) .
For now I've got this gcc-3.4 build, and I'm able to build wine-20041201 up to an error in ntdll:
make[2]: Entering directory `/home/g2p/Construction/wine-20041201/dlls/ntdll'
ccache gcc-3.4 -m32 -c -I. -I. -I../../include -I../../include  -D__WINESRC__  -D_NTSYSTEM_ -D_REENTRANT -fPIC -Wall -pipe -mpreferred-stack-boundary=2 -fno-strict-aliasing -gstabs+ -Wpointer-arith  -g -O2 -o signal_i386.o signal_i386.c
signal_i386.c: In function `wine_sigaction':
signal_i386.c:114: error: `SYS_sigaction' undeclared (first use in this function)
signal_i386.c:114: error: (Each undeclared identifier is reported only once
signal_i386.c:114: error: for each function it appears in.)
make[2]: *** [signal_i386.o] Error 1

The problem has already occured in the past, according to gmane and google, so I have good hope.

---

### Post by brad.arth on 2005-05-14
I am having the same issue, if anyone knows a fix, or if one was released and I missed it, please post or email me at [email]brad.arth@gmail.com[/email]

thanks!

---

### Post by Tobu on 2005-05-15
[QUOTE=brad.arth]I am having the same issue, if anyone knows a fix, or if one was released and I missed it, please post or email me at [email]brad.arth@gmail.com[/email]

thanks![/QUOTE]
 I haven't had a look for a while. I know that, starting from 3.4 (4.0 too), ubuntu (hoary)'s gcc enables multilib, so you don't have to install a debian one as I did. But I think the errors in compiling wine remained. Even compiling from a chroot gave broken binaries, which is weird.
The wine package installed in a chroot works, however, and installing a chroot is quite easy: see [http://www.ubuntulinux.org/wiki/DebootstrapChroot](http://www.ubuntulinux.org/wiki/DebootstrapChroot)

---

### Post by drach on 2005-06-11
[QUOTE=Tobu]I haven't had a look for a while. I know that, starting from 3.4 (4.0 too), ubuntu (hoary)'s gcc enables multilib, so you don't have to install a debian one as I did. But I think the errors in compiling wine remained. Even compiling from a chroot gave broken binaries, which is weird.
The wine package installed in a chroot works, however, and installing a chroot is quite easy: see [http://www.ubuntulinux.org/wiki/DebootstrapChroot](http://www.ubuntulinux.org/wiki/DebootstrapChroot)[/QUOTE]
 So were you able to get this working?  I can't even compile a simple hello program with the -m32 flag.

---

### Post by Tobu on 2005-06-11
-m32 works if gcc was built with multilib. If gcc -v says '--enable-multilib', or doesn't mention multilib, it should work. With tarballs, you can do CC='gcc -m32' ./configure , it works provided the libraries are there in 32 bit too. But building in a chroot is really failsafe, and then you can do a make install out of the chroot if there are no dependencies.

---

### Post by drach on 2005-06-11
> -m32 works if gcc was built with multilib. If gcc -v says '--enable-multilib', or 
> doesn't mention multilib, it should work.

It says "--disable-multilib", so I guess I am out of luck.  This is the standard gcc
that comes with ubuntu -- gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2).  I wonder
why they would build one without multilib set.

> With tarballs, you can do CC='gcc -m32' ./configure , it works provided the
>  libraries are there in 32 bit too.

And provided the compiler is provisioned for multilib, I presume.

> But building in a chroot is really failsafe, and then you can do a make install out of
> the chroot if there are no dependencies.

I'll look into that.  It seems strange the compiler will do the right thing, when it's not provisioned with the correct libraries.

---

### Post by drach on 2005-06-11
You don't happen to have a pointer to the 32 bit chroot instructions do you?  I'm not finding them.

---

### Post by drach on 2005-06-11
I found it at [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575).

Phew!  Seems like a lot of work just to get the -m32 flag to work on gcc.  It might be easier for me to just compile my own gcc.

Is the ubuntu gcc maintainer out there somewhere?  Is there some obvious reason why compiling gcc with the multilib flags is not done?

---

### Post by drach on 2005-06-12
It turns out that the gcc-4.0 compiler from the universe repository can get past the problem I was having, since it appears to have a 32 bit mode. It seems to have been built without disabling multilib.

However, there doesn't appear to be a 32 bit version of libc to link with.  Any pointers to finding one of those is appreciated.

---

### Post by drach on 2005-06-12
Finally successful after installing ia32-libs and ia32-libs-dev.  I can now compile a simple hello program for 386 architecture with just the -m32 flag.  No need to
build in a chroot environment.

---

### Post by Phkillah on 2008-05-17
> **drach said:**
> Finally successful after installing ia32-libs and ia32-libs-dev.  I can now compile a simple hello program for 386 architecture with just the -m32 flag.  No need to
build in a chroot environment.
There is no ia32-libs-dev :( What should i do ?

---

### Post by Tobu on 2008-05-17
> **Phkillah said:**
> There is no ia32-libs-dev :( What should i do ?

ia32-libs has everything you need.

---

### Post by Phkillah on 2008-05-17
i "emerged" gcc-multilib.... And then, with success, my .c became a binary ;)

Thanks anyway :)

---

