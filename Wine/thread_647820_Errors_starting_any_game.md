---
title: "Errors starting any game"
date: 2007-12-22
forum: Wine
---

### Post by 0g_Trans_Fat on 2007-12-22
I've been using wine for a few months now, and have just had this problem while starting games.

If i run the code from the terminal, i find a common set of lines within multiple games: 

err: ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D8 is not available without opengl

I am using v0.9.51 , on Nvidia 6100, using the Restricted Drivers, gnome desktop, and XGL.

This occurs while trying to run games such as WoW, or Warcraft III, but not applications like DC++ or uTorrrent.

Any help is greatly appreciated, thanks.

---

### Post by cogadh on 2007-12-22
I'm confused by the XGL statement. Technically, the Nvidia driver is using AIGLX by default. XGL is not needed and could be conflicting.

---

### Post by 0g_Trans_Fat on 2007-12-22
Oh, thanks

I guess that was the error because i removed the XGL and its working again, I think it got messed up when i messed around with compiz-fusion, thanks for the quick reply and help.

---

