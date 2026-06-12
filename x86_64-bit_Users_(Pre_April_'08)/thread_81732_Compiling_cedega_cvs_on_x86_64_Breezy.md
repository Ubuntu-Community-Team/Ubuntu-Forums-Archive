---
title: "Compiling cedega cvs on x86_64 Breezy"
date: 2005-10-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by RAOF on 2005-10-25
Ok, following [these]("http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45") instructions as a base, I can **almost** get cedega to compile (if you install linux32 and run linux32 ./configure, it won't fail by not recognising an amd64 processor).  However, I've hit a bit of a snag:  winex will obviously need to be compiled as a 32bit binary.  That's fine, there's the -m32 compiler option to generate 32bit code.  

However, while gcc-4 is perfectly happy to generate 32bit code with the -m32 option (after installing the ia32-libs-dev package), it seems that winex doesn't compile under gcc-4.  It **does** compile under gcc-3.4, but gcc-3.4 won't produce 32bit code!  Aargh.  Running "gcc-3.4 -m32 helloworld.c" results in ld complaining that it can't find "-lgcc_s_32".  I've tried symlinking the 32bit libgcc_s.so to libgcc_s_32.so and running ldconfig, but to no avail.

So, has anyone managed to successfully compile cedega for amd64?  Or, get gcc-3.4 to generate 32bit code?

---

### Post by ntony on 2005-10-31
pump.

Any solution with RAOF's problem?
I got problem with compiling WineCVS.

```
configure:1862: gcc -m32 -V </dev/null >&5
gcc: '-V' must come at the start of the command line
configure:1865: $? = 1
configure:1888: checking for C compiler default output file name
configure:1891: gcc -m32    conftest.c  >&5
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.0.2/../../..$
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.0.2/../../..$
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libc.so when searching for -$
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.a when searching for -lc
/usr/bin/ld: cannot find -lc
collect2: ld returned 1 exit status

```

---

### Post by queenorych on 2005-10-31
compile it in a chroot.  Or just run a precomiled version in a chroot.  See the debian amd64 howto.  It's not that diffiuclt.  Really.

---

### Post by RAOF on 2005-10-31
[QUOTE=ntony]pump.

Any solution with RAOF's problem?
I got problem with compiling WineCVS.

```
configure:1862: gcc -m32 -V </dev/null >&5
gcc: '-V' must come at the start of the command line
configure:1865: $? = 1
configure:1888: checking for C compiler default output file name
configure:1891: gcc -m32    conftest.c  >&5
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.0.2/../../..$
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.0.2/../../..$
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libc.so when searching for -$
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.a when searching for -lc
/usr/bin/ld: cannot find -lc
collect2: ld returned 1 exit status

```[/QUOTE]
I can solve **this** problem, at least.  If you install the ia32-libs-dev package, you'll get a 32bit libc library, and ./configure will work.  Of course, you'll then run into the problem that the wine code is broken under gcc-4, and I'm yet to find a way to build 32bit binaries under gcc-3.x.

However, if you just want wine, you can just download the 32bit binary deb from winehq.  See [this thread]("http://www.ubuntuforums.org/showthread.php?t=82676").  You don't need a chroot.  Chroots are inelegant ;)

---

### Post by ntony on 2005-10-31
I got ia32-libs and ia32-libs-dev already. This problem was occured after I got the 32bit libs. Right! Installing a 32bit OS into a 64bit OS sounds... haha! We should get some experts on CPU instructions, ASM and OS.
I could wait until new Ubuntu version, that supports both 32bit & 64bit applications, to release. But that would take long. Or wait for new release of Wine/Cegeda, that supports 64bit OS. This would be shorter because Cegeda is a commercial application.

I install Cedega for WoW. And I don't think Blizzard would develop Linux version of WoW as you can see people are using different distro and kernels, getting compatibility problem.

I used to have x64_64 Red Hat FC4. I got Wine RPM installed and running in good condition. I suppose Ubuntu can do it too.

---

### Post by RAOF on 2005-10-31
**This** version of ubuntu supports 32bit & 64bit code.  It just doesn't support 32bit code/compiling completely ;).  AFAIK, the open office shipped with breezy is 32bit, and that works.

I wouldn't hold your breath waiting for cedega to implement Win64, either.  It's hardly a top priority - there just aren't a lot of Win64 games.

Oh, you might want to run ldconfig again, too.  I seem to recall fiddling with it at some point, maybe that fixed something somewhere...

---

### Post by Atreju on 2005-12-30
Ok, I see that there's not much solution on how to get cegeda working on breezy 64...

I'll give it a try. Maybe my recent experience with CLFS (cross linux from scratch) could help us there.

I'll be back to give some news

---

### Post by Atreju on 2006-01-02
Hehe !

back for some news about cegeda CVS.

well first thing I noticed is that I noticed : there are packages that do not exist on the repositories that are needed (they need to be 32 bit...):

- xrender
- xcursor
- Xvlib
- DGA extension
- XFree86 VMODE

to compile these cleanly for 32 bit, you need to have the proper toolchain on your system (that is glibc + binutils + gcc) 

So there's nothing impossible here but it will take some time.

I'll keep you posted.

---

### Post by tpoindex on 2006-01-13
I had a similar problem when trying to compile another app as 32bits with gcc-3.4 (mplayer).  It seems that there is a broken link in the gcc-3-4 package:

in /usr/lib/gcc/x86_64-linux-gnu/3.4.5/32:
```

lrwxrwxrwx  1 root root      20 2006-01-13 10:38 [COLOR="Red"]libgcc_s_32.so[/COLOR] -> /lib32/libgcc_s.so.1
lrwxrwxrwx  1 root root      20 2006-01-13 10:38 [COLOR="Red"]libgcc_s.so[/COLOR] -> /lib32/libgcc_s.so.1

```

Turns out the /lib32/libgcc_s.so.1 is missing.
I made an additional link to fix:

```

sudo ln -s /usr/lib32/libgcc_s.so.1 /lib32/libgcc_s.so.1

```

Good luck.

---

