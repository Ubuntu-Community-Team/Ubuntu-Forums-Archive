---
title: "Cannont find lxext error"
date: 2008-10-05
forum: Wine
---

### Post by crazyguy510 on 2008-10-05
I'm compiling wine from the source so I could patch it for Call of duty 4
but I get this error:
/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc failed
make[2]: *** [winex11.drv.so] Error 2
make[2]: Leaving directory `/home/jon/wine/wine-0.9.56/dlls/winex11.drv'
make[1]: *** [winex11.drv] Error 2
make[1]: Leaving directory `/home/jon/wine/wine-0.9.56/dlls'
make: *** [dlls] Error 2
any reason why??

---

### Post by ghantoos on 2008-10-05
It seems like it compiles when  when removing: #include <X11/IntrinsicP.h> from x11drv/winpos.c 

Where's a link:
[http://bugs.winehq.org/show_bug.cgi?id=3228](http://bugs.winehq.org/show_bug.cgi?id=3228)

Hope this helps,

Cheers,

---

### Post by crazyguy510 on 2008-10-05
I've seen people with similar problems and most of them tried to install with 64-bit version so I guess I'll try that out and see if it works. Other sugestions?

---

