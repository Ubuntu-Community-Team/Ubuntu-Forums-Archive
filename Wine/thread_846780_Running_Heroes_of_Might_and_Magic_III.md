---
title: "Running Heroes of Might and Magic III"
date: 2008-07-01
forum: Wine
---

### Post by culperat on 2008-07-01
I've installed the game with no errors. However, when I go to run it, it gives me a weird error.

```

fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x33f900,0x00000000), stub!
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 800x600x16 @0! (NoRes)
wine: Unhandled page fault on read access to 0x00000000 at address 0x5ffec0 (thread 0009), starting debugger...

```Any ideas on what I have to do to get this running? (Running wine-1.0, and Ubuntu 7.10 x86_64)

---

### Post by brazemcee on 2008-07-03
DirectX is missing. I'm sure of that.

Try installing PlayOnLinux and ask it to install DirectX.

See you.

---

