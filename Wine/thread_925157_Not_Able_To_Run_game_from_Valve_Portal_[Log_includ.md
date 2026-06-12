---
title: "Not Able To Run game from Valve: Portal [Log included]"
date: 2008-09-20
forum: Wine
---

### Post by Batatolol on 2008-09-20
Hello everyone
I am currently trying to run the game 'Portal', using Wine Version 1.1.5;
I at a Asus EEE 900 computer. That game works fine on this model when using windows XP.
I get the game opening, showing Valve and steam logo, then, at the loading screen, the game breaks and quits.
> wine hl2.exe -game portal
I also tried to run the game with the command
```
wine hl2.exe -game portal -dxlevel 81 -novid
```
Here is the log i got on console:

```
skywalker@lucas-eee:/media/disk/portal$ wine hl2.exe -game portal
fixme:win:EnumDisplayDevicesW ((null),0,0x32e2a0,0x00000000), stub!
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 1024x600x32 @60! (XRandR)
fixme:d3d9:D3DPERF_SetOptions (0x1) : stub
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x155728) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x155728) Event query: Unimplemented, but pretending to be supported
fixme:d3d_surface:IWineD3DSurfaceImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glGenTextures @ surface.c / 2366
Mesa 7.0.3-rc2 implementation error: bad target in BindTexture
Please report at bugzilla.freedesktop.org
fixme:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexImage2D @ surface.c / 357
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCopyTexSubImage2D @ surface.c / 940
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x155728) : stub
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x155728) Event query: Unimplemented, but pretending to be supported
Unable to remove e:\portal\portal\gamestats.log!
fixme:d3d_surface:IWineD3DSurfaceImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glGenTextures @ surface.c / 2366
Mesa 7.0.3-rc2 implementation error: bad target in BindTexture
Please report at bugzilla.freedesktop.org
fixme:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexImage2D @ surface.c / 357
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCopyTexSubImage2D @ surface.c / 940
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x155728) : stub
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x155728) Event query: Unimplemented, but pretending to be supported
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e174 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1554f058) : pBox=0x32e1c8 stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x155728) : stub
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:shdocvw:ViewObject_SetAdvise (0x16052dc0)->(1 00000002 0x78c488)
fixme:shdocvw:PersistStreamInit_InitNew (0x16052dc0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x16052dc0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x16052dc0)->(ffffffff)
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:d3d_surface:IWineD3DSurfaceImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glGenTextures @ surface.c / 2366
Mesa 7.0.3-rc2 implementation error: bad target in BindTexture
Please report at bugzilla.freedesktop.org
fixme:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexImage2D @ surface.c / 357
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCopyTexSubImage2D @ surface.c / 940
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x155728) : stub
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x155728) Event query: Unimplemented, but pretending to be supported
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1558ae58) : pBox=0x32e1e0 stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:d3d_surface:IWineD3DSurfaceImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glGenTextures @ surface.c / 2366
Mesa 7.0.3-rc2 implementation error: bad target in BindTexture
Please report at bugzilla.freedesktop.org
fixme:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexImage2D @ surface.c / 357
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCopyTexSubImage2D @ surface.c / 940
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x155728) : stub
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x155728) Event query: Unimplemented, but pretending to be supported
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1679feb8) : pBox=0x32e2d8 stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x155728) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x155728) : stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x155728) : stub
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x134978) call to IWineD3DDevice_CreateQuery failed
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x155728) : stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e288 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2dc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1540fc30) : pBox=0x32e2ec stub
Mesa 7.0.3-rc2 implementation error: i915_program_error: Exceeded max nr indirect texture lookups
Please report at bugzilla.freedesktop.org
intel_batchbuffer.c:145: intel_flush_inline_primitive: Assertion `intel->prim.primitive != ~0' failed.
DRM_I830_CMDBUFFER: -22
skywalker@lucas-eee:/media/disk/portal$ 

```

I would be glad for your help
Thanks in advance,

EDIT: I am sorry for any english mistakes (:

---

### Post by Dark9204 on 2008-09-20
Hi.
I noticed this line: Mesa 7.0.3-rc2 implementation error: i915_program_error: Exceeded max nr indirect texture lookups
Please report at bugzilla.freedesktop.org

Your graphics card (Intel 915) is trash. It is way to weak to run any game with the source engine.

The reason that the game ran in windows are because Intels linux drivers arent that good.

---

### Post by Batatolol on 2008-09-20
> **Dark9204 said:**
> Hi.
You should have said your specs at first.
I noticed this line: Mesa 7.0.3-rc2 implementation error: i915_program_error: Exceeded max nr indirect texture lookups
Please report at bugzilla.freedesktop.org

Your graphics card (Intel 915) is trash. It is way to weak to run any game with the source engine.

Well. It's the Asus EEE 900 card.
I can run Portal on it when using Windows XP istead of Ubuntu, so the computer specs should do the job,  I just don't know how to make it load =P
EDIT:  yea i know that video card is sucky ;s  but it's all I got right now :P

---

### Post by aoanla on 2008-09-20
> I can run Portal on it when using Windows XP istead of Ubuntu, so the computer specs should do the job, I just don't know how to make it load =P

You can't - the linux drivers for the Intel 915 series integrated graphics solutions don't support the same range of operations as the Windows drivers do. This is because the Windows drivers fake a lot of the functionality by making your CPU do it instead, and the Linux drivers don't.

---

### Post by Batatolol on 2008-09-20
> **aoanla said:**
> You can't - the linux drivers for the Intel 915 series integrated graphics solutions don't support the same range of operations as the Windows drivers do. This is because the Windows drivers fake a lot of the functionality by making your CPU do it instead, and the Linux drivers don't.

Is there a way of making that under Linux?

Thanks

---

### Post by aoanla on 2008-09-20
It is, of course, hypothetically possible for a driver to be written for linux which would provide equivalent functionality.

However, it doesn't exist and no effort is being made to make it exist - the Intel 915 GPU itself is practically considered obsolete, and even Intel themselves don't seem to be interested in continuing development of support for it. (The Windows driver hasn't changed much, either - it's just that it had more effort put into it originally.)

---

