---
title: "Ghost Recon Advanced Warfighter &amp; wine"
date: 2007-03-11
forum: Wine
---

### Post by Iarwain ben-adar on 2007-03-11
Hi there people,

Today i got the ingenious idea of installing GRAW on my FF box (Feisty Fawn).

The game itself installed perfectly, only complaining about DirectX that couldn't be installed :KS 

When i start the game, it loads, i even get to the main menu!!
But when i try to start the game, i choose Single Player, New Campaign.

It loads for about 10 seconds, and then crashes..

Here is the output of wine
> fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x177d28, L"szCatName", 0x1c0f648)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x177d28, L"szClsidCat", 0x1c0f648)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x177d28, L"szName", 0x1c0f648)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"DirectSound: dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x177d28, L"szClsidFilter", 0x1c0f648)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x177d28, L"szName", 0x1c0f638)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x177d28, L"dwMerit", 0x1c0f638)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x177d28, L"dwInputs", 0x1c0f638)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x177d28, L"dwOutputs", 0x1c0f638)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x177ff0, 1, 0x17a2e0)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x177d28, L"szCatName", 0x1c0f648)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x177d28, L"szClsidCat", 0x1c0f648)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x177d28, L"szName", 0x1c0f648)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D1-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x177d28, L"szClsidFilter", 0x1c0f648)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x177d28, L"szName", 0x1c0f638)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x177d28, L"dwMerit", 0x1c0f638)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x177d28, L"dwInputs", 0x1c0f638)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x177d28, L"dwOutputs", 0x1c0f638)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x163948, L"DxDiag_DirectShowFilters", 0x177d28)
fixme:dxdiag:IDxDiagContainerImpl_GetChildContainer (0x163948, L"DxDiag_SystemInfo", 0x1c0f5f0)
fixme:dxdiag:IDxDiagContainerImpl_GetProp (0x163968, L"dwDirectXVersionMajor", 0x1c0f634)
fixme:dxdiag:IDxDiagContainerImpl_GetProp (0x163968, L"dwDirectXVersionMinor", 0x1c0f634)
fixme:dxdiag:IDxDiagContainerImpl_GetProp (0x163968, L"szDirectXVersionLetter", 0x1c0f634)
fixme:dxdiag:IDxDiagContainerImpl_GetChildContainer (0x163948, L"DxDiag_DisplayDevices", 0x1c0f610)
fixme:dxdiag:IDxDiagContainerImpl_GetChildContainer (0x177560, L"0", 0x1c0f588)
fixme:dxdiag:IDxDiagContainerImpl_GetChildContainer (0x163948, L"DxDiag_DirectSound", 0x1c0f548)
fixme:dxdiag:IDxDiagContainerImpl_GetChildContainer (0x1775d0, L"DxDiag_SoundDevices", 0x1c0f548)
fixme:dxdiag:IDxDiagContainerImpl_GetChildContainer (0x1775f0, L"0", 0x1c0f5d0)
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x17afe8) : stub, simulating 256MB for now, returning 256MB left
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 53 (SPI_SETTOGGLEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
fixme:setupapi:SetupDiGetClassDevsW : returning empty list
fixme:setupapi:SetupDiEnumDeviceInterfaces 0x174cb8, (nil), {29d2a384-2e47-49b5-aebf-6962c22bd7c2}, 0x00000000, 0x1c0f5a0
Unable to find any Athena Hardware devices!
fixme:d3d_shader:shader_get_opcode Unsupported opcode 0x4000025(67108901) masked 0x25, shader version 0xfffe0201
fixme:d3d_shader:shader_trace_init Unrecognized opcode: token=04000025
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=80020000 addr_token=00000000 name=
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=80aa0001 addr_token=00000000 name=
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=a0e400ed addr_token=00000000 name=
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=80550000 addr_token=00000000 name=
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=80080000 addr_token=00000000 name=
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=80080000 addr_token=00000000 name=
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=a0ff00e9 addr_token=00000000 name=
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=80030001 addr_token=00000000 name=
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=80040003 addr_token=00000000 name=
fixme:d3d_shader:shader_get_opcode Unsupported opcode 0x4000025(67108901) masked 0x25, shader version 0xfffe0201
fixme:d3d_shader:shader_trace_init Unrecognized opcode: token=04000025
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=80030000 addr_token=00000000 name=
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=80aa0001 addr_token=00000000 name=
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=a0e400ed addr_token=00000000 name=
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=80e10000 addr_token=00000000 name=
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=81ff0001 addr_token=00000000 name=
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=90550004 addr_token=00000000 name=
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=80550001 addr_token=00000000 name=
fixme:d3d_shader:shader_get_opcode Unsupported opcode 0x4000025(67108901) masked 0x25, shader version 0xfffe0201
fixme:d3d_shader:shader_get_opcode Unsupported opcode 0x4000025(67108901) masked 0x25, shader version 0xfffe0201
fixme:d3d_shader:shader_get_opcode Unsupported opcode 0x4000025(67108901) masked 0x25, shader version 0xfffe0201
fixme:d3d_shader:shader_trace_init Unrecognized opcode: token=04000025
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=80020000 addr_token=00000000 name=
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=80ff0001 addr_token=00000000 name=
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=a0e40074 addr_token=00000000 name=
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=80c90001 addr_token=00000000 name=
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=80550000 addr_token=00000000 name=
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=80e40001 addr_token=00000000 name=
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=a0000072 addr_token=00000000 name=
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=80ff0000 addr_token=00000000 name=
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=a0aa0071 addr_token=00000000 name=
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=80ff0000 addr_token=00000000 name=
fixme:d3d_shader:shader_get_opcode Unsupported opcode 0xa0552050(-1605033904) masked 0x2050, shader version 0xfffe0201
fixme:d3d_shader:shader_trace_init Unrecognized opcode: token=a0552050
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=b0ff0000 addr_token=00000000 name=
fixme:d3d_shader:shader_get_opcode Unsupported opcode 0x4000025(67108901) masked 0x25, shader version 0xfffe0201
fixme:d3d_shader:shader_trace_init Unrecognized opcode: token=04000025
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=80030001 addr_token=00000000 name=
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=80ff0000 addr_token=00000000 name=
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=a0e40074 addr_token=00000000 name=
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=80e40000 addr_token=00000000 name=
fixme:d3d_shader:shader_skip_unrecognized Unrecognized opcode param: token=91000003 addr_token=00000000 name=
fixme:d3d_shader:shader_dump_ins_modifiers _unrecognized_modifier(0x8)Unsupported opcode 0x4000025(67108901) masked 0x25, shader version 0xfffe0201
fixme:d3d_shader:shader_get_opcode Unsupported opcode 0x4000025(67108901) masked 0x25, shader version 0xfffe0201
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 3, state 6 D3DSAMP_MIPFILTER value 3, state 7
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 3, state 6 D3DSAMP_MIPFILTER value 3, state 7
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 3, state 6 D3DSAMP_MIPFILTER value 3, state 7
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 2, state 6 D3DSAMP_MIPFILTER value 3, state 7
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 2, state 6 D3DSAMP_MIPFILTER value 3, state 7
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 2, state 6 D3DSAMP_MIPFILTER value 3, state 7
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 2, state 6 D3DSAMP_MIPFILTER value 3, state 7
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 2, state 6 D3DSAMP_MIPFILTER value 3, state 7
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 2, state 6 D3DSAMP_MIPFILTER value 3, state 7
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 2, state 6 D3DSAMP_MIPFILTER value 3, state 7
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 2, state 6 D3DSAMP_MIPFILTER value 3, state 7
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 2, state 6 D3DSAMP_MIPFILTER value 3, state 7
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 2, state 6 D3DSAMP_MIPFILTER value 3, state 7
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 3, state 6 D3DSAMP_MIPFILTER value 3, state 7
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 3, state 6 D3DSAMP_MIPFILTER value 3, state 7
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 3, state 6 D3DSAMP_MIPFILTER value 3, state 7
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 2, state 6 D3DSAMP_MIPFILTER value 3, state 7
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 2, state 6 D3DSAMP_MIPFILTER value 3, state 7
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 2, state 6 D3DSAMP_MIPFILTER value 3, state 7
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 2, state 6 D3DSAMP_MIPFILTER value 3, state 7
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 2, state 6 D3DSAMP_MIPFILTER value 3, state 7
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 2, state 6 D3DSAMP_MIPFILTER value 3, state 7
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 2, state 6 D3DSAMP_MIPFILTER value 3, state 7
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 2, state 6 D3DSAMP_MIPFILTER value 3, state 7
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 2, state 6 D3DSAMP_MIPFILTER value 3, state 7
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 2, state 6 D3DSAMP_MIPFILTER value 3, state 7
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 2, state 6 D3DSAMP_MIPFILTER value 3, state 7
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 2, state 6 D3DSAMP_MIPFILTER value 3, state 7
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 2, state 6 D3DSAMP_MIPFILTER value 3, state 7
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 2, state 6 D3DSAMP_MIPFILTER value 3, state 7
wine: Unhandled page fault on read access to 0x000002a0 at address 0x7ec5bb26 (thread 002b), starting debugger...
Unhandled exception: page fault on read access to 0x000002a0 in 32-bit code (0x7ec5bb26).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7ec5bb26 ESP:791a67d0 EBP:791a680c EFLAGS:00010202(   - 00      - -RI1)
 EAX:00000000 EBX:7ee320bc ECX:7d8d9164 EDX:791a6800
 ESI:001cab58 EDI:791a6884
Stack dump:
0x791a67d0:  7ede6af3 00000de1 7ee2d280 791a6800
0x791a67e0:  791a6830 30015e68 80000005 000000c0
0x791a67f0:  086d4cfc 000000c0 0000002e 7ede002b
0x791a6800:  00000000 7ee320bc 791a6860 791a68bc
0x791a6810:  7eda14c2 001cab58 791a6860 791a686c
0x791a6820:  7edea35a 7ee320bc 791a68dc 791a685c
Backtrace:
=>1 0x7ec5bb26 glTexImage2D+0x406() in libgl.so.1 (0x791a680c)
  2 0x7eda14c2 in wined3d (+0x114c2) (0x791a68bc)
  3 0x7ee4a17d in d3d9 (+0xa17d) (0x791a68ec)
  4 0x005b157a in graw (+0x1b157a) (0x10c9df50)
  5 0x0000001c (0x00cfcc24)
  6 0x004d83d0 in graw (+0xd83d0) (0x0048f1f0)
0x7ec5bb26 glTexImage2D+0x406 in libgl.so.1: jmp        *0x2a0(%eax)
Modules:
Module  Address                 Debug info      Name (107 modules)
PE      230000-27d000   Deferred        nxcooking
PE      280000-28e000   Deferred        physxloader
PE      400000-19f2000  Export          graw
PE      6b40000-6d0e000 Deferred        wrap_oal
PE      78b0000-7af9000 Deferred        physxcore
PE      10000000-10016000       Deferred        openal32
PE      30000000-3006d000       Deferred        binkw32
ELF     7b800000-7b91c000       Deferred        kernel32<elf>
  \-PE  7b820000-7b91c000       \               kernel32
ELF     7bc00000-7bc83000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc83000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c21f000-7c27b000       Deferred        setupapi<elf>
  \-PE  7c230000-7c27b000       \               setupapi
ELF     7c27b000-7c27e000       Deferred        libnss_mdns4_minimal.so.2
ELF     7c2c3000-7c2c9000       Deferred        libnss_dns.so.2
ELF     7c2fc000-7c345000       Deferred        dsound<elf>
  \-PE  7c300000-7c345000       \               dsound
ELF     7c785000-7c799000       Deferred        avicap32<elf>
  \-PE  7c790000-7c799000       \               avicap32
ELF     7c799000-7c7b8000       Deferred        devenum<elf>
  \-PE  7c7a0000-7c7b8000       \               devenum
ELF     7c7b8000-7c7cc000       Deferred        lz32<elf>
  \-PE  7c7c0000-7c7cc000       \               lz32
ELF     7c7cc000-7c7e5000       Deferred        version<elf>
  \-PE  7c7d0000-7c7e5000       \               version
ELF     7c7e5000-7c7ff000       Deferred        dxdiagn<elf>
  \-PE  7c7f0000-7c7ff000       \               dxdiagn
ELF     7c81f000-7c851000       Deferred        uxtheme<elf>
  \-PE  7c830000-7c851000       \               uxtheme
ELF     7c851000-7c866000       Deferred        midimap<elf>
  \-PE  7c860000-7c866000       \               midimap
ELF     7c88c000-7c951000       Deferred        libasound.so.2
ELF     7c951000-7c97a000       Deferred        winealsa<elf>
  \-PE  7c960000-7c97a000       \               winealsa
ELF     7cbd7000-7cbef000       Deferred        msacm32<elf>
  \-PE  7cbe0000-7cbef000       \               msacm32
ELF     7cbf1000-7cbf6000       Deferred        libxfixes.so.3
ELF     7cbf6000-7cbff000       Deferred        libxcursor.so.1
ELF     7cbff000-7cc1b000       Deferred        imm32<elf>
  \-PE  7cc10000-7cc1b000       \               imm32
ELF     7cc1b000-7cc21000       Deferred        libxrandr.so.2
ELF     7cc21000-7cc29000       Deferred        libxrender.so.1
ELF     7cc29000-7cc2c000       Deferred        libxinerama.so.1
ELF     7d852000-7d8df000       Deferred        winex11<elf>
  \-PE  7d860000-7d8df000       \               winex11
ELF     7d98e000-7d9ae000       Deferred        libexpat.so.1
ELF     7d9ae000-7d9d9000       Deferred        libfontconfig.so.1
ELF     7d9d9000-7d9ed000       Deferred        libz.so.1
ELF     7d9ed000-7da57000       Deferred        libfreetype.so.6
ELF     7da57000-7daef000       Deferred        oleaut32<elf>
  \-PE  7da70000-7daef000       \               oleaut32
ELF     7daef000-7dbaf000       Deferred        comctl32<elf>
  \-PE  7db00000-7dbaf000       \               comctl32
ELF     7dbaf000-7dc07000       Deferred        shlwapi<elf>
  \-PE  7dbc0000-7dc07000       \               shlwapi
ELF     7dc07000-7dcf9000       Deferred        shell32<elf>
  \-PE  7dc20000-7dcf9000       \               shell32
ELF     7dcf9000-7dd87000       Deferred        winmm<elf>
  \-PE  7dd00000-7dd87000       \               winmm
ELF     7dd87000-7ddb3000       Deferred        ws2_32<elf>
  \-PE  7dd90000-7ddb3000       \               ws2_32
ELF     7ddb3000-7ddd1000       Deferred        iphlpapi<elf>
  \-PE  7ddc0000-7ddd1000       \               iphlpapi
ELF     7ddd1000-7de25000       Deferred        rpcrt4<elf>
  \-PE  7dde0000-7de25000       \               rpcrt4
ELF     7de25000-7debe000       Deferred        ole32<elf>
  \-PE  7de30000-7debe000       \               ole32
ELF     7debe000-7def5000       Deferred        dinput<elf>
  \-PE  7ded0000-7def5000       \               dinput
ELF     7def5000-7df0e000       Deferred        dinput8<elf>
  \-PE  7df00000-7df0e000       \               dinput8
ELF     7df0e000-7df54000       Deferred        advapi32<elf>
  \-PE  7df20000-7df54000       \               advapi32
ELF     7df54000-7e00a000       Deferred        gdi32<elf>
  \-PE  7df70000-7e00a000       \               gdi32
ELF     7e00a000-7e142000       Deferred        user32<elf>
  \-PE  7e020000-7e142000       \               user32
ELF     7e1a5000-7e1aa000       Deferred        libxdmcp.so.6
ELF     7e1aa000-7e1b6000       Deferred        libgcc_s.so.1
ELF     7e1b7000-7e1ca000       Deferred        libresolv.so.2
ELF     7e2b6000-7e2b8000       Deferred        libnvidia-tls.so.1
ELF     7e2b8000-7eb3e000       Deferred        libglcore.so.1
ELF     7eb3e000-7eb56000       Deferred        libxcb.so.1
ELF     7eb56000-7eb58000       Deferred        libxcb-xlib.so.0
ELF     7eb58000-7ebd8000       Deferred        libglu.so.1
ELF     7ebd8000-7ec64000       Export          libgl.so.1
ELF     7ec64000-7ed4f000       Deferred        libx11.so.6
ELF     7ed4f000-7ed5d000       Deferred        libxext.so.6
ELF     7ed5d000-7ed62000       Deferred        libxxf86vm.so.1
ELF     7ed62000-7ed7a000       Deferred        libice.so.6
ELF     7ed7a000-7ee33000       Export          wined3d<elf>
  \-PE  7ed90000-7ee33000       \               wined3d
ELF     7ee33000-7ee5d000       Export          d3d9<elf>
  \-PE  7ee40000-7ee5d000       \               d3d9
ELF     7ef8e000-7ef99000       Deferred        libnss_files.so.2
ELF     7ef99000-7efa3000       Deferred        libnss_nis.so.2
ELF     7efa3000-7efba000       Deferred        libnsl.so.1
ELF     7efba000-7efc3000       Deferred        libnss_compat.so.2
ELF     7efc3000-7efea000       Deferred        libm.so.6
ELF     7efeb000-7efee000       Deferred        libxau.so.6
ELF     7efee000-7eff7000       Deferred        libsm.so.6
ELF     b7c93000-b7c97000       Deferred        libdl.so.2
ELF     b7c97000-b7dd8000       Deferred        libc.so.6
ELF     b7dd9000-b7df0000       Deferred        libpthread.so.0
ELF     b7e06000-b7f17000       Deferred        libwine.so.1
ELF     b7f19000-b7f34000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a
        0000000c    0
        0000000b    0
00000008 (D) Z:\home\iarwain\.wine\drive_c\Program Files\Ubisoft\Ghost Recon Advanced Warfighter\graw.exe
        0000002b    0 <==
        00000029    0
        00000028   15
        00000010   15
        0000000e    0
        0000000d    0
        00000009    0

What could be giving this error? (the machine is perfectly capable of playing the game)


Iarwain

---

### Post by PurplePenguin on 2007-03-11
You're surprised that Wine won't run Advanced Warfighter?  I'm surprised that you got to the menu! :)

---

### Post by Iarwain ben-adar on 2007-03-11
I said it was an ingenious idea :D


I copied my d3dx* from my real Windows to my Wine system32.
That cleared some errors :D


Iarwain

---

### Post by rexless on 2007-11-04
Hey All.
I've got my machine setup in a dual-boot with XP and Ubuntu 7.10
I thought, for kicks, I'd see what happens when I try to run GRAW2 off of my XP partition using WINE.  I had to download and install the Ageia PhysX drivers with WINE which seemed to work fine.

I then launched GRAW2 and it took a fair bit of time, but did get as far as loading the menu.  It complained I had an unsupported video card (GeoForce 7900GS - Dell Inspiron version) which isn't actually true since I run GRAW2 on XP.

Anyway, it tried to load the campaign but blew chunks after about 5 minutes of trying to start the game.  Too bad Cedega is dead these days... looks like it would be possible to get running with a guru's touch.

---

### Post by hikaricore on 2007-11-04
Cedega = crap

Just so ya know.

---

### Post by Crafty Kisses on 2007-11-04
> **hikaricore said:**
> Cedega = crap

Just so ya know.
I don't like Cedega either.

---

