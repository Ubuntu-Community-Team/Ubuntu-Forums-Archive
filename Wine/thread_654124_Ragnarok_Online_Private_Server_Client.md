---
title: "Ragnarok Online Private Server Client"
date: 2007-12-30
forum: Wine
---

### Post by sakatana on 2007-12-30
I'm running on a Dell 600m (problem already, right?).
512MB RAM, Radeon 9000M, Ubuntu 7.10, Wine 0.9.52

This is the terminal output.
```

fixme:ddraw:print_gdi_surface_warning This is a hacked ddraw defaulting to GDI even when opengl surfaces would be used!
fixme:ddraw:print_gdi_surface_warning The normal way to default to GDI surfaces is to set "HKEY_CURRENT_USER\Software\Wine\Direct3D" to "gdi"
fixme:ddraw:print_gdi_surface_warning If that works for you then you shouldn't use this hack.
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5e4,0x00000000), stub!
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel This is a hacked ddraw drawing to the desktop window instead of the window the app requested!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
err:d3d7:IDirect3DImpl_7_CreateDevice The application wants to create a Direct3D device, but non-opengl surfaces are set in the registry. Please set the surface implementation to opengl or autodetection to allow 3D rendering

```

After I change Direct3D to gdi, I get:
```
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5e4,0x00000000), stub!
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel This is a hacked ddraw drawing to the desktop window instead of the window the app requested!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
err:d3d7:IDirect3DImpl_7_CreateDevice The application wants to create a Direct3D device, but non-opengl surfaces are set in the registry. Please set the surface implementation to opengl or autodetection to allow 3D rendering

```

I have searched the internet for hours with no luck.

---

### Post by Crumpets and Jam on 2007-12-30
I'm not really an expert on Wine. I have used it very little. I found this that might help you though.

[http://wiki.jswindle.com/index.php/Ragnarok_Online]("http://wiki.jswindle.com/index.php/Ragnarok_Online")

If it doesn't help you, wait for someone with more experience to post.

Sorry I couldn't help a bit more.

---

