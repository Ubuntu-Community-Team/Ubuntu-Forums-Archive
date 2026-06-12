---
title: "yact : compiling 32bit source on 64bit : info"
date: 2007-10-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by cacycleworks on 2007-10-08
yact = yet another compiling thread...  I'm submitting in hopes the next time someone searches this may help out.

I was trying to build a program and it was giving me this:
```
/usr/bin/ld: warning: i386 architecture of input file `ad2.a(adaudit.o)' is incompatible with i386:x86-64 output
```
for about 100 files...

I searched the forums and almost got my answer from what I found. I needed the -m32 option for both gcc and ld, however neither responded to environment variables set. 

A grep showed me some location of FLAGS...

```

19:20 root@outside:/home/chris/.packages/dwg2dxf-2.1# grep -R "LDFLAGS" *
dwg2dxf/Makefile:LDFLAGS =
dwg2dxf/Makefile:dwg2dxf_LDFLAGS =
INSTALL:     env CPPFLAGS=-I/usr/local/include LDFLAGS=-s ./configure
19:20 root@outside:/home/chris/.packages/dwg2dxf-2.1#
```

After running the typical ./configure to create the makefiles, I edited the source file subdir makefile lines as follows:
```
CPPFLAGS = [COLOR="Red"]**-m32 -Wno-deprecated**[/COLOR]
LDFLAGS = **[COLOR="Red"]-m32[/COLOR]**
dwg2dxf_LDFLAGS = **[COLOR="Red"]-m32[/COLOR]**
CXXFLAGS = -g -O2 [COLOR="Red"]**-m32 -Wno-deprecated**[/COLOR]
```


What's the program? Doesn't really matter, as the info is pretty generic... the -Wno-deprecated option was a suggestion from the compiling output to get rid of a warning....

```
make[3]: Entering directory `/home/chris/.packages/dwg2dxf-2.1/dwg2dxf'
c++ -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -c main.cpp
In file included from /usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../include/c++/4.1.2/backward/iostream.h:31,
                 from main.cpp:39:
/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../include/c++/4.1.2/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
c++  -g -O2  -o dwg2dxf  main.o ad2.a

```

Program is dwg2dxf to convert autocad dwg to something open source.

---

### Post by incidence on 2007-10-08
This is just a guessing, but check that mtune and march are the same, and they are compatible with 32-bit environment, see: [ http://gcc.gnu.org/onlinedocs/gcc-4.1.2/gcc/i386-and-x86_002d64-Options.html#i386-and-x86_002d64-Options]("http://gcc.gnu.org/onlinedocs/gcc-4.1.2/gcc/i386-and-x86_002d64-Options.html#i386-and-x86_002d64-Options")

---

