---
title: "trouble compiling wine"
date: 2007-12-17
forum: Wine
---

### Post by dawp on 2007-12-17
When I try to ./configure wine i get:

configure: WARNING: No OpenGL library found on this system.
Wine will be built without OpenGL or Direct3D support.

configure: WARNING: FreeType development files not found.
Fonts will not be built. Dialog text may be invisible or unaligned.

this on a x86_64 7.10 with a nvidia 6800gt and i have the restricted drivers installed.

I know that there's a package available, but the game i'm installing requires a patch to work properly.

I've followed the instructions here but it doesn't get me any farther:

edit: I'm not worried about the freetype error as it doesn't matter much to me if i see the type or not, but i did try to fine that package anyways.


[http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)

---

### Post by CarpKing on 2007-12-17
Do you have all the OpenGL -dev packages?  That might be your problem.  Did you already do "sudo apt-get build-dep wine"?

---

### Post by dawp on 2007-12-17
apt get build-dep wine was one of the first things i did and i have libghc6-opengl-dev installed

---

### Post by yabbadabbadont on 2007-12-17
Just to be sure, see if you have mesa-common-dev installed.

---

### Post by YokoZar on 2007-12-17
You didn't make the links to the 32 bit libs properly.

---

### Post by dawp on 2007-12-17
got it to configure correctly, they had

CC="gcc-4.2 -m32" LDFLAGS="-L/lib32 -L/usr/lib32 -L`pwd`/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" 

and ./configure on next line instead of 

CC="gcc-4.2 -m32" LDFLAGS="-L/lib32 -L/usr/lib32 -L`pwd`/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure; as it should have been and was later in the day.

---

