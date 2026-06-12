---
title: "Error while trying to compile wine"
date: 2005-06-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by ::DoGG:: on 2005-06-01
I followed the guide found on this forum about installing wine. It configures fine but when i run the wineinstall script, after logging as root to compile the wine it gives me this:
```
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__ -D_REENTRANT -fPIC  -Wall -pipe -fno-strict-aliasing -gstabs+ -Wpointer-arith  -g -O2 -D__i386__ -o  interlocked.o interlocked.c
{standard input}: Assembler messages:
{standard input}:283: Error: `12(%esp)' is not a valid 64 bit base/index express ion
{standard input}:284: Error: `8(%esp)' is not a valid 64 bit base/index expressi on
{standard input}:285: Error: `4(%esp)' is not a valid 64 bit base/index expressi on
{standard input}:286: Error: `(%edx)' is not a valid 64 bit base/index expressio n
{standard input}:294: Error: `12(%esp)' is not a valid 64 bit base/index express ion
{standard input}:295: Error: `8(%esp)' is not a valid 64 bit base/index expressi on
{standard input}:296: Error: `4(%esp)' is not a valid 64 bit base/index expressi on
{standard input}:297: Error: `(%edx)' is not a valid 64 bit base/index expressio n
{standard input}:305: Error: `8(%esp)' is not a valid 64 bit base/index expressi on
{standard input}:306: Error: `4(%esp)' is not a valid 64 bit base/index expressi on
{standard input}:307: Error: `(%edx)' is not a valid 64 bit base/index expressio n
{standard input}:315: Error: `8(%esp)' is not a valid 64 bit base/index expressi on
{standard input}:316: Error: `4(%esp)' is not a valid 64 bit base/index expressi on
{standard input}:317: Error: `(%edx)' is not a valid 64 bit base/index expressio n
{standard input}:325: Error: `8(%esp)' is not a valid 64 bit base/index expressi on
{standard input}:326: Error: `4(%esp)' is not a valid 64 bit base/index expressi on
{standard input}:327: Error: `(%edx)' is not a valid 64 bit base/index expressio n
make[2]: *** [interlocked.o] B&#322;&#261;d 1
make[2]: Opuszczenie katalogu `/home/mizer/cvs/wine/libs/port'
make[1]: *** [port] B&#322;&#261;d 2
make[1]: Opuszczenie katalogu `/home/mizer/cvs/wine/libs'
make: *** [libs] B&#322;&#261;d 2
```

any ideas ??

---

### Post by ::DoGG:: on 2005-06-01
Ok, update about that, i found this on some mailing list:

```
The "Error: `(%esi)' is not a valid 64 bit base/index expression" is 
caused by timer.cpp.

This file mainly contains four conditional compilation paths:
  - Win32
  - GCC Assembly (not for Win32)
  - Generic Unix
  - Mac

The compilation error comes from the fact that the GCC assembly is not 
correct in x86-64. ESI being a 32 bits register, it cannot be used to 
give a 64 bits address during a movl.

The configurator.c program should detect that when on a x86-64 platform 
it should not #define PENTIUM 1.
Another solution is to provide an assembly for x86-64.

My personal opinion would be to drop the assembly path, since RDTSC does 
not work on modern CPUs that changes their frequency depending on the 
workload (it's particularly obvious on a laptop).
This means that using RDTSC on such CPU (laptops, P4 6xx, etc) won't be 
able to provide you with a linear time mesure, only a number of clock 
cycles.
```

Since i`m not that kind of guy to digg in source compiler scripts (i don`t know much about that) can anybody tell me what should i do ??  :|

---

### Post by ::DoGG:: on 2005-06-02
Guys, do You have any clue ??? I really don`t want to use windows, but i`m forced to do that by working with studioMX and Photoshop. I really need to compile wien to let the windows go to hell... I tried compile it under kernel  2.6.7 but still no luck...

---

### Post by AndersAA on 2005-06-02
well first of all which compiler are you using?  You'll have to use gcc3.4 or higher, and second I dont see any -m32 in there.  If your compiling on amd64 for running 32bit binaries you'll have to crosscompile, or you'll only be able to run 64bit windows apps.

---

### Post by ::DoGG:: on 2005-06-02
Well, when i set CC="gcc -m32" configure script spits out error then gcc compiler cannot create executables and the fun stops at the very beginning  :-| 
I`m using gcc in version 3.4.

---

### Post by AndersAA on 2005-06-02
check config.log then
you can also search through this forum, I believe I posted something about wine here (when it was new), did get it to compile.

---

### Post by hammett111 on 2005-06-12
[QUOTE=::DoGG::]Well, when i set CC="gcc -m32" configure script spits out error then gcc compiler cannot create executables and the fun stops at the very beginning  :-| 
I`m using gcc in version 3.4.[/QUOTE]

Did you get it to work?? I have the same problem at the moment

Quentin@ubuntu:~/cvs/wine$ sudo make
Password:
make[1]: Entering directory `/home/quentin/cvs/wine/libs'
make[2]: Entering directory `/home/quentin/cvs/wine/libs/port'
gcc-4.0 -c -I. -I. -I../../include -I../../include  -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -gstabs+ -Wpointer-arith  -g -O2 -D__i386__ -o interlocked.o interlocked.c
{standard input}: Assembler messages:
{standard input}:214: Error: `12(%esp)' is not a valid 64 bit base/index expression

---

### Post by AndersAA on 2005-06-12
got it compiled, but never got it working after that.  I ended up simply using a binary instead, which I did get working.

---

### Post by ::DoGG:: on 2005-06-12
I didn`t get that one figured out. I`m using the CrossOverOffce now. It`s working for me since i needed wine mostly for the application support.

---

### Post by adsman on 2007-11-03
> **AndersAA said:**
> got it compiled, but never got it working after that.  I ended up simply using a binary instead, which I did get working.

hi there im having the same error as you but cant work out how to compile 
```
{standard input}: Assembler messages:
{standard input}:38: Error: suffix or operands invalid for `push'
{standard input}:39: Error: suffix or operands invalid for `push'
{standard input}:46: Error: suffix or operands invalid for `pop'
{standard input}:47: Error: suffix or operands invalid for `pop'
make[2]: *** [interlocked.o] Error 1

```

thanks for any help.

---

