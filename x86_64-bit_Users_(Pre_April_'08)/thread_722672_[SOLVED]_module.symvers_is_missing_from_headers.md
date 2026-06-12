---
title: "[SOLVED] module.symvers is missing from headers?"
date: 2008-03-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jedimaniac on 2008-03-12
Hi all. Using this [**Guide**]("http://ubuntuforums.org/showpost.php?p=3768914&postcount=60") i am trying to install the latest OSS4 so that i can use my XFi soundcard, The installation seems to go well but when i run "sudo soundon" I get the following problem:

```
OSS build environment set up for REGPARM kernels

Building module osscore
Failed to compile OSS
make -C /lib/modules/2.6.22-14-generic/build M=/usr/lib/oss/build modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.22-14-generic/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /usr/lib/oss/build/osscore.o
/bin/sh: scripts/genksyms/genksyms: No such file or directory
make[2]: *** [/usr/lib/oss/build/osscore.o] Error 1
make[1]: *** [_module_/usr/lib/oss/build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2

Relinking the OSS kernel modules failed
soundon has failed!

```

Unfortunately I am still a bit of a noob around linux and there is quite a steep learning curve. Reading around the net suggests that i have to recompile the kernel, Is there no easier way to get this file?

Any help appreciated.

---

### Post by Jedimaniac on 2008-03-13
Problem fixed. It would appear that the headers had been corrupted. I removed them completely and reinstalled them using apt-get.

finally have sound on my XFi :D

---

