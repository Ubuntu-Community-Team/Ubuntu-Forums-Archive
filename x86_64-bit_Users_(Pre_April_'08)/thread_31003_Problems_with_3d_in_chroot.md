---
title: "Problems with 3d in chroot"
date: 2005-05-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Woolmonkey on 2005-05-01
I have the ati drivers installed in both my 64 and 32 bit (chroot).  When I type glxinfo in the chroot it has direct rendering yes.  glxgears can run fine.  The only problem is when I run anything more complicate then glxgears like fgl_glxgears or cedega I get this error message.

_[COLOR=Blue]_FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!
[/COLOR]

over and over again and the window pops up but nothing is drawn in it.

edit: It is a permision problem because I can run fgl_glxgears sudoed.
any ideas what?

---

### Post by yohan on 2005-11-11
i have the exact same problem....help anyone!

---

