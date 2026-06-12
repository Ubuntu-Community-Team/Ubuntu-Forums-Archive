---
title: "[SOLVED] Gambas2 64 bit doesnt work so what's the solution?"
date: 2007-11-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Creative2 on 2007-11-07
we have developed an interfaces( [http://ubuntuforums.org/showthread.php?t=567016](http://ubuntuforums.org/showthread.php?t=567016) ) to convert photo video and etc, unluckly it is based on gambas2 and this pack cannot be used into 64 bit systems  because it has some problems.

i am in 32 bit system so.... someone could  tell me how to compile 32bit gambas2 into 64 bit system ?????

---

### Post by damvcoool on 2007-11-07
why not just Gambas, it is avalible for 64.

---

### Post by Darll on 2008-01-29
The True is, that i almost success to compile it.
i use that code:
```

sudo apt-get install libxcomposite-dev gcc-4.2-multilib 
mkdir -p `pwd`/lib32
ln -s /usr/lib32/libX11.so.6 `pwd`/lib32/libX11.so
ln -s /usr/lib32/libXext.so.6 `pwd`/lib32/libXext.so
ln -s /usr/lib32/libfreetype.so.6 `pwd`/lib32/libfreetype.so
ln -s /usr/lib32/libfontconfig.so.1 `pwd`/lib32/libfontconfig.so
ln -s /usr/lib32/libGL.so.1 `pwd`/lib32/libGL.so
ln -s /usr/lib32/libGLU.so.1 `pwd`/lib32/libGLU.so
ln -s /usr/lib32/libXrender.so.1 `pwd`/lib32/libXrender.so
ln -s /usr/lib32/libXinerama.so.1 `pwd`/lib32/libXinerama.so
ln -s /usr/lib32/libXi.so.6 `pwd`/lib32/libXi.so
ln -s /usr/lib32/libXrandr.so.2 `pwd`/lib32/libXrandr.so
ln -s /usr/lib32/liblcms.so.1 `pwd`/lib32/liblcms.so
ln -s /usr/lib32/libcrypto.so.0.9.8 `pwd`/lib32/libcrypto.so
ln -s /usr/lib32/libssl.so.0.9.8 `pwd`/lib32/libssl.so
ln -s /usr/lib32/libxml2.so.2 `pwd`/lib32/libxml2.so
ln -s /usr/lib32/libjpeg.so.62 `pwd`/lib32/libjpeg.so
ln -s /usr/lib32/libXcomposite.so.1 `pwd`/lib32/libXcomposite.so
ln -s /usr/lib32/libcups.so.2 `pwd`/lib32/libcups.so
ln -s /usr/lib32/libXcursor.so.1 `pwd`/lib32/libXcursor.so
ln -s /usr/lib32/libsane.so.1 `pwd`/lib32/libsane.so
ln -s /usr/lib32/libhal.so.1 `pwd`/lib32/libhal.so
ln -s /usr/lib32/libpng12.so.0 `pwd`/lib32/libpng.so
ln -s /usr/lib32/libgphoto2.so.2 `pwd`/lib32/libgphoto2.so
ln -s /usr/lib32/libgphoto2_port.so.0 `pwd`/lib32/libgphoto2_port.so
ln -s /usr/lib32/libldap.so.2 `pwd`/lib32/libldap.so
ln -s /usr/lib32/libldap_r.so.2 `pwd`/lib32/libldap_r.so
ln -s /usr/lib32/liblber.so.2 `pwd`/lib32/liblber.so
ln -s /usr/lib32/libxslt.so.1 `pwd`/lib32/libxslt.so

 ./configure CC="gcc-4.2 -m32" LDFLAGS="-L/lib32 -L/usr/lib32 -L`pwd`/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32"
make

```
Like i use for compile wine.

now the problem is
```

CImage.lo -MD -MP -MF .deps/gb_image_la-CImage.Tpo -c CImage.cpp  -fPIC -DPIC -o .libs/gb_image_la-CImage.o
CImage.cpp:332: error: cast from 'const char*' to 'int' loses precision
CImage.cpp:333: error: cast from 'const char*' to 'int' loses precision
CImage.cpp:334: error: cast from 'const char*' to 'int' loses precision
CImage.cpp:335: error: cast from 'const char*' to 'int' loses precision
CImage.cpp:336: error: cast from 'const char*' to 'int' loses precision
CImage.cpp:337: error: cast from 'const char*' to 'int' loses precision
CImage.cpp:338: error: cast from 'const char*' to 'int' loses precision
CImage.cpp:339: error: cast from 'const char*' to 'int' loses precision
CImage.cpp:341: error: cast from 'const char*' to 'int' loses precision
CImage.cpp:342: error: cast from 'const char*' to 'int' loses precision
CImage.cpp:343: error: cast from 'const char*' to 'int' loses precision
CImage.cpp:344: error: cast from 'const char*' to 'int' loses precision
CImage.cpp:346: error: cast from 'const char*' to 'int' loses precision
CImage.cpp:347: error: cast from 'const char*' to 'int' loses precision
CImage.cpp:348: error: cast from 'const char*' to 'int' loses precision
CImage.cpp:349: error: cast from 'const char*' to 'int' loses precision
CImage.cpp:350: error: cast from 'const char*' to 'int' loses precision
CImage.cpp:351: error: cast from 'const char*' to 'int' loses precision
CImage.cpp:353: error: cast from 'void*' to 'int' loses precision
CImage.cpp:353: error: cast from 'void (*)(void*, void*)' to 'int' loses precision
CImage.cpp:353: error: cast from 'void*' to 'int' loses precision
CImage.cpp:355: error: cast from 'void*' to 'int' loses precision
CImage.cpp:355: error: cast from 'void (*)(void*, void*)' to 'int' loses precision
CImage.cpp:355: error: cast from 'void*' to 'int' loses precision
CImage.cpp:356: error: cast from 'void*' to 'int' loses precision
CImage.cpp:356: error: cast from 'void (*)(void*, void*)' to 'int' loses precision
CImage.cpp:356: error: cast from 'void*' to 'int' loses precision
CImage.cpp:357: error: cast from 'void*' to 'int' loses precision
CImage.cpp:357: error: cast from 'void (*)(void*, void*)' to 'int' loses precision
CImage.cpp:357: error: cast from 'void*' to 'int' loses precision
CImage.cpp:358: error: cast from 'void*' to 'int' loses precision
CImage.cpp:358: error: cast from 'void (*)(void*, void*)' to 'int' loses precision
CImage.cpp:358: error: cast from 'void*' to 'int' loses precision
CImage.cpp:359: error: cast from 'void*' to 'int' loses precision
CImage.cpp:359: error: cast from 'void (*)(void*, void*)' to 'int' loses precision
CImage.cpp:359: error: cast from 'void*' to 'int' loses precision
CImage.cpp:360: error: cast from 'void*' to 'int' loses precision
CImage.cpp:360: error: cast from 'void (*)(void*, void*)' to 'int' loses precision
CImage.cpp:360: error: cast from 'void*' to 'int' loses precision
CImage.cpp:361: error: cast from 'void*' to 'int' loses precision
CImage.cpp:361: error: cast from 'void (*)(void*, void*)' to 'int' loses precision
CImage.cpp:361: error: cast from 'void*' to 'int' loses precision
CImage.cpp:362: error: cast from 'void*' to 'int' loses precision
CImage.cpp:362: error: cast from 'void (*)(void*, void*)' to 'int' loses precision
CImage.cpp:362: error: cast from 'void*' to 'int' loses precision
CImage.cpp:363: error: cast from 'void*' to 'int' loses precision
CImage.cpp:363: error: cast from 'void (*)(void*, void*)' to 'int' loses precision
CImage.cpp:363: error: cast from 'void*' to 'int' loses precision
CImage.cpp:364: error: cast from 'void*' to 'int' loses precision
CImage.cpp:364: error: cast from 'void (*)(void*, void*)' to 'int' loses precision
CImage.cpp:364: error: cast from 'void*' to 'int' loses precision
CImage.cpp:365: error: cast from 'void*' to 'int' loses precision
CImage.cpp:365: error: cast from 'void (*)(void*, void*)' to 'int' loses precision
CImage.cpp:365: error: cast from 'void*' to 'int' loses precision
CImage.cpp:367: error: cast from 'void*' to 'int' loses precision
CImage.cpp:367: error: cast from 'void (*)(void*, void*)' to 'int' loses precision
CImage.cpp:367: error: cast from 'void*' to 'int' loses precision
CImage.cpp:368: error: cast from 'void*' to 'int' loses precision
CImage.cpp:368: error: cast from 'void (*)(void*, void*)' to 'int' loses precision
CImage.cpp:368: error: cast from 'void*' to 'int' loses precision
CImage.cpp:369: error: cast from 'void*' to 'int' loses precision
CImage.cpp:369: error: cast from 'void (*)(void*, void*)' to 'int' loses precision
CImage.cpp:369: error: cast from 'void*' to 'int' loses precision
CImage.cpp:370: error: cast from 'void*' to 'int' loses precision
CImage.cpp:370: error: cast from 'void (*)(void*, void*)' to 'int' loses precision
CImage.cpp:370: error: cast from 'void*' to 'int' loses precision
CImage.cpp:371: error: cast from 'void*' to 'int' loses precision
CImage.cpp:371: error: cast from 'void (*)(void*, void*)' to 'int' loses precision
CImage.cpp:371: error: cast from 'void*' to 'int' loses precision
CImage.cpp:372: error: cast from 'void*' to 'int' loses precision
CImage.cpp:372: error: cast from 'void (*)(void*, void*)' to 'int' loses precision
CImage.cpp:372: error: cast from 'void*' to 'int' loses precision
CImage.cpp:373: error: cast from 'void*' to 'int' loses precision
CImage.cpp:373: error: cast from 'void (*)(void*, void*)' to 'int' loses precision
CImage.cpp:373: error: cast from 'void*' to 'int' loses precision
CImage.cpp:374: error: cast from 'void*' to 'int' loses precision
CImage.cpp:374: error: cast from 'void (*)(void*, void*)' to 'int' loses precision
CImage.cpp:374: error: cast from 'void*' to 'int' loses precision
CImage.cpp:375: error: cast from 'void*' to 'int' loses precision
CImage.cpp:375: error: cast from 'void (*)(void*, void*)' to 'int' loses precision
CImage.cpp:375: error: cast from 'void*' to 'int' loses precision
CImage.cpp:376: error: cast from 'void*' to 'int' loses precision
CImage.cpp:376: error: cast from 'void (*)(void*, void*)' to 'int' loses precision
CImage.cpp:376: error: cast from 'void*' to 'int' loses precision
CImage.cpp:377: error: cast from 'void*' to 'int' loses precision
CImage.cpp:377: error: cast from 'void (*)(void*, void*)' to 'int' loses precision
CImage.cpp:377: error: cast from 'void*' to 'int' loses precision
CImage.cpp:378: error: cast from 'void*' to 'int' loses precision
CImage.cpp:378: error: cast from 'void (*)(void*, void*)' to 'int' loses precision
CImage.cpp:378: error: cast from 'void*' to 'int' loses precision
CImage.cpp:379: error: cast from 'void*' to 'int' loses precision
CImage.cpp:379: error: cast from 'void (*)(void*, void*)' to 'int' loses precision
CImage.cpp:379: error: cast from 'void*' to 'int' loses precision

```
anyway, i still  thinking that it's possible to compile it, i just need to find the Solution. 
If I will not find, i compile it in 34-bit computer and then i will make a packages. and then i will install it in my 64-bit computer.

---

### Post by Creative2 on 2008-01-30
i know now gambas works in 64 sistems :)

---

### Post by damvcoool on 2008-02-27
Gambas2 now compiles on 64 bit ubuntu. and works!!!!

download the latest version and compile it.

make sure you get all the required library before compiling.

---

