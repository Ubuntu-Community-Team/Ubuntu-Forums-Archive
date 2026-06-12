---
title: "EVE Online + WINE 1.1.0 no textures"
date: 2008-07-05
forum: Wine
---

### Post by Webnapper on 2008-07-05
Hi,

I just managed to install EVE Online on my Ubuntu Laptop. It does start up and I can log in. But I have major graphic glitches. EVE is not loading any textures. Not even the portrait is displayed correctly and some icons are missing. 

Please take a look at the screenshots and at the console output. Maybe someone has an idea how to fix that.

I already tried OffscreenRenseringMode=fbo! It doesn't work. The client crashes after the splash screen.
I also have the voice turned off in EVE (Voiceenenabled=0).
I know that I wont be able to get the advanced graphics working with my video card. I want to use EVE on my Laptop mainly for Skill changing and some trading.

Information to my graphics card:
```
 glxinfo | grep 'OpenGL\|direct'
direct rendering: Yes
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 965GM 4.1.3002 x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 7.0.3-rc2
OpenGL extensions:

``` 

WINE output until Login Screen:
```
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x33ad84,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
thomas@thomas-scheugenpflug:~$ err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x30028 0x00000000
fixme:imm:ImmReleaseContext (0x30028, 0x1426f8): stub
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302
fixme:d3d_draw:drawPrimitive Using software emulation because not all material properties could be tracked
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_texture:IWineD3DBaseTextureImpl_BindTexture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ basetexture.c / 302

```

The WINE Version is 1.1.0
EVE Version 5.10.58188 Premium (Premium Graphics switched off)

Please help me on this problem.

Regards
Thomas

---

### Post by Zsola on 2008-09-03
Hey i have the same video card, so mine is supposed to be working also....
I cannot get past the charachter selection screen, after it it freezes. Did you do anything special to log in the game?
And i have the same graphical problem, and looking for a solution right now. Will notify if i had some progress.

---

### Post by Webnapper on 2008-09-03
Hi,

I'm sorry, but I can't help you on that issue. My EVE runs with a standard WiNE installation. The only problems I have (had):
EULA did not show (fixed by installing Arial Font)
No textures showing up (still not fixed)

I had no problems with crashes. Maybe because I'm running EVE on a virtual wine desktop.

Good luck with your problem and keep me udated.

Regards
Thomas

---

### Post by Zsola on 2008-09-03
Hm yes, thanks. I tried the virtual desktop mode and the other too also, there was no change...

---

### Post by Webnapper on 2008-09-03
Maybe some of my configurations can give you a clue. I was playing around with some Parameters from the beginning.

.wine/user.reg
```
[Software\\Wine\\Direct3D] 1215297939
"DirectDrawRenderer"="opengl"
"PixelShaderMode"="enabled"
"VertexShaderMode"="hardware"
"VideoMemorySize"="384"

[Software\\Wine\\Drivers] 1215229386
"Audio"="alsa"
```

.wine/drive_c/windows/profiles/thomas/Local Setting/application data/CCP/EVE/c_programme_ccp_eve_tranquility/settings/prefs.ini

```
clusterMode=LOCAL

clusterName=LOCALHOST@NODOMAIN

debug=0

decimal=.

digit=,

eulaagreed=0

host=0

inputhost=localhost

languageID=DE

messagePeriod=200

movecapturedone=1

movesettingsdone=1

newbie=0

port=26000

voiceenabled=0
```

Regards
Thomas

---

### Post by Zsola on 2008-09-05
Ok i reinstalled Wine and Eve too and used your config options, and i got the same result as you (with the graphics)... at least it logs in. But every time i try to jump through a gate it just freezes my whole system and have to hard reset my laptop...
Scanning the wine forums for anything useful.

---

### Post by mrbrice on 2008-09-05
I'm curious. Did you install wine and then install Eve, or are you using the package ccp provides? 

I've always used the package off eve-online.com and it's always worked with no issues. 

Sorry, I can't be any help, I was just curious. At least I can bump your thread. 

Good luck.

---

### Post by Zsola on 2008-09-05
Eve with Wine, hence the post name ;) The debian package works until the splash screen and then eve dies :(

---

### Post by mrbrice on 2008-09-05
> **Zsola said:**
> Eve with Wine, hence the post name ;) The debian package works until the splash screen and then eve dies :(

I just wanted to be clear :)

That's unfortunate the ccp package doesn't work for you. Wish I could be more help than just leaving a comment.

---

### Post by Zsola on 2008-09-06
Well yes, id like that too. But i think it is because of my video card. It is an intel  built in card and not especially supported for the linux version of eve. Could be that's why the graphics are, what they are with the wine version.

---

