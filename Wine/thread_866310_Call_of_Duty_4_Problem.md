---
title: "Call of Duty 4 Problem"
date: 2008-07-21
forum: Wine
---

### Post by chaosdesigner on 2008-07-21
Hi, 

for quite some time now I've been trying to get cod4 to run, i looked at many guides on how to install cod4 and i already patched wine and everything, now the games starts but immediately gets black and the resolution gets very low (which somehow always happens when i start wine applications ...) and I get this message:

```

err:module:import_dll Library d3dx8.dll (which is needed by L"C:\\windows\\system32\\d3dx9_36.dll") not found
err:module:find_forwarded_export module not found for forward 'd3dx9_36.D3DXCompileShader' used by L"C:\\windows\\system32\\d3dx9_34.dll"
err:module:import_dll Library d3dx8.dll (which is needed by L"C:\\windows\\system32\\d3dx9_36.dll") not found
err:module:find_forwarded_export module not found for forward 'd3dx9_36.D3DXGetShaderInputSemantics' used by L"C:\\windows\\system32\\d3dx9_34.dll"
err:module:import_dll Library d3dx8.dll (which is needed by L"C:\\windows\\system32\\d3dx9_36.dll") not found
err:module:find_forwarded_export module not found for forward 'd3dx9_36.D3DXCreateBuffer' used by L"C:\\windows\\system32\\d3dx9_34.dll"
err:module:import_dll Library d3dx8.dll (which is needed by L"C:\\windows\\system32\\d3dx9_36.dll") not found
err:module:find_forwarded_export module not found for forward 'd3dx9_36.D3DXGetShaderConstantTable' used by L"C:\\windows\\system32\\d3dx9_34.dll"
err:module:import_dll Library d3dx8.dll (which is needed by L"C:\\windows\\system32\\d3dx9_36.dll") not found
err:module:find_forwarded_export module not found for forward 'd3dx9_36.D3DXGetShaderOutputSemantics' used by L"C:\\windows\\system32\\d3dx9_34.dll"
fixme:win:EnumDisplayDevicesW ((null),0,0x32f8e4,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1c6c01e8) : pBox=(nil) stub
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2559
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2559
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2559
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2559
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
wine: Unhandled page fault on read access to 0x0000003c at address 0x4ed006 (thread 0061), starting debugger...
Unhandled exception: page fault on read access to 0x0000003c in 32-bit code (0x004ed006).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:004ed006 ESP:0032fd10 EBP:0032fd54 EFLAGS:00010206(   - 00      - RIP1)
 EAX:00000000 EBX:7edff740 ECX:0cbbece0 EDX:0000ffff
 ESI:00000000 EDI:00000001
Stack dump:
0x0032fd10:  0cc1b450 00000000 0032fcf4 0057aebc
0x0032fd20:  00000000 027faf78 0000ffff 0046c9f7
0x0032fd30:  00001388 00001388 0cc12048 0050019a
0x0032fd40:  00400000 7b88c540 0032fd54 00000000
0x0032fd50:  0050038f 0032fd60 0050039d 7b88e5f0
0x0032fd60:  0032ff08 005777a3 00000a28 00000002
Backtrace:
=>1 0x004ed006 in iw3mp (+0xed006) (0x0032fd54)
  2 0x0050039d in iw3mp (+0x10039d) (0x0032fd60)
  3 0x005777a3 in iw3mp (+0x1777a3) (0x0032ff08)
  4 0x7b877b37 start_process+0xc7(arg=0x0) [/home/jakob/wine-1.0/dlls/kernel32/process.c:904] in kernel32 (0x0032ffe8)
  5 0xf7e44a37 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x004ed006: cmpb	$0x0,0x3c(%esi)
Modules:
Module	Address			Debug info	Name (90 modules)
PE	  400000- d936000	Export          iw3mp
PE	18000000-18033000	Deferred        binkw32
PE	21100000-21197000	Deferred        mss32
ELF	7b800000-7b92d000	Dwarf           kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca5000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca5000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7d5dd000-7e0f2000	Deferred        libglcore.so.1
ELF	7e100000-7e103000	Deferred        libnss_mdns4.so.2
ELF	7e103000-7e109000	Deferred        libnss_dns.so.2
ELF	7e109000-7e10c000	Deferred        libnss_mdns4_minimal.so.2
ELF	7e10c000-7e1b0000	Deferred        libgl.so.1
ELF	7e205000-7e238000	Deferred        uxtheme<elf>
  \-PE	7e210000-7e238000	\               uxtheme
ELF	7e260000-7e274000	Deferred        midimap<elf>
  \-PE	7e270000-7e274000	\               midimap
ELF	7e274000-7e29a000	Deferred        msacm32<elf>
  \-PE	7e280000-7e29a000	\               msacm32
ELF	7e29a000-7e2b1000	Deferred        msacm32<elf>
  \-PE	7e2a0000-7e2b1000	\               msacm32
ELF	7e2b1000-7e2ec000	Deferred        wineoss<elf>
  \-PE	7e2c0000-7e2ec000	\               wineoss
ELF	7e2ec000-7e2f1000	Deferred        libxfixes.so.3
ELF	7e2fe000-7e300000	Deferred        libnvidia-tls.so.1
ELF	7e302000-7e30b000	Deferred        libxcursor.so.1
ELF	7e30b000-7e30e000	Deferred        libxcomposite.so.1
ELF	7e30e000-7e314000	Deferred        libxrandr.so.2
ELF	7e314000-7e31c000	Deferred        libxrender.so.1
ELF	7e31c000-7e31f000	Deferred        libxinerama.so.1
ELF	7e31f000-7e33f000	Deferred        imm32<elf>
  \-PE	7e330000-7e33f000	\               imm32
ELF	7e33f000-7e344000	Deferred        libxdmcp.so.6
ELF	7e344000-7e35c000	Deferred        libxcb.so.1
ELF	7e35c000-7e35e000	Deferred        libxcb-xlib.so.0
ELF	7e35e000-7e361000	Deferred        libxau.so.6
ELF	7e361000-7e448000	Deferred        libx11.so.6
ELF	7e448000-7e456000	Deferred        libxext.so.6
ELF	7e456000-7e45b000	Deferred        libxxf86vm.so.1
ELF	7e45b000-7e4f2000	Deferred        winex11<elf>
  \-PE	7e470000-7e4f2000	\               winex11
ELF	7e530000-7e551000	Deferred        libexpat.so.1
ELF	7e551000-7e57b000	Deferred        libfontconfig.so.1
ELF	7e57b000-7e590000	Deferred        libz.so.1
ELF	7e5aa000-7e61a000	Deferred        libfreetype.so.6
ELF	7e61a000-7e671000	Deferred        ddraw<elf>
  \-PE	7e620000-7e671000	\               ddraw
ELF	7e671000-7e730000	Deferred        comctl32<elf>
  \-PE	7e680000-7e730000	\               comctl32
ELF	7e730000-7e789000	Deferred        shlwapi<elf>
  \-PE	7e740000-7e789000	\               shlwapi
ELF	7e789000-7e89d000	Deferred        shell32<elf>
  \-PE	7e7a0000-7e89d000	\               shell32
ELF	7e89d000-7e8fe000	Deferred        rpcrt4<elf>
  \-PE	7e8b0000-7e8fe000	\               rpcrt4
ELF	7e8fe000-7e9a2000	Deferred        ole32<elf>
  \-PE	7e910000-7e9a2000	\               ole32
ELF	7e9a2000-7e9ec000	Deferred        dsound<elf>
  \-PE	7e9b0000-7e9ec000	\               dsound
ELF	7e9ec000-7ea05000	Deferred        d3dx9_34<elf>
  \-PE	7e9f0000-7ea05000	\               d3dx9_34
ELF	7ea05000-7eb08000	Deferred        wined3d<elf>
  \-PE	7ea20000-7eb08000	\               wined3d
ELF	7eb08000-7eb38000	Deferred        d3d9<elf>
  \-PE	7eb10000-7eb38000	\               d3d9
ELF	7eb38000-7eb4b000	Deferred        libresolv.so.2
ELF	7eb4b000-7eb69000	Deferred        iphlpapi<elf>
  \-PE	7eb50000-7eb69000	\               iphlpapi
ELF	7eb69000-7eb95000	Deferred        ws2_32<elf>
  \-PE	7eb70000-7eb95000	\               ws2_32
ELF	7eb95000-7ebe7000	Deferred        advapi32<elf>
  \-PE	7eba0000-7ebe7000	\               advapi32
ELF	7ebe7000-7ec82000	Deferred        gdi32<elf>
  \-PE	7ec00000-7ec82000	\               gdi32
ELF	7ec82000-7edc9000	Deferred        user32<elf>
  \-PE	7eca0000-7edc9000	\               user32
ELF	7edc9000-7ee5b000	Deferred        winmm<elf>
  \-PE	7edd0000-7ee5b000	\               winmm
ELF	7ef7b000-7ef86000	Deferred        libnss_files.so.2
ELF	7ef86000-7efa0000	Deferred        wsock32<elf>
  \-PE	7ef90000-7efa0000	\               wsock32
ELF	7efa0000-7efb8000	Deferred        libnsl.so.1
ELF	7efc8000-7efd2000	Deferred        libnss_nis.so.2
ELF	7efd2000-7efdb000	Deferred        libnss_compat.so.2
ELF	7efdb000-7f000000	Deferred        libm.so.6
ELF	f7cd1000-f7cd5000	Deferred        libdl.so.2
ELF	f7cd5000-f7e24000	Deferred        libc.so.6
ELF	f7e25000-f7e3d000	Deferred        libpthread.so.0
ELF	f7e3d000-f7f73000	Dwarf           libwine.so.1
ELF	f7f75000-f7f94000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
	00000033    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000018 
	00000019    0
0000001c 
	0000002e    0
	00000020    0
	0000001f    0
	0000001e    0
	0000001d    0
00000030 
	00000037    0
	00000036    0
	00000035    0
	00000032    0
	00000031    0
0000003d 
	00000009    0
	00000041    0
	00000040    0
	0000003f    0
	0000003e    0
00000063 
	00000049    0
	00000067    0
	00000066    0
	00000065    0
	00000064    0
00000024 (D) C:\Program_Files\Activision\CallOfDuty4\iw3mp.exe
	00000022   15
	0000004e    0
	00000056    0
	00000028    0
	00000051    0
	00000062    1
	00000061    0 <==
Backtrace:
=>1 0x004ed006 in iw3mp (+0xed006) (0x0032fd54)
  2 0x0050039d in iw3mp (+0x10039d) (0x0032fd60)
  3 0x005777a3 in iw3mp (+0x1777a3) (0x0032ff08)
  4 0x7b877b37 start_process+0xc7(arg=0x0) [/home/jakob/wine-1.0/dlls/kernel32/process.c:904] in kernel32 (0x0032ffe8)
  5 0xf7e44a37 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)

```

I have wine-1.0 ...

does somebody have an idea what i could do?

I think first im going to try to maybe install some dll that were mentioned.

---

### Post by chaosdesigner on 2008-07-21
Update:

I've made d3dx9_36, d3dx9_34, and d3dx8.dll native and now i get this message :

```

fixme:win:EnumDisplayDevicesW ((null),0,0x32f8e4,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1b2d0238) : pBox=(nil) stub
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2559
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2559
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2559
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2559
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
wine: Unhandled page fault on read access to 0x0000003c at address 0x4ed006 (thread 005a), starting debugger...
Unhandled exception: page fault on read access to 0x0000003c in 32-bit code (0x004ed006).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:004ed006 ESP:0032fd10 EBP:0032fd54 EFLAGS:00010206(   - 00      - RIP1)
 EAX:00000000 EBX:7ee29740 ECX:0cbbece0 EDX:0000ffff
 ESI:00000000 EDI:00000001
Stack dump:
0x0032fd10:  0cc1b450 00000000 0032fcf4 0057aebc
0x0032fd20:  00000000 027faf78 0000ffff 0046c9f7
0x0032fd30:  00001388 00001388 0cc12048 0050019a
0x0032fd40:  00400000 7b88c540 0032fd54 00000000
0x0032fd50:  0050038f 0032fd60 0050039d 7b88e5f0
0x0032fd60:  0032ff08 005777a3 00000a28 00000002
Backtrace:
=>1 0x004ed006 in iw3mp (+0xed006) (0x0032fd54)
  2 0x0050039d in iw3mp (+0x10039d) (0x0032fd60)
  3 0x005777a3 in iw3mp (+0x1777a3) (0x0032ff08)
  4 0x7b877b37 start_process+0xc7(arg=0x0) [/home/jakob/wine-1.0/dlls/kernel32/process.c:904] in kernel32 (0x0032ffe8)
  5 0xf7eaea37 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x004ed006: cmpb	$0x0,0x3c(%esi)
Modules:
Module	Address			Debug info	Name (91 modules)
PE	  400000- d936000	Export          iw3mp
PE	 d940000- dcaf000	Deferred        d3dx9_34
PE	18000000-18033000	Deferred        binkw32
PE	21100000-21197000	Deferred        mss32
ELF	7b800000-7b92d000	Dwarf           kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca5000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca5000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7d595000-7e0aa000	Deferred        libglcore.so.1
ELF	7e0bb000-7e0be000	Deferred        libnss_mdns4.so.2
ELF	7e0be000-7e0c4000	Deferred        libnss_dns.so.2
ELF	7e0c4000-7e168000	Deferred        libgl.so.1
ELF	7e190000-7e193000	Deferred        libnss_mdns4_minimal.so.2
ELF	7e1bd000-7e1f0000	Deferred        uxtheme<elf>
  \-PE	7e1c0000-7e1f0000	\               uxtheme
ELF	7e218000-7e22c000	Deferred        midimap<elf>
  \-PE	7e220000-7e22c000	\               midimap
ELF	7e22c000-7e252000	Deferred        msacm32<elf>
  \-PE	7e230000-7e252000	\               msacm32
ELF	7e252000-7e269000	Deferred        msacm32<elf>
  \-PE	7e260000-7e269000	\               msacm32
ELF	7e269000-7e2a4000	Deferred        wineoss<elf>
  \-PE	7e270000-7e2a4000	\               wineoss
ELF	7e2a4000-7e2a9000	Deferred        libxfixes.so.3
ELF	7e2b6000-7e2b8000	Deferred        libnvidia-tls.so.1
ELF	7e2ba000-7e2c3000	Deferred        libxcursor.so.1
ELF	7e2c3000-7e2c6000	Deferred        libxcomposite.so.1
ELF	7e2c6000-7e2cc000	Deferred        libxrandr.so.2
ELF	7e2cc000-7e2d4000	Deferred        libxrender.so.1
ELF	7e2d4000-7e2d7000	Deferred        libxinerama.so.1
ELF	7e2d7000-7e2f7000	Deferred        imm32<elf>
  \-PE	7e2e0000-7e2f7000	\               imm32
ELF	7e2f7000-7e2fc000	Deferred        libxdmcp.so.6
ELF	7e2fc000-7e314000	Deferred        libxcb.so.1
ELF	7e314000-7e316000	Deferred        libxcb-xlib.so.0
ELF	7e316000-7e319000	Deferred        libxau.so.6
ELF	7e319000-7e400000	Deferred        libx11.so.6
ELF	7e400000-7e40e000	Deferred        libxext.so.6
ELF	7e40e000-7e413000	Deferred        libxxf86vm.so.1
ELF	7e413000-7e4aa000	Deferred        winex11<elf>
  \-PE	7e420000-7e4aa000	\               winex11
ELF	7e4ef000-7e510000	Deferred        libexpat.so.1
ELF	7e510000-7e53a000	Deferred        libfontconfig.so.1
ELF	7e53a000-7e54f000	Deferred        libz.so.1
ELF	7e569000-7e5d9000	Deferred        libfreetype.so.6
ELF	7e5d9000-7e630000	Deferred        ddraw<elf>
  \-PE	7e5e0000-7e630000	\               ddraw
ELF	7e630000-7e6ef000	Deferred        comctl32<elf>
  \-PE	7e640000-7e6ef000	\               comctl32
ELF	7e6ef000-7e748000	Deferred        shlwapi<elf>
  \-PE	7e700000-7e748000	\               shlwapi
ELF	7e748000-7e85c000	Deferred        shell32<elf>
  \-PE	7e760000-7e85c000	\               shell32
ELF	7e85c000-7e8bd000	Deferred        rpcrt4<elf>
  \-PE	7e870000-7e8bd000	\               rpcrt4
ELF	7e8bd000-7e961000	Deferred        ole32<elf>
  \-PE	7e8d0000-7e961000	\               ole32
ELF	7e961000-7e9ab000	Deferred        dsound<elf>
  \-PE	7e970000-7e9ab000	\               dsound
ELF	7e9ab000-7ea15000	Deferred        msvcrt<elf>
  \-PE	7e9c0000-7ea15000	\               msvcrt
ELF	7ea15000-7eb18000	Deferred        wined3d<elf>
  \-PE	7ea30000-7eb18000	\               wined3d
ELF	7eb18000-7eb48000	Deferred        d3d9<elf>
  \-PE	7eb20000-7eb48000	\               d3d9
ELF	7eb48000-7eb5b000	Deferred        libresolv.so.2
ELF	7eb5b000-7eb79000	Deferred        iphlpapi<elf>
  \-PE	7eb60000-7eb79000	\               iphlpapi
ELF	7eb79000-7eba5000	Deferred        ws2_32<elf>
  \-PE	7eb80000-7eba5000	\               ws2_32
ELF	7eba5000-7ebbf000	Deferred        wsock32<elf>
  \-PE	7ebb0000-7ebbf000	\               wsock32
ELF	7ebbf000-7ec11000	Deferred        advapi32<elf>
  \-PE	7ebd0000-7ec11000	\               advapi32
ELF	7ec11000-7ecac000	Deferred        gdi32<elf>
  \-PE	7ec20000-7ecac000	\               gdi32
ELF	7ecac000-7edf3000	Deferred        user32<elf>
  \-PE	7ecd0000-7edf3000	\               user32
ELF	7edf3000-7ee85000	Deferred        winmm<elf>
  \-PE	7ee00000-7ee85000	\               winmm
ELF	7efa9000-7efc1000	Deferred        libnsl.so.1
ELF	7efc6000-7efd1000	Deferred        libnss_files.so.2
ELF	7efd1000-7efdb000	Deferred        libnss_nis.so.2
ELF	7efdb000-7f000000	Deferred        libm.so.6
ELF	f7d31000-f7d3a000	Deferred        libnss_compat.so.2
ELF	f7d3b000-f7d3f000	Deferred        libdl.so.2
ELF	f7d3f000-f7e8e000	Deferred        libc.so.6
ELF	f7e8f000-f7ea7000	Deferred        libpthread.so.0
ELF	f7ea7000-f7fdd000	Dwarf           libwine.so.1
ELF	f7fdf000-f7ffe000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
	00000033    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000018 
	00000019    0
0000001c 
	0000002e    0
	00000020    0
	0000001f    0
	0000001e    0
	0000001d    0
00000030 
	00000037    0
	00000036    0
	00000035    0
	00000032    0
	00000031    0
0000003d 
	00000009    0
	00000041    0
	00000040    0
	0000003f    0
	0000003e    0
00000063 
	00000049    0
	00000067    0
	00000066    0
	00000065    0
	00000064    0
00000058 (D) C:\Program_Files\Activision\CallOfDuty4\iw3mp.exe
	00000051   15
	00000055    0
	0000003c    0
	00000029    0
	00000060    0
	00000042    1
	0000005a    0 <==
Backtrace:
=>1 0x004ed006 in iw3mp (+0xed006) (0x0032fd54)
  2 0x0050039d in iw3mp (+0x10039d) (0x0032fd60)
  3 0x005777a3 in iw3mp (+0x1777a3) (0x0032ff08)
  4 0x7b877b37 start_process+0xc7(arg=0x0) [/home/jakob/wine-1.0/dlls/kernel32/process.c:904] in kernel32 (0x0032ffe8)
  5 0xf7eaea37 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
Terminated


```

---

### Post by thefishki345 on 2008-07-23
check this thread:
[http://ubuntuforums.org/showthread.php?t=641987&page=28&highlight=call+duty+opengl+issue](http://ubuntuforums.org/showthread.php?t=641987&page=28&highlight=call+duty+opengl+issue)

it is mostly me monitoring it at the moment, but troll through there and see if anyone was having the same problem and got it fixed.

---

### Post by mad_golfer on 2008-07-23
You sure call of duty will work through wine ?



- Anthony
[Found a great deal on PC Magazines]("http://www.magazinesusa.com/pc-magazine-subscription.cfm") :lolflag::guitar::):KS

---

### Post by chaosdesigner on 2008-07-24
@ thefishki345

thx I'll look through it but doesn't anybody know what to do with my problem?


Oh and COD4 should work....

Edit:

I just scanned through the error report again and could it be that the problem lies in this line?

err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.


if so, how do i solve it?

---

