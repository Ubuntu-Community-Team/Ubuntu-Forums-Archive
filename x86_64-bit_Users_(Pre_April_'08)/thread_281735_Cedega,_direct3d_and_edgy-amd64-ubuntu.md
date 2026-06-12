---
title: "Cedega, direct3d and edgy-amd64-ubuntu"
date: 2006-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Zurgol on 2006-10-21
Hello!
I'm trying to get cedega to work under 64bit-ubuntu and it works with opengl but not with direct3d. I've tried running WoW with opengl, and it works but i get low fps and lots of graphic bugs and when i try to use direct3d the game starts fine but when i try to "enter world" it crashes during the loading screen. It's the same with gta vice city. If i start cedega through a console i get this when the game crashes:
```
wine: glx_texture_compression.c:58: __indirect_glGetCompressedTexImageARB: Assertion `image_bytes >= ((4 * reply.length) - 3)' failed.
Xlib: sequence lost (0x30000 > 0x20b49) in reply type 0x0!
X Error of failed request:  0
  Major opcode of failed request:  0 ()
  Serial number of failed request:  131072
  Current serial number in output stream:  133961

```

I installed cedega with the usual way, but with --force-architecture since the .deb is i386.

---

