---
title: "Linux32 packages"
date: 2004-12-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by litbos on 2004-12-29
Hello,

somody know where i can find the packages linux32 

linux32 can execute ia32 program , i use it on fedora core but i can't find it in ubuntu
i need it to install enemy territory

---

### Post by cybrjackle on 2005-01-01
```

$ sudo apt-cache show linux32
Package: linux32
Priority: extra
Section: universe/utils
Installed-Size: 56
Maintainer: Kurt Roeckx <Q@ping.be>
Architecture: i386
Version: 1-3
Depends: libc6 (>= 2.3.2.ds1-4)
Filename: pool/universe/l/linux32/linux32_1-3_i386.deb
Size: 5208
MD5sum: aaa193a810e46b1f6113420df4abc10a
Description: Wrapper to set the execution domain
 the linux32 tools allows 64bit systems with support for 32 bit
 applications to set the personality to the 32 bit native type.
 .
 For instance, on an amd64 or ia64 machine, commands run with this
 wrapper will think the machine type is i686, as returned by uname -m.
 .
 On systems without support for the PER_LINUX_32 execution domain, this
 program has no effect.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

Means it is in universe, do you have universe in your sources.list

---

### Post by Psy on 2005-01-03
That package is in the i386 repository, and not in x86_64.
I found it availiable for ia64 only (couldnt find a package for amd64), so I just compiled it from source and got ET and Q3A working.

---

### Post by litbos on 2005-01-09
I have compile linux32.c like this :

```
gcc linux32.c -o linux32
``` 

I have put linux32 program in /usr/bin

but when I run ennemy territory program, like this 

```
sudo linux32 ./et-linux-2.55.x86.run
``` 

I have this error

```
./setup.sh: line 278:  4306 Erreur de segmentation  "$setup" "$@" 2>>$NULL
The setup program seems to have failed on x86/glibc-2.0
``` 

Can you tell me how you a made to make it's work with linux32 program

---

### Post by Psy on 2005-01-09
This problem is answered in the ET linux FAQ. You need the 2.56 installer before it will work with linux32.

Edit: You can find it here: [http://www.fileplanet.com/124801/120000/fileinfo/Return-to-Castle-Wolfenstein:-Enemy-Territory-Client-%5BLinux%5D](http://www.fileplanet.com/124801/120000/fileinfo/Return-to-Castle-Wolfenstein:-Enemy-Territory-Client-%5BLinux%5D)

---

### Post by litbos on 2005-01-09
thanks it works ,

but i have some graphical bug , some texture blink , other don't show.

(sorry for my english)

i have an nvidia graphic card (fx5200)

do you have this problem ?

---

### Post by Psy on 2005-01-09
The game runs perfectly for me. 
I have a Geforce 6600 GT card with the latest drivers from nvidia.com (version 1.0.6629). The packages you can download with apt-get is version 1.0.6111, if you use those then maybe you should try the latest.

---

