---
title: "MOL and OSX 10.4 Tiger"
date: 2005-11-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Leonida on 2005-11-23
Does anyone run MOL (Mac On Linux) with MAC OSX 10.4.x (Tiger)?

The wiki [MacOnLinuxHowto]("https://wiki.ubuntu.com//MacOnLinuxHowto/") install MOL 0.9.70-20 provided with debian packages that is not compatible with OSX 10.4.x.
Last source with recent patches provided from a [gentoo developer]("http://forums.gentoo.org/viewtopic-p-2794665.html#2794665") are: [http://dev.gentoo.org/~josejx/mol-0.9.71_pre4.tar.bz2](http://dev.gentoo.org/~josejx/mol-0.9.71_pre4.tar.bz2)
Do you know how to install last MOL source?

---

### Post by Leonida on 2005-11-23
I've donloaded [http://dev.gentoo.org/~josejx/mol-0.9.71_pre4.tar.bz2](http://dev.gentoo.org/~josejx/mol-0.9.71_pre4.tar.bz2)
Untar with:
```
tar -xvjpf /tmp/mol-0.9.71_pre4.tar.bz2
```
than
```
export CC=gcc-3.4
``` to use gcc3.4 instead of gcc4.

To get no[ error]("http://paste.ubuntulinux.nl/4918") during ./configure I've installed **autoconf 2.13**

Then when I've run make I get an yacc missing error so I've installed **byacc,** **bison** and **flex.**
Bur now when I ran make I get these errors:
```
gand@ubu:/usr/src/mol-0.9.71_pre4$ sudo make
Password:
+ Entering lxdialog
+ Entering kconfig
yacc: e - line 30 of "zconf-y.y", syntax error
%expect 40
^
make[2]: *** [zconf-y.c] Error 1
make[1]: *** [sub-kconfig-all] Error 2
make: *** [do-bootstrap] Error 2
```
Any idea?

---

