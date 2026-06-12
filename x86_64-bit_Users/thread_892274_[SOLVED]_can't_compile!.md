---
title: "[SOLVED] can't compile!"
date: 2008-08-17
forum: x86 64-bit Users
---

### Post by stldirty on 2008-08-17
everytime i try to make a file i get this error.

```
make: *** No targets specified and no makefile found.  Stop.

```

i have build-essentials installed.  what could be the problem???

and for the love of god please dont tell me to find a deb.

---

### Post by ad_267 on 2008-08-17
What are you trying to compile?

Often you need to run a configure script first using "./configure" which generates a makefile.

---

### Post by ibutho on 2008-08-17
That error usually shows up if you did not run ./configure or if ./configure did not finish successfully.

---

### Post by stldirty on 2008-08-17
ok u may be on to something.

```
configure: error: X11 development libraries/headers not found

```

---

### Post by stldirty on 2008-08-17
ok i got it working by installing these files

    * libtiff4-dev
    * libjasper-dev
    * libgdbm-dev
    * libxml-simple-perl
    * libxt-dev
thanks for the tip!

---

