---
title: "little mplayer 32bit without chroot howto"
date: 2005-10-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by gorod on 2005-10-07
I recently tried latest ubunty and liked it much but was pretty disappointed by lack of 32bit compatibility which is in my opinion not so hard to implement. Here is what i did to make most of 32bit applications work, especially mplayer and wine. 

1)Go to [http://www.gentoo.org/main/en/mirrors.xml](http://www.gentoo.org/main/en/mirrors.xml) and
select a mirror , then browse into distfiles and get latest mplayer-bin , emul-linux-x86-medialibs , *-soundlibs, *-sdl, *-compat, *-xlibs and *-baselibs. 

All needed emul libs are ~10mb alltogether so it's much better than a separate chroot. Btw for people who want to use opera with shared qt libs you can also get emul-linux-x86-qtlibs there.

2) Extract the contents of mplayer-bin in /opt . Extract all emul files to some folder , then browse into emul/linux/x86/usr/lib32 and copy everything there in your own /usr/lib32. Reinstall nvidia-glx, nvidia-kernel (cause some 32bit glx files are getting overwritten). 

3)run ldconfig

4) make a link from mplayer-bin executable to gmplayer so it'l start in graphical mode and link it to /usr/bin.

for 32bit codecs:
 
1) go to mplayer web site->download->codecs->other binary codec packages->all-20050412.tar.bz2
or newer.

2)extract that file somewhere , change to all- directory and copy everything inside to /usr/lib/win32.
It should be working from now on.

edit: 
I tried it with breezy. 
edit2: fixed some errors.

---

### Post by nwillis on 2005-10-08
Wow.  Have you thought of packaging that and making it available?

---

### Post by gorod on 2005-10-08
Here's the script , hope it works. If it does mention it here. It's also a swedish gentoo mirror, you can choose anothre one by changing the mirror var in this script. 
```

#!/bin/bash
echo --------------------------------------
echo you have to be root to run this skript
echo --------------------------------------

MIRROR=http://linuv.uv.es/mirror/gentoo/distfiles
cd ~
mkdir tmp
cd tmp
wget ${MIRROR}/emul-linux-x86-baselibs-2.3.tar.bz2 
wget ${MIRROR}/emul-linux-x86-compat-1.0.tar.bz2 
wget ${MIRROR}/emul-linux-x86-medialibs-1.1.tar.bz2 
wget ${MIRROR}/emul-linux-x86-sdl-2.2.tar.bz2 
wget ${MIRROR}/emul-linux-x86-soundlibs-2.1.tar.bz2
wget ${MIRROR}/emul-linux-x86-xlibs-2.1.tar.bz2
tar -jxf emul-linux-x86-baselibs-2.3.tar.bz2 
tar -jxf emul-linux-x86-compat-1.0.tar.bz2 
tar -jxf emul-linux-x86-medialibs-1.1.tar.bz2 
tar -jxf emul-linux-x86-sdl-2.2.tar.bz2 
tar -jxf emul-linux-x86-soundlibs-2.1.tar.bz2
tar -jxf emul-linux-x86-xlibs-2.1.tar.bz2
cd ./emul/linux/x86/lib
cp -rf * /lib32
cd ../usr/lib
cp -rf * /usr/lib32

echo -----------------
echo installing codecs
echo -----------------
cd ~/tmp
wget http://www1.mplayerhq.hu/MPlayer/releases/codecs/all-20050412.tar.bz2
tar -jxf all-20050412.tar.bz2
cd all-20050412
mkdir /usr/lib/win32
cp * /usr/lib/win32

cd /
echo -------------------
echo getting mplayer-bin
echo -------------------

wget ${MIRROR}/mplayer-bin-1.0_pre7-r2.tar.bz2  
tar -jxf mplayer-bin-1.0_pre7-r2.tar.bz2  


ln -sf /opt/mplayer-bin/bin/mplayer-bin /usr/bin/gmplayer

ldconfig

rm -rf ~/tmp
rm /mplayer-bin-1.0_pre7-r2.tar.bz2

echo -------------------------------------------------
echo use "gmplayer" to start mplayer in graphical mode
echo tested on breezy amd64
echo -------------------------------------------------

```

---

### Post by mterlouw on 2005-10-09
Thanks for posting this. When running the script, I got:

ln: `/usr/bin/gmplayer': File exists

Maybe need ln -sf ?

Also, when running /usr/bin/mplayer-bin, I get:

/opt/mplayer-bin/bin/mplayer-bin: error while loading shared libraries: libgpm.so.1: cannot open shared object file: No such file or directory

Any ideas?

---

### Post by gorod on 2005-10-09
Yeah, you are right ln -sf.

Looks like gpm is in emul/linux/x86/lib (not usr/lib) so i have to copy it from there to /lib also. I updated the script above
So i changed this:
```

cd ./emul/linux/x86/usr/lib
cp -rf ./* /lib32

```
to this:
```

cd ./emul/linux/x86/lib
cp -rf * /lib32
cd ../usr/lib
cp -rf * /usr/lib32

```
and added -sf to ln. It will overwrite the link to your original mplayer, which you can still revert by linking original /usr/bin/mplayer to gmplayer. Post results anyway.

---

### Post by mterlouw on 2005-10-11
Thanks for the help, gorod.  The script completes now, but I'm still having some trouble.  It might specific to my system, but I don't have the time to dig into it at the moment.  Mplayer hangs when starting, the player window shows up but the controls window is just a black silhouette. It spits this out on the terminal:

```
MPlayer 1.0pre7try2-3.3.5-20050130 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices  (Family: 8, Stepping: 0)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection - WARNING - this is not optimal!
To get best performance, recompile MPlayer with --disable-runtime-cpudetection.

vo: X11 running at 1680x1050 with depth 24 and 32 bpp (":0.0" => local display)
85 audio & 196 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.

Gdk-WARNING **: locale not supported by Xlib, locale set to C

Gdk-WARNING **: can not set locale modifiers

```

I'll try and figure it out in the coming days, and post the solution if I find it.

---

### Post by gorod on 2005-10-12
I tried it with vanilla breezy and it worked. The only things i had installed were nvidia drivers  and opera. I've got athlon64 + via k8v800 +nvidia and audigy sound. I cant test it now cause i migrated back to my old gentoo installation but I don't see any fatal error in the message you posted. You schould also put this "echo 1024 > /proc/sys/dev/rtc/max-user-freq" in some startup script.

---

### Post by nrwilk on 2005-11-21
How can the script be modified to install video support for Opera if we already have mplayer?  Would that be easy?

---

### Post by Mamonetti on 2008-06-07
Hi

Following your guide i've seen a pair of things:
- File versions (for emul-*, codecs and mplayer-bin) have to be manually updated for newer versions. You may use a set of vars at the beginning for making it easier to check.
- You should change to lib32 and usr/lib32 instead of lib and usr/lib (emul-* keeps this directory naming scheme).
- I'm having problems with libaa.so.1
I have a x86_64 version installed. With no action i receive an error message like this one:
./mplayer-bin: error while loading shared libraries: libaa.so.1: cannot open shared object file: No such file or directory

And if i set LD_LIBRARY_PATH pointing to /usr/lib i get this other one:
./mplayer-bin: error while loading shared libraries: libaa.so.1: wrong ELF class: ELFCLASS64

That is, it recognizes the problem when going to use the 64-bit version of this library. So, how can i fix this? where can i find a 32-bit compiled version of aalib in order to put it in a different folder and use it after setting LD_LIBRARY_PATH? (every time i run mplayer-bin instead of adding this folder to ldconfig config, in order to prevent conflicts between both versions).

Regards

---

