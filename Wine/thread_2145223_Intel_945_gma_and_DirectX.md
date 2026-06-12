---
title: "Intel 945 gma and DirectX"
date: 2013-05-14
forum: Wine
---

### Post by gipawu on 2013-05-14
Hi guys, I got an old Dell mini 10v with Intel 945 gma and I wanted to try some old games. The native OpenGL games run flawlessly (and also OpenGL games in Wine, for example Warcraft 3 with -opengl parameter), but I can't run any Direct3D game in Wine. I get this in terminal:
```
fixme:win:EnumDisplayDevicesW ((null),0,0x32ee30,0x00000000), stub!
err:d3d:wined3d_adapter_init_gl_caps Received a NULL GL_RENDERER.
err:d3d:wined3d_adapter_init Failed to initialize GL caps for adapter 0x145438.
err:d3d:wined3d_adapter_init_gl_caps Received a NULL GL_RENDERER.
err:d3d:wined3d_adapter_init Failed to initialize GL caps for adapter 0x14baa0.
fixme:win:EnumDisplayDevicesW ((null),0,0x32f3a0,0x00000000), stub!

```
I'm pretty sure that I have drivers correctly installed, as in system settings I read "Intel 945GME x86/MMX/SSE2". All this on a fresh Ubuntu 13.04 and Wine installation with default settings. I tried to search on Google, but I do not find anything. Thank you for any help and sorry for my English :)

---

### Post by gipawu on 2013-05-18
No one can help me? :(

---

### Post by Mark Phelps on 2013-05-18
Direct3D includes DirectX versions all the way up through 11 (at present) -- but your card ends with supporting DirectX v9.  If the games you are trying to use need DirectX 10 or higher, you won't be able to run them with that graphics chipset.

---

