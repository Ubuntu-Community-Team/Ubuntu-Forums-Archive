---
title: "Installing/building gcc 4.2 on a 64 bit machine"
date: 2006-09-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by maubp on 2006-09-03
I want to try gcc 4.2, ideally on my Ubuntu 64 bit machine.

Looking over at [http://gcc.gnu.org/](http://gcc.gnu.org/) they are still in active development of gcc 4.2, currently at [stage 3](http://gcc.gnu.org/develop.html#stage3) which looks like bug fixing only in preparation for the release of gcc 4.2.0

Based on [previous releases](http://gcc.gnu.org/develop.html#timeline), I would guess the official release is a month away - plus a further delay before its eventually available via and apt-get on ubuntu.

So is the only option (for now) to download a snapshot, and build it myself?

Has anyone done this and got it to work?

**Any advice on how to do this without disturbing my existing apt-get installed gcc-4.0 or gcc-3.4 installations?**

Can I use the debian experimental package [here](http://packages.qa.debian.org/g/gcc-4.2.html)

(link to [old thread](http://www.ubuntuforums.org/showthread.php?t=184932) on the desktop forum)

---

### Post by maubp on 2006-09-03
I've already got a load of build stuff installed, you will probably need at least the following:

sudo apt-get install build-essential flex bison expect

And to get makeinfo, do:

sudo apt-get install texinfo

Then I did the following:

md gcc-4.2
cd gcc-4.2
wget [ftp://ftp.mirrorservice.org/sites/sources.redhat.com/pub/gcc/snapshots/4.2-20060902/gcc-core-4.2-20060902.tar.bz2](ftp://ftp.mirrorservice.org/sites/sources.redhat.com/pub/gcc/snapshots/4.2-20060902/gcc-core-4.2-20060902.tar.bz2)
wget [ftp://ftp.mirrorservice.org/sites/sources.redhat.com/pub/gcc/snapshots/4.2-20060902/gcc-g++-4.2-20060902.tar.bz2](ftp://ftp.mirrorservice.org/sites/sources.redhat.com/pub/gcc/snapshots/4.2-20060902/gcc-g++-4.2-20060902.tar.bz2)
wget [ftp://ftp.mirrorservice.org/sites/sources.redhat.com/pub/gcc/snapshots/4.2-20060902/gcc-testsuite-4.2-20060902.tar.bz2](ftp://ftp.mirrorservice.org/sites/sources.redhat.com/pub/gcc/snapshots/4.2-20060902/gcc-testsuite-4.2-20060902.tar.bz2)
bunzip2 gcc-core-4.2-20060902.tar.bz2
bunzip2 gcc-g++-4.2-20060902.tar.bz2
bunzip2 gcc-testsuite-4.2-20060902.tar.bz2
tar -xf gcc-core-4.2-20060902.tar
tar -xf gcc-g++-4.2-20060902.tar
tar -xf gcc-testsuite-4.2-20060902.tar
cd gcc-4.2-20060902
./configure
make

I'm trying to do this on a dual core 64bit system, so its a little faster to do this:

make -j 2

Either way, it fails like so:

...
/home/maubp/downloads/gcc-4.2/gcc-4.2-20060902/host-x86_64-unknown-linux-gnu/gcc/xgcc -B/home/maubp/downloads/gcc-4.2/gcc-4.2-20060902/host-x86_64-unknown-linux-gnu/gcc/ -B/usr/local/x86_64-unknown-linux-gnu/bin/ -B/usr/local/x86_64-unknown-linux-gnu/lib/ -isystem /usr/local/x86_64-unknown-linux-gnu/include -isystem /usr/local/x86_64-unknown-linux-gnu/sys-include -O2  -O2 -g -O2  -DIN_GCC    -W -Wall -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -Wold-style-definition  -isystem ./include  -fPIC -g -DHAVE_GTHR_DEFAULT -DIN_LIBGCC2 -D__GCC_FLOAT_NOT_NEEDED  -shared -nodefaultlibs -Wl,--soname=libgcc_s.so.1 -Wl,--version-script=libgcc/32/libgcc.map -o 32/libgcc_s.so.1.tmp  -m32 libgcc/32/_muldi3_s.o libgcc/32/_negdi2_s.o libgcc/32/_lshrdi3_s.o libgcc/32/_ashldi3_s.o libgcc/32/_ashrdi3_s.o libgcc/32/_cmpdi2_s.o libgcc/32/_ucmpdi2_s.o libgcc/32/_clear_cache_s.o libgcc/32/_enable_execute_stack_s.o libgcc/32/_trampoline_s.o libgcc/32/__main_s.o libgcc/32/_absvsi2_s.o libgcc/32/_absvdi2_s.o libgcc/32/_addvsi3_s.o libgcc/32/_addvdi3_s.o libgcc/32/_subvsi3_s.o libgcc/32/_subvdi3_s.o libgcc/32/_mulvsi3_s.o libgcc/32/_mulvdi3_s.o libgcc/32/_negvsi2_s.o libgcc/32/_negvdi2_s.o libgcc/32/_ctors_s.o libgcc/32/_ffssi2_s.o libgcc/32/_ffsdi2_s.o libgcc/32/_clz_s.o libgcc/32/_clzsi2_s.o libgcc/32/_clzdi2_s.o libgcc/32/_ctzsi2_s.o libgcc/32/_ctzdi2_s.o libgcc/32/_popcount_tab_s.o libgcc/32/_popcountsi2_s.o libgcc/32/_popcountdi2_s.o libgcc/32/_paritysi2_s.o libgcc/32/_paritydi2_s.o libgcc/32/_powisf2_s.o libgcc/32/_powidf2_s.o libgcc/32/_powixf2_s.o libgcc/32/_powitf2_s.o libgcc/32/_mulsc3_s.o libgcc/32/_muldc3_s.o libgcc/32/_mulxc3_s.o libgcc/32/_multc3_s.o libgcc/32/_divsc3_s.o libgcc/32/_divdc3_s.o libgcc/32/_divxc3_s.o libgcc/32/_divtc3_s.o libgcc/32/_fixunssfsi_s.o libgcc/32/_fixunsdfsi_s.o libgcc/32/_fixunsxfsi_s.o libgcc/32/_fixsfdi_s.o libgcc/32/_fixunssfdi_s.o libgcc/32/_floatdisf_s.o libgcc/32/_floatundisf_s.o libgcc/32/_fixdfdi_s.o libgcc/32/_fixunsdfdi_s.o libgcc/32/_floatdidf_s.o libgcc/32/_floatundidf_s.o libgcc/32/_fixxfdi_s.o libgcc/32/_fixunsxfdi_s.o libgcc/32/_floatdixf_s.o libgcc/32/_floatundixf_s.o libgcc/32/_fixtfdi_s.o libgcc/32/_fixunstfdi_s.o libgcc/32/_floatditf_s.o libgcc/32/_floatunditf_s.o libgcc/32/_divdi3_s.o libgcc/32/_moddi3_s.o libgcc/32/_udivdi3_s.o libgcc/32/_umoddi3_s.o libgcc/32/_udiv_w_sdiv_s.o libgcc/32/_udivmoddi4_s.o libgcc/32/unwind-dw2_s.o libgcc/32/unwind-dw2-fde-glibc_s.o libgcc/32/unwind-sjlj_s.o libgcc/32/gthr-gnat_s.o libgcc/32/unwind-c_s.o -lc && rm -f 32/libgcc_s.so && if [ -f 32/libgcc_s.so.1 ]; then mv -f 32/libgcc_s.so.1 32/libgcc_s.so.1.backup; else true; fi && mv 32/libgcc_s.so.1.tmp 32/libgcc_s.so.1 && ln -s libgcc_s.so.1 32/libgcc_s.so
/usr/bin/ld: skipping incompatible /usr/lib/../lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/../lib/libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.a when searching for -lc
/usr/bin/ld: cannot find -lc
collect2: ld returned 1 exit status

I've got libc6, libc6-dev, libc6-i386, libc6-dev-i386 all installed - version 2.3.6-0unbuntu20

I'm guessing this is some 32/64 bit issue?  Or do I have so pass some additional settings to configure/make?

---

### Post by maubp on 2006-09-03
Some progress,
(a) some googling suggests it better to do the build in a separate directory to the source
(b) passing --disable-multilib to configure seems to help.

---

### Post by maubp on 2006-09-03
> **maubp said:**
> Can I use the debian experimental package [here](http://packages.qa.debian.org/g/gcc-4.2.html)

(link to [old thread](http://www.ubuntuforums.org/showthread.php?t=184932) on the desktop forum)

Seem to do something...

sudo dpkg -i gcc-4.2-base_4.2-20060709-1_amd64.deb cpp-4.2_4.2-20060709-1_amd64.deb

On the bright side, g++ now claims to be 4.2.0

On the downside, I can't seem to run anything now:

apt-get: /lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

Curses.

---

### Post by maubp on 2006-09-03
> **maubp said:**
> Seem to do something...

sudo dpkg -i gcc-4.2-base_4.2-20060709-1_amd64.deb cpp-4.2_4.2-20060709-1_amd64.deb

On the bright side, g++ now claims to be 4.2.0

On the downside, I can't seem to run anything now.  For example, it looks like any C++ prog "xxx" will complain:

xxx: /lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

Curses.

---

### Post by maubp on 2006-09-04
One re-install later, and I'm back.  I would rather have gone to bed a midnight, but I guess I learned to meddle with important shared libraries at my peril.

On the bright side, having the home directory on a separate partition was a really really good move.

So, back to square one.

If I upgraded from Dapper to Edgy, I would get gcc 4.1 but I really want 4.2 in order to have a go with their OpenMP implementation, GOMP.

Anyone got any suggestions?

---

### Post by maubp on 2006-09-04
(Sorry for double post - forum is being slow on my connection)

---

### Post by chevrier on 2006-09-11
Here is how I did it on my Dell XPS M1710, CoreDuo 2.13 GHz, Linux chevrier-laptop 2.6.15-26-686 #1 SMP PREEMPT Thu Aug 3 03:13:28 UTC 2006 i686 GNU/Linux

COMPILING GCC:
1. To download the latest source (it takes some while, the first time around):
svn [update] -q co svn://gcc.gnu.org/svn/gcc/trunk gcc
2. Configure (i read the manual + copied the ubuntu-4.0 config!!):
../gcc/configure -v --prefix=/usr --enable-shared --libexecdir=/usr/lib --enable-threads=posix --program-suffix=-4.2 --enable-__cxa_atexit --enable-java-awt=gtk-default --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre --enable-mpfr
3. make
make -j
4. check
make -k check
5. install
last time I did make install.  This time, i will do checkinstall.

I do not know if I did it right, but it seemed to work...  and the performance seems better than gcc-4.0 (i am an ATLAS BLAS user).

rgds,

thomas

---

### Post by chevrier on 2006-09-11
btw - i can always use any of my old gcc's at any time, by just changing the link in /usr/bin, so that it points to the gcc i want to use (useful for instance, when i want to compile ndiswrapper who will not let me compile with a gcc different than the one used to compile the kernel).

PS: if anyone knows how to help with the irq#177 disabling by ndiswrapper, i would very muchc appreciate!  just do a google to find more info.

thanks and rgds,

thomas

---

### Post by jespdj on 2006-09-12
> **maubp said:**
> **Any advice on how to do this without disturbing my existing apt-get installed gcc-4.0 or gcc-3.4 installations?**
Did you see the [GCC installation documentation](http://gcc.gnu.org/install/), especially the [configuration page](http://gcc.gnu.org/install/configure.html)?

It explains in detail how to configure and build GCC, and what versions of what tools you need to build it. During the configuration step you can specify where (in which directory) you want the new GCC to be built and installed. Just install it somewhere so that it doesn't overwrite your current GCC.

---

