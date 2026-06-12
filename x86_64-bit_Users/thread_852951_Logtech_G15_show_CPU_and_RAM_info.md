---
title: "Logtech G15 show CPU and RAM info"
date: 2008-07-08
forum: x86 64-bit Users
---

### Post by obsrv on 2008-07-08
Hello,
Is it possible for Ubuntu to make Logtech G15 keyboard to show CPU and RAM info like in Windows? I only get Clock with G15Daemon.

---

### Post by obsrv on 2008-08-04
I have found G15Stats for this. But I cant compile it.

```
root@ubuntu:/home/obsrv/g15stats-1.0# make
make  all-am
make[1]: Entering directory `/home/obsrv/g15stats-1.0'
gcc -DHAVE_CONFIG_H -I.   -I/usr/include/libgtop-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -O3 -Wall  -I/usr/include/libgtop-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libgtop-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I. -I.  -I/usr/include/libgtop-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libgtop-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -MT g15stats.o -MD -MP -MF .deps/g15stats.Tpo -c -o g15stats.o g15stats.c
g15stats.c: In function ‘main’:
g15stats.c:454: error: ‘PACKAGE_NAME’ undeclared (first use in this function)
g15stats.c:454: error: (Each undeclared identifier is reported only once
g15stats.c:454: error: for each function it appears in.)
make[1]: *** [g15stats.o] Error 1
make[1]: Leaving directory `/home/obsrv/g15stats-1.0'
make: *** [all] Error 2
```

---

### Post by obsrv on 2008-08-04
I have found a debian package of G15Stats, it works good on KUbuntu KDE4 AMD64.

---

### Post by Moustacha on 2008-09-07
Do you know how to set it up so that you can change the information that is displayed?
Using the intrepid package worked fine for me on hardy btw.

---

