---
title: "configure, ,make, install"
date: 2006-04-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by journeyman01 on 2006-04-21
Howdy,
  I just installed 5.10 on a G4 laptop because my studies require me to use a lot of programs that can only be installed from source (i.e. .tar.gz).  I have been fine on doing this on my office machine using ./configure and make.  However Ubuntu seems to lack a number of critical things.  Can anyone give me a list of programs and libraries one needs to add to Ubuntu to be able to build up source code from C, C++, FORTRAN, etc...I have given it a couple shots and failed miserably.

Cheers

---

### Post by linear on 2006-04-21
Start by installing the "build-essential" package. This will get you all the things you need for C.
 
Also read this: [CompilingSoftware]("https://wiki.ubuntu.com/CompilingSoftware"). Note the recommendation of **checkinstall** (another package) instead of **make install**.
 
[InstallingCompilers]("https://wiki.ubuntu.com/InstallingCompilers") has instructions for Fortran.

---

### Post by soonindallas on 2006-04-21
[http://packages.ubuntu.com/breezy/devel/build-essential](http://packages.ubuntu.com/breezy/devel/build-essential)

to get it:

```
sudo apt-get install build-essential
```

> build-essentials is exactly what the name suggests. The essentials for doing any kind of building on a Linux system, at least C/C++ compilation. It contains things like GCC, the GNU C compiler, GCPP (or G++), the GNU C++ compiler, GDB, the GNU debugger, and various other libraries and headerfiles. When you've installed it, you should be able to compile most programs, those that you can't compile are either not supposed to be compiled on your system, or they will clearly state what package/library is missing, which can be simply apt-get'ed.

quoting a knowledgeable member from post #5 on this thread:

[http://www.ubuntuforums.org/showthread.php?t=163095](http://www.ubuntuforums.org/showthread.php?t=163095)

---

