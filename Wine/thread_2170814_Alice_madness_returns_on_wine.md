---
title: "Alice madness returns on wine"
date: 2013-08-27
forum: Wine
---

### Post by valentina_papa on 2013-08-27
Hi all, 
I'm in trouble with "Alice madness returns" game and I hope someone can help me. 
Just some quick infos: searched the net, no luck. Reinstalled wine/OS, no luck.

OS: Ubuntu 12.10
EDIT: switched to Ubuntu 13.04)
Wine version: 1.6
Graphic card: AMD Radeon 7870 (pc custom build)
(I know this graphic card is not the best one, but I saw people able to play Alice)
Output of
 ```
glxinfo | grep "OpenGL version"
```
```
OpenGL version string: 4.2.11903 Compatibility Profile Context
```

Output of ```
glxinfo | grep render
```
```
OpenGL renderer string: AMD Radeon HD 7800 Series
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_conditional_render, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_conditional_render, 
```

Output of  ```
lshw -c display | grep driver
``````
configuration: driver=fglrx_pci latency=0
```

When I launch the game it freezes on "EA" logo and then the d3d errors start spamming.
Here is the terminal output:
Same issues with PlayOnLinux.

```
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:win:EnumDisplayDevicesW ((null),0,0x1a5e390,0x00000000), stub!
fixme:wbemprox:client_security_SetBlanket 0xb69db280, 0x14d828, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0xb69db280
fixme:wbemprox:client_security_SetBlanket 0xb69db280, 0x152a18, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0xb69db280
fixme:wbemprox:client_security_SetBlanket 0xb69db280, 0x152a18, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0xb69db280
fixme:wbemprox:client_security_SetBlanket 0xb69db280, 0x152a18, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0xb69db280
fixme:wbemprox:client_security_SetBlanket 0xb69db280, 0x152a18, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0xb69db280
fixme:wbemprox:client_security_SetBlanket 0xb69db280, 0x152a18, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0xb69db280
fixme:wbemprox:client_security_SetBlanket 0xb69db280, 0x152a18, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0xb69db280
fixme:win:EnumDisplayDevicesW ((null),0,0x1a5cb40,0x00000000), stub!
fixme:wbemprox:client_security_SetBlanket 0xb69db280, 0x14d810, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0xb69db280
fixme:wbemprox:client_security_SetBlanket 0xb69db280, 0x14d810, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0xb69db280
fixme:wbemprox:client_security_SetBlanket 0xb69db280, 0x14d810, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0xb69db280
fixme:wbemprox:client_security_SetBlanket 0xb69db280, 0x14d810, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0xb69db280
fixme:wbemprox:client_security_SetBlanket 0xb69db280, 0x14d810, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0xb69db280
fixme:wbemprox:client_security_SetBlanket 0xb69db280, 0x14d810, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0xb69db280
fixme:win:EnumDisplayDevicesW ((null),0,0x1a5dbc0,0x00000000), stub!
fixme:wtsapi:WTSQuerySessionInformationW Stub (nil) 0xffffffff 5 0x2c4d4b4 0x2c4d4a8
fixme:gameux:GameExplorerImpl_VerifyAccess (0x21ed80, L"C:\\Program Files\\EA Games\\Alice Madness Returns\\Alice2\\Binaries\\Win32\\AliceMadnessReturns.exe", 0x1a5e3f8)
fixme:win:EnumDisplayDevicesW ((null),0,0x1a5cfb8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x1a5cd68,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x1a5e448,0x00000000), stub!
fixme:winediag:AUDDRV_GetAudioEndpoint Winepulse is not officially supported by the wine project
fixme:winediag:AUDDRV_GetAudioEndpoint For sound related feedback and support, please visit http://ubuntuforums.org/showthread.php?t=1960599
fixme:imm:ImmEnumInputContext Stub
fixme:imm:ImmEnumInputContext Stub
fixme:imm:ImmEnumInputContext Stub
fixme:pulse:AudioSessionControl_RegisterAudioSessionNotification (0x2c62f30)->(0x1107aacc) - stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Audio",0x1f9ce958): stub
fixme:avrt:AvSetMmThreadPriority (0x12345678)->(1) stub
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 53 (SPI_SETTOGGLEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
fixme:imm:ImmEnumInputContext Stub
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:win:EnumDisplayDevicesW ((null),0,0x214d840,0x00000000), stub!
fixme:d3d9:D3DPERF_SetOptions (0x1) : stub
fixme:d3d:query_init Unhandled query type 0xc.
fixme:imm:ImmEnumInputContext Stub
fixme:imm:ImmEnumInputContext Stub
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
fixme:imm:ImmReleaseContext (0x50024, 0x61e8d60): stub
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1579
fixme:imm:ImmEnumInputContext Stub
fixme:imm:ImmEnumInputContext Stub
fixme:imm:ImmEnumInputContext Stub
fixme:imm:ImmEnumInputContext Stub

```

Thank you so much for every attempt :)

---

### Post by Mark Phelps on 2013-08-28
Wine tends to behave rather poorly with Windows games.  Look through the test results in the link to see if anything helps:  [http://appdb.winehq.org/objectManager.php?sClass=application&iId=13194]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=13194")

But ... a rating of Silver for games generally means that so many features won't work that you're wasting your time.

---

### Post by valentina_papa on 2013-08-30
Yes I read it and it seems only two people reported the same issue. For my problem I only found a couple resources. Is there a way to see if it's an hardware or a wine issue? Because it's my first build I'm a little bit worried about that.

---

