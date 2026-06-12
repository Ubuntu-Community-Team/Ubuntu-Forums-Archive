---
title: "Compiling in x86_64. . ."
date: 2006-05-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Diskobolos on 2006-05-01
Hey all, I'm pretty much a total linux newbie; installed about two weeks ago. Me and the rest of my family have personally given MS a small fortune over the years (DOS 5.0, DOS 6.0, Win 3.1, Win 95, Win 98, Win ME, Win 2K. . . Win XP!). Doing my best to learn Linux, though :D

So, here's the problem. I'm trying to install WINE in order to (hopefully!) get some of my Windows games humming along. WINE has no AMD64 binaries, but the site says if you compile from source it should work.
I downloaded the source package, installed the relevant libraries using apt-get build-dep, and ran ./configure.

Configure yields the following:

[B]root@Diskobolos:/usr/src/wine-build# /usr/src/win*/configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc -m32
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
root@Diskobolos:/usr/src/wine-build#[/B]

So I nano config.log; here's the relevant bit.

[B]configure:1888: checking for C compiler default output file name
configure:1891: gcc -m32    conftest.c  >&5
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.0.2/../../../libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.0.2/../../../libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.a when searching for -lc
/usr/bin/ld: cannot find -lc
collect2: ld returned 1 exit status
configure:1894: $? = 1
configure: failed program was:
| /* confdefs.h.  */
|
| #define PACKAGE_NAME "Wine"
| #define PACKAGE_TARNAME "wine"
| #define PACKAGE_VERSION "0.9.12"
| #define PACKAGE_STRING "Wine 0.9.12"
| #define PACKAGE_BUGREPORT "wine-devel@winehq.org"
| /* end confdefs.h.  */
|
| int
| main ()
| {
|
|   ;
|   return 0;
| }
configure:1933: error: C compiler cannot create executables
See `config.log' for more details.
[/B]

As near as I can tell, there's some kind of imcompatibility with my current glibc installation (libc6, w/ dev).
I tried reinstalling all the gcc packages, binutils etc. with no success.
Tried googling, but there weren't any solutions available (and only a few reasonably similar situations).

Anyone out there who can help? :)
Thanks!

---

### Post by Yagisan on 2006-05-02
wine is a special case. if you do get it to build 64bit, it can only run 64bit windows apps.

In short your problem is you are trying to build a 32bit wine (-m32) and link it with 64bit support libaries. That does not work.

Please save yourself some trouble and make a 32bit chroot, and install wine from the .deb in there.

---

### Post by Diskobolos on 2006-05-02
Ah, so that's the problem. . . thanks a bunch for saving me the trouble ^^

I guess I'll start working on setting up a 32-bit chroot then. . .

---

### Post by Yagisan on 2006-05-03
Glad I could help. I spent 3 days trying to build it, then found out 64bit wine can't run 32bit windows apps. ](*,) Only took 10 minutes to setup a chroot and to download 32bit wine.

---

