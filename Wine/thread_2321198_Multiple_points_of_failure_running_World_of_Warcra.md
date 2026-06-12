---
title: "Multiple points of failure running World of Warcraft with Wine 1.8?"
date: 2016-04-21
forum: Wine
---

### Post by Allen_Hundley on 2016-04-21
I am trying to get World of Warcraft 6.2.4 to run on Ubuntu 16.04. I've solved a couple of problems already by updating Wine to 1.8. I have tried using Wine in XP and Windows 7 "compatibility" mode. 

Here is a full log of the output on terminal when launching the executable...

```
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
fixme:process:SetProcessDEPPolicy (1): stub
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
fixme:heap:RtlSetHeapInformation 0x1560000 0 0x32fda8 4 stub
err:winediag:schan_imp_init Failed to load libgnutls, secure connections will not be available.
err:winediag:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path. Usually, you can find it in the winbind package of your distribution.
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:winhttp:WinHttpDetectAutoProxyConfigUrl discovery via DHCP not supported
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:mpr:WNetGetUniversalNameW (L"Z:\\home\\allen\\Games\\World of Warcraft\\data\\data", 0x00000001, 0x176e910, 0x176e90c): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x176f5b4,0x00000000), stub!
fixme:d3d11:D3D11CoreCreateDevice Ignoring feature levels.
fixme:dxgi:dxgi_check_d3d10_support Ignoring adapter type.
fixme:winediag:dxgi_check_d3d10_support Direct3D 10 is not supported on this GPU with the current shader backend.
fixme:win:EnumDisplayDevicesW ((null),0,0x176ecc4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x176ec04,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x176f214,0x00000000), stub!
fixme:dxgi:dxgi_check_d3d10_support Ignoring adapter type.
fixme:winediag:dxgi_check_d3d10_support Direct3D 10 is not supported on this GPU with the current shader backend.
fixme:win:EnumDisplayDevicesW ((null),0,0x176f0e4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x176efc4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x176ef04,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x176f5b4,0x00000000), stub!
fixme:d3d9:D3DPERF_SetOptions (0x1) : stub
fixme:d3d:debug_d3dformat Unrecognized 0x5a574152 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a574152) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a574152 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a574152) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a574152 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a574152) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:win:EnumDisplayDevicesW ((null),0,0x176e6c4,0x00000000), stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x176fa08,0,(nil),0x3b69870,0x176fa00,0x176fa64) stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x176fa08,0,(nil),0x3b69870,0x176fa00,0x176fa64) stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Audio",0x93de938): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x176ed14,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x176ec44,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x176ecf4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x176ec34,0x00000000), stub!
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:imm:ImmReleaseContext (0x8003e, 0x3b68fa0): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x176f0f4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x176f024,0x00000000), stub!
	[format/1] [..\src\format.cpp:1430]: invalid length modifier for format 'u' in 'Client net stats: %Lu bytes sent, %Lu bytes received, %Lu msec elapsed' (ignored)
[format/1] [..\src\format.cpp:1430]: invalid length modifier for format 'u' in 'Client net stats: %Lu bytes sent, %Lu bytes received, %Lu msec elapsed' (ignored)
[format/1] [..\src\format.cpp:1430]: invalid length modifier for format 'u' in 'Client net stats: %Lu bytes sent, %Lu bytes received, %Lu msec elapsed' (ignored)

```

I am able to get into the game launcher, use Battle.net to check and update my files, and I can even get into the login page itself. The problem is that when I attempt to login I'm greeted with "Connecting" and then the error "BLZ51901016." I have looked up that error code and couldn't really find anything on it. I suspect that the problem here lies in connecting to the server...specifically some kind of security handshake. 

Now, I don't know that much about any of this, I'm fairly new to Linux and today was my first try with Wine. However, looking at the log I suspect this to be the main culprit...

```
schan_imp_init Failed to load libgnutls, secure connections will not be available.
```

I looked up how to get libgnutls but was unable to find the library in the Ubuntu repositories, and I also wasn't able to find it anywhere online. I've created a 32 bit prefix to use for WOW. It doesn't seem to like 64 bit. I use the 32 bit prefix in conjunction with the launcher and the 32 bit version of the WOW executable. 

I have used Battle.net to check my files, and it doesn't see anything wrong with WOW. I copied the files to a Windows VM and it seemed to work correctly. I'm guessing someone will suggest just playing on the VM but I don't really have the system resources for that, I don't particularly like Windows, I don't want to dual-boot and I don't like using proprietary software anymore than I have to...plus...where's the fun in that?! 

Any help would be greatly appreciated.

---

