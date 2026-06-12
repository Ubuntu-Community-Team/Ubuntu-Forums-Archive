---
title: "Guild Wars in Wine Error Message while installing"
date: 2008-07-26
forum: Wine
---

### Post by VexVishnu on 2008-07-26
I bought the disc a while back but just got around to installing it yesterday. It's the game of the year edition (if that makes any difference). I installed with the disc and it seems like it actually finished installing but when I tried to start the game my screens resolution would change and nothing would pop up. So I looked for a fix online and ended up deciding to just reinstall over the previous install using this sites guide.

[http://czarism.com/easy-peasy-guild-wars-ubuntu-linux](http://czarism.com/easy-peasy-guild-wars-ubuntu-linux)

I did all the steps up to "wine ./GwSetup.exe"
That's when I got this error message

vexvishnu@Cryptyx:~$ wine ./GwSetup.exe
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80040111
err:ole:CoGetClassObject no class object {fbf23b40-e3f0-101b-8488-00aa003e56f8} could be created for context 0x1
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80040111
err:ole:CoGetClassObject no class object {fbf23b40-e3f0-101b-8488-00aa003e56f8} could be created for context 0x1
fixme:shell:DllCanUnloadNow stub
vexvishnu@Cryptyx:~$ fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33f034,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ec20,0x00000000), stub!
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:IWineD3DDeviceImpl_SetDialogBoxMode (0x13a3d0) Dialogs cannot be disabled yet
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x149de0) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x23a11c8) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x26b0050) : stub
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:IWineD3DDeviceImpl_SetDialogBoxMode (0x13a3d0) Dialogs cannot be disabled yet
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x131de8) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x132418) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x26b0050) : stub
Mesa 7.0.3-rc2 implementation error: i915_program_error: Exceeded max temporary reg
Please report at bugzilla.freedesktop.org
DRM_I830_CMDBUFFER: -22

I couldn't actually go to the freedesktop site because Firefox said something about it not being a trustworthy site so I decided to ask for help here.

Has anyone encountered this problem? Does anyone have any suggestions?
Thanks in advance.

---

### Post by aoanla on 2008-07-27
Looks like you're using a laptop with builtin Intel graphics, yes?

Does 3d rendering work for other applications? That looks like a 3d subsystem problem to me...

Can you tell us what the output of 

glxinfo | grep render 

is?

---

### Post by piercleo on 2008-10-04
Up.

I have the exact same problem.

glxinfo | grep render  gives :

```
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20061017 x86/MMX/SSE2

```

Any help would be appreciated.

Thanks in advance.

PierC

---

