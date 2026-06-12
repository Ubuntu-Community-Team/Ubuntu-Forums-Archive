---
title: "problem installing pidgin"
date: 2007-06-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by graysn05 on 2007-06-03
so i have had a very hard time getting pidgin "the new name for gaim"

when compiling pidgin i got an error that i didn't have gtk installed
when installing gtk i got a error that i didn't have pango, cairo.... installed
i tried adding these packages through synaptic but i still had the same errors when compiling gtk

i then downloaded the package code and tried to install them.

i'm now at the point where all but cairo are installed
[PHP]checking for pkg-config... /usr/local/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 2.12.0    atk >= 1.9.0    pango >= 1.12.0    cairo >= 1.2.0) were not met:

No package 'cairo' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
[/PHP]

when i attempt to configure cairo i get

[PHP]cairo will be compiled with the following surface backends:
  image:         yes (always builtin)
  Xlib:          yes
  Xlib Xrender:  yes
  Quartz:        no (disabled, use --enable-quartz to enable)
  XCB:           no (disabled, use --enable-xcb to enable)
  Win32:         no (requires a Win32 platform)
  OS2:           no (disabled, use --enable-os2 to enable)
  PostScript:    yes
  PDF:           yes
  SVG:           yes
  glitz:         no (disabled, use --enable-glitz to enable)
  BeOS:          no (disabled, use --enable-beos to enable)
  DirectFB:      no (disabled, use --enable-directfb to enable)

the following font backends:
  FreeType:      no (requires fontconfig
  Win32:         no (requires a Win32 platform)
  ATSUI:         no (disabled, use --enable-atsui to enable)

the following features:
  PNG functions: yes

and the following debug options:
  gcov support:  no
  test surfaces: no
  pdf testing:   no (requires poppler-glib >= 0.4.1)
  svg testing:   no (requires librsvg-2.0 >= 2.15.0)

using CFLAGS:
-DPNG_NO_MMX_CODE -I/usr/local/include/libpng12 -Wall -Wextra -Wsign-compare -Werror-implicit-function-declaration -Wpointer-arith -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -Wpacked -Wswitch-enum -Wmissing-format-attribute -Wstrict-aliasing=2 -Winit-self -Wunsafe-loop-optimizations -Wdeclaration-after-statement -Wold-style-definition -Wno-missing-field-initializers -Wno-unused-parameter -Wno-attributes -fno-strict-aliasing

configure: error: Cairo requires at least one font backend.
                  Please install freetype and fontconfig, then try again:
                  http://freetype.org/  http://fontconfig.org/
[/PHP]
i downloaded freetype and it compiled and installed fine
fontconfig configured without errors but when "make"ing it gave me this at the end
[PHP]/usr/bin/ld: /usr/local/lib/libz.a(inflate.o): relocation R_X86_64_32S against `a local symbol' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libz.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[3]: *** [libfontconfig.la] Error 1
make[3]: Leaving directory `/home/nic/Desktop/fontconfig-2.4.2/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/nic/Desktop/fontconfig-2.4.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/nic/Desktop/fontconfig-2.4.2'
make: *** [all] Error 2
[/PHP]

i'm not sure how i can fix this please help

---

### Post by Cappy on 2007-06-05
There's a repository for it here:
[http://ubuntuforums.org/showthread.php?t=196093](http://ubuntuforums.org/showthread.php?t=196093)

---

