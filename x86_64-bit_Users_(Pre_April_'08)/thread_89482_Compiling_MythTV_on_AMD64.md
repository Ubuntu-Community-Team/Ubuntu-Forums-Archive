---
title: "Compiling MythTV on AMD64"
date: 2005-11-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Drain on 2005-11-12
Since the thread that talks about [compiling MythTV under Breezy]("http://www.ubuntuforums.org/showthread.php?t=74660") was originally was under a Hoary Hedgehog thread, I figure I'd start a new one here detailing my problems. 

I attempted to try the following:

**$ sudo apt-get -b source mythtv-frontend**

I got three files: 
mythtv_0.18.1.orig.tar.gz
mythtv_0.18.1-5.dsc
mythtv_0.18.1-5.diff.gz

Here is the result:
```
dpkg-source: extracting mythtv in mythtv-0.18.1
dpkg-source: unpacking mythtv_0.18.1.orig.tar.gz
dpkg-source: applying ./mythtv_0.18.1-5.diff.gz
dpkg-buildpackage: source package is mythtv
dpkg-buildpackage: source version is 0.18.1-5
dpkg-buildpackage: source changed by Matt Zimmerman <mdz@ubuntu.com>
dpkg-buildpackage: host architecture amd64
 debian/rules clean
dh_testdir
dh_testroot
rm -f build-arch-stamp build-indep-stamp
# Add here commands to clean up after the build process.
/usr/bin/make distclean
make[1]: Entering directory `/home/drain/mythtv-0.18.1'
make[1]: *** No rule to make target `distclean'.  Stop.
make[1]: Leaving directory `/home/drain/mythtv-0.18.1'
make: [clean] Error 2 (ignored)
find . -name '.qmake*' | xargs --no-run-if-empty rm -f
rm -f config.mak config.h
rm -rf debian/shlibs.local
dh_clean
 debian/rules build
dh_testdir
if [ $PWD != ${PWD#/usr} ]; then \
        echo "You must not build this package under /usr due to Debian bug #180240" >&2; \
        exit 1; \
fi
CC=gcc-3.4 CXX=g++-3.4 LINK=g++-3.4 ./configure --prefix=/usr \
        --cpu=i486 --tune=pentium4 --enable-mmx \
        --enable-lirc \
        --enable-audio-alsa \
        --enable-audio-oss \
        --enable-audio-jack \
        --enable-audio-arts \
        --enable-opengl-vsync \
        --enable-dvb \
        --dvb-path=/usr/include \
        --enable-firewire \
        --enable-ivtv \
        --enable-joystick-menu
ERROR: CPU specific ./configure options failed compile test
       Removing CPU specific compilation options. (-mcpu=i486 -mtune=pentium4)

# Basic Settings
Compile type     release
Compiler cache   no
DistCC           no
Install prefix   /usr
CPU              x86 (i486)
Big Endian       no
MMX enabled      yes
Vector Builtins  yes

# Input Support
Joystick menu    yes
lirc support     yes
ivtv support     yes
FireWire support no
DVB support      yes [/usr/include]

# Sound Output Support
OSS support      yes
ALSA support     yes
aRts support     no
JACK support     no

# Video Output Support
x11 support      yes
xrandr support   no
xv support       yes
XvMC support     no
XvMC VLD support no
OpenGL vsync     yes
DirectFB         no

Creating config.mak and config.h
CC=gcc-3.4 CXX=g++-3.4 LINK=g++-3.4 qmake -o Makefile PREFIX=/usr mythtv.pro
dh_testdir
/usr/bin/make CC=gcc-3.4 CXX=g++-3.4 LINK=g++-3.4
make[1]: Entering directory `/home/drain/mythtv-0.18.1'
cd libs && qmake libs.pro "PREFIX=/usr" -o Makefile
cd libs && /usr/bin/make -f Makefile
make[2]: Entering directory `/home/drain/mythtv-0.18.1/libs'
cd libavcodec && qmake libavcodec.pro "PREFIX=/usr" -o Makefile
cd libavcodec && /usr/bin/make -f Makefile
make[3]: Entering directory `/home/drain/mythtv-0.18.1/libs/libavcodec'
gcc-3.4 -c -pipe -w -O3 -Wall -Wno-switch -fomit-frame-pointer -D_REENTRANT -DPIC -fPIC  -DMMX -Di386 -DUSING_IVTV -DUSING_DVB -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -DPREFIX=\"/usr\" -DHAVE_AV_CONFIG_H -D_LARGEFILE_SOURCE -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I.. -I../.. -I/usr/include/qt3 -o utils.o utils.c
gcc-3.4 -c -pipe -w -O3 -Wall -Wno-switch -fomit-frame-pointer -D_REENTRANT -DPIC -fPIC  -DMMX -Di386 -DUSING_IVTV -DUSING_DVB -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -DPREFIX=\"/usr\" -DHAVE_AV_CONFIG_H -D_LARGEFILE_SOURCE -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I.. -I../.. -I/usr/include/qt3 -o mem.o mem.c
gcc-3.4 -c -pipe -w -O3 -Wall -Wno-switch -fomit-frame-pointer -D_REENTRANT -DPIC -fPIC  -DMMX -Di386 -DUSING_IVTV -DUSING_DVB -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -DPREFIX=\"/usr\" -DHAVE_AV_CONFIG_H -D_LARGEFILE_SOURCE -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I.. -I../.. -I/usr/include/qt3 -o allcodecs.o allcodecs.c
gcc-3.4 -c -pipe -w -O3 -Wall -Wno-switch -fomit-frame-pointer -D_REENTRANT -DPIC -fPIC  -DMMX -Di386 -DUSING_IVTV -DUSING_DVB -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -DPREFIX=\"/usr\" -DHAVE_AV_CONFIG_H -D_LARGEFILE_SOURCE -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I.. -I../.. -I/usr/include/qt3 -o mpegvideo.o mpegvideo.c
mpegvideo.c: In function `ff_copy_bits':
mpegvideo.c:26: error: extended registers have no high halves
{standard input}: Assembler messages:
{standard input}:15149: Error: bad register name `%'
make[3]: *** [mpegvideo.o] Error 1
make[3]: Leaving directory `/home/drain/mythtv-0.18.1/libs/libavcodec'
make[2]: *** [sub-libavcodec] Error 2
make[2]: Leaving directory `/home/drain/mythtv-0.18.1/libs'
make[1]: *** [sub-libs] Error 2
make[1]: Leaving directory `/home/drain/mythtv-0.18.1'
make: *** [build-arch-stamp] Error 2
Build command 'cd mythtv-0.18.1 && dpkg-buildpackage -b -uc' failed.
E: Child process failed

```

When I try and go back and follow jimbolaya's instructions, I find that I've already got the mythtv-0.18.1 directory untar'd in my home directory, so I skip on to the next command:

**$ sudo gzip -dc mythtv_0.18.1-5.diff.gz | sudo patch -p1**

and get the result:

```
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- mythtv-0.18.1.orig/settings.pro
|+++ mythtv-0.18.1/settings.pro
--------------------------
File to patch:
```

I then tell the patch program which files to patch (I'm making the assumption that the ones with the +++ in front are the ones I should patch? There are 4 of them, I believe), and get a message stating that the patches have failed at the end. 

At this point, I have no idea where and how to troubleshoot this. Anyone have some suggestions or alternate solutions that I'm missing? Please, point out where I'm going wrong! :-)

---

### Post by RAOF on 2005-11-12
At least one reason why the patch won't apply is that it has **already** been applied by the "apt-get -b source mythtv".  That's the reason why the rest of the instructions don't work.

However, you should be able to edit the debian/rules as in the first post of that thread to get the source to compile.  Just modify the debian/rules file, go back to the directory containing the mythtv-0.18.1 directory, and run apt-get -b source mythtv again.

---

### Post by Drain on 2005-11-13
[QUOTE=RAOF]At least one reason why the patch won't apply is that it has **already** been applied by the "apt-get -b source mythtv".  That's the reason why the rest of the instructions don't work.

However, you should be able to edit the debian/rules as in the first post of that thread to get the source to compile.  Just modify the debian/rules file, go back to the directory containing the mythtv-0.18.1 directory, and run apt-get -b source mythtv again.[/QUOTE]

I got it going after re-reading the steps.  I guess I was just unclear about the changes I was supposed to make to the debian/rules file.  ( changing the line  "cpu=i486 --tune=pentium4 --enable-mmx \" to "cpu=x86_64 --tune=generic --enable-mmx \" and then commenting out "# --enable-opengl-vsync \") 

I then went back and tried to follow the step: **dpkg-buildpackage -rfakeroot -b** and got a "Permission Denied Error", before going back and doing **$ apt-get -b source mythtv** and getting it right. 

Now on to the challenge of getting the mythplugins and mythweb to work. :-)

---

### Post by RAOF on 2005-11-13
I think the correct versions of those are in the repository.  It might be a good idea to try that first :)

---

