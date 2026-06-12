---
title: "Cedega/Wine complain about no direct rendering"
date: 2009-06-21
forum: x86 64-bit Users
---

### Post by innerlogic on 2009-06-21
So right now I'm trying to get Cedega runing, but when I run the diagnostics test I get this

```
Cedega Diagnostics Report
Generated: Mon Jun 22 03:22:16 2009 GMT

Starting test: dependency
dependency: passed
Starting test: soundcard
soundcard: passed
Starting test: copy-protection
copy-protection: passed
Starting test: videocard
videocard: error: no direct rendering support detected
videocard: Direct rendering support is required for 3D graphics.
videocard: error: unsupported videocard vendor: unknown
videocard: Video cards from either NVIDIA or ATI are recommended.  Other video cards may not have enough hardware or driver support to run games under Cedega.
videocard: failed
Diagnostics complete

```

Now I have an Nvidia card and installed the drivers manually. I did install the 32-bit libraries and they are in the /usr/lib32 so I don't think it's them (though it may very well be).  Even if I try to run a 3d game anyway, it still won't work.

I think it's probably an extra 32-bit library I need installed. On Fedora I needed to install these libraries to get the 3d working

```
yum install glibc.i686 zlib.i686 libXext.i686 alsa-lib.i686 mesa-libGLU.i686 libjpeg-6b.i686 mesa-libGL.i686 fontconfig.i686 freetype.i686 openssl.i686 dbus-libs.i686 libSM.i686 libICE.i686 libXrandr.i686 libXrender.i686
```

I tried using getlibs to find the same drivers and I think I got them all, but still I have no direct rendering. With Wine I get the same issues; any 3D app with just fail out and not run.

I'm stumped. I'm hoping it's something stupidly easy that I forgot. I tried to find other threads about the issue but could not seem to find any. So can anyone help out? :confused:

---

### Post by markharding557 on 2009-06-27
> yum install glibc.i686 zlib.i686 libXext.i686 alsa-lib.i686 mesa-libGLU.i686 libjpeg-6b.i686 mesa-libGL.i686 fontconfig.i686 freetype.i686 openssl.i686 dbus-libs.i686 libSM.i686 libICE.i686 libXrandr.i686 libXrender.i686
what os are you using yum is not used in ubuntu or debian based os

---

### Post by n3xx on 2009-06-28
I'm haveing this exact same problem .... cedega won't do anything everything crashes i have 2 7950 GT in sli on nvidia 185 drivers for ubuntu 9 64bit on amd fx 62... and when you run the test it says i have no direct rendering but i can use the 3D desktop stuff with compiz so the card must be working right?

---

### Post by markharding557 on 2009-07-06
just occurred to me i think you have to disable compiz when running a 3d app on wine,
i remember reading that somewhere.

---

### Post by manlypain on 2009-07-07
if i removed "padsp" and just run "\usr\bin\cedega" my sound stops working but my rendering problem goes away.  

I think we have the same issue.  i have reinstalled drivers through the utility (downgraded, rebooted, reinstalled, rebooted) and the error stays.  I found out about the padsp thing while cruising the forums.

---

