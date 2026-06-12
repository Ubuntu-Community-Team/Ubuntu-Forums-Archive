---
title: "VariCAD on x86-64?"
date: 2007-02-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by hizaguchi on 2007-02-14
I'm having a little trouble getting the demo version of VariCAD to run on 64-bit Edgy.  I force installed the i386.deb and that seemed to go fine, but when I try to run the program I get the error:
```
varicad: error while loading shared libraries: libXft.so.2: cannot open shared object file: No such file or directory

```

I installed everything related to libXft (there is no lib32Xft or I would have done that too), and I can see that libXft.so.2 is actually on my system:
```
$ locate libXft
/usr/lib/libXft.so.2
/usr/lib/libXft.so.2.1.2

```

I checked some computers at work and found that sometimes libXft is in /usr/X11R6/lib/, so I made a symlink there just in case, but no luck.

Anybody know how to fix this, please?

---

### Post by Kilz on 2007-02-14
> **hizaguchi said:**
> I'm having a little trouble getting the demo version of VariCAD to run on 64-bit Edgy.  I force installed the i386.deb and that seemed to go fine, but when I try to run the program I get the error:
```
varicad: error while loading shared libraries: libXft.so.2: cannot open shared object file: No such file or directory

```

I installed everything related to libXft (there is no lib32Xft or I would have done that too), and I can see that libXft.so.2 is actually on my system:
```
$ locate libXft
/usr/lib/libXft.so.2
/usr/lib/libXft.so.2.1.2

```

I checked some computers at work and found that sometimes libXft is in /usr/X11R6/lib/, so I made a symlink there just in case, but no luck.

Anybody know how to fix this, please?

Here are generic directions to getting any 32bit application running on 64bit. Including how to solve missing libraries. [http://tghc.org/32biton64bit.php](http://tghc.org/32biton64bit.php)

---

### Post by hizaguchi on 2007-02-14
^Ah, it's like magic.

```
sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-sdl dpkg-dev
```Fixed it.

Thank you, Kilz. :)

---

