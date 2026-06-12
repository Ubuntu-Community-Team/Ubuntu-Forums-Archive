---
title: "installing new gcc does not change version used by cc"
date: 2006-09-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by KimJarvis on 2006-09-10
I need to use GCC 4.1.1.  I installed the .deb package but the C compiler still uses the GCC 4.0.3 supplied with Dapper.  Am I missing some step or the setting of an environment variable or something?

kim@shuttle:~$ sudo dpkg -i gcc-4.1-base_4.1.1-13_amd64.deb
(Reading database ... 89207 files and directories currently installed.)
Preparing to replace gcc-4.1-base 4.1.1-13 (using gcc-4.1-base_4.1.1-13_amd64.deb) ...
Unpacking replacement gcc-4.1-base ...
Setting up gcc-4.1-base (4.1.1-13) ...

kim@shuttle:~$ cc -v
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.0 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-java-awt=gtk-default --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre --enable-mpfr --disable-werror --enable-checking=release x86_64-linux-gnu
Thread model: posix
gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
kim@shuttle:~$

---

### Post by Sloth on 2006-09-10
I had to update the links in /usr/bin to point to /usr/local/bin, but I built it myself and did not install from a deb.

---

### Post by manuska on 2006-09-10
IIRC

```

sudo update-alternatives --install cc cc /usr/bin/gcc-4.1 20
sudo update-alternatives --config cc

```

This is assuming that gcc-4.1 is what you want to use and priority is ok. Those can be adjusted if you want to.

You might first want to read man-page for update-alternatives to see how it works. There's also galternatives package for gui.

---

