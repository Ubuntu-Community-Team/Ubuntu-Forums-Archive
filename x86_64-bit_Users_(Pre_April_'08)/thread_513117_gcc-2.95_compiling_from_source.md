---
title: "gcc-2.95 compiling from source"
date: 2007-07-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by pchaffey on 2007-07-30
Hi all,

I need to have gcc-2.95 compiled on my system (Kubuntu 7.04) with a AMD64 processor. This is for
compiling an old version of systemC (2.01) which needs this old compiler.

I cannot find a pre built AMD64 gcc-2.95 package anywhere and hence I am trying to build from source.


I have done the following:

apt-get install subversion autoconf automake texinfo flex bison gawk build-essential
apt-get source gcc-2.95
apt-get build-dep gcc-2.95
apt-get install libtool

cd gcc-2.95-2.95.4.ds15/
./debian/rules patch

cd src-native/
mkdir objdir
cp /usr/share/aclocal/libtool.m4 aclocal.m4
libtoolize --force

cd objdir
../configure --prefix=/usr/local

I get the following :
Configure in /home/paul/gcc/gcc-2.95-2.95.4.ds15/src-native/objdir/gcc failed, exiting.

checking the configure log I get :
configure:1955:20: error: direct.h: No such file or directory
configure: failed program was:
#line 1954 "configure"
#include "confdefs.h"
#include <direct.h>
configure:1989: checking for thread.h
configure:1999: gcc -E  conftest.c >/dev/null 2>conftest.out
configure:1995:20: error: thread.h: No such file or directory
configure: failed program was:
#line 1994 "configure"
#include "confdefs.h"
#include <thread.h>

So my first question is, am I approaching this correctly ? and if so how would I proceed from here ?

Many thanks...

---

### Post by pchaffey on 2007-07-30
I didn't think I would get a quick response to this one !

I know that perhaps this is a gcc problem  - but does anyone have any suggestion on where to go
to sort this type of problem out ?

Many thanks, Paul

---

### Post by praxis22 on 2007-07-30
Hi, 

It's likely that unless you specified otherwise it's looking for a 32bit thread library, and on a 64bit system you don't have one.

This is what I did to build gcc 4.2 I imagine you can do something like the same:

[http://ubuntuforums.org/showthread.php?t=487221](http://ubuntuforums.org/showthread.php?t=487221)

I'd advise you to go to the gentoo forums, (google it) and search there. In gentoo you have to compile everything by hand so you'll find a lot more technical threads about that sort of thing there.

good luck!

---

### Post by pchaffey on 2007-07-30
Hi,

I think this is easier going forward to a newer gcc version. I think that going backwards so far to
gcc-2.95 will be harder. As far as I can see...

I think I might go down the chroot route - this will be easier in the long run.

Thanks, Paul.

---

### Post by praxis22 on 2007-07-30
having had a look, it appears there is a version for fiesty:

[http://packages.ubuntu.com/feisty/devel/gcc-2.95](http://packages.ubuntu.com/feisty/devel/gcc-2.95)

That's the 32 bit, but I see no reason why they wouldn't have backported it to 64 bit too.

Check synaptic see what it says.

---

