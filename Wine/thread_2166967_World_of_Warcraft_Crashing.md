---
title: "World of Warcraft Crashing"
date: 2013-08-11
forum: Wine
---

### Post by x5metalmonster on 2013-08-11
Hello.. my world of warcraft game keeps crashing at random times.. im currently running it under wine 1.5.29 with operating system ubuntu 13.04
my graphics card is Radeon HD 6520G. This is currently what my registry looks like under wine--->> ```
“DirectDrawRenderer”=”opengl”
“Nonpower2Mode”=”repack”
“OffscreenRenderingMode”=”fbo”
“RenderTargetLockMode”=”auto”
“UseGLSL”=”readtex”
“VertexShaderMode”=”hardware” 
“VideoDescription”=”Radeon HD 6520G"
“VideoMemorySize”=”4000"
```

here are some of the error logs i get while running through playonlinux (wine1.5.29)


```
0x24cc, 0x0, 2, 0x138fa760, 19, 0x19f7ec, 5, 0x189a554, 0x189a61c): stub
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189a180,0,(nil),0x147530,0x189a1a 8,0x189a1b4) stub!
[08/11/13 07:07:03] - Running wine-1.5.29 Wow.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x148c000 0 0x189fee4 4
fixme:win:EnumDisplayDevicesW ((null),0,0x189ed00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189eb58,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189f038,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa5c,0,(nil),0x150af8,0x189fa5 4,0x189faa8) stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa58,0,(nil),0x150af8,0x189fa5 0,0x189faa4) stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f704): stub
fixme:imm:ImmReleaseContext (0x4005a, 0x1504b8): stub
fixme:advapi:CreateRestrictedToken (0x253c, 0x0, 2, 0xcf3b318, 19, 0x1a028c, 5, 0x189a554, 0x189a61c): stub
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189a180,0,(nil),0x1a0698,0x189a1a 8,0x189a1b4) stub!
[08/11/13 07:10:13] - Running wine-1.5.29 regedit
[08/11/13 07:10:13] - Content of 
-----------
-----------
[08/11/13 07:14:10] - Running wine-1.5.29 regedit /home/hhdda/.PlayOnLinux//tmp/regkey.reg
[08/11/13 07:14:10] - Content of /home/hhdda/.PlayOnLinux//tmp/regkey.reg
-----------
REGEDIT4

[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"Multisampling"="enabled"
-----------
[08/11/13 07:14:13] - Running wine-1.5.29 regedit /home/hhdda/.PlayOnLinux//tmp/regkey.reg
[08/11/13 07:14:13] - Content of /home/hhdda/.PlayOnLinux//tmp/regkey.reg
-----------
REGEDIT4

[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"StrictDrawOrdering"="enabled"
-----------
[08/11/13 07:14:24] - Running wine-1.5.29 Wow.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x148c000 0 0x189fee4 4
fixme:win:EnumDisplayDevicesW ((null),0,0x189ed00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189eb58,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189f038,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa5c,0,(nil),0x150630,0x189fa5 4,0x189faa8) stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa58,0,(nil),0x150630,0x189fa5 0,0x189faa4) stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f704): stub
fixme:imm:ImmReleaseContext (0x4005a, 0x150130): stub
fixme:advapi:CreateRestrictedToken (0x24cc, 0x0, 2, 0xbfc8458, 19, 0x19f824, 5, 0x189a554, 0x189a61c): stub
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189a180,0,(nil),0x147688,0x189a1a 8,0x189a1b4) stub!
[08/11/13 07:20:13] - Running wine-1.5.29 regedit
[08/11/13 07:20:13] - Content of 
-----------
-----------
[08/11/13 07:21:36] - Running wine-1.5.29 regedit
[08/11/13 07:21:36] - Content of 
-----------
-----------
[08/11/13 07:24:47] - Running wine-1.5.29 Wow.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x148c000 0 0x189fee4 4
fixme:win:EnumDisplayDevicesW ((null),0,0x189ed00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189eb58,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189f038,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa5c,0,(nil),0x1501b0,0x189fa5 4,0x189faa8) stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa58,0,(nil),0x1501b0,0x189fa5 0,0x189faa4) stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f704): stub
fixme:imm:ImmReleaseContext (0x400a4, 0x14ff60): stub
fixme:advapi:CreateRestrictedToken (0x24c8, 0x0, 2, 0x120605a0, 19, 0x19f61c, 5, 0x189a554, 0x189a61c): stub
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189a180,0,(nil),0x158468,0x189a1a 8,0x189a1b4) stub!
[08/11/13 07:42:13] - Running wine-1.5.29 Wow.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x148c000 0 0x189fee4 4
fixme:win:EnumDisplayDevicesW ((null),0,0x189ed00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189eb58,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189f038,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa5c,0,(nil),0x150428,0x189fa5 4,0x189faa8) stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa58,0,(nil),0x150428,0x189fa5 0,0x189faa4) stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f704): stub
fixme:imm:ImmReleaseContext (0x4005a, 0x1501f0): stub
fixme:advapi:CreateRestrictedToken (0x24a8, 0x0, 2, 0xca3cd28, 19, 0x19fbc4, 5, 0x189a554, 0x189a61c): stub
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189a180,0,(nil),0x19f560,0x189a1a 8,0x189a1b4) stub!
[08/11/13 08:03:13] - Running wine-1.5.29 Wow.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x148c000 0 0x189fee4 4
fixme:win:EnumDisplayDevicesW ((null),0,0x189ed00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189eb58,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189f038,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa5c,0,(nil),0x1509d0,0x189fa5 4,0x189faa8) stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa58,0,(nil),0x1509d0,0x189fa5 0,0x189faa4) stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f704): stub
fixme:imm:ImmReleaseContext (0x4005a, 0x150248): stub
fixme:advapi:CreateRestrictedToken (0x253c, 0x0, 2, 0x159a3150, 19, 0x152584, 5, 0x189a554, 0x189a61c): stub
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189a180,0,(nil),0x1521c0,0x189a1a 8,0x189a1b4) stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189e450,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189e2b8,0x00000000), stub!
[08/11/13 14:28:23] - Running wine-1.5.29 Wow.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x148c000 0 0x189fee4 4
fixme:win:EnumDisplayDevicesW ((null),0,0x189ed00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189eb58,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189f038,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa5c,0,(nil),0x150a30,0x189fa5 4,0x189faa8) stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa58,0,(nil),0x150a30,0x189fa5 0,0x189faa4) stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f704): stub
fixme:imm:ImmReleaseContext (0x4005a, 0x1501f8): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f948): stub
fixme:advapi:CreateRestrictedToken (0x254c, 0x0, 2, 0xe700a98, 19, 0x1920dc, 5, 0x189a554, 0x189a61c): stub
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189a180,0,(nil),0x1477e0,0x189a1a 8,0x189a1b4) stub!
fixme:dbghelp:i386_stack_walk new PC=b758590b different from Eip=6ade348
fixme:dbghelp:i386_stack_walk new PC=7bc7c62f different from Eip=7bc7c6fb
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
XIO: fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
after 10767 requests (10767 known processed) with 0 events remaining.
fixme:winhttp:WinHttpDetectAutoProxyConfigUrl discovery via DHCP not supported
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x148c000 0 0x189fee4 4
fixme:win:EnumDisplayDevicesW ((null),0,0x189ed00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189eb58,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189f038,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa5c,0,(nil),0x150600,0x189fa5 4,0x189faa8) stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa58,0,(nil),0x150600,0x189fa5 0,0x189faa4) stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f704): stub
fixme:imm:ImmReleaseContext (0xa007a, 0x1500c0): stub
fixme:advapi:CreateRestrictedToken (0x24e4, 0x0, 2, 0x15240a68, 19, 0x15233c, 5, 0x189a554, 0x189a61c): stub
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189a180,0,(nil),0x152980,0x189a1a 8,0x189a1b4) stub!
[08/11/13 15:52:20] - Running wine-1.5.29 winecfg
[08/11/13 15:52:53] - Running wine-1.5.29 Wow.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x148c000 0 0x189fee4 4
fixme:win:EnumDisplayDevicesW ((null),0,0x189ed00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189eb58,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189f038,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa5c,0,(nil),0x150490,0x189fa5 4,0x189faa8) stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa58,0,(nil),0x150490,0x189fa5 0,0x189faa4) stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f704): stub
fixme:imm:ImmReleaseContext (0x500c8, 0x14ffd0): stub
fixme:advapi:CreateRestrictedToken (0x254c, 0x0, 2, 0xf2d3970, 19, 0x19f48c, 5, 0x189a554, 0x189a61c): stub
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189a180,0,(nil),0x14ffb0,0x189a1a 8,0x189a1b4) stub!
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x7bc35465
```




~~~heres a 2nd one~~~



```
dSecurityDescriptorW ((nil),(nil),1,0x189fa58,0,(nil),0x1504b8,0x189fa5 0,0x189faa4) stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f704): stub
fixme:imm:ImmReleaseContext (0x4005a, 0x150008): stub
fixme:advapi:CreateRestrictedToken (0x24a8, 0x0, 2, 0x13ad49a8, 19, 0x19f8d4, 5, 0x189a554, 0x189a61c): stub
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189a180,0,(nil),0x1476c8,0x189a1a 8,0x189a1b4) stub!
[08/09/13 21:02:21] - Running wine-1.5.29 Wow.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x148c000 0 0x189fee4 4
fixme:win:EnumDisplayDevicesW ((null),0,0x189ed00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189eb58,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189f038,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa5c,0,(nil),0x150c58,0x189fa5 4,0x189faa8) stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa58,0,(nil),0x150c58,0x189fa5 0,0x189faa4) stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f704): stub
fixme:imm:ImmReleaseContext (0x4005a, 0x14a358): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f948): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f948): stub
fixme:advapi:CreateRestrictedToken (0x254c, 0x0, 2, 0x1201aaf8, 19, 0x15ab84, 5, 0x189a554, 0x189a61c): stub
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189a180,0,(nil),0x19f1a0,0x189a1a 8,0x189a1b4) stub!
[08/09/13 21:10:14] - Running wine-1.5.29 Wow.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x148c000 0 0x189fee4 4
fixme:win:EnumDisplayDevicesW ((null),0,0x189ed00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189eb58,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189f038,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa5c,0,(nil),0x150c70,0x189fa5 4,0x189faa8) stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa58,0,(nil),0x150c70,0x189fa5 0,0x189faa4) stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f704): stub
fixme:imm:ImmReleaseContext (0x4005a, 0x14a358): stub
fixme:advapi:CreateRestrictedToken (0x24a8, 0x0, 2, 0x12e7ab10, 19, 0x199334, 5, 0x189a554, 0x189a61c): stub
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189a180,0,(nil),0x152308,0x189a1a 8,0x189a1b4) stub!
[08/09/13 22:20:46] - Running wine-1.5.29 Wow.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x148c000 0 0x189fee4 4
fixme:win:EnumDisplayDevicesW ((null),0,0x189ed00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189eb58,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189f038,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa5c,0,(nil),0x1502e8,0x189fa5 4,0x189faa8) stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa58,0,(nil),0x1502e8,0x189fa5 0,0x189faa4) stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f704): stub
fixme:imm:ImmReleaseContext (0x4005a, 0x14fe30): stub
fixme:advapi:CreateRestrictedToken (0x24cc, 0x0, 2, 0x177b6dd8, 19, 0x1502ec, 5, 0x189a554, 0x189a61c): stub
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189a180,0,(nil),0x19b4d0,0x189a1a 8,0x189a1b4) stub!
[08/10/13 01:12:53] - Running wine-1.5.29 Wow.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x148c000 0 0x189fee4 4
fixme:win:EnumDisplayDevicesW ((null),0,0x189ed00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189eb58,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189f038,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa5c,0,(nil),0x1502e8,0x189fa5 4,0x189faa8) stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa58,0,(nil),0x1502e8,0x189fa5 0,0x189faa4) stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f704): stub
fixme:imm:ImmReleaseContext (0x4005a, 0x14fe30): stub
fixme:advapi:CreateRestrictedToken (0x24cc, 0x0, 2, 0x106d64d0, 19, 0x19f73c, 5, 0x189a554, 0x189a61c): stub
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189a180,0,(nil),0x19f448,0x189a1a 8,0x189a1b4) stub!
[08/10/13 14:20:14] - Running wine-1.5.29 Wow.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x148c000 0 0x189fee4 4
fixme:win:EnumDisplayDevicesW ((null),0,0x189ed00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189eb58,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189f038,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa5c,0,(nil),0x1502e8,0x189fa5 4,0x189faa8) stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa58,0,(nil),0x1502e8,0x189fa5 0,0x189faa4) stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f704): stub
fixme:imm:ImmReleaseContext (0x4005a, 0x14fe30): stub
fixme:advapi:CreateRestrictedToken (0x24cc, 0x0, 2, 0x10a98190, 19, 0x15fc1c, 5, 0x189a554, 0x189a61c): stub
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189a180,0,(nil),0x15fc18,0x189a1a 8,0x189a1b4) stub!
[08/10/13 14:25:09] - Running wine-1.5.29 Wow.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x148c000 0 0x189fee4 4
fixme:win:EnumDisplayDevicesW ((null),0,0x189ed00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189eb58,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189f038,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa5c,0,(nil),0x1502e8,0x189fa5 4,0x189faa8) stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa58,0,(nil),0x1502e8,0x189fa5 0,0x189faa4) stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f704): stub
fixme:imm:ImmReleaseContext (0x4005a, 0x14fe30): stub
fixme:advapi:CreateRestrictedToken (0x24cc, 0x0, 2, 0x102e2e88, 19, 0x156254, 5, 0x189a554, 0x189a61c): stub
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189a180,0,(nil),0x151a30,0x189a1a 8,0x189a1b4) stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189e450,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189e2b8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189e450,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189e2b8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189e450,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189e2b8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189e450,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189e2b8,0x00000000), stub!
XIO: fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
after 43089 requests (43089 known processed) with 2 events remaining.
[08/10/13 17:10:55] - Running wine-1.5.29 Wow.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x148c000 0 0x189fee4 4
fixme:win:EnumDisplayDevicesW ((null),0,0x189ed00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189eb58,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189f038,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa5c,0,(nil),0x1502e8,0x189fa5 4,0x189faa8) stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa58,0,(nil),0x1502e8,0x189fa5 0,0x189faa4) stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f704): stub
fixme:imm:ImmReleaseContext (0x4005a, 0x14fe30): stub
fixme:advapi:CreateRestrictedToken (0x24a8, 0x0, 2, 0xcd58120, 19, 0x15275c, 5, 0x189a554, 0x189a61c): stub
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189a180,0,(nil),0x151b68,0x189a1a 8,0x189a1b4) stub!
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
XIO: fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
after 116 requests (116 known processed) with 0 events remaining.
XIO: fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
after 115 requests (115 known processed) with 0 events remaining.
[08/10/13 17:20:29] - Running wine-1.5.29 Wow.exe
[08/10/13 20:09:42] - Running wine-1.5.29 Wow.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x148c000 0 0x189fee4 4
fixme:win:EnumDisplayDevicesW ((null),0,0x189ed00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189eb58,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189f038,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa5c,0,(nil),0x1506b0,0x189fa5 4,0x189faa8) stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa58,0,(nil),0x1506b0,0x189fa5 0,0x189faa4) stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f704): stub
fixme:imm:ImmReleaseContext (0x180068, 0x14fde0): stub
fixme:advapi:CreateRestrictedToken (0x2564, 0x0, 2, 0x129f2270, 19, 0x156a2c, 5, 0x189a554, 0x189a61c): stub
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189a180,0,(nil),0x1525d8,0x189a1a 8,0x189a1b4) stub!
fixme:dbghelp:i386_stack_walk new PC=159410 different from Eip=7bc7c9ea
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
XIO: fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
after 143 requests (143 known processed) with 0 events remaining.
XIO: fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
after 40861 requests (40861 known processed) with 0 events remaining.
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x148c000 0 0x189fee4 4
fixme:win:EnumDisplayDevicesW ((null),0,0x189ed00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189eb58,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189f038,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa5c,0,(nil),0x1502e8,0x189fa5 4,0x189faa8) stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa58,0,(nil),0x1502e8,0x189fa5 0,0x189faa4) stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f704): stub
fixme:imm:ImmReleaseContext (0x4005a, 0x14fe30): stub
fixme:advapi:CreateRestrictedToken (0x24cc, 0x0, 2, 0x14c39d20, 19, 0x1577cc, 5, 0x189a554, 0x189a61c): stub
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189a180,0,(nil),0x1577c8,0x189a1a 8,0x189a1b4) stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f948): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f948): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f948): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f948): stub
```



~~and here is a third one~~~



```
EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa5c,0,(nil),0x150818,0x189fa5 4,0x189faa8) stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa58,0,(nil),0x150818,0x189fa5 0,0x189faa4) stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f704): stub
fixme:imm:ImmReleaseContext (0x4005a, 0x14ffd0): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f948): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f948): stub
fixme:advapi:CreateRestrictedToken (0x2524, 0x0, 2, 0xcd97f18, 19, 0x19f5bc, 5, 0x189a554, 0x189a61c): stub
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189a180,0,(nil),0x199480,0x189a1a 8,0x189a1b4) stub!
[08/09/13 20:17:48] - Running wine-1.5.29 Wow.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x148c000 0 0x189fee4 4
fixme:win:EnumDisplayDevicesW ((null),0,0x189ed00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189eb58,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189f038,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa5c,0,(nil),0x1504b8,0x189fa5 4,0x189faa8) stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa58,0,(nil),0x1504b8,0x189fa5 0,0x189faa4) stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f704): stub
fixme:imm:ImmReleaseContext (0x4005a, 0x150008): stub
fixme:advapi:CreateRestrictedToken (0x24a8, 0x0, 2, 0x13ad49a8, 19, 0x19f8d4, 5, 0x189a554, 0x189a61c): stub
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189a180,0,(nil),0x1476c8,0x189a1a 8,0x189a1b4) stub!
[08/09/13 21:02:21] - Running wine-1.5.29 Wow.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x148c000 0 0x189fee4 4
fixme:win:EnumDisplayDevicesW ((null),0,0x189ed00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189eb58,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189f038,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa5c,0,(nil),0x150c58,0x189fa5 4,0x189faa8) stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa58,0,(nil),0x150c58,0x189fa5 0,0x189faa4) stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f704): stub
fixme:imm:ImmReleaseContext (0x4005a, 0x14a358): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f948): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f948): stub
fixme:advapi:CreateRestrictedToken (0x254c, 0x0, 2, 0x1201aaf8, 19, 0x15ab84, 5, 0x189a554, 0x189a61c): stub
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189a180,0,(nil),0x19f1a0,0x189a1a 8,0x189a1b4) stub!
[08/09/13 21:10:14] - Running wine-1.5.29 Wow.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x148c000 0 0x189fee4 4
fixme:win:EnumDisplayDevicesW ((null),0,0x189ed00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189eb58,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189f038,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa5c,0,(nil),0x150c70,0x189fa5 4,0x189faa8) stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa58,0,(nil),0x150c70,0x189fa5 0,0x189faa4) stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f704): stub
fixme:imm:ImmReleaseContext (0x4005a, 0x14a358): stub
fixme:advapi:CreateRestrictedToken (0x24a8, 0x0, 2, 0x12e7ab10, 19, 0x199334, 5, 0x189a554, 0x189a61c): stub
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189a180,0,(nil),0x152308,0x189a1a 8,0x189a1b4) stub!
[08/09/13 22:20:46] - Running wine-1.5.29 Wow.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x148c000 0 0x189fee4 4
fixme:win:EnumDisplayDevicesW ((null),0,0x189ed00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189eb58,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189f038,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa5c,0,(nil),0x1502e8,0x189fa5 4,0x189faa8) stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa58,0,(nil),0x1502e8,0x189fa5 0,0x189faa4) stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f704): stub
fixme:imm:ImmReleaseContext (0x4005a, 0x14fe30): stub
fixme:advapi:CreateRestrictedToken (0x24cc, 0x0, 2, 0x177b6dd8, 19, 0x1502ec, 5, 0x189a554, 0x189a61c): stub
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189a180,0,(nil),0x19b4d0,0x189a1a 8,0x189a1b4) stub!
[08/10/13 01:12:53] - Running wine-1.5.29 Wow.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x148c000 0 0x189fee4 4
fixme:win:EnumDisplayDevicesW ((null),0,0x189ed00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189eb58,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189f038,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa5c,0,(nil),0x1502e8,0x189fa5 4,0x189faa8) stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa58,0,(nil),0x1502e8,0x189fa5 0,0x189faa4) stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f704): stub
fixme:imm:ImmReleaseContext (0x4005a, 0x14fe30): stub
fixme:advapi:CreateRestrictedToken (0x24cc, 0x0, 2, 0x106d64d0, 19, 0x19f73c, 5, 0x189a554, 0x189a61c): stub
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189a180,0,(nil),0x19f448,0x189a1a 8,0x189a1b4) stub!
[08/10/13 14:20:14] - Running wine-1.5.29 Wow.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x148c000 0 0x189fee4 4
fixme:win:EnumDisplayDevicesW ((null),0,0x189ed00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189eb58,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189f038,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa5c,0,(nil),0x1502e8,0x189fa5 4,0x189faa8) stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa58,0,(nil),0x1502e8,0x189fa5 0,0x189faa4) stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f704): stub
fixme:imm:ImmReleaseContext (0x4005a, 0x14fe30): stub
fixme:advapi:CreateRestrictedToken (0x24cc, 0x0, 2, 0x10a98190, 19, 0x15fc1c, 5, 0x189a554, 0x189a61c): stub
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189a180,0,(nil),0x15fc18,0x189a1a 8,0x189a1b4) stub!
[08/10/13 14:25:09] - Running wine-1.5.29 Wow.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x148c000 0 0x189fee4 4
fixme:win:EnumDisplayDevicesW ((null),0,0x189ed00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189eb58,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189f038,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa5c,0,(nil),0x1502e8,0x189fa5 4,0x189faa8) stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa58,0,(nil),0x1502e8,0x189fa5 0,0x189faa4) stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f704): stub
fixme:imm:ImmReleaseContext (0x4005a, 0x14fe30): stub
fixme:advapi:CreateRestrictedToken (0x24cc, 0x0, 2, 0x102e2e88, 19, 0x156254, 5, 0x189a554, 0x189a61c): stub
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189a180,0,(nil),0x151a30,0x189a1a 8,0x189a1b4) stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189e450,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189e2b8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189e450,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189e2b8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189e450,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189e2b8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189e450,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189e2b8,0x00000000), stub!
XIO: fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
after 43089 requests (43089 known processed) with 2 events remaining.
[08/10/13 17:10:55] - Running wine-1.5.29 Wow.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x148c000 0 0x189fee4 4
fixme:win:EnumDisplayDevicesW ((null),0,0x189ed00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189eb58,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189f038,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x189ee38,0x00000000), stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa5c,0,(nil),0x1502e8,0x189fa5 4,0x189faa8) stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189fa58,0,(nil),0x1502e8,0x189fa5 0,0x189faa4) stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x189f704): stub
fixme:imm:ImmReleaseContext (0x4005a, 0x14fe30): stub
fixme:advapi:CreateRestrictedToken (0x24a8, 0x0, 2, 0xcd58120, 19, 0x15275c, 5, 0x189a554, 0x189a61c): stub
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x189a180,0,(nil),0x151b68,0x189a1a 8,0x189a1b4) stub!
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
XIO: fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
after 116 requests (116 known processed) with 0 events remaining.
XIO: fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
after 115 requests (115 known processed) with 0 events remaining.
```





Any help would be greatly appreciated

---

### Post by Bucky Ball on 2013-08-11
Welcome. Please use [code] tags in future and black text. Thanks.

---

### Post by x5metalmonster on 2013-08-11
I just tried editing the Libraries within wine config and now world of warcraft wont even start, I removed all the libraries and its still not starting now. 
**Got it working again by allowing playonlinux to repair the virtual drive.** but it still crashes randomly.

---

### Post by x5metalmonster on 2013-08-11
> **Bucky Ball said:**
> Welcome. Please use [code] tags in future and black text. Thanks.
Im not sure how to put text within a box.

---

### Post by Bucky Ball on 2013-08-11
Use this tag at the beginning of the code:

[code]

---

### Post by Bucky Ball on 2013-08-11
And this one at the end:

[/code]

;)

---

### Post by x5metalmonster on 2013-08-11
```

***Test***

```

---

### Post by x5metalmonster on 2013-08-11
> **Bucky Ball said:**
> And this one at the end:

[/code]

;)


now that iv solved how to put code in boxes.. anyone know anything about my issue :confused:

---

### Post by x5metalmonster on 2013-08-11
When i type this in terminal 

```

glxinfo | grep direct

```

i get this 

```

direct rendering: Yes
    GL_AMD_multi_draw_indirect, GL_AMD_name_gen_delete, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_draw_indirect, 
    GL_EXT_copy_buffer, GL_EXT_copy_texture, GL_EXT_direct_state_access, 
    GL_AMD_multi_draw_indirect, GL_AMD_name_gen_delete, 
    GL_ARB_draw_indirect, GL_ARB_draw_instanced, 
    GL_EXT_copy_buffer, GL_EXT_copy_texture, GL_EXT_direct_state_access, 

```

---

### Post by bapoumba on 2013-08-12
Moved to Wine.

---

### Post by x5metalmonster on 2013-08-14
The error #132 i read may be caused either by a driver.. or a RAM stick. I tried changing my video drivers a few times and none seemed to work, i then decided to try taking out one of my two 4gb RAM sticks.. (Took out the older one) and vualaa i no longer get crashes and game seems to run more smooth.. if you receive an error like this while playing any game in wine try taking out one of your RAM sticks and doing a memory test and eliminate the bad memory stick. 

):P

---

### Post by Bucky Ball on 2013-08-14
Good news about the fix, bad news about the dead RAM.

Please mark thread as solved by following the link in my signature. ;)

---

