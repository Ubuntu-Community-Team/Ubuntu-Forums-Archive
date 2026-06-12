---
title: "Steam-based Applications Crash"
date: 2008-04-06
forum: Wine
---

### Post by driley on 2008-04-06
System Info:

Ubuntu 7.10 (AMD64)
ATI HD2600XT - Using the proprietary fglrx driver (8.47.3)
Wine 0.9.58

Whenever I try to launch a steam application such as TF2 or Hammer from the SDK the application will close. WIth TF2 it will show the Valve logo and the Source engine copyright information then close. WIth Hammer I can launch it, but if I try to open a map or create a new one it the application will close when it tries to create the 4 viewports.

With TF2 I have tried setting it to windowed mode. I've also tried forcing it down to dxlevel 81. I have also used Wine-doors to install DIrectX 9c. None of these methods have made any changes. In the Wine configuration in the graphics tab, vertex shader support is set to hardware and allow pixel shader is checked. Also just to note Compiz is turned off. I've also tried running it with 2000, XP, and VIsta.

If I try running it from the terminal here is the output:

> err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x140508 ) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x140508 ) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x140508 ) : stub
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x140508 ) Event query: Unimplemented, but pretending to be supported
fixme: process:IsWow64Process (0xffffffff 0x34d28c ) stub!
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
fixme:avifile:AVIFileExit (): stub!


If anyone has any advice it would be greatly appreciated. :)

---

### Post by Maxymillion on 2008-06-11
I have this issue as well.

Any luck resolving it?!

---

