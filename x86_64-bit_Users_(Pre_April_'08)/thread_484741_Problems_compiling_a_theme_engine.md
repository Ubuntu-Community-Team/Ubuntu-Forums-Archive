---
title: "Problems compiling a theme engine"
date: 2007-06-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by fakie_flip on 2007-06-26
I'd like to get the theme in Solaris for Gnome called Nimbus. Packages for Ubuntu are here.
[http://gnome-look.org/content/show.php/Nimbus+%28Ubuntu+and+Debian%29?content=54755](http://gnome-look.org/content/show.php/Nimbus+%28Ubuntu+and+Debian%29?content=54755)
However there are no packages for 64 bit there, and the package there is out of date. Here is the source code for the newest one.
[http://zap.tartarus.org/~ds/debian/dists/sid/main/source/nimbus_0.0.6.orig.tar.gz](http://zap.tartarus.org/~ds/debian/dists/sid/main/source/nimbus_0.0.6.orig.tar.gz)
I need help compiling it in 64 bit Ubuntu. Trying to compile it keeps giving me errors about intltool not being found and that I should install it. I have intltool installed.

```
chris@ubuntu:~/Desktop$ tar -xzf nimbus_0.0.6.orig.tar.gz  
chris@ubuntu:~/Desktop$ cd nimbus-0.0.6.orig/
chris@ubuntu:~/Desktop/nimbus-0.0.6.orig$ ./configure 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for intltool >= 0.23... awk: cannot open ./intltool-update.in (No such file or directory)
awk: cannot open ./intltool-update.in (No such file or directory)
 found
./configure: line 3648: test: : integer expression expected
configure: error: Your intltool is too old.  You need intltool 0.23 or later.
chris@ubuntu:~/Desktop/nimbus-0.0.6.orig$ which intltool-update 
/usr/bin/intltool-update
chris@ubuntu:~/Desktop/nimbus-0.0.6.orig$ dpkg -l | grep intltool
ii  intltool                               0.35.5-0ubuntu2                        Utility scripts for internationalizing XML
ii  intltool-debian                        0.35.0+20060710.1                      Help i18n of RFC822 compliant config files
chris@ubuntu:~/Desktop/nimbus-0.0.6.orig$ which intltool
intltool-extract  intltool-merge    intltool-update   
intltoolize       intltool-prepare  
chris@ubuntu:~/Desktop/nimbus-0.0.6.orig$ intltool-update --version
intltool-update (intltool) 0.35.5
Written by Kenneth Christiansen, Maciej Stachowiak, and Darin Adler.

Copyright (C) 2000-2003 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
chris@ubuntu:~/Desktop/nimbus-0.0.6.orig$ 
    
```

---

### Post by kuja on 2007-06-26
Yes, it's installed, but, it's not finding it for some reason or another, try copying the intltool files it's looking for to the directory containing configure because it seems to be looking for it there (for whatever reason). Maybe that will let it work.

---

