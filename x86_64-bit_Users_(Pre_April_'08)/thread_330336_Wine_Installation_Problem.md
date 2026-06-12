---
title: "Wine Installation Problem"
date: 2007-01-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by sarracenia88 on 2007-01-03
I have built a custom wine package for x64 ubuntu as directed by the wine website. When I run make install, the installation runs for a while and then quits, showing the error in the attached picture. I have installed and run wine perfectly with version 9.21. I ran Jedi Academy just fine on it. There seems to be a problem with the wine build.

---

### Post by antgul3382 on 2007-01-04
cant help you there pal but i am lookin for wine  for 64 ubuntu where can i get it???

---

### Post by Azakus on 2007-01-05
I made one for AMD64 following this: [http://wiki.winehq.org/WineOn64bit#head-56206e8bc74083807ffe06ccb471d3f964cb670a](http://wiki.winehq.org/WineOn64bit#head-56206e8bc74083807ffe06ccb471d3f964cb670a)
This is officially for Dapper, but it works on Edgy too.
I would also suggest using checkinstall instead of "make install" in the directions as it packages a .deb file instead of just installing it without a .deb.
I'll post the script I made to do it for me:
(Run the .sh script, not this code. This is just so you know what's in it)
```
#!/bin/bash
sudo aptitude update
sudo aptitude install libfreetype6-dev fontforge gcc flex bison libc6-i386 libc6-dev-i386 checkinstall
cd /usr/lib32
sudo ln -s libX11.so.6 libX11.so
sudo ln -s libXext.so.6 libXext.so
sudo ln -s libfreetype.so.6 libfreetype.so
sudo ln -s libz.so.1 libz.so
sudo ln -s libGL.so.1 libGL.so
sudo ln -s libGLU.so.1 libGLU.so
cd ~
wget http://umn.dl.sourceforge.net/sourceforge/wine/wine-0.9.28.tar.bz2
tar -xjf wine-0.9.28.tar.bz2
cd wine-0.9.28
LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure
make depend
make all
sudo checkinstall
```

---

