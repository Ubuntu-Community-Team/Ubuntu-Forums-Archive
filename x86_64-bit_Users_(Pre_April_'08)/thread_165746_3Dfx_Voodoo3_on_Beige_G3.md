---
title: "3Dfx Voodoo3 on Beige G3"
date: 2006-04-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by zuus on 2006-04-25
I've been searching for info on this for quite a while but have found nothing but dead ends.

What I'm after is getting my Voodoo3 2000 PCI working in OpenGL on an old-world Beige G3 266. Now, I know it's old but it's all I have at the moment. I've read a whole lot about x86 users getting "glide3", "libglide" or other such drivers but I can't seem to find any of it for ppc. There is a "device3dfx-source" in the repositories but to tell the truth, I have no idea what to do with it. 

Here's what pops up after I launch glxgears (while the gears run at about 1 frame per 4 seconds);

> zuus@muse:/usr/src/modules/device3dfx$ glxgears
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
libGL warning: 3D driver claims to not support visual 0x35
libGL warning: 3D driver claims to not support visual 0x36
libGL warning: 3D driver claims to not support visual 0x39
libGL warning: 3D driver claims to not support visual 0x3a
libGL warning: 3D driver claims to not support visual 0x3d
libGL warning: 3D driver claims to not support visual 0x3e
libGL warning: 3D driver claims to not support visual 0x41
libGL warning: 3D driver claims to not support visual 0x42
X connection to :0.0 broken (explicit kill or server shutdown).

Also, glxinfo tells me "Direct Rendering" is off. 

I have turned off all colour depths other than 16 bit (and set 16 bit default) in xorg as well as removing all resolutions higher than 1024x768, and adding "DRI 0666" section.

Basically, It's got me stumped. If anyone could help out, it'd be very appreciated.

---

