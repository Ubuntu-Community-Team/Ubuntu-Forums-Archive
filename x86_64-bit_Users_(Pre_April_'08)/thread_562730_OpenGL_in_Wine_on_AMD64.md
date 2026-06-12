---
title: "OpenGL in Wine on AMD64"
date: 2007-09-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by tsh on 2007-09-29
Using the wine package 0.9.45 worked fine for me. It seems that wine 0.9.46 is not yet availible as a package for feisty on 64 bit, so I try building from source.
```
 sudo apt-get build-dep wine
```
got me enough to make the configure script happy, but it tells me
```
configure: WARNING: No OpenGL library found on this system.
Wine will be build without OpenGL or Direct3D support.

configure: WARNING: FreeType development files not found.
Fonts will not be built. Dialog text may be invisible or unaligned.

```
glxgears runs ok, and in /usr/lib32 I have
```
-rw-r--r-- 1 root root    672 2007-09-26 22:34 /usr/lib32/libGL.la
lrwxrwxrwx 1 root root     10 2007-09-23 10:53 /usr/lib32/libGL.so -> libGL.so.1
lrwxrwxrwx 1 root root     18 2007-09-26 22:35 /usr/lib32/libGL.so.1 -> libGL.so.100.14.19
-rw-r--r-- 1 root root 605712 2007-09-26 22:34 /usr/lib32/libGL.so.100.14.19

```
which is the latest nvidia driver. Looking through the config.log, it says it is only looking in the /usr/lib directories for *.so, not the /usr/lib32, despite wine using gcc -m32.

I'm sure it's trivial, but what am I missing?

Thanks,

Sean

---

### Post by tsh on 2007-09-29
Fixed with
```
cd /usr/lib32
sudo ln -s libX11.so.6 libX11.so
sudo ln -s libXext.so.6 libXext.so
sudo ln -s libfreetype.so.6 libfreetype.so
sudo ln -s /usr/lib32/libXrender.so.1 /usr/lib32/libXrender.so
sudo ln -s libGL.so.1 libGL.so
sudo ln -s libGLU.so.1 libGLU.so
```

from
[http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)

---

### Post by Sockerdrickan on 2007-09-29
Works on gutsy?

---

### Post by Kilz on 2007-09-29
> **tsh said:**
> **Using the wine package 0.9.45 worked fine for me**. It seems that wine 0.9.46 is not yet availible as a package for feisty on 64 bit, so I try building from source.


Why did you try building from source? Was it some bug?

---

