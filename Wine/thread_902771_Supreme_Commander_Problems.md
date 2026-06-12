---
title: "Supreme Commander Problems"
date: 2008-08-27
forum: Wine
---

### Post by Kai001 on 2008-08-27
Hey everyone,

     I noticed that Supreme Commander is one of the top rated "gold" games in the WineDB, and since it's one of my favorite games of all time, I thought I'd try to run it in Ubuntu. (I'm dual-booting an NTFS Windows XP Pro SP2 partition with my Ubuntu Hardy Heron Wubi installation. Although I can't tell, I think I may be running the 64-bit version. Seeing as how Flash wouldn't install because it said "Your architecture, \'x86_64\', is not supported by the Adobe Flash Player installer.").

     Anyway, I'm trying to run the original Supreme Commander (NOT the sequal Forged Alliance), patched to version 1.0.3254. When I run it by putting "wine " and then dragging/dropping SupremeCommander.exe into the terminal to get the directory and run, I get many lines of errors:

```

err:module:find_forwarded_export function not found for forward 'd3dx8.D3DXGetImageInfoFromFileInMemory' used by L"C:\\windows\\system32\\d3dx9_36.dll". If you are using builtin L"d3dx9_36.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'd3dx9_36.D3DXGetImageInfoFromFileInMemory' used by L"C:\\windows\\system32\\d3dx9_31.dll". If you are using builtin L"d3dx9_31.dll", try using the native one instead.
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 53 (SPI_SETTOGGLEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
err:ole:CoGetClassObject class {bc3e0fc6-2e0d-4c45-bc61-d9c328319bd8} not registered
err:ole:CoGetClassObject no class object {bc3e0fc6-2e0d-4c45-bc61-d9c328319bd8} could be created for context 0x1
err:ole:CoGetClassObject class {bc3e0fc6-2e0d-4c45-bc61-d9c328319bd8} not registered
err:ole:CoGetClassObject no class object {bc3e0fc6-2e0d-4c45-bc61-d9c328319bd8} could be created for context 0x1
err:ole:CoGetClassObject class {bc3e0fc6-2e0d-4c45-bc61-d9c328319bd8} not registered
err:ole:CoGetClassObject no class object {bc3e0fc6-2e0d-4c45-bc61-d9c328319bd8} could be created for context 0x1
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x33f244,0x00000000), stub!
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 1024x768x32 @60! (XRandR)
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
wine: Call from 0x7b844c50 to unimplemented function d3dx9_36.dll.D3DXGetVertexShaderProfile, aborting
fixme:faultrep:ReportFault 0x33ea18 0x0 stub
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
err:heap:GlobalFree (0x17e880): Page fault occurred ! Caused by bug ?
fixme:faultrep:ReportFault 0x7ca3a448 0x0 stub
err:ntdll:RtlpWaitForCriticalSection section 0x110048 "heap.c: main process heap section" wait timed out in thread 0089, blocked by 0087, retrying (60 sec)

```

     The Supreme Commander splash shows up, the screen goes black (as if the game was about to launch) and the resolution gets turned down and I can see my desktop and the splash again. Eventually it greys out and I have to terminate the process.

     I should probably point out that I'm attempting to run Supreme Commander from the installation of it on my Windows partition. I can't install it through Wine.

     I followed all the instruction on the Wine DB page "How To" section about it, including installing Mono and Winetricks. But this is as far as I've gotten. (I noticed for certain files it said 'If you are using builtin L"example.dll", try using the native one instead.". So for the two files, "d3dx9_36.dll" and "d3dx9_31.dll", I set them to "native then built-in" in Wine's libraries tab.

Any help is greatly appreciated, as I'd really like to get this running. :)

---

### Post by Kai001 on 2008-08-27
Alright, sorry for the double-post, but seems I am running the 64-bit version then. I'm pondering whether I should reinstall the 32-bit version. Could this possibly fix or even solve this problem? :)

---

