---
title: "Guild Wars - Wine 1.0 - Won't start."
date: 2008-07-02
forum: Wine
---

### Post by WirlWind on 2008-07-02
I installed GW last night and it managed to get into the loading screen (I shut it, was DLing while in bed) but now all I get is an error message: "Unable to initialize 3d output. Please verify you have DirectX 8 and an updated video driver."

I've tried running GW in 95/98/2000/XP and had nothing work.

Graphics are set to Allow window manager to decorate/control the windows
Emulate a virtual desktop (800x600)

Vertex shader support = Hardware (Pixel shader allowed)

I've tried turning off vertex shaders, turning off virtual desktop and have no idea what decorate/controlling windows options does.

The thing that confuzzles me is that the settings were identical to last night, when the game actually got to the login screen and suddenly now it won't.

If you need to know anything else, let me know. I'm pretty new :KS

---

### Post by cogadh on 2008-07-02
Run the game from the terminal and post the output. Error messages from the application itself are usually useless, while error messages from Wine (which are only output to the terminal) are usually very helpful.

---

### Post by WirlWind on 2008-07-02
Finally figured it out :p (How to launch via terminal I mean lol)

```
ineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl
err:wine_d3d:WineDirect3DCreate Direct3D8 is not available without opengl
err:wine_d3d:WineDirect3DCreate Direct3D8 is not available without opengl
err:wine_d3d:WineDirect3DCreate Direct3D8 is not available without opengl

```

As I said, I havn't changed a thing since last night when I had it working.

::EDIT:: I'm running "NVIDIA-Linux-x86_64-173.14.09-pkg2"

---

### Post by WirlWind on 2008-07-02
I think I've managed to figure it out.

I managed to stop gdm, install the driver again then reload it and GWars loaded fine.

I think the driver must have fubar'd during the first install or something.

---

