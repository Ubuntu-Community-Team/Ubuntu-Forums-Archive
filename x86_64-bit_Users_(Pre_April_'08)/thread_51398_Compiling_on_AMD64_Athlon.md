---
title: "Compiling on AMD64 Athlon"
date: 2005-07-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by StefanStefanov on 2005-07-23
Hi,
I got new AMD64 Athlon 3500+ and after installing Ubuntu 5.04 (FC4 64 refused to be installed - freeze during installation of the software) I cannot compile anything except "HelloWord" type of programs.
My compilers are:
---------------------------
gcc/g++:
Reading specs from /usr/lib/gcc-lib/x86_64-linux/3.3.5/specs
Configured with: ../src/configure -v --enable-languages=c,c++,java,f77,pascal,objc,ada,treelang --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --with-gxx-include-dir=/usr/include/c++/3.3 --enable-shared --with-system-zlib --enable-nls --without-included-gettext --enable-__cxa_atexit --enable-clocale=gnu --enable-debug --enable-java-gc=boehm --enable-java-awt=xlib --enable-objc-gc --disable-multilib x86_64-linux
Thread model: posix
gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)
----------------------

Whenever I try to compile it get frozen during make installation and I have to reboot.
Please can somebody help me by compiling a package on similar 64bit machine and telling me what do I do wrong!!!
It is a small molecular-genetcs package dealing with DNA sequences. It is in Department of Statistics, University of Oxford, UK - so it is not evil thing ;)
[http://www.stats.ox.ac.uk/~mcvean/LDhat/LDhat2.0.tar.gz](http://www.stats.ox.ac.uk/~mcvean/LDhat/LDhat2.0.tar.gz)
It had to be untared and given command 'make' in its directory. Eventually one must finished up with couple of binaries: convert, pairwise, interval, stat, complete, lkgen. I cannot do this because I cannot understand why my compiler freezes the whole computer.
Thank you.
Stefan

---

### Post by negatory on 2005-07-24
I've managed to compile it with no problems.My gcc version is the same as yours...I don't know why your computer is freezing,maybe a corrupt gcc library?
If you want I've compiled it,you can find the binaries [here](http://pwp.netcabo.pt/0245939201/linux/ldhat2.0.bin.tar.gz).
Hope I could help.
Pedro Carrico

---

### Post by Pse on 2005-07-24
Could it be your hardware? FC64 crashed, now Ubuntu crashes badly while compiling a simple program?

---

### Post by amigo_boy2000 on 2005-07-24
[QUOTE=Pse]Could it be your hardware? FC64 crashed, now Ubuntu crashes badly while compiling a simple program?[/QUOTE]

I had *a lot* of problems for about a year with Red Hat. It usually only manifested itself during a new install. I always thought I had a bad hard drive. I went through two drives in 9 months. Some kind soul on the Fedora mailing list finally told me to run the "memtest" diagnostic from the boot disk. I think it was at the "boot:" prompt, I typed "memtest86". It took a long time writing all permutations of bits to every memory location. But, eventually it discovered an error. I replaced the stick and have never had trouble again.

It seems like the installation (and some memory intensive post-install activities, like compiling) would access the memory. It was weird to realize the problem was as simple as a stick of memory. I don't know how I would have discovered it without the suggestion to run the diagnostic.

I think the tool it is running is this:

[http://www.memtest86.com/](http://www.memtest86.com/)

Mark

---

### Post by StefanStefanov on 2005-07-25
Thanks to everybody!
Pedro, thank you for the binnaries. I will use them for now and later I will really check my hardware.

Stefan

---

### Post by StefanStefanov on 2005-07-25
[QUOTE=negatory]I've managed to compile it with no problems.My gcc version is the same as yours...I don't know why your computer is freezing,maybe a corrupt gcc library?
If you want I've compiled it,you can find the binaries [here](http://pwp.netcabo.pt/0245939201/linux/ldhat2.0.bin.tar.gz).
Hope I could help.
Pedro Carrico[/QUOTE]
 Thanks for the binaries.

---

