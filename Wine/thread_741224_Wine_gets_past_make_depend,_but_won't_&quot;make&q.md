---
title: "Wine gets past make depend, but won't &quot;make&quot;...?"
date: 2008-03-31
forum: Wine
---

### Post by chazdraves on 2008-03-31
Well, it was a real bugger getting past ./configure in the first place, but I've made it all the way to "make" now in the instructions found here under "Cursor Support"

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7440&iTestingId=22725](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7440&iTestingId=22725)

But I can't get Wine to "make". Here's what I get:

-------------------------------------------------------------------------------------------------------------------------------

make[1]: Entering directory `/home/chaz/Desktop/wine-0.9.58/tools'
make[1]: `makedep' is up to date.
make[1]: Leaving directory `/home/chaz/Desktop/wine-0.9.58/tools'
make[1]: Entering directory `/home/chaz/Desktop/wine-0.9.58/libs'
make[2]: Entering directory `/home/chaz/Desktop/wine-0.9.58/libs/port'
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith  -g -O2 -D__i386__  -o interlocked.o interlocked.c
{standard input}: Assembler messages:
{standard input}:38: Error: suffix or operands invalid for `push'
{standard input}:39: Error: suffix or operands invalid for `push'
{standard input}:46: Error: suffix or operands invalid for `pop'
{standard input}:47: Error: suffix or operands invalid for `pop'
make[2]: *** [interlocked.o] Error 1
make[2]: Leaving directory `/home/chaz/Desktop/wine-0.9.58/libs/port'
make[1]: *** [port] Error 2
make[1]: Leaving directory `/home/chaz/Desktop/wine-0.9.58/libs'
make: *** [libs] Error 2
chaz@chaz-desktop:~/Desktop/wine-0.9.58$ 

-------------------------------------------------------------------------------------------------------------------------------

Any idea what's happening and why? This is apparently the only way to get cursors to work in CNC3. And I have a feeling it won't even run well enough to justify this trouble, but I want to say I gave it the proper effort.

Thanks, all!
- Chaz

---

### Post by chazdraves on 2008-03-31
Anybody have a clue?

Thanks,
- Chaz

---

### Post by clear_sky on 2008-04-02
I am having the same problem, anyone know how to fix this?

---

### Post by happyhamster on 2008-04-02
Are you running the 64-bit version of ubuntu perhaps? If so, take a look at:
[http://wiki.winehq.org/WineOn64bit#head-15ce773b2453307f593a3045e558b30a0e8ed64d](http://wiki.winehq.org/WineOn64bit#head-15ce773b2453307f593a3045e558b30a0e8ed64d)

---

