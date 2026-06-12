---
title: "libgstreamer-0.8.so.1: cannot open shared object file"
date: 2008-09-02
forum: x86 64-bit Users
---

### Post by peddy on 2008-09-02
Hey everyone.

When trying to run the Sony Ericsson Themes Creator (the Linux version, of course), I get the following error: 

```
ThemesCreator: error while loading shared libraries: libgstreamer-0.8.so.1: cannot open shared object file: No such file or directory

```

I have a newer version of libgstreamer installed already. I am running Hardy AMD64. 

Thanks in advance for your help :)

---

### Post by IntuitiveNipple on 2008-09-02
You could try creating a symbolic link to the new version of the library, but the version difference could indicate substantial internal library changes that might break the application.
```

sudo ln -s /usr/lib//usr/lib/libgstreamer-0.10.so.0  /usr/lib/libgstreamer-0.8.so.1

```

---

### Post by peddy on 2008-09-02
Thanks for the help. However, ThemesCreator still reports the file as nonexistant. 


(also, I compiled 0.8, which created the .so file naturally, and ThemesCreator still reported it as nonexistant. So the program isn't locating the files.)

Any ideas?

---

### Post by IntuitiveNipple on 2008-09-02
Is Themes Creator a 32-bit program? If so, you'll need to install the i386 versions of the library - maybe use **getlibs** to make it easier.

---

### Post by peddy on 2008-09-02
Good call. I was using getlibs incorrectly before, so I was doing 'getlibs libgstreamer-0.8.so.1', incorrectly. I just tried 'getlibs ThemesCreator', and apparently I need 2 other packages as well (not described in the SE documentation).

```
No match for libgstreamer-0.8.so.1
No match for libgstplay-0.8.so.0
No match for libgstinterfaces-0.8.so.0
No packages to install

```

I'll have a look for them tomorrow [img]http://www.iobloggo.com/static/img/smiley/deviant/icon_sleep.gif[/img].

Thanks for your support :D

---

### Post by IntuitiveNipple on 2008-09-02
> **peddy said:**
> Good call. I was using getlibs incorrectly before, so I was doing 'getlibs libgstreamer-0.8.so.1', incorrectly. I just tried 'getlibs ThemesCreator', and apparently I need 2 other packages as well (not described in the SE documentation).

```
No match for libgstreamer-0.8.so.1
No match for libgstplay-0.8.so.0
No match for libgstinterfaces-0.8.so.0
No packages to install

```

I'll have a look for them tomorrow [img]http://www.iobloggo.com/static/img/smiley/deviant/icon_sleep.gif[/img].

Thanks for your support :D
Here you go:
```

$ dpkg-query -S 'libgstreamer*.so'
libgstreamer0.10-0: /usr/lib/libgstreamer-0.10.so.0
libgstreamer0.10-0: /usr/lib/libgstreamer-0.10.so.0.16.0

$ dpkg-query -S 'libgstplay*'
gstreamer0.10-plugins-base: /usr/lib/gstreamer-0.10/libgstplaybin.so

$ dpkg-query -S 'libgstinterfaces*'
libgstreamer-plugins-base0.10-0: /usr/lib/libgstinterfaces-0.10.so.0.13.0
libgstreamer-plugins-base0.10-0: /usr/lib/libgstinterfaces-0.10.so.0

```

---

### Post by atoc on 2008-09-20
Forget about using the SE version, man.
The SE devs used gstreamer 8, ubuntu has 10. Applications will use either GStreamer-0.8 or GStreamer-0.10, since the 0.8 and 0.10 API/ABI are not compatible.
Use the Lasyk.net mTC [http://www.lasyk.net/mTC/](http://www.lasyk.net/mTC/)

---

### Post by peddy on 2008-09-20
yeah I gave up the official one and starting using Lasyk a while ago. I actually got ThemesCreator working to some extent, but it was extremely unstable and whenever I used gstreamer with another app, it would crash.

Cheers

edit: oh and Lasyk does support UIQ3 themes. Works only on my w810, not w950.

---

### Post by corden on 2008-09-26
See this one please:

[http://ubuntuforums.org/showthread.php?t=721430&highlight=themes+creator](http://ubuntuforums.org/showthread.php?t=721430&highlight=themes+creator)

---

### Post by waigx on 2009-02-01
hi,there,I have the same problem with the se themes creator,
just try [http://packages.ubuntu.com/feisty/libs/libgstreamer0.8-0]("http://packages.ubuntu.com/feisty/libs/libgstreamer0.8-0")
[http://packages.ubuntu.com/feisty/libs/libgstreamer-plugins0.8-0]("http://packages.ubuntu.com/feisty/libs/libgstreamer-plugins0.8-0")

you will got the amd64 version deb bag's name :
libgstreamer-plugins0.8-0_0.8.12-6ubuntu3_amd64.deb
libgstreamer0.8-0_0.8.12-2_amd64.deb

google these name above

download them and install!!!

have fun!!!:p

---

### Post by peddy on 2009-02-01
Thanks, works great :)

---

