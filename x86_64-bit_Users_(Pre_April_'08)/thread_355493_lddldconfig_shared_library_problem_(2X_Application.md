---
title: "ldd/ldconfig shared library problem (2X Application Server)"
date: 2007-02-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by ktulu1115 on 2007-02-07
I'm having a small problem running the 2x Application Server as outlined in this article [[http://searchopensource.techtarget.com/tip/0,289483,sid39_gci1238129,00.html]](http://searchopensource.techtarget.com/tip/0,289483,sid39_gci1238129,00.html]).

trying to run gives the following results:

$ ./appserverclient 
./appserverclient: error while loading shared libraries: libesd.so.0: cannot open shared object file: No such file or directory

$ ldd appserverclient 
        linux-gate.so.1 =>  (0xffffe000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7e1c000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7e0f000)
        libXpm.so.4 => /usr/lib32/libXpm.so.4 (0xf7dfe000)
        libesd.so.0 => not found
        libXcursor.so.1 => /usr/lib32/libXcursor.so.1 (0xf7df5000)
        libexpat.so.1 => /usr/lib32/libexpat.so.1 (0xf7dd7000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7dc4000)
        libc.so.6 => /lib32/libc.so.6 (0xf7c90000)
        libm.so.6 => /lib32/libm.so.6 (0xf7c69000)
        /lib/ld-linux.so.2 (0xf7ef9000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf7c66000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf7c61000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7c5d000)
        libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf7c55000)
        libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0xf7c50000)


however:

$ ldconfig -p | grep esd
        libesd.so.0 (libc6,x86-64) => /usr/lib/libesd.so.0
        libesd.so (libc6,x86-64) => /usr/lib/libesd.so

I'm assuming the problem is the binary can't find any 32-bit versions of the library.  What workarounds are possible in this situation?  I believe a 32-bit chroot could probably solve it, but are there any others?

---

### Post by kuja on 2007-02-07
You're right, it can't find a 32-bit version of the library.

First, find out what package libesd.so belongs too
```

dpkg -S libesd.so

```

Then, download the 32-bit version of the package it tells you it's in. Next:
```
dpkg -x *386.deb temporary
sudo cp temporary/usr/lib/libesd* /usr/lib32

```

This should more or less rectify your problems. Not sure how copy and pastable that bit was, but I can always assume.

---

### Post by ktulu1115 on 2007-02-07
Thanks for the suggestions!  The process worked.  I'm curious if this will work for other applications I've had similar issues with.

I'm also wondering why there's no built-in functionality for this on the AMD64 arch.  It almost seems like it'd be a more common problem then it is.

---

