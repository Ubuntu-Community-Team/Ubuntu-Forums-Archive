---
title: "How to compile SCILAB from source for Ubuntu AMD 64?"
date: 2005-11-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by smaiitm on 2005-11-06
Hi,

I want to install SCILAB, a mathematical package, on my AMD 64 machine that i have recently loaded with the Ubuntu 5.10 Breezy AMD 64 OS (Gnome). Of course i am new to Linux and have just about managed to get things running on my machine (with frequent search of this forum). 

I found an old version of SCILAB*.deb but it would not install on my machine. This is because some tcl/tk versions are the old versions rather than the current ones breezy 5.10 installs. I downloaded the source from SCILAB and was wondering if it is possible to compile this source and get it to run on my machine?

Thanks for your suggestions and help.

Mahesh

---

### Post by jon_gunnar on 2005-11-07
[QUOTE=smaiitm]Hi,
I found an old version of SCILAB*.deb but it would not install on my machine. This is because some tcl/tk versions are the old versions rather than the current ones breezy 5.10 installs.

Mahesh[/QUOTE]

I don't know what you means by old, but I find Version: 3.0-12. That should not be so bad.

jon@privat:~$ sudo apt-cache show scilab
Package: scilab
Priority: optional
Section: multiverse/math
Installed-Size: 28956
Maintainer: Torsten Werner <twerner@debian.org>
Architecture: all
Version: 3.0-12

---

### Post by smaiitm on 2005-11-07
I did not find the Scilab version you have indicated. I may have to look at the respositories again to find that. 

Thanks very much for your reply. It is highly appreciated.

Mahesh

---

### Post by RAOF on 2005-11-07
Have you read the [installing stuff howto]("http://help.ubuntu.com/starterguide/C/ch02.html")?  Installing that version of scilab should be as easy as "apt-get install scilab"

---

### Post by smaiitm on 2005-11-07
I installed Scilab 3.0-12 for the AMD64 OS. It installed the Scilab-bin and the doc files. After installing i tried to run the application. It starts and gives a set of Tamil language fonts and then the run prompt. 

What do i need to do to correct this?

When i try running the application i get this message before Scilab loads:
/usr/bin/scilab: line 31: /usr/lib/pvm3//lib/pvmgetarch: No such file or directory


Thanks for your help.

Mahesh

---

### Post by srott on 2005-11-14
I also have problems with weird fonts (see attached window), i was trying to compile it myself but configure quits with 
```

checking for tcl library tcl.... configure: error: header file tcl.h  has been found for 8.4*  but no corresponding tcl library
```
message.

---

### Post by srott on 2005-11-14
After removing ttf-tamal font scilab uses some readable latin font, still nothing extra but at least works.

---

### Post by kao on 2005-11-15
it doesn't work correctly on my system
segfault (maybe related with scilex 
because it works fine in terminal)

---

### Post by shazihoo on 2006-10-13
Maybe you can try like:
> sudo apt-get remove scilab scilab-bin
sudo apt-get install checkinstall build-essential
cd
wget [http://www.scilab.org/download/stable/scilab-4.0.bin.linux-i686.tar.gz](http://www.scilab.org/download/stable/scilab-4.0.bin.linux-i686.tar.gz)
tar xvfz scilab-4.0.bin.linux-i686.tar.gz
cd scilab-4.0
make
sudo checkinstall
sudo dpkg -i scilab_4.0-1_i386.deb
scilab

---

