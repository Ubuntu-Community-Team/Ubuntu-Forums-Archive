---
title: "Team Fortress 2 Troubles"
date: 2008-06-21
forum: Wine
---

### Post by Zaiden on 2008-06-21
I'm having some issues getting TF2 to run in WINE. Main issue is an error message popping up when I try to run TF2, saying "Registry in Use by another program", though sometimes it doesn't come up, but very rarely does it happen. Both -dxlevel 80 and 81 work with the game, but twice have I gotten the game to run. What happens is that it'll load up to the very last bar, and then freeze up. Not sure why it's doing that.

Under Regedit, I have these strings in the Direct3D part of the WINE directory:

> AllowMultiSampling = Disabled
DirectDrawRenderer = opengl
OffscreenRenderingMode = pbuffer
PixelShaderMode = enabled
VideoMemorySize = 320000

Also I've tried both Windows XP and Windows 98 set in the OS part of the Wine Configuration, but both seem to be the same. Any help is greatly appreciated.

---

