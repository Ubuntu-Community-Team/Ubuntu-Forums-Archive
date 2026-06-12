---
title: "problem compiling OpenGL applications"
date: 2005-03-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by benguin on 2005-03-09
Hi there,
I recently upgraded to an AMD64 3200+ processor and an ASUS-A8V deluxe motherboard with 512Megs of DDR400 RAM. I installed Ubuntu64 and dist-upgraded to hoary. Everything looks fine except macromedia flash animations, but that isn't my primary concern. My linux box is mostly used for research in computer vision and I use an open source library called VXL. VXL depends on OpenGL for a few of its functions, notably the user interface part called vgui. Sadly, everytime I try compiling VXL with vgui enabled, I get errors, one of which is like this:
```

/usr/X11R6/lib/libGL.a(glxext.o)(.text+0x1f): In function
`__glXGetCurrentContext':: undefined reference to `pthread_key_create'

```

Looks like a linker error, and something to do with pthread. Anyone has any idea why I'm getting this?

This is the output of uname -a:
```
Linux rhino 2.6.10-4-amd64-generic #1 Wed Mar 2 06:12:17 UTC 2005 x86_64 GNU/Linux
``` 

and output of gcc -v:
```

Reading specs from /usr/lib/gcc-lib/x86_64-linux/3.3.5/specs
Configured with: ../src/configure -v --enable-languages=c,c
++,java,f77,pascal,objc,ada,treelang --prefix=/usr
--mandir=/usr/share/man --infodir=/usr/share/info
--with-gxx-include-dir=/usr/include/c++/3.3 --enable-shared
--with-system-zlib --enable-nls --without-included-gettext
--enable-__cxa_atexit --enable-clocale=gnu --enable-debug
--enable-java-gc=boehm --enable-java-awt=xlib --enable-objc-gc
--disable-multilib x86_64-linux
Thread model: posix
gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)

```

Thanks a bunch!

---

### Post by p!=f on 2005-03-09
Try to add the -lpthread option to link the pthread library.

---

### Post by benguin on 2005-03-09
[QUOTE=p!=f]Try to add the -lpthread option to link the pthread library.[/QUOTE]

Thanks, that fixed the pthread errors. I got some more though, sorry!

```

Building executable 
/opt/Work/vxlbin/core/vgui/examples/basic01_display_image...
/usr/X11R6/lib/libGL.a(glxcmds.o)(.text+0x2fc1): In function `glXGetMscRateOML':
: undefined reference to `XF86VidModeQueryVersion'
/usr/X11R6/lib/libGL.a(glxcmds.o)(.text+0x2ffd): In function `glXGetMscRateOML':
: undefined reference to `XF86VidModeGetModeLine'
/opt/Work/vxlbin/lib/libvgui.a(vgui_register_all.o)(.text+0x5): In function `vgui_register_all_implementations()':
: undefined reference to `vgui_glut_tag_function()'

```

What library am I missing now?

-J-

---

### Post by benguin on 2005-03-10
[QUOTE=benguin]Thanks, that fixed the pthread errors. I got some more though, sorry!

```

Building executable 
/opt/Work/vxlbin/core/vgui/examples/basic01_display_image...
/usr/X11R6/lib/libGL.a(glxcmds.o)(.text+0x2fc1): In function `glXGetMscRateOML':
: undefined reference to `XF86VidModeQueryVersion'
/usr/X11R6/lib/libGL.a(glxcmds.o)(.text+0x2ffd): In function `glXGetMscRateOML':
: undefined reference to `XF86VidModeGetModeLine'
/opt/Work/vxlbin/lib/libvgui.a(vgui_register_all.o)(.text+0x5): In function `vgui_register_all_implementations()':
: undefined reference to `vgui_glut_tag_function()'

```

What library am I missing now?

-J-[/QUOTE]
 Okay, figured it out myself. Had to install the xxf86mv-dev package, and add -lXxf86mv flag to the linker command line.

Cheers,
-J-

---

### Post by mvandeg on 2005-04-02
Thanks a lot, although I don't have a 64-bit machine this post fixed my problem too. I suppose that you meant xxf86vm-dev instead of xxf86mv-dev.

Ciao

---

