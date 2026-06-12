---
title: "Looking for glib 2.10.3 headers"
date: 2006-08-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by tomdkat on 2006-08-16
So, I'm trying to build Gimp 2.3.10 from source and the configure script fails since it can't find glib.h:

```
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.8.2... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error: Test for GLIB failed. See the file 'INSTALL' for help.
tom@linux:~/gimp-2.3.10$

```

config.log:```
configure:26505: checking for GLIB - version >= 2.8.2
configure:26665: result: no
configure:26703: gcc -o conftest -g -O2 -Wall    conftest.c   >&5
conftest.c:47:18: error: glib.h: No such file or directory
conftest.c: In function 'main':
conftest.c:53: error: 'glib_major_version' undeclared (first use in this function)
conftest.c:53: error: (Each undeclared identifier is reported only once
conftest.c:53: error: for each function it appears in.)
conftest.c:53: error: 'glib_minor_version' undeclared (first use in this function)
conftest.c:53: error: 'glib_micro_version' undeclared (first use in this function)
configure:26709: $? = 1
configure: failed program was:

```
So, I went to the package manager to install libglib-2.0-dev and found only the 2.10.2 glib header package is available and not the 2.10.3 header package.  The 2.10.2 header package is version "2.10.2-1ubuntu3" where the glib libraries actually installed are version "2.10.3-0ubuntu1".

I'm not used to this kind of thing since I'm used to simply build libraries like glib from source and installing everything.  :)

So, how do I get the 2.10.3 glib headers so I can continue my Gimp 2.3.10 build?

Thanks!

Peace...

---

### Post by tomdkat on 2006-08-17
Ok, I'm new to the installation of pre-built packages concept so would it be safe for me to simply download and install glib-2.10.3 from source, so I'll be sure to get everything I need to build other stuff that uses glib or will I run the risk of breaking other parts of my system if I do this?

If I build glib-2.10.3 all from source, will that prevent future Ubuntu glib package updates from being installable?

Thanks!

Peace...

---

### Post by tomdkat on 2006-08-23
Well, I got glib-2.10.3 installed from source ok, but now GTK+ 2.10.2 headers can't be found and I couldn't find them in the package manager.

So, I'm off to build that now.  *sigh*

Peace...

---

### Post by tomdkat on 2006-08-25
I had an incomplete repository list which prevented me from installing the glib/gtk+ headers.  I've got that fixed so we'll see what happens now. :)

Peace...

---

