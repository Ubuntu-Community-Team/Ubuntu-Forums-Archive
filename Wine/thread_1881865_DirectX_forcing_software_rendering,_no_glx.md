---
title: "DirectX forcing software rendering, no glx"
date: 2011-11-16
forum: Wine
---

### Post by diskmaster23 on 2011-11-16
I am using FreeNX to connect to my server at home, but FreeNX doesn't allow for GLX rendering. I was wondering if there is a way I can force DirectX to use software rendering instead of trying to use the GLX?

These are the errors I get when I try and run a windows game that needs OpenGL
```
00D2FBC0 00D2FBC4Xlib:  extension "NV-GLX" missing on display ":2008.0".
Xlib:  extension "NV-GLX" missing on display ":2008.0".
err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly (using GL renderer "Mesa GLX Indirect", version "1.2 (1.5 Mesa 6.4.1)").
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
Direct3D9 is not available without OpenGL.
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
Direct3D9 is not available without OpenGL.
fixme:dpnet:IDirectPlay8PeerImpl_Close (0x131d28)->(0): stub
```

glxinfo | grep direct
```
Xlib:  extension "NV-GLX" missing on display ":2008.0".
Xlib:  extension "NV-GLX" missing on display ":2008.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
```

I am running Ubuntu 10.04 Lucid.

---

