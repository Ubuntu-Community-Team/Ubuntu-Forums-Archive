---
title: "Yandere Simulator"
date: 2016-08-04
forum: Wine
---

### Post by goldenfreddy42 on 2016-08-04
I am trying to play Yandere Simulator using a custom made wine. I am new to ubuntu, so I might've messed it up. Here is the code I got while trying to run the game from a shell script.
```
./USB
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:system:SetProcessDPIAware stub!
Mono path[0] = 'F:/Yandere/YandereSimulator_Data/Managed'
Mono path[1] = 'F:/Yandere/YandereSimulator_Data/Mono'
Mono config path = 'F:/Yandere/YandereSimulator_Data/Mono/etc'
fixme:win:EnumDisplayDevicesW ((null),0,0x33f494,0x00000000), stub!
fixme:win:EnumDisplayDevicesW (L"\\\\.\\DISPLAY1",0,0x33f494,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x33f494,0x00000000), stub!
fixme:imm:ImmReleaseContext (0x1006c, 0x147be8): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6e4,0x00000000), stub!
fixme:d3d11:D3D11CreateDevice stub: adapter 0x1496a8, driver_type D3D_DRIVER_TYPE_UNKNOWN, swrast (nil), flags 0x1, feature_levels 19964484, levels 0x3, sdk_version 7, device 0xe3ed60, feature_level 0x33fbb0, context 0xe3ed1c
fixme:win:EnumDisplayDevicesW ((null),0,0x33f524,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f424,0x00000000), stub!
fixme:dxgi:dxgi_output_GetDesc iface 0x150520, desc 0x33f9cc stub!
fixme:wbemprox:client_security_SetBlanket 0xf73902c4, 0x150580, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0xf73902c4
fixme:win:EnumDisplayDevicesW ((null),0,0x33f304,0x00000000), stub!
fixme:dbghelp:validate_addr64 Unsupported address fffffffff73f0000
fixme:dbghelp:validate_addr64 Unsupported address fffffffff73e0000
fixme:dbghelp:validate_addr64 Unsupported address fffffffff7370000
fixme:dbghelp:validate_addr64 Unsupported address fffffffff7340000
fixme:dbghelp:validate_addr64 Unsupported address fffffffff2970000
fixme:dbghelp:validate_addr64 Unsupported address fffffffff72e0000
fixme:dbghelp:validate_addr64 Unsupported address fffffffff19b0000
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x7bc367a1


```

Any help is appreciated

---

### Post by goldenfreddy42 on 2016-08-04
I went to where the dll files are at in winecfg and set them to remove all of the settings, and it fixed it.

---

### Post by QDR06VV9 on 2016-08-04
Good Job... and thanks for sharing your solution.
Kind Regards
Welcome to UF

---

