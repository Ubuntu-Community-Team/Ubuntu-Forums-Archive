---
title: "Can't get allegro/wine to compile"
date: 2006-07-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by sonshadowcat on 2006-07-16
Prior to switching to Ubuntu 6.06, I was using Mandrake where I had no problems installing allegro.

Now when I try to install allegro( latest 4.2 from the official site), I get this error:

gcc -s -L/usr/X11R6/lib -Wl,--export-dynamic  -o setup/setup obj/unix/setup.o -Llib/unix -lalleg-4.2.0 -lalleg_unsharable -lm
lib/unix/liballeg-4.2.0.so: undefined reference to `system_xwin'
lib/unix/liballeg-4.2.0.so: undefined reference to `_colorconv_rgb_scale_5x35'
lib/unix/liballeg-4.2.0.so: undefined reference to `_colorconv_indexed_palette'
lib/unix/liballeg-4.2.0.so: undefined reference to `_colorconv_rgb_map'

I've also asked on the allegro forums but they're pretty stumped too.

I also tried installing allegro via the package manager but when I try to compile a program I get this error:

Main.o: file not recognized: File format not recognized






Now for the wine problem:

When I try to install either via the wineinstall or compile myself, I get this error:

checking for C compiler default output file name... configure: error: C compiler cannot create executables


I can't install via the package manager because the site is giving it a 404 error.


I'm pretty new to linux( haven't used in a long time) so any help is appreciated. I'm also using the AMD64 version of Ubuntu if that helps any.

---

### Post by Kilz on 2006-07-16
Look in my signature, you will find a link to my Wine howto that will help you install wine.

---

