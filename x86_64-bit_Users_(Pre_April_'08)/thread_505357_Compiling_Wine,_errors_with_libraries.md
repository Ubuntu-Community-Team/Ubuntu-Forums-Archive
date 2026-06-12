---
title: "Compiling Wine, errors with libraries?"
date: 2007-07-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by darkcarnival on 2007-07-20
I'm on Feisty Fawn and I often compile my own versions of wine simply because I like to have multiple installations of Wine (for testing etc).

Using my home-compiled wine 0.9.41 I get no text at all in Age of Empires 3, but the text is there if I use the 0.9.41 version of wine which Ubuntu supplies..

When compiling I see that fontconfig isn't utilised (neither is libjpeg or libpng for that matter...) although those libraries are in /usr/lib32 -- I don't know if it looks there though!
[B]
Here's a couple of files with the output I've got from the configure process:[/B]

[config.log from a configure]("http://www.insanelylinux.com/wine-problem-tmp/config.log")

[Output from "CFLAGS=-fno-stack-protector ./configure --prefix="/home/jesper/.winebuilds/0.9.41/" --verbose"]("http://www.insanelylinux.com/wine-problem-tmp/configure-output.txt")

What's interesting to me in configure-output.txt is:
```

checking fontconfig/fontconfig.h usability... yes
checking fontconfig/fontconfig.h presence... yes
checking for fontconfig/fontconfig.h... yes

```

And further down:
```

checking for -lfontconfig... not found

```

A more detailed reason for this may be in config.log, where it says:
```

configure:14444: checking for -lfontconfig
configure:14479: gcc -m32 -o conftest -fno-stack-protector   conftest.c -lfontconfig   >&5
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libfontconfig.so when searching for -lfontconfig
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libfontconfig.a when searching for -lfontconfig
/usr/bin/ld: skipping incompatible /usr/lib/libfontconfig.so when searching for -lfontconfig
/usr/bin/ld: skipping incompatible /usr/lib/libfontconfig.a when searching for -lfontconfig
/usr/bin/ld: cannot find -lfontconfig

```

This example was with fontconfig, which is the library I'm most interested in getting working, but I imagine it's the same for the other libraries which are:

```

configure: Xxf86vm development files not found.
Wine will be built without XF86 Vidmode support. (winex11.drv)
configure: XRandr development files not found.
Wine will be built without XRandr support. (winex11.drv)
configure: Xinerama development files not found.
Wine will be built without Xinerama support. (winex11.drv)
configure: libxml2 development files not found.
Wine will be built without XML support. (msxml.dll)
configure: libxslt development files not found.
Wine will be built without xslt support. (msxml.dll)
configure: libhal development files not found.
Wine will be built without dynamic device support. (explorer.exe)
configure: lib(n)curses development files not found.
Wine will be built without (n)curses support. (wineconsole.exe)
configure: libsane development files not found.
Wine will be built without scanner support. (sane.ds/twain_32.dll)
configure: libgphoto2 development files not found.
Wine will be built without Digital Camera support. (gphoto2.ds/twain_32.dll)
configure: libicu development files not found.
Wine will be built without bidi (Right to Left) support. (gdi32.dll)
configure: liblcms development files not found.
Wine will be built without Color Management support. (mscms.dll)
configure: libldap (OpenLDAP) development files not found.
Wine will be built without LDAP support. (wldap32.dll)
configure: libcapi20 development files not found.
Wine will be built without ISDN support. (capi2032.dll)
configure: libcups development files not found.
Wine will be built without CUPS support.
configure: fontconfig development files not found.
Wine will be built without fontconfig support.
configure: OpenSSL development files not found.
Wine will be built without SSL support. (wininet.dll)
configure: libjpeg development files not found.
Wine will be built without JPEG support. (oleaut32.dll)
configure: libpng development files not found.
Wine will be built without PNG support. (oleaut32.dll)

```

I can most certainly live without scanner and ISDN support, but I would like to have the other libraries too if possible. But fontconfig is absolutely needed...!


What to do ? please oh please help :)

---

### Post by darkcarnival on 2007-07-21
I'm surprised no one knew the actual answer. 

But it doesn't matter all that much, I found another way of doing this :)

First of all. It's cumbersome to compile wine under 64bit linux, especially since wine will still be a 32bit binary.. So what I did was this:

1) Create a chrooted environment.
I more or less followed this guide: [Ubuntu 32bit Chroot]("http://ubuntuforums.org/showthread.php?t=24575")
But of course I made the necessary adjustments!

After that.. I issued "apt-get build-dep wine" to get the dependencies needed to build wine. Then I built and compiled Wine under the 32bit chroot and installed it to my home directory (if you follow the guide, the /home dir in the chroot will be linked to the actual /home dir ).

Now.. I looked with "ldd wine" to see if I missed any libraries when running it from my 64bit environment.. but I didn't :) Seems like the extra libraries are compiled in or something..

Anyway.. This ended up giving me fontconfig which in turn gave me fonts when playing Age of Empires 3..

With this method, YOU can compile Wine for your 64bit machine and get ALL the extra functionalities that Wine can handle - verbose configure didn't warn me of ANY missing packages.

All in all a sweet solution if you ask me, cheers !:)

---

