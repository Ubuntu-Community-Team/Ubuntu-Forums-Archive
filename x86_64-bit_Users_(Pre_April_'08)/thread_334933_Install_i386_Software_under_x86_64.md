---
title: "Install i386 Software under x86_64"
date: 2007-01-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by dmbrown00 on 2007-01-09
I have Ubuntu 6.10 x86_64 installed.  Whenever I try to install an i386-only package, I get an error that it is not available for my architecture.  In other distros, 32- and 64-bit packages would both install happily.  Why can't I install these packages.  What can I do to install them without recompiling everything for 64-bit, especially since there are non-open source packages available only for 32-bit.

---

### Post by OrkanSpec on 2007-01-15
You should install the following packages: linux32, ia32-libs*, lib32ncurses5.
The most important are ia32-libs*.

To install an i386 package, execute:
dpkg -i --force-architecture package_i386.deb
where package_i386.deb is a package name.

You may sometimes face an error while installing from binary install files (bin).  Try the following syntax then:
linux32 ./installer.bin

And finally:
search the forum!

Regards,

---

