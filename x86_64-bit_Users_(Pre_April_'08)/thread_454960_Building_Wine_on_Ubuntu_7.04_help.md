---
title: "Building Wine on Ubuntu 7.04 help"
date: 2007-05-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Warsaw on 2007-05-26
Well this is the guid on the wine site and I got threw most of it. I got to this part :When you run configure, do it like: ./configure > configoutput.txt Then cat configoutput.txt | grep soname, and you'll find a bunch of sonames of the form *.so rather than, say, *.so.1 -- these are likely libraries linked to the 64 bit version. I don't know what not having a hand-created symlink in /usr/lib32 will do here.

Run configure, build and install with:

./configure
make 
sudo make install

Dont know what exactly they want me to do. I tryed ./configure but it didnt work anyone help me out from the config part on ?





Building Wine on Ubuntu / Kubuntu 7.04 (Feisty Fawn)

Warning: Wine will not compile if you install libicu34-dev listed at Recommended Packages on 32bit. No bi-directional text support. However, see below for a potential solution.

First one must install the necessary libraries: Finding the correct set may take a few minutes and several tries.

sudo apt-get install libfreetype6-dev fontforge ia32-libs

There are others to be gotten by hand. I did them by installing the various -dev packages in the 32-bit packages build dependency.

Make sure you have the following packages installed:

sudo apt-get install gcc flex bison libc6-i386 libc6-dev-i386 lib32z1-dev

Now add the following links that the library install does not make:

cd /usr/lib32
sudo ln -s libX11.so.6 libX11.so
sudo ln -s libXext.so.6 libXext.so
sudo ln -s libfreetype.so.6 libfreetype.so

Others that may be needed:

sudo ln -s /usr/lib32/libXrender.so.1 /usr/lib32/libXrender.so
sudo ln -s libGL.so.1 libGL.so
sudo ln -s libGLU.so.1 libGLU.so

When you run configure, do it like: ./configure > configoutput.txt Then cat configoutput.txt | grep soname, and you'll find a bunch of sonames of the form *.so rather than, say, *.so.1 -- these are likely libraries linked to the 64 bit version. I don't know what not having a hand-created symlink in /usr/lib32 will do here.

Run configure, build and install with:

./configure
make 
sudo make install

If all needed libraries are present there will be no missing-library warnings or errors anywhere.

If you have the libicu36-dev package installed, it will confuse the build process unless you add the following to your CONFFLAGS:

CONFFLAGS += ICU_LIB_DIR=/usr/lib32

wine seems to work (installed in /usr/local)

---

### Post by tgm4883 on 2007-05-26
In case you wanted to know, you can get the 64-bit deb here
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by Warsaw on 2007-05-26
Thanks that sounds alot easyer. Easy to install to. But all the commands I did before how do I delete everything I didnt since I dont want trash directories or files that are uneeded

---

