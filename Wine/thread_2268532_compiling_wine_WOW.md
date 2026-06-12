---
title: "compiling wine WOW"
date: 2015-03-09
forum: Wine
---

### Post by roxas2 on 2015-03-09
hi i'm running xubuntu 15.04 pre-release on 64bit
and compiling wine 1.7.38

using the guide in
[http://wiki.winehq.org/Wine64](http://wiki.winehq.org/Wine64)

when i'm compiling 64bit version there is no error.
however when i try to compile 32bit wow with the same source code,
like what the guide says,

there are following errors:
configure: error: FreeType 32-bit development files not found. Fonts will not be built.

configure: libxcursor 32-bit development files not found, the Xcursor extension won't be supported.
configure: libxi 32-bit development files not found, the Xinput extension won't be supported.
configure: libXxf86vm 32-bit development files not found, XFree86 Vidmode won't be supported.
configure: libxrandr 32-bit development files not found, XRandr won't be supported.
configure: libxcomposite 32-bit development files not found, Xcomposite won't be supported.
configure: libGLU 32-bit development files not found, GLU won't be supported.
configure: libOSMesa 32-bit development files not found (or too old), OpenGL rendering in bitmaps won't be supported.
configure: OpenCL 32-bit development files not found, OpenCL won't be supported.
configure: pcap 32-bit development files not found, wpcap won't be supported.
configure: libdbus 32-bit development files not found, no dynamic device support.
configure: lib(n)curses 32-bit development files not found, curses won't be supported.
configure: libsane 32-bit development files not found, scanners won't be supported.
configure: libgphoto2 32-bit development files not found, digital cameras won't be supported.
configure: libgphoto2_port 32-bit development files not found, digital cameras won't be auto-detected.
configure: gstreamer-0.10 base plugins 32-bit development files not found, gstreamer support disabled
configure: libcups 32-bit development files not found, CUPS won't be supported.
configure: fontconfig 32-bit development files not found, fontconfig won't be supported.
configure: libtiff 32-bit development files not found, TIFF won't be supported.
configure: WARNING: libxrender 32-bit development files not found, XRender won't be supported.
configure: WARNING: No OpenGL library found on this system. OpenGL and Direct3D won't be supported.
configure: WARNING: libxslt 32-bit development files not found, xslt won't be supported.
configure: WARNING: libgnutls 32-bit development files not found, no schannel support.
configure: WARNING: libpng 32-bit development files not found, PNG won't be supported.



help

starcraft does not run on wine64

i used this method too
[http://wiki.winehq.org/BuildingBiarchWineOnUbuntu](http://wiki.winehq.org/BuildingBiarchWineOnUbuntu)
same errors

---

### Post by roxas2 on 2015-04-12
bump...

does wine64 run 32 bit apps??

---

### Post by user_of_gnomes on 2015-04-13
> **roxas2 said:**
> bump...

does wine64 run 32 bit apps??

Yes, you can use winearch=win32 option to force it to do so.

---

