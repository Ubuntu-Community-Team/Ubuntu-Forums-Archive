---
title: "Anjuta 2.1.1 Compile Error"
date: 2007-03-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by russell.h on 2007-03-08
I've been trying to compile Anjuta 2.1.1, and after installing, and in several cases compiling quite a few dependencies I finally got the config to go ok.

But now when I compile I get a weird error:
```
 /usr/bin/ld: /usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib64/libiberty.a(cplus-dem.o): relocation R_X86_64_32S against `_sch_istable' can not be used when making a shared object; recompile with -fPIC
/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib64/libiberty.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[3]: *** [libanjuta-valgrind.la] Error 1
make[3]: Leaving directory `/home/russell/Desktop/anjuta-2.1.1/plugins/valgrind'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/russell/Desktop/anjuta-2.1.1/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/russell/Desktop/anjuta-2.1.1'
make: *** [all] Error 2

```
I've found threads where people had similar problems when compiling other programs, but I can't seem to find the solution.

I'm running Feisty, but since this problem seems to be 64bit related I posted here. Please feel free to move it.

Thanks,

Russell

---

### Post by alextud on 2007-03-08
You can disable the plugin :
./configure --disable-plugin-valgrind

---

### Post by russell.h on 2007-03-08
Worked beautifully. At least for that error. It refused to install if I had glade3 installed, but checkinstall wouldn't build the package if it wasn't. So I had to build the package, remove glade, then install it. Whatever works.

Thanks!

Russell

---

