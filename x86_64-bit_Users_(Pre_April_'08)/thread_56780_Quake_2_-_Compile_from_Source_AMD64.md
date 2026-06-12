---
title: "Quake 2 - Compile from Source AMD64"
date: 2005-08-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by hammett111 on 2005-08-14
I have downloaded the following quake2 source "quake2-r0.16.1.tar.gz" and done the make command for my kernel, and this is the error output:

ANY HINTS PEOPLE?

quentin@andromeda:~/Games/quake2/installs/source-compile$ make
make targets BUILDDIR=debugx86_64 CFLAGS="-Wall -pipe -Dstricmp=strcasecmp -DJoystick -DC_ONLY -g -DLINUX_VERSION='\"3.21+r0.16 Debug\"'"
make[1]: Entering directory `/home/quentin/Games/quake2/installs/source-compile'
gcc -Wall -pipe -Dstricmp=strcasecmp -DJoystick -DC_ONLY -g -DLINUX_VERSION='"3.21+r0.16 Debug"' -fPIC  -o debugx86_64/ref_gl/gl_glx.o -c src/linux/gl_glx.c -I/usr/X11R6/include -DOPENGL
src/linux/gl_glx.c:57:36: X11/extensions/xf86dga.h: No such file or directory
src/linux/gl_glx.c:58:38: X11/extensions/xf86vmode.h: No such file or directory
src/linux/gl_glx.c:111: error: syntax error before '*' token
src/linux/gl_glx.c:111: warning: type defaults to `int' in declaration of `vidmodes'
src/linux/gl_glx.c:111: warning: data definition has no type or storage class
src/linux/gl_glx.c:114: error: syntax error before "oldgamma"
src/linux/gl_glx.c:114: warning: type defaults to `int' in declaration of `oldgamma'
src/linux/gl_glx.c:114: warning: data definition has no type or storage class
src/linux/gl_glx.c: In function `install_grabs':
src/linux/gl_glx.c:164: warning: implicit declaration of function `XF86DGAQueryVersion'
src/linux/gl_glx.c:170: warning: implicit declaration of function `XF86DGADirectVideo'
src/linux/gl_glx.c:170: error: `XF86DGADirectMouse' undeclared (first use in this function)
src/linux/gl_glx.c:170: error: (Each undeclared identifier is reported only once
src/linux/gl_glx.c:170: error: for each function it appears in.)
src/linux/gl_glx.c: In function `GLimp_SetMode':
src/linux/gl_glx.c:684: warning: implicit declaration of function `XF86VidModeQueryVersion'
src/linux/gl_glx.c:740: warning: implicit declaration of function `XF86VidModeGetAllModeLines'
src/linux/gl_glx.c:748: error: request for member `hdisplay' in something not a structure or union
src/linux/gl_glx.c:749: error: request for member `vdisplay' in something not a structure or union
src/linux/gl_glx.c:752: error: request for member `hdisplay' in something not a structure or union
src/linux/gl_glx.c:753: error: request for member `vdisplay' in something not a structure or union
src/linux/gl_glx.c:762: error: request for member `hdisplay' in something not a structure or union
src/linux/gl_glx.c:763: error: request for member `vdisplay' in something not a structure or union
src/linux/gl_glx.c:766: warning: implicit declaration of function `XF86VidModeSwitchToMode'
src/linux/gl_glx.c:769: warning: implicit declaration of function `XF86VidModeGetGamma'
src/linux/gl_glx.c:779: warning: implicit declaration of function `XF86VidModeSetViewPort'
src/linux/gl_glx.c: In function `GLimp_Shutdown':
src/linux/gl_glx.c:896: warning: implicit declaration of function `XF86VidModeSetGamma'
src/linux/gl_glx.c: In function `UpdateHardwareGamma':
src/linux/gl_glx.c:978: error: `XF86VidModeGamma' undeclared (first use in this function)
src/linux/gl_glx.c:978: error: syntax error before "gamma"
src/linux/gl_glx.c:983: error: request for member `red' in something not a structure or union
src/linux/gl_glx.c:983: error: request for member `red' in something not a structure or union
src/linux/gl_glx.c:984: error: request for member `green' in something not a structure or union
src/linux/gl_glx.c:984: error: request for member `green' in something not a structure or union
src/linux/gl_glx.c:985: error: request for member `blue' in something not a structure or union
src/linux/gl_glx.c:985: error: request for member `blue' in something not a structure or union
make[1]: *** [debugx86_64/ref_gl/gl_glx.o] Error 1
make[1]: Leaving directory `/home/quentin/Games/quake2/installs/source-compile'
make: *** [build_debug] Error 2

---

### Post by hammett111 on 2005-08-14
[QUOTE=hammett111]I have downloaded the following quake2 source "quake2-r0.16.1.tar.gz" and done the make command for my kernel, and this is the error output:

ANY HINTS PEOPLE?

quentin@andromeda:~/Games/quake2/installs/source-compile$ make
make targets BUILDDIR=debugx86_64 CFLAGS="-Wall -pipe -Dstricmp=strcasecmp -DJoystick -DC_ONLY -g -DLINUX_VERSION='\"3.21+r0.16 Debug\"'"
make[1]: Entering directory `/home/quentin/Games/quake2/installs/source-compile'
gcc -Wall -pipe -Dstricmp=strcasecmp -DJoystick -DC_ONLY -g -DLINUX_VERSION='"3.21+r0.16 Debug"' -fPIC  -o debugx86_64/ref_gl/gl_glx.o -c src/linux/gl_glx.c -I/usr/X11R6/include -DOPENGL
src/linux/gl_glx.c:57:36: X11/extensions/xf86dga.h: No such file or directory
src/linux/gl_glx.c:58:38: X11/extensions/xf86vmode.h: No such file or directory
src/linux/gl_glx.c:111: error: syntax error before '*' token
src/linux/gl_glx.c:111: warning: type defaults to `int' in declaration of `vidmodes'
src/linux/gl_glx.c:111: warning: data definition has no type or storage class
src/linux/gl_glx.c:114: error: syntax error before "oldgamma"
src/linux/gl_glx.c:114: warning: type defaults to `int' in declaration of `oldgamma'
src/linux/gl_glx.c:114: warning: data definition has no type or storage class
src/linux/gl_glx.c: In function `install_grabs':
src/linux/gl_glx.c:164: warning: implicit declaration of function `XF86DGAQueryVersion'
src/linux/gl_glx.c:170: warning: implicit declaration of function `XF86DGADirectVideo'
src/linux/gl_glx.c:170: error: `XF86DGADirectMouse' undeclared (first use in this function)
src/linux/gl_glx.c:170: error: (Each undeclared identifier is reported only once
src/linux/gl_glx.c:170: error: for each function it appears in.)
src/linux/gl_glx.c: In function `GLimp_SetMode':
src/linux/gl_glx.c:684: warning: implicit declaration of function `XF86VidModeQueryVersion'
src/linux/gl_glx.c:740: warning: implicit declaration of function `XF86VidModeGetAllModeLines'
src/linux/gl_glx.c:748: error: request for member `hdisplay' in something not a structure or union
src/linux/gl_glx.c:749: error: request for member `vdisplay' in something not a structure or union
src/linux/gl_glx.c:752: error: request for member `hdisplay' in something not a structure or union
src/linux/gl_glx.c:753: error: request for member `vdisplay' in something not a structure or union
src/linux/gl_glx.c:762: error: request for member `hdisplay' in something not a structure or union
src/linux/gl_glx.c:763: error: request for member `vdisplay' in something not a structure or union
src/linux/gl_glx.c:766: warning: implicit declaration of function `XF86VidModeSwitchToMode'
src/linux/gl_glx.c:769: warning: implicit declaration of function `XF86VidModeGetGamma'
src/linux/gl_glx.c:779: warning: implicit declaration of function `XF86VidModeSetViewPort'
src/linux/gl_glx.c: In function `GLimp_Shutdown':
src/linux/gl_glx.c:896: warning: implicit declaration of function `XF86VidModeSetGamma'
src/linux/gl_glx.c: In function `UpdateHardwareGamma':
src/linux/gl_glx.c:978: error: `XF86VidModeGamma' undeclared (first use in this function)
src/linux/gl_glx.c:978: error: syntax error before "gamma"
src/linux/gl_glx.c:983: error: request for member `red' in something not a structure or union
src/linux/gl_glx.c:983: error: request for member `red' in something not a structure or union
src/linux/gl_glx.c:984: error: request for member `green' in something not a structure or union
src/linux/gl_glx.c:984: error: request for member `green' in something not a structure or union
src/linux/gl_glx.c:985: error: request for member `blue' in something not a structure or union
src/linux/gl_glx.c:985: error: request for member `blue' in something not a structure or union
make[1]: *** [debugx86_64/ref_gl/gl_glx.o] Error 1
make[1]: Leaving directory `/home/quentin/Games/quake2/installs/source-compile'
make: *** [build_debug] Error 2[/QUOTE]
 Solved. Problem required some xf86 development files from synaptic. DOH!!

---

