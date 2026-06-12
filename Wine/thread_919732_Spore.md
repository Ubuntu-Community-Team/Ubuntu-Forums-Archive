---
title: "Spore"
date: 2008-09-14
forum: Wine
---

### Post by grjemo on 2008-09-14
I installed Spore, with the patch I was supposed to, but when i try to run it from the terminal in safe mode, I get this:

```
fixme:thread:SetThreadIdealProcessor (0x7c): stub
fixme:thread:SetThreadIdealProcessor (0x84): stub
fixme:system:SystemParametersInfoW Unimplemented action: 94 (SPI_GETMOUSETRAILS)
fixme:system:SystemParametersInfoW Unimplemented action: 4124 (SPI_GETMOUSESONAR)
err:d3d:InitAdapters Can't load opengl32.dll!
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl
```

---

### Post by nwlinkvxd on 2008-09-14
Try adding "-opengl" to the command. Also check that your Direct3D [registry keys]("http://wiki.winehq.org/UsefulRegistryKeys") have UseGLSL = "enabled" and OffscreenRenderingMode = "pbuffer" or "backbuffer". Spore won't run with "fbo".

It just occurred to me as well, that if you're compiling Wine on 64-bit architecture you may have left out OpenGL. Make sure and follow [this guide]("http://wiki.winehq.org/WineOn64bit") if you're running 64-bit Ubuntu.

---

### Post by grjemo on 2008-09-14
> **nwlinkvxd said:**
> Try adding "-opengl" to the command. Also check that your Direct3D [registry keys]("http://wiki.winehq.org/UsefulRegistryKeys") have UseGLSL = "enabled" and OffscreenRenderingMode = "pbuffer" or "backbuffer". Spore won't run with "fbo".

It just occurred to me as well, that if you're compiling Wine on 64-bit architecture you may have left out OpenGL. Make sure and follow [this guide]("http://wiki.winehq.org/WineOn64bit") if you're running 64-bit Ubuntu.

Okay, I'm in regedit now, but I don't know where to find my Direct3D registry keys.  I am on 32-bit Ubuntu, but I do have a 64-bit processor.  64-bit Ubuntu just causes too many issues.

---

### Post by nwlinkvxd on 2008-09-14
You want to go to HKEY_Current_User\\Software\\Wine\\Direct3D

---

### Post by grjemo on 2008-09-14
There is no Direct3D directory there.

---

### Post by grjemo on 2008-09-14
Also, when I try to run it, I get a popup error:
```
Could not start the renderer.
Please ensure your display is set to 32-bit colour. [1001]
```

---

### Post by nwlinkvxd on 2008-09-14
Ok, you could create the directory manually, but I recommend running "winecfg" and going to the graphics tab, change both the settings under Direct3D, and then change them back, then hit Apply and OK. Then when you run "wine regedit" you should see the Direct3D folder with 2 other string values.

---

### Post by grjemo on 2008-09-14
> **nwlinkvxd said:**
> Ok, you could create the directory manually, but I recommend running "winecfg" and going to the graphics tab, change both the settings under Direct3D, and then change them back, then hit Apply and OK. Then when you run "wine regedit" you should see the Direct3D folder with 2 other string values.

The only values it gives me are (Default), Pixel Shader Mode, and Vertex Shader mode.

---

### Post by grjemo on 2008-09-14
I created new string values with the names and values you suggested.  I'm still getting the same error.  I'm not sure I did it correctly.

---

### Post by fusiondog77 on 2008-09-14
I had similar errors after compiling wine without all the dependencies covered.  

I'm not getting "Can't open opengl.dll" error anymore but I still get this:

ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0x292a3b0,0x00000004,0x292a3ac) Unknown information class
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x292929c): Stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x29290e8,0x00000000), stub!
fixme:psapi:EnumPageFilesA (0x1de88d0, 0x290988c) stub
fixme:psapi:EnumPageFilesA (0x1de88d0, 0x28d41a8) stub
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x293f918): Stub!
fixme:thread:SetThreadIdealProcessor (0x230): stub
fixme:thread:SetThreadIdealProcessor (0x238): stub
fixme:system:SystemParametersInfoW Unimplemented action: 94 (SPI_GETMOUSETRAILS)
fixme:system:SystemParametersInfoW Unimplemented action: 4124 (SPI_GETMOUSESONAR)

---

### Post by nwlinkvxd on 2008-09-14
> **grjemo said:**
> Also, when I try to run it, I get a popup error:
```
Could not start the renderer.
Please ensure your display is set to 32-bit colour. [1001]
```

Okay, apparently that problem is caused by installing DirectX at the end of the Spore installer. Note: you should never need to install DirectX. Wine is a replacement for DirectX.

As recommended by a related post on the 
[official WINE Spore page]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=13652") you should delete your .wine folder in your home directory ("rm -r .wine") and start over with "winecfg". After that, you'll need to re-run the Spore installer. Do not install DirectX.

---

### Post by lronclawbigun on 2008-09-15
Now today we discuss the game of warhammer online. Warhammer online is the full name of this game ,warhammer always abbreviation of war ,so [warhammer power leveling](http://www.item4u.com/Warhammer-Online/Power-Leveling) often called war power leveling, and in fact. All war power leveling , [war power leveling](http://www.item4u.com/Warhammer-Online/Power-Leveling), [warhammer online power leveling](http://www.item4u.com/Warhammer-Online/Power-Leveling) is the same meaning ,so here not to puzzle with this.firstly ,when you want  [Warhammer cd key](http://www.item4u.com/bestSelling-CDKey/Warhammer-Online-CDKey),i suggest you go to gamevive.com. They sell the lowest price for warhammer gold and other [warhammer online cd key](http://www.item4u.com/bestSelling-CDKey/Warhammer-Online-CDKey) .and their delivery  is fastest.it is worth to try.

---

### Post by grjemo on 2008-09-15
Followed your instructions.  Same error.

---

