---
title: "WMA with beep"
date: 2005-08-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by dsbeav on 2005-08-23
I followed the directions for installing WMA playback with beep from here 
[http://ubuntuforums.org/showthread.php?t=33213&highlight=wma+beep](http://ubuntuforums.org/showthread.php?t=33213&highlight=wma+beep)

The ./configure was succussful.
When I ran the make, I got 2 errors.  
I ran make a second time and this is the error


dsbeav@ubuntu:~/bmp-wma-0.1.1$ make
make  all-recursive
make[1]: Entering directory `/home/dsbeav/bmp-wma-0.1.1'
Making all in src
make[2]: Entering directory `/home/dsbeav/bmp-wma-0.1.1/src'
Making all in libffwma
make[3]: Entering directory `/home/dsbeav/bmp-wma-0.1.1/src/libffwma'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/dsbeav/bmp-wma-0.1.1/src/libffwma'
Making all in wma123
make[3]: Entering directory `/home/dsbeav/bmp-wma-0.1.1/src/wma123'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/dsbeav/bmp-wma-0.1.1/src/wma123'
make[3]: Entering directory `/home/dsbeav/bmp-wma-0.1.1/src'
/bin/sh ../libtool --mode=link gcc -DXTHREADS -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2   -I./libffwma -L./libffwma -g -O2    -o libwma.la -rpath /usr/lib/bmp/Input -module -avoid-version bmp-wma.lo iir.lo  -lbeep -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangoxft-1.0 -lpangox-1.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lffwma
gcc -shared  .libs/bmp-wma.o .libs/iir.o  -L/usr/lib -L/home/dsbeav/bmp-wma-0.1.1/src/libffwma /usr/lib/libbeep.so /usr/lib/libgtk-x11-2.0.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libpangoxft-1.0.so /usr/lib/libpangox-1.0.so /usr/lib/libpango-1.0.so /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so -lffwma  -Wl,-soname -Wl,libwma.so -o .libs/libwma.so
/usr/bin/ld: /home/dsbeav/bmp-wma-0.1.1/src/libffwma/libffwma.a(libffwma_a-allcodecs.o): relocation R_X86_64_32 can not be used when making a shared object; recompile with -fPIC
/home/dsbeav/bmp-wma-0.1.1/src/libffwma/libffwma.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[3]: *** [libwma.la] Error 1
make[3]: Leaving directory `/home/dsbeav/bmp-wma-0.1.1/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/dsbeav/bmp-wma-0.1.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dsbeav/bmp-wma-0.1.1'
make: *** [all] Error 2

What does it mean recompile with -fPIC?  Am I missing a package that is necessary for this plugin? Any ideas?

Thanks for you help

---

### Post by Tamir on 2005-08-24
> **dsbeav]I followed the directions for installing WMA playback with beep from here 
[http://ubuntuforums.org/showthread.php?t=33213&highlight=wma+beep](http://ubuntuforums.org/showthread.php?t=33213&highlight=wma+beep)

The ./configure was succussful.
When I ran the make, I got 2 errors.  
I ran make a second time and this is the error


dsbeav@ubuntu:~/bmp-wma-0.1.1$ make
make  all-recursive
make[1]: Entering directory `/home/dsbeav/bmp-wma-0.1.1'
Making all in src
make[2]: Entering directory `/home/dsbeav/bmp-wma-0.1.1/src'
Making all in libffwma
make[3]: Entering directory `/home/dsbeav/bmp-wma-0.1.1/src/libffwma'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/dsbeav/bmp-wma-0.1.1/src/libffwma'
Making all in wma123
make[3]: Entering directory `/home/dsbeav/bmp-wma-0.1.1/src/wma123'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/dsbeav/bmp-wma-0.1.1/src/wma123'
make[3]: Entering directory `/home/dsbeav/bmp-wma-0.1.1/src'
/bin/sh ../libtool --mode=link gcc -DXTHREADS -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2   -I./libffwma -L./libffwma -g -O2    -o libwma.la -rpath /usr/lib/bmp/Input -module -avoid-version bmp-wma.lo iir.lo  -lbeep -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangoxft-1.0 -lpangox-1.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lffwma
gcc -shared  .libs/bmp-wma.o .libs/iir.o  -L/usr/lib -L/home/dsbeav/bmp-wma-0.1.1/src/libffwma /usr/lib/libbeep.so /usr/lib/libgtk-x11-2.0.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libpangoxft-1.0.so /usr/lib/libpangox-1.0.so /usr/lib/libpango-1.0.so /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so -lffwma  -Wl,-soname -Wl,libwma.so -o .libs/libwma.so
/usr/bin/ld: /home/dsbeav/bmp-wma-0.1.1/src/libffwma/libffwma.a(libffwma_a-allcodecs.o): relocation R_X86_64_32 can not be used when making a shared object said:**
> : *** [libwma.la] Error 1
make[3]: Leaving directory `/home/dsbeav/bmp-wma-0.1.1/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/dsbeav/bmp-wma-0.1.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dsbeav/bmp-wma-0.1.1'
make: *** [all] Error 2

What does it mean recompile with -fPIC?  Am I missing a package that is necessary for this plugin? Any ideas?

Thanks for you help
 I have this too, I realy don't know what to do (I have that with another package)

---

### Post by Corbelius on 2005-08-24
Maybe the plugin is only for the 32bit systems?

---

### Post by dsbeav on 2005-08-24
[QUOTE=Corbelius]Maybe the plugin is only for the 32bit systems?[/QUOTE]

I hope not... I'm sure someone has been able to play wma with beep with an AMD64?

---

### Post by Tamir on 2005-08-24
[QUOTE=dsbeav]I hope not... I'm sure someone has been able to play wma with beep with an AMD64?[/QUOTE]
Edit: I don't know

---

### Post by FluffyElmo on 2005-08-25
I ran into this same sort of problem trying to compile transcode and ffmpeg. For transcode to use ffmpeg as a shared library, ffmpeg must be compiled with the -fPic flag in gcc. Alternately you can statically link the ffmpeg code with transcode for a larger executable that doesn't use shared libraries.

I think this is true of all shared libraries on the amd64 platform so I assume Beep would be the same. So if you have the source for the wma library I'd try recompiling it with -fPic. Or try to statically link it with Beep.

As for the reason, it's related to register useage differences between amd64 and x86...I forget the details. This link isn't the best but it's the only one I still seem to have around.
[http://itdp.fh-biergarten.de/transcode-devel/2004-08/msg00110.html](http://itdp.fh-biergarten.de/transcode-devel/2004-08/msg00110.html)

Though I'm sure if you search with the terms 'amd64', 'transcode', 'ffmpeg' and '-fPic' google will tell you more than you ever wanted to know about the subject:) 

Hope this at least gives you a starting point, good luck!

---

### Post by dsbeav on 2005-08-29
[QUOTE=FluffyElmo]I ran into this same sort of problem trying to compile transcode and ffmpeg. For transcode to use ffmpeg as a shared library, ffmpeg must be compiled with the -fPic flag in gcc. Alternately you can statically link the ffmpeg code with transcode for a larger executable that doesn't use shared libraries.

I think this is true of all shared libraries on the amd64 platform so I assume Beep would be the same. So if you have the source for the wma library I'd try recompiling it with -fPic. Or try to statically link it with Beep.

[/QUOTE]

Using the ./configure, make and make install, how would I changed the ffmpeg to be compiled with -fPic. I don't have much experience modifying and playing with make files.

Thanks for your help

---

