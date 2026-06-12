---
title: "python 2.5 packaging policy"
date: 2009-01-20
forum: x86 64-bit Users
---

### Post by tontonraoul on 2009-01-20
Hello,
installing a program on my Hardy 64bit machine, I met a problem, partially solved but... not completely !

This program has a python GUI, and the installation from source requires to lay out a simlink to the libgdi library. I typed :
```

$ locate _gdi_.so
$ /usr/lib/python2.4/site-packages/wx-2.8-gtk2-unicode/wx/_gdi_.so
$ /usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_gdi_.so
```
then :
```
$ sudo ln -s /usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_gdi_.so /usr/local/lib/libgdi.so
```

Running the program, one module returned errors related to this lib. In fact, the symlink pointed to a wrong .so file. The correct _gdi_.so file was located elsewhere, in /usr/**lib64**/python2.5/...

Setting up the correct redirection, the program finally worked fine.

My question is : why does python seem to be installed in two distinct places ? is it that /usr/lib/python2.5 contains the 32bit version ? the *file* command would deny this assertion :
```
$ file /usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_gdi_.so 
$ /usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_gdi_.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), stripped
```
And what is more puzzling is the result of a *locate *, which simply ignores the /usr/lib64/python2.5/ directory :
```
$ sudo /usr/bin/updatedb
$ locate _gdi_.so
$ /usr/lib/python2.4/site-packages/wx-2.8-gtk2-unicode/wx/_gdi_.so
$ /usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_gdi_.so
```

Damned ! thanks for shedding some light on my problem ;)

---

