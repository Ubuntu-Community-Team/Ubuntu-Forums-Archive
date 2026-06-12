---
title: "some games doesnot start"
date: 2008-08-05
forum: Wine
---

### Post by lio_013 on 2008-08-05
hello every body i have installed wine specially for the games but not all the games works 
i read here that i can start the exe files from the terminal so i tryed then i get the following on the terminal
```

ahmed@Lio:/media/Games/ZuMa_2007$ wine tumblebugs.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x32f644,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x32f644,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32d02c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32b5e0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32a188,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d7:IDirect3DImpl_7_CreateDevice (0x2deb278): Only one Direct3D device per DirectDraw object supported
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d7:IDirect3DImpl_7_CreateDevice (0x2deb278): Only one Direct3D device per DirectDraw object supported
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d7:IDirect3DImpl_7_CreateDevice (0x2deb278): Only one Direct3D device per DirectDraw object supported
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d7:IDirect3DImpl_7_CreateDevice (0x2deb278): Only one Direct3D device per DirectDraw object supported
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d7:IDirect3DImpl_7_CreateDevice (0x2deb278): Only one Direct3D device per DirectDraw object supported
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d7:IDirect3DImpl_7_CreateDevice (0x2deb278): Only one Direct3D device per DirectDraw object supported
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d7:IDirect3DImpl_7_CreateDevice (0x2deb278): Only one Direct3D device per DirectDraw object supported
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d7:IDirect3DImpl_7_CreateDevice (0x2deb278): Only one Direct3D device per DirectDraw object supported
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
err:seh:raise_exception Exception frame is not in stack limits => unable to dispatch exception.
ahmed@Lio:/media/Games/ZuMa_2007$

```
and when i double click the file it just give me a black screen and i had to reboot 
any one can help

---

### Post by /////// on 2008-08-05
Not all games are supported by WINE. You are probably trying to run a game that is unsupported. Check the WINE HQ DB for your game to see if its compatible and if it is check to see if other people also get your error.

---

