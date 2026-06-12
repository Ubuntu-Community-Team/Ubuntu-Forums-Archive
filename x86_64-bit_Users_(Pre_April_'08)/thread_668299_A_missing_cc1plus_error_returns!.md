---
title: "A missing cc1plus error returns!"
date: 2008-01-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by NFITC1 on 2008-01-15
**EDIT:** I figured out that my /usr/lib/gcc/x86_64-linux-gnu/4.1.3 dir (which is really 4.1.2) didn't have a link to the cc1plus dir in 4.1. I added that and it no longer says it can't find cc1plus. I'm still having problems, however.
Runnin' Gutsy trying to install ZSNES from source. Updated to the ATI 8.443.1 drivers and now it won't work.
I set LDFLAGS to "-L/usr/lib32" and CFLAGS to "-m32" and then the log states that it can't find a compatible -lgcc. If I try to compile without those flags it says it can't find cc1plus. I've installed and reinstalled gcc and g++ but didn't help. Versions:

gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
g++ (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

Relevant error log portion:
```
configure:2372: checking for C compiler default output file name
configure:2399: gcc -m32 -pipe -I. -I/usr/local/include -I/usr/include  -L/usr/lib32 -L/usr/local/lib -L/usr/lib conftest.c  >&5
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.1.3/libgcc.a when searching for -lgcc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.1.3/libgcc.a when searching for -lgcc
/usr/bin/ld: cannot find -lgcc
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
```

What can I do?

---

### Post by NFITC1 on 2008-01-15
I also just installed the gcc and g++ 4.2, but it's still trying to use gcc and g++ 4.1.3. I forgot how to change this. How do I do that?

EDIT: -V 4.2 didn't help. Just gave me more errors so forget that.

---

### Post by skibrianski on 2008-01-17
> **NFITC1 said:**
> I also just installed the gcc and g++ 4.2, but it's still trying to use gcc and g++ 4.1.3. I forgot how to change this. How do I do that?

EDIT: -V 4.2 didn't help. Just gave me more errors so forget that.

I had the same problem, but this fixes it:
apt-get install gcc-multilib

---

