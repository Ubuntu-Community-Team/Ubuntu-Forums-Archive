---
title: "[SOLVED] How do i compile this:(kumbayo=a wine-git capable of running joost)"
date: 2007-06-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by theharshone on 2007-06-18
Hi 
I want to install this so i can watch joost in kubuntu. How do i compile wine in amd64. I am using feisty.

Here is the link for the source 

```
http://users.skynet.be/muaddib/gentoo/wine-kumbayo.tar.bz2
```




Thanks in advance

---

### Post by theharshone on 2007-06-21
Is is it impossible to compile wine from source in 64 bit?
is this what you are saying. 
if not plz plz give me instructions.

Thanks

---

### Post by incubus on 2007-06-22
theharshone,

Sometimes people won't answer your question because they just don't know it.  That was my case.  But it also makes a huge difference when you provide detailed information, so that whoever reads your post doesn't have to google around to know what you're talking about.  Remember, nobody here is getting paid to help out, so minimum effort naturally prevails.  : )

So, I searched for what you said and I found this:
[http://forums.gentoo.org/viewtopic-t-558046-highlight-joost.html](http://forums.gentoo.org/viewtopic-t-558046-highlight-joost.html)

I assume that's what you're talking about.  You're asking about compiling that fork of wine.  I've never compiled wine myself, but I'm sure there are existing threads about it here, in the 64 bit section.  But here's my suggestion.  I put the wine repositories in my sources.list and issued:
```

$ sudo apt-get build-dep wine

```

That should install the necessary packages to compile wine.  Then you can try to follow the instructions in that Gentoo post.

Good luck,

incubus

---

### Post by theharshone on 2007-06-22
For some reason, build-dep doesnt work. Probably cuz im using a private repo. anyways, i found another howto. I tried to do it their way. I got the same error i got when i tried before:

```
make[1]: Entering directory `/tmp/wine-kumbayo/kumbayo/tools'
../tools/makedep -C. -S.. -T.. -I/usr/include/freetype2 bin2res.c fnt2bdf.c fnt2fon.c make_ctests.c makedep.c relpath.c sfnt2fnt.c
make[1]: Leaving directory `/tmp/wine-kumbayo/kumbayo/tools'
make[1]: Entering directory `/tmp/wine-kumbayo/kumbayo/tools'
gcc -c -I. -I. -I../include -I../include -I/usr/include/freetype2   -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith  -fno-stack-protector -O2 -Os -march=athlon64 -mtune=athlon64 -fomit-frame-pointer -w -s -D__i386__  -o makedep.o makedep.c
gcc -fno-stack-protector -O2 -Os -march=athlon64 -mtune=athlon64 -fomit-frame-pointer -w -s -D__i386__ -o makedep makedep.o -s
make[1]: Leaving directory `/tmp/wine-kumbayo/kumbayo/tools'
make[1]: Entering directory `/tmp/wine-kumbayo/kumbayo/libs'
make[2]: Entering directory `/tmp/wine-kumbayo/kumbayo/libs/port'
../../tools/makedep -C. -S../.. -T../..  ffs.c fstatvfs.c futimes.c getopt.c getopt1.c getpagesize.c gettid.c interlocked.c lstat.c memcpy_unaligned.c memmove.c mkstemps.c pread.c pwrite.c readlink.c sigsetjmp.c spawn.c statvfs.c strcasecmp.c strerror.c strncasecmp.c usleep.c
make[2]: Leaving directory `/tmp/wine-kumbayo/kumbayo/libs/port'
make[2]: Entering directory `/tmp/wine-kumbayo/kumbayo/libs/port'
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith  -fno-stack-protector -O2 -Os -march=athlon64 -mtune=athlon64 -fomit-frame-pointer -w -s -D__i386__  -o ffs.o ffs.c
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith  -fno-stack-protector -O2 -Os -march=athlon64 -mtune=athlon64 -fomit-frame-pointer -w -s -D__i386__  -o fstatvfs.o fstatvfs.c
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith  -fno-stack-protector -O2 -Os -march=athlon64 -mtune=athlon64 -fomit-frame-pointer -w -s -D__i386__  -o futimes.o futimes.c
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith  -fno-stack-protector -O2 -Os -march=athlon64 -mtune=athlon64 -fomit-frame-pointer -w -s -D__i386__  -o getopt.o getopt.c
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith  -fno-stack-protector -O2 -Os -march=athlon64 -mtune=athlon64 -fomit-frame-pointer -w -s -D__i386__  -o getopt1.o getopt1.c
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith  -fno-stack-protector -O2 -Os -march=athlon64 -mtune=athlon64 -fomit-frame-pointer -w -s -D__i386__  -o getpagesize.o getpagesize.c
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith  -fno-stack-protector -O2 -Os -march=athlon64 -mtune=athlon64 -fomit-frame-pointer -w -s -D__i386__  -o gettid.o gettid.c
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith  -fno-stack-protector -O2 -Os -march=athlon64 -mtune=athlon64 -fomit-frame-pointer -w -s -D__i386__  -o interlocked.o interlocked.c
{standard input}: Assembler messages:
{standard input}:30: Error: suffix or operands invalid for `push'
{standard input}:31: Error: suffix or operands invalid for `push'
{standard input}:38: Error: suffix or operands invalid for `pop'
{standard input}:39: Error: suffix or operands invalid for `pop'
make[2]: *** [interlocked.o] Error 1
make[2]: Leaving directory `/tmp/wine-kumbayo/kumbayo/libs/port'
make[1]: *** [port] Error 2
make[1]: Leaving directory `/tmp/wine-kumbayo/kumbayo/libs'
make: *** [libs] Error 2

```

---

### Post by theharshone on 2007-07-07
I compiled it successfully. You have to run configure with ```
CC="gcc -m32" configure --prefix=/your/prefix
```

Hope this helps:D

---

