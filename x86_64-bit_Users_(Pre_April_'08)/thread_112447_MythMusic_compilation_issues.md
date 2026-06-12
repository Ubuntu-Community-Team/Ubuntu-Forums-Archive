---
title: "MythMusic compilation issues"
date: 2006-01-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by t0bb3 on 2006-01-04
I'm trying to compile the MythMusic plugin, but get a lot of errors. Can someone please help me fix them?

> htpc@htpc:/opt/mythplugins-0.18.1$ sudo dpkg-buildpackage -rfakeroot -b
dpkg-buildpackage: source package is mythplugins
dpkg-buildpackage: source version is 0.18.1-3
dpkg-buildpackage: source changed by Fabio M. Di Nitto <fabbione@ubuntu.com>
dpkg-buildpackage: host architecture amd64
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp
# Add here commands to clean up after the build process.
/usr/bin/make distclean
make[1]: Entering directory `/opt/mythplugins-0.18.1'
make[1]: *** No rule to make target `distclean'.  Stop.
make[1]: Leaving directory `/opt/mythplugins-0.18.1'
make: [clean] Error 2 (ignored)
find . -name '.qmake*' | xargs --no-run-if-empty rm -f
rm -f config.mak config.h
rm -f debian/shlibs.local
dh_clean
 debian/rules build
dh_testdir
if [ $PWD != ${PWD#/usr} ]; then \
        echo "You must not build this package under /usr due to Debian bug #1802 40" >&2; \
        exit 1; \
fi
CC=gcc-3.4 CXX=g++-3.4 LINK=g++-3.4 ./configure --prefix=/usr --enable-opengl -- disable-mythgame --disable-mythphone --enable-mythgallery --enable-mythmusic --e nable-mythbrowser --enable-aac --enable-fftw --compile-type=debug

Configuration settings:

        MythBrowser   plugin will be built
        MythDVD       plugin will be built
        MythGallery   plugin will be built
        MythGame      plugin will not be built
        MythMusic     plugin will be built
        MythNews      plugin will be built
        MythPhone     plugin will not be built
        MythVideo     plugin will be built
        MythWeather   plugin will be built
        Transcode     support will not be included in MythDVD
        VCD           support will not be included in MythDVD
        OpenGL        support will be included in MythGallery
        EXIF          support will not be included in MythGallery
        OpenGL        support will be included in MythMusic
        FFTW          support will be included in MythMusic
        SDL           support will not be included in MythMusic
        AAC           support will be included in MythMusic

CC=gcc-3.4 CXX=g++-3.4 LINK=g++-3.4 qmake -o Makefile PREFIX=/usr mythplugins.pr o
dh_testdir
/usr/bin/make CC=gcc-3.4 CXX=g++-3.4 LINK=g++-3.4
make[1]: Entering directory `/opt/mythplugins-0.18.1'
cd mythbrowser && qmake mythbrowser.pro "PREFIX=/usr" -o Makefile
cd mythbrowser && /usr/bin/make -f Makefile
make[2]: Entering directory `/opt/mythplugins-0.18.1/mythbrowser'
cd mythbrowser && qmake mythbrowser.pro "PREFIX=/usr" -o Makefile
cd mythbrowser && /usr/bin/make -f Makefile
make[3]: Entering directory `/opt/mythplugins-0.18.1/mythbrowser/mythbrowser'
g++-3.4 -c -pipe -Wall -W -O3 -march=pentiumpro -fomit-frame-pointer -D_REENTRAN T  -D_GNU_SOURCE -DPREFIX=\"/usr\" -DHAVE_MMX -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/incl ude -I/usr/include/kde -I/opt/kde3/include -I/usr/include/qt3 -o main.o main.cpp
main.cpp:1: error: CPU you selected does not support x86-64 instruction set
main.cpp:1: error: CPU you selected does not support x86-64 instruction set
make[3]: *** [main.o] Error 1
make[3]: Leaving directory `/opt/mythplugins-0.18.1/mythbrowser/mythbrowser'
make[2]: *** [sub-mythbrowser] Error 2
make[2]: Leaving directory `/opt/mythplugins-0.18.1/mythbrowser'
make[1]: *** [sub-mythbrowser] Error 2
make[1]: Leaving directory `/opt/mythplugins-0.18.1'
make: *** [build-stamp] Error 2
I got all the files from [http://packages.ubuntu.com/breezy/sound/mythmusic](http://packages.ubuntu.com/breezy/sound/mythmusic)

Thanks

---

### Post by Pridkett on 2006-01-06
open up settings.pro and comment out the line that says "remove for x86-64", I believe it's "DEFINES += HAVE_MMX"

you'll still get a few more issues, but most are easy to deal with.

---

### Post by t0bb3 on 2006-01-16
Yes, thank you, I have solved it

---

