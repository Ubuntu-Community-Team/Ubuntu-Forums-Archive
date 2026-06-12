---
title: "Building gpsbabel 1.3.5 error"
date: 2008-05-17
forum: x86 64-bit Users
---

### Post by dabang on 2008-05-17
Hi there!

I'm trying to build an Ubuntu package for gpsbabel 1.3.5 on Gutsy amd64 via "uupdate" (unfortunately gutsy's version is to old for my needs), but when compiling I get this error:
```
gcc   -c   -I.  -Wall -g -O2 -Wall lmx.c -o lmx.o
lmx.c:34: Fehler: »link« als andere Symbolart redeklariert
/usr/include/unistd.h:757: Fehler: Vorherige Deklaration von »link« war hier
make[1]: *** [lmx.o] Fehler 1
make[1]: Verlasse Verzeichnis '/home/gerrit/gvtemp/gps/gpsbabel-1.3.5'
make: *** [build-stamp] Fehler 2
dpkg-buildpackage: Fehlschlag: debian/rules build gab Fehler-Exitstatus 2
```
This is line 34 of "lmx.c":
```
char *link, *linkt;
```
I'm sorry, I don't know the correct English translation for this message... Hope someone can help though...

---

### Post by dabang on 2008-05-21
OK, got it! This gave me hard time... You need to edit debian/rules:

In line 26 remove
```
--with-zlib=system
```

and it'll work!

---

