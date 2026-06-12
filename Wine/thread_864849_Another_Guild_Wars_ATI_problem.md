---
title: "Another Guild Wars ATI problem"
date: 2008-07-20
forum: Wine
---

### Post by The Tronyx on 2008-07-20
Hello all.  I saw a post which looked like it might be somewhat related but the error messages are a bit different.  I am currently trying to run Guild Wars on an ATI x1600 pro using wine 1.1.1

The error messages are posted below.  Any help would be greatly appreciated as this is the first time I have really attempted to mess with anything wine-related:

The initial download and install of wine GwSetup.exe.  Note that it downloads all files successfully but dies when trying to launch:
```

tronyx@wrekx:~$ wine GwSetup.exe
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80040111
err:ole:CoGetClassObject no class object {fbf23b40-e3f0-101b-8488-00aa003e56f8} could be created for context 0x1
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80040111
err:ole:CoGetClassObject no class object {fbf23b40-e3f0-101b-8488-00aa003e56f8} could be created for context 0x1
fixme:shell:DllCanUnloadNow stub
tronyx@wrekx:~$ fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33f034,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3594
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:reg:GetNativeSystemInfo (0x33985c) using GetSystemInfo()
fixme:dsound:IKsPrivatePropertySetImpl_Get unsupported property: {f2957840-260c-11d1-a4d8-00c04fc28aca}
fixme:win:EnumDisplayDevicesW ((null),0,0x3398c8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW (L"\\\\.\\DISPLAY1",0,0x339580,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x3398c8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ec20,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3594
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:reg:GetNativeSystemInfo (0x339448) using GetSystemInfo()
fixme:dsound:IKsPrivatePropertySetImpl_Get unsupported property: {f2957840-260c-11d1-a4d8-00c04fc28aca}
fixme:win:EnumDisplayDevicesW ((null),0,0x3394b4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW (L"\\\\.\\DISPLAY1",0,0x33916c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x3394b4,0x00000000), stub!
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:IWineD3DDeviceImpl_SetDialogBoxMode (0x141828) Dialogs cannot be disabled yet
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x1ef0670) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x1ef0b68) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x1ef1060) : stub
fixme:d3d_surface:IWineD3DSurfaceImpl_PreLoad >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glGenTextures @ surface.c / 513
fixme:d3d_surface:IWineD3DSurfaceImpl_PreLoad >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ surface.c / 517
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:IWineD3DDeviceImpl_SetDialogBoxMode (0x141828) Dialogs cannot be disabled yet
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x2200140) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x1ef0648) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x2510250) : stub
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #1: "Fragment shader was successfully compiled to run on hardware.\nWARNING: 0:2: extension 'GL_ARB_draw_buffers' is not supported"
err:seh:setup_exception_record stack overflow 1104 bytes in thread 002d eip b7d371e3 esp 7e002ee0 stack 0x7e002000-0x7e004000-0x7e113000
tronyx@wrekx:~$ 

```

This next dump is the error message reported when trying to run wine Gw.exe from the .wine directory and of course the appropriate Program Files sub-directory:
```

tronyx@wrekx:~/.wine/drive_c/Program Files/Guild Wars$ wine Gw.exe 
fixme:advapi:SetEntriesInAclA 1 0x33f79c (nil) 0x33f7d4
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntriesInAclA 1 0x33f788 (nil) 0x33f7d0
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntriesInAclA 1 0x33f7a8 (nil) 0x33f7f0
fixme:advapi:SetSecurityInfo stub
Could not load Mozilla. HTML rendering will be disabled.
fixme:win:EnumDisplayDevicesW ((null),0,0x33ec20,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3594
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:reg:GetNativeSystemInfo (0x339448) using GetSystemInfo()
fixme:dsound:IKsPrivatePropertySetImpl_Get unsupported property: {f2957840-260c-11d1-a4d8-00c04fc28aca}
fixme:win:EnumDisplayDevicesW ((null),0,0x3394b4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW (L"\\\\.\\DISPLAY1",0,0x33916c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x3394b4,0x00000000), stub!
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:IWineD3DDeviceImpl_SetDialogBoxMode (0x141ac0) Dialogs cannot be disabled yet
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x1ef16e8) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x1ef1be0) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x1ef20d8) : stub
fixme:d3d_surface:IWineD3DSurfaceImpl_PreLoad >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glGenTextures @ surface.c / 513
fixme:d3d_surface:IWineD3DSurfaceImpl_PreLoad >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ surface.c / 517
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:IWineD3DDeviceImpl_SetDialogBoxMode (0x141ac0) Dialogs cannot be disabled yet
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x2200140) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x2200638) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x2200b30) : stub
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #1: "Fragment shader was successfully compiled to run on hardware.\nWARNING: 0:2: extension 'GL_ARB_draw_buffers' is not supported"
err:seh:setup_exception_record stack overflow 1104 bytes in thread 001f eip b7d051e3 esp 7dff2ee0 stack 0x7dff2000-0x7dff4000-0x7e103000

```

And lastly here is the result of running the command WINEDEBUG="fixme-all" wine Gw.exe -noshaders -dx8 -nosound -windowed:
```

[email]tronyx@wrekx:~/.wine[/email]/drive_c/Program Files/Guild Wars$ WINEDEBUG="fixme-all" wine Gw.exe -noshaders -dx8 -nosound -windowed
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
err:ntdll:RtlpWaitForCriticalSection section 0x7e5d6900 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 0009, blocked by 0017, retrying (60 sec)

```

Again, I suspect this may be related to the bug with fglrx rather than wine that others have been having problem with regarding the "unrecoverable graphics error," and if this is simply another version of the thread located at [http://ubuntuforums.org/showthread.php?t=788668](http://ubuntuforums.org/showthread.php?t=788668) I apologize and please merge =]

Thanks again for any and all help as it is very much appreciated!

---

### Post by Eviljim on 2008-07-21
Im no expert, but im going to throw some suggestions your way. I had a bit of trouble running WoW on my machine with an ATi card installed.

My card doesnt like running in DirectX/3d much, therefore I had to force WoW to run in OpenGl mode. You may have to do the same with Guildwars.

There would probably be some config type file where you could add such a line?

I found another post which may be of help

[http://ubuntuforums.org/showthread.php?t=283122]("http://ubuntuforums.org/showthread.php?t=283122")

---

### Post by The Tronyx on 2008-07-21
Thanks for the link.  Just a small update but upgrading my driver didn't do much to help, I think it made it worse (if that's possible).

---

