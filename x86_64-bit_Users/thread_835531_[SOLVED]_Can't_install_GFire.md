---
title: "[SOLVED] Can't install GFire"
date: 2008-06-20
forum: x86 64-bit Users
---

### Post by Sam324 on 2008-06-20
Hi.  I want to install GFire for Pidgin on my 8.04 Hardy, but I get errors.  I'm trying to install the source code version, because the DEB says "Wrong arcitechture" and the RPM opens as an archive, which is of an unknown type.  So, I type ./configure and get:
```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
checking for gcc... gcc
[COLOR=Red]checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.[/COLOR]

```then I try make and get:
```
[COLOR=Red]
make: *** No targets specified and no makefile found.  Stop.[/COLOR]

```How do I properly install it (64-bit, of course!)?

---

### Post by cariboo on 2008-06-20
If you can get a 64bit rpm use alien to convert it to a deb. It might be a lot easier than compiling from source. Alien is available in the repositories. To use it type man alien in a terminal.

Jim

---

### Post by Sam324 on 2008-06-20
Thanks, but there is no 64-bit RPM available.  Only a 32-bit DEB, RPM, and src.  How do I install a 32-bit one?

---

### Post by Cappy on 2008-06-20
The 64-bit pre-compiled plugin is here: [http://downloads.sourceforge.net/gfire/gfire_0.7.0-amd64.deb](http://downloads.sourceforge.net/gfire/gfire_0.7.0-amd64.deb)

---

### Post by Sam324 on 2008-06-23
TY!  I now have it working.

---

