---
title: "So, what do you do to compile wine on x64 ubuntu?"
date: 2008-03-27
forum: Wine
---

### Post by Mr.Johnny on 2008-03-27
Hi!

I've followed the instructions on the wiki about compiling wine on ubuntu x64, but apparently that's not all, since it still complains about missing dependencies.

Anybody knows what else is needed?

Also, can I install the x86 *.deb on ubuntu x64?

thanks

---

### Post by Mr.Johnny on 2008-03-28
bump

---

### Post by Joeb454 on 2008-03-28
You need to find the dependencies :) That's the "joy" of compiling ;)

Why not just add the Wine repo's?

---

### Post by Mr.Johnny on 2008-03-28
> **Joeb454 said:**
> You need to find the dependencies :) That's the "joy" of compiling ;)

Why not just add the Wine repo's?

:lolflag: But that's no fun for me.

I do add the wine's repo's but sometimes it takes a few days... And it won't hurt to know what's needed to compile it. :)

---

### Post by Joeb454 on 2008-03-28
You just need to get the source, cd into the directory from a terminal, and run ```
./configure
```

When it fails, you need to install the package-dev it complains about ;) At least...that's how I compile stuff :lol:

---

### Post by Mr.Johnny on 2008-03-28
I'm afraid it's not that simple... :( You need to do some manual linking for the 32-bit libs too, and apt-get install build-dep wine doesn't configure all the dependencies.

---

### Post by mc4man on 2008-03-28
If your talking about install/run depends installing a repo or other deb first and then removing before installing your built ver. will usually take care of those depends
you can always get appropriate versions here. [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
If you build using ```
dpkg-buildpackage -rfakeroot -b
``` you'll get a package that when you install will take care of any depends
edit: -sorry missed your on x64 - not to sure if you can edit debian rules as needed for dpkg.....

---

### Post by Mr.Johnny on 2008-03-29
Hey thanks, for the tip, but I think I'm getting close:

here's my script file, according to winewiki + some needed lines:

#!/bin/bash
sudo apt-get build-dep wine
sudo apt-get install libxcomposite-dev gcc-4.2-multilib
sudo apt-get install python-fontforge
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
ln -s /usr/lib32/libXxf86vm.so.1 `pwd`/lib32/libXxf86vm.so
ln -s /usr/lib32/libcapi20.so.3.0.4 `pwd`/lib32/libcapi20.so
#end

however, I still get one message:

configure: libhal development files not found, no dynamic device support.

but the link is there... any clue?

---

### Post by mc4man on 2008-03-29
I've never used 64 bit but ck. in synaptic for libhal-dev

---

### Post by Mr.Johnny on 2008-03-29
I did. :guitar: no luck.

---

### Post by mc4man on 2008-03-29
_read_ thru here - 64 bit is unknown territory for me
[http://packages.ubuntu.com/gutsy/libhal-dev](http://packages.ubuntu.com/gutsy/libhal-dev)

edit; I'm making assumption your using 7.10

giving a quick read to your guide I think that may not be what you want or is the issue
> if all needed libraries are present there will be no missing-library warnings or errors anywhere. If you find that this process misses a library, then it means we are either missing a link or the ia32-libs package is missing the 32 bit version of the library.

---

### Post by Mr.Johnny on 2008-03-29
I'm using 8.04. Hum, maybe that's it. I'll wait for the final release to give it another go.

---

### Post by slavik on 2008-03-29
there is a reason I made this: [http://ubuntuforums.org/showthread.php?t=732262](http://ubuntuforums.org/showthread.php?t=732262)

---

### Post by Mr.Johnny on 2008-03-29
Ah, perfect! :)

---

