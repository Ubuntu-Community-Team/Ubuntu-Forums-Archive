---
title: "Missing library - can't find/download."
date: 2009-02-27
forum: x86 64-bit Users
---

### Post by coffee is the colour on 2009-02-27
Hi all,

I have a 64-bit Dell Ubuntu, on which I am trying to install software.  During the installation process I get the following error:

/usr/accelrys/I2005/Linux_2_Intel_32/exe/special/wish: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

I attempted installation of several packages from Syn.Pac.Manager, including libstdc++5-33-dev, libstdc++6-4.2-dbg and libstdc++6-4.2-dev.  All packages were successfully installed via S.P.M but I still encounter the shared libraries error.  I also attempted to download and install libstdc++2.10-glibc2.2-2.95.4-24-i386.deb file, which, as I am aware contains the library.  The problem is I can only find the .deb for i386 architecture.  Can anyone advise on where to find/download the package/file for the amd64 architecture? :confused:

Many Thanx,

---

### Post by smani on 2009-02-27
Have a look with apt-file (sudo apt-get install apt-file and then sudo apt-file update and finally sudo apt-file search libstdc++-libc6.2-2.so.3) which package includes that specific library. If you already got it installed somewhere you may want to try and symlinking it to the location where the program expects it to be.

---

### Post by Yellow Pasque on 2009-02-27
The program you're trying to run is a 32-bit program, so no matter what 64-bit libraries you install, it's still going to look for 32-bit libraries in /usr/lib32

> I also attempted to download and install libstdc++2.10-glibc2.2-2.95.4-24-i386.deb... Can anyone advise on where to find/download the package/file for the amd64 architecture?
You already have the package for amd64 (libstdc++6). However, this doesn't help when you're trying to run a 32-bit program.

Use:
```
sudo apt-get install ia32-libs
```
If that doesn't work (and I suspect it won't because your program is looking for a very specific/obsolete version of libstdc++6), try getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by coffee is the colour on 2009-03-04
Hi Guys,

Thanx for the replies.  The issue was finally resolved with the command

dpkg -i --force-architecture libstdc++2.10-glibc2.2_2.95.4-24_i386.deb

Thanx for the advice.

---

