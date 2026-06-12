---
title: "undefined symbol: _nv000110gl"
date: 2009-05-07
forum: x86 64-bit Users
---

### Post by mtm_spm on 2009-05-07
Hello folks,

Updating from 8.04 to 9.4 (Kubuntu X64) left me without OpenGL on nvidia card.
It worked OK before (even the fonts not found now). 

The problem is an undefined reference in glx module.  Here are the relevant lines from Xorg.log:

(--) PCI:*(0@0:16:0) nVidia Corporation GeForce 7100/nForce 630i rev 162, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfc000000/16777216, BIOS @ 0x????????/131072

.......

(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"
(WW) Warning, couldn't open module freetype
(II) UnloadModule: "freetype"
(EE) Failed to load module "freetype" (module does not exist, 0)

(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
dlopen: /usr/lib/xorg/modules/extensions//libglx.so: undefined symbol: _nv000110gl
(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)

Any idea what went wrong and how to fix it ? 

Thank you,
MTM

---

### Post by mtm_spm on 2009-05-08
Apparently the newer version of libGLcore coming with 9.04 is broken. Why they released it ?

I rolled back from  libGLcore.so.185.18.04  to  libGLcore.so.180.44 and of course 
libGL.so.185.18.04 to  libGL.so.180.44 and that fixed the issue.

---

### Post by gxwilson on 2009-06-25
How exactly did you do the roll back? Via package manager?

I have the same problem but I can see the correct libs on my box however, it looks like some of the symbolic links are broken.

---

