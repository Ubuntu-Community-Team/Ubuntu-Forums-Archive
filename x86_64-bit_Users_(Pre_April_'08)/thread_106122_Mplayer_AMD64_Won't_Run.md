---
title: "Mplayer AMD64 Won't Run"
date: 2005-12-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by mrgnash on 2005-12-19
I installed this via Synaptic, but when I try and execute it returns:

```
mplayer: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

What's the deal? :(

---

### Post by azcrumpty on 2005-12-21
I have kubuntu 64 installed and I get the same error.  I checked the library with the file command and I discovered it is a 32 bit library.  I don't know who or what put it there, but I believe it was the ATI propprietary install program, in my particular case.


[QUOTE=mrgnash]I installed this via Synaptic, but when I try and execute it returns:

```
mplayer: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

What's the deal? :([/QUOTE]

---

### Post by stats on 2005-12-23
Im running kubuntu 64 breezy
i was initially able to install mplayer from source. but it lacked xv support.
so i installed the ati propreitary drivers(i have a radeon 9600 pro). but when i try to compile mplayer again it gives the errors:

/usr/bin/ld: skipping incompatible /usr/lib/libGL.so when searching for -lGL
/usr/lib/libGL.a(glxext.o): In function `__glXInitialize':
: undefined reference to `drmUnmap'
/usr/lib/libGL.a(glxext.o): In function `__glXInitialize':
: undefined reference to `drmUnmap'
/usr/lib/libGL.a(glxext.o): In function `__glXInitialize':
: undefined reference to `drmClose'
/usr/lib/libGL.a(glxext.o): In function `__glXInitialize':
: undefined reference to `drmOpen'
/usr/lib/libGL.a(glxext.o): In function `__glXInitialize':
: undefined reference to `drmGetMagic'
/usr/lib/libGL.a(glxext.o): In function `__glXInitialize':
: undefined reference to `drmGetVersion'
/usr/lib/libGL.a(glxext.o): In function `__glXInitialize':
: undefined reference to `drmFreeVersion'
/usr/lib/libGL.a(glxext.o): In function `__glXInitialize':
: undefined reference to `drmMap'
/usr/lib/libGL.a(glxext.o): In function `__glXInitialize':
: undefined reference to `drmMap'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

any solution?

thanks in advance

---

