---
title: "MythTV 0.18.1 for Hoary amd64"
date: 2005-10-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by jimbolaya on 2005-10-12
I got tired of waiting for MythTV 0.18.1 for Hoary amd64, so I went ahead and grabbed the sources from [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) and made the debs myself.  I changed a few things to get it to compile.  

root@dvrsrvr:/opt/mythtv-0.18 # diff rules rules.orig 
28c28
<               --cpu=x86_64 --tune=generic --enable-mmx \
---
>               --cpu=i486 --tune=pentium4 --enable-mmx \
34c34
< #             --enable-opengl-vsync \
---
>               --enable-opengl-vsync \

I kept getting an error witht he opengl-vsync.  I think that's because I'm using the nVidia proprietary drivers.  Those libraries are pretty closed and don't match the mesa stuff very well.  Since I was compiling this for the backend, I didn't really care much about that anyway.  Also there doesn't seem to be any tuning rules specifically for the amd64.  

Please let me know if I should submit these packages somewhere.  If someone wants them, please contact me and I'd be happy to send them to you, with of course the caveat that your mileage may vary.

James

---

### Post by FluffyElmo on 2005-10-12
I recently compiled MythTV 18.x with the Nvidia drivers and didn't get this error. However I used the cvs version from a few weeks ago and I had  a few options set in my xorg.conf and Nvidia settings relating to vsync and OpenGL.

I don't have access to the box right this moment, but if your interested I could get the exact versions and settings later today.

---

### Post by FluffyElmo on 2005-10-12
Sorry! Just realized there is one *big* difference I forgot. I'm actually using Breezy amd64 on my MythTV box so that might explain all on it's own.

---

### Post by jimbolaya on 2005-10-12
I'm not sure how much the Hoary vs Breezy thing matters in terms of compiling from source.  Not much I'm pretty sure.  I'm still trying to get Xorg running on the box.  For some reason the 32-bit compatability GL libraries, which seem to compile fine, make the NVIDIA installer barf.

I also might have a broken video card, since X tends to freeze or not work completely when I try to start it.  I also can't switch back to a tty after I start X.  I'll have to look in the conf file to make sure it's not blocking the console switching.  I hate coming up with an xorg/xfree86 conf file from scratch.  Is yours generic enough that I might be able to use it?

Thanks.
James

---

### Post by FluffyElmo on 2005-10-12
I didn't install the 32bit OpenGL compatability libraries because I'd read they cause problems. OpenGL seems to work just fine in any games I've tried anyways. 

I had some problems with X freezing and being unable to switch to a tty as well until I got my Nvidia drivers working properly. I followed this guide to get my Nividia card running, it may help you as well:
[http://ubuntuforums.org/showthread.php?t=57368]("http://ubuntuforums.org/showthread.php?t=57368")

My Xorg.conf is fairly generic, I'm running a Nvidia 6600GT with Xinerama and TV-Out as the second display. I can post it this evening if you don't make any headway before then.

It works, though my MythTV front-end playback has minor artifacts (tearing mostly) on scenes with slow pans. Haven't had the time to fully debug it, and I have a dedicated box with a Nvidia 4400mx to try when I find time anyways.

Good Luck!

---

### Post by Joshua on 2005-10-13
Could one of you show me the commands you used to compile MythTV.  I'm running Breezy and I was hoping the MythTV packaging would be done by the time it was released, but it still wouldn't install this morning.  I've never been able to get anything to compile.

---

### Post by jimbolaya on 2005-10-13
After you've downloaded mythtv_0.18.1-5.diff.gz, mythtv_0.18.1-5.dsc, mythtv_0.18.1.orig.tar.gz unpack the tar.gz, then patch it with the diff:

```
cd <path>
tar -xzvf mythtv_0.18.1.orig.tar.gz
cd mythtv-0.18.1
gzip -dc mythtv_0.18.1-5.diff.gz | patch -p1
```

Go to the debian subdirectory and edit the rules file as directed above.  My first go around, I had trouble with the --enable-opengl-vsync option so I disabled it, ymmv.  Go back up to the base directory (<path>/mythtv_0.18.1) and run:

```
dpkg-buildpackage -rfakeroot -b
```

If there are no errors and it finished compiling, you should see a boatload of debs in <path>.  Don't build it anywhere in /usr (as in /usr/src), it won't build and it says there's a bug if you try to build it somewhere in /usr.  I just made a directory in /opt to build it.

Good luck.

---

### Post by Joshua on 2005-10-14
Well thanks!  Seriously, I think this is one of two times that I've been able to get something to compile!  It took a lot of installing dependencies and stuff, but then it worked.  I think it might not be worth the effort though :-(

After I got it up and running, there was very little performance increase and it didn't come with MythMusic, or MythDVD, etc.  I think I may just reinstall with i386 until someone has it up and running for AMD64.

---

### Post by FluffyElmo on 2005-10-14
If you got the main Myth distro running, you should be able to compile Myth-plugins and Myth-themes the same way. Once I got the front/backend compiled getting Myth-game/weather/news/etc running compiled from source was easy.

Alternately you may also want to check the Breezy repositories, most of the Myth packages are at version 18.1 whith only the frontend being 17.x if I remember correctly. So if you built the frontend deb from source you should just be able to install the rest via Synaptic.

Not certain if it'll work, as I said I compiled everything from source...but don't see why it wouldn't.

---

### Post by jimbolaya on 2005-10-14
[QUOTE=Joshua]After I got it up and running, there was very little performance increase and it didn't come with MythMusic, or MythDVD, etc.  I think I may just reinstall with i386 until someone has it up and running for AMD64.[/QUOTE]

I'm not really doing for the performance difference.  I don't really want to muck around with the 32bit compatability libraries.  One more level of complexity I don't need to deal with.

James

---

### Post by Drain on 2005-10-22
Out of the people who got this working on their machines, are their any of you who are willing to write up a complete noob-ified How-To on the process? I'm sure it would be appreciated by the MythTV and Ubuntu-64bit communities. :-)

---

### Post by Drain on 2005-11-12
This is an attempt to get my request moved along a little further. :-) 

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

### Post by Fry-kun on 2005-12-18
If you see a "debian/rules: Permission denied" error while trying to compile, it means the patch process didn't set the proper flags on the debian/rules file.
Try
$ chmod +x debian/rules

---

