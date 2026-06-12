---
title: "How to convert i386 debian package to amd64 debian package?"
date: 2007-09-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Debadeepta on 2007-09-16
Hi,

I am running Feisty Fawn 64 bit on an AMD64 bit processor.

I have a debian package for i386 which I need to install for a very critical piece of robot simulator to run. 

When I try a dpkg -i command then it exits with an error saying that the package is for i386 and not for amd64.

I force installed it using dpkg --force......

But my program's scons file refuses to accept the installed libraries saying that they are incompatible.

I also have the source for the debian package and the debian/changelog and the *.diff  *.dsc and the *.orig.tar files. But debuild also exited saying that the rules did not have an amd64 target build. 

I cant make sense of the rules script file as I am not very familiar with debian and have recently moved to this architecture on my new laptop.

I will appreciate any help on reconfiguring the i386 package for amd64.

Thanks.

---

### Post by Kilz on 2007-09-16
> **Debadeepta said:**
> Hi,

I am running Feisty Fawn 64 bit on an AMD64 bit processor.

I have a debian package for i386 which I need to install for a very critical piece of robot simulator to run. 

When I try a dpkg -i command then it exits with an error saying that the package is for i386 and not for amd64.

I force installed it using dpkg --force......

But my program's scons file refuses to accept the installed libraries saying that they are incompatible.

I also have the source for the debian package and the debian/changelog and the *.diff  *.dsc and the *.orig.tar files. But debuild also exited saying that the rules did not have an amd64 target build. 

I cant make sense of the rules script file as I am not very familiar with debian and have recently moved to this architecture on my new laptop.

I will appreciate any help on reconfiguring the i386 package for amd64.

Thanks.

[http://tghc.org/32apps.php](http://tghc.org/32apps.php) this may not be what you asked, but it may help.

---

