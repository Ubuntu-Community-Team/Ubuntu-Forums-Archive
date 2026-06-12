---
title: "Call of Duty 4 error message (maybe OpenGL problem)"
date: 2008-05-24
forum: Wine
---

### Post by Sneaky07 on 2008-05-24
I followed the tutorial here [http://ubuntuforums.org/showthread.php?t=641987&page=2]("http://ubuntuforums.org/showthread.php?t=641987&page=2") by ahaslam, but I get this error message in the terminal when I try and run it:

err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl
wine: Unhandled page fault on read access to 0x00000000 at address 0x7ebac024 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7ebac024).
(Bunch of other code like register dump, stack dump, backtrace, and modules)

Anyone ever see this message?  I pretty sure it's an OpenGL problem but don't know how to fix it.

---

