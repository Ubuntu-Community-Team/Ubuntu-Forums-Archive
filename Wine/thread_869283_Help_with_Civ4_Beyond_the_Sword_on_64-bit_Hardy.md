---
title: "Help with Civ4 Beyond the Sword on 64-bit Hardy"
date: 2008-07-24
forum: Wine
---

### Post by Celebloki on 2008-07-24
Hello I have been trying to get Civ4: BTS version 3.17 installed on my 64-bit Hardy machine. My wine version is 1.0. I installed it per the guides on wines web-page for the appropriate version to the letter. I have Vertex Shader Support on none and allow pixel shading checked.I am not doing an emulated desktop and have tried checking and unchecking All the window manager...options. I have msxml3 in the DLL overrides and running in windows XP mode. I have also copied over the appropriate d3dx9 files to my system 32 folder. I am pretty sure my problem is because my 64-bit version of hardy is causing the problem. Is there any known work-arounds to this problem. My hardware specs are as follows.
Intel Xeon X5450
4GB RAM
Nvidia Quadro FX 1700

And here is the terminal error output from wine.

```

fixme:system:SystemParametersInfoW Unimplemented action: 55 (SPI_SETMOUSEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for C:\Program Files\2K Games\Firaxis Games\Sid Meier's Civilization 4 Gold\Beyond the Sword\Saves.lnk
fixme:shell:DllCanUnloadNow stub
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for C:\Program Files\2K Games\Firaxis Games\Sid Meier's Civilization 4 Gold\Beyond the Sword\CivilizationIV.ini.lnk
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:wtsapi:WTSRegisterSessionNotification Stub 0xf0024 0x00000000
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "<string>", line 2, in ?
IOError: [Errno 2] No such file or directory: 'C:\\windows\\profiles\ratcliffed\\My Documents\\My Games\\Beyond the Sword\\Logs\\PythonErr2.log'
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x32efb8,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x32f4f0,0x00000000), stub!
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
fixme:system:SystemParametersInfoW Unimplemented action: 55 (SPI_SETMOUSEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x18b1a8) : stub
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x18b1a8) : stub
fixme:d3d_surface:IWineD3DSurfaceImpl_PreLoad >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glGenTextures @ surface.c / 513
fixme:d3d_surface:IWineD3DSurfaceImpl_PreLoad >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ surface.c / 517
fixme:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexImage2D @ surface.c / 340
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCopyTexSubImage2D @ surface.c / 937
fixme:d3d:state_lastpixel Last Pixel Drawing Disabled, not handled yet
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x18b1a8) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x18b1a8) : stub
wine: Unhandled page fault on read access to 0x00000000 at address 0x7dbd144a (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7dbd144a).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7dbd144a ESP:0032f1f8 EBP:00000000 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:00000078 ECX:00000000 EDX:00001000
 ESI:0000bd2c EDI:7c5e4054
Stack dump:
0x0032f1f8:  7d333000 20000000 7c5e4054 00000000
0x0032f208:  00000000 00000000 1b591480 00000020
0x0032f218:  00000001 fffff000 7d333000 00000000
0x0032f228:  00000000 00000000 7d333000 7c1e9cc4
0x0032f238:  00000003 00000078 00001403 7dbd51f2
0x0032f248:  7c1e9c28 00000078 00001403 00000000
Backtrace:
=>1 0x7dbd144a in libglcore.so.1 (+0x81844a) (0x00000000)
0x7dbd144a: movzwl	0x0(%ecx),%eax
Modules:
Module	Address			Debug info	Name (107 modules)
PE	  330000-  343000	Deferred        zlib1
PE	  350000-  35e000	Deferred        hapdbg
PE	  400000- 1038186	Deferred        civ4beyondsword
PE	 1040000- 13af000	Deferred        d3dx9_33
PE	 1ca0000- 2153000	Deferred        cvgamecoredll
PE	10000000-1002b000	Deferred        boost_python-vc71-mt-1_32
PE	18000000-18038000	Deferred        binkw32
PE	1ac60000-1aec7000	Deferred        d3dx9_31
PE	1e000000-1e1ca000	Deferred        python24
PE	21100000-2118c000	Deferred        mss32
PE	74980000-74a93000	Deferred        msxml3
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
PE	7c340000-7c396000	Deferred        msvcr71
PE	7c3a0000-7c41b000	Deferred        msvcp71
ELF	7d3b9000-7dece000	Export          libglcore.so.1
ELF	7dece000-7df72000	Deferred        libgl.so.1
ELF	7df89000-7e08c000	Deferred        wined3d<elf>
  \-PE	7dfa0000-7e08c000	\               wined3d
ELF	7e08c000-7e0bc000	Deferred        d3d9<elf>
  \-PE	7e090000-7e0bc000	\               d3d9
ELF	7e0bc000-7e124000	Deferred        crypt32<elf>
  \-PE	7e0d0000-7e124000	\               crypt32
ELF	7e124000-7e15f000	Deferred        rsaenh<elf>
  \-PE	7e130000-7e15f000	\               rsaenh
ELF	7e1b1000-7e1c5000	Deferred        wtsapi32<elf>
  \-PE	7e1c0000-7e1c5000	\               wtsapi32
ELF	7e1c5000-7e1d9000	Deferred        midimap<elf>
  \-PE	7e1d0000-7e1d9000	\               midimap
ELF	7e1d9000-7e1ff000	Deferred        msacm32<elf>
  \-PE	7e1e0000-7e1ff000	\               msacm32
ELF	7e1ff000-7e2c2000	Deferred        libasound.so.2
ELF	7e2c2000-7e2d9000	Deferred        msacm32<elf>
  \-PE	7e2d0000-7e2d9000	\               msacm32
ELF	7e2d9000-7e30f000	Deferred        winealsa<elf>
  \-PE	7e2e0000-7e30f000	\               winealsa
ELF	7e33f000-7e341000	Deferred        libnvidia-tls.so.1
ELF	7e345000-7e350000	Deferred        libgcc_s.so.1
ELF	7e354000-7e387000	Deferred        uxtheme<elf>
  \-PE	7e360000-7e387000	\               uxtheme
ELF	7e387000-7e390000	Deferred        libxcursor.so.1
ELF	7e390000-7e395000	Deferred        libxfixes.so.3
ELF	7e395000-7e398000	Deferred        libxcomposite.so.1
ELF	7e398000-7e39e000	Deferred        libxrandr.so.2
ELF	7e39e000-7e3a6000	Deferred        libxrender.so.1
ELF	7e3a6000-7e3a9000	Deferred        libxinerama.so.1
ELF	7e3a9000-7e3c9000	Deferred        imm32<elf>
  \-PE	7e3b0000-7e3c9000	\               imm32
ELF	7e3c9000-7e3ce000	Deferred        libxdmcp.so.6
ELF	7e3ce000-7e3e6000	Deferred        libxcb.so.1
ELF	7e3e6000-7e3e8000	Deferred        libxcb-xlib.so.0
ELF	7e3e8000-7e3eb000	Deferred        libxau.so.6
ELF	7e3eb000-7e4d2000	Deferred        libx11.so.6
ELF	7e4d2000-7e4e0000	Deferred        libxext.so.6
ELF	7e4e0000-7e4e5000	Deferred        libxxf86vm.so.1
ELF	7e4fc000-7e593000	Deferred        winex11<elf>
  \-PE	7e510000-7e593000	\               winex11
ELF	7e5cc000-7e5ed000	Deferred        libexpat.so.1
ELF	7e5ed000-7e617000	Deferred        libfontconfig.so.1
ELF	7e617000-7e62c000	Deferred        libz.so.1
ELF	7e62c000-7e69c000	Deferred        libfreetype.so.6
ELF	7e6b3000-7e6fd000	Deferred        dsound<elf>
  \-PE	7e6c0000-7e6fd000	\               dsound
ELF	7e6fd000-7e79f000	Deferred        oleaut32<elf>
  \-PE	7e710000-7e79f000	\               oleaut32
ELF	7e79f000-7e800000	Deferred        rpcrt4<elf>
  \-PE	7e7b0000-7e800000	\               rpcrt4
ELF	7e800000-7e8a4000	Deferred        ole32<elf>
  \-PE	7e810000-7e8a4000	\               ole32
ELF	7e8a4000-7e8bd000	Deferred        version<elf>
  \-PE	7e8b0000-7e8bd000	\               version
ELF	7e8bd000-7e8d0000	Deferred        libresolv.so.2
ELF	7e8d3000-7e8e7000	Deferred        lz32<elf>
  \-PE	7e8e0000-7e8e7000	\               lz32
ELF	7e8e7000-7e905000	Deferred        iphlpapi<elf>
  \-PE	7e8f0000-7e905000	\               iphlpapi
ELF	7e905000-7e931000	Deferred        ws2_32<elf>
  \-PE	7e910000-7e931000	\               ws2_32
ELF	7e931000-7e9c3000	Deferred        winmm<elf>
  \-PE	7e940000-7e9c3000	\               winmm
ELF	7e9c3000-7ea2d000	Deferred        msvcrt<elf>
  \-PE	7e9d0000-7ea2d000	\               msvcrt
ELF	7ea2d000-7eaec000	Deferred        comctl32<elf>
  \-PE	7ea40000-7eaec000	\               comctl32
ELF	7eaec000-7eb45000	Deferred        shlwapi<elf>
  \-PE	7eb00000-7eb45000	\               shlwapi
ELF	7eb45000-7ec58000	Deferred        shell32<elf>
  \-PE	7eb60000-7ec58000	\               shell32
ELF	7ec58000-7ecaa000	Deferred        advapi32<elf>
  \-PE	7ec60000-7ecaa000	\               advapi32
ELF	7ecaa000-7ed45000	Deferred        gdi32<elf>
  \-PE	7ecc0000-7ed45000	\               gdi32
ELF	7ed45000-7ee8c000	Deferred        user32<elf>
  \-PE	7ed60000-7ee8c000	\               user32
ELF	7efac000-7efc4000	Deferred        libnsl.so.1
ELF	7efc4000-7efe9000	Deferred        libm.so.6
ELF	7efeb000-7eff6000	Deferred        libnss_files.so.2
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	f7ca0000-f7ca9000	Deferred        libnss_compat.so.2
ELF	f7caa000-f7cae000	Deferred        libdl.so.2
ELF	f7cae000-f7dfd000	Deferred        libc.so.6
ELF	f7dfe000-f7e16000	Deferred        libpthread.so.0
ELF	f7e2d000-f7f63000	Deferred        libwine.so.1
ELF	f7f65000-f7f84000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\2K Games\Firaxis Games\Sid Meier's Civilization 4 Gold\Beyond the Sword\Civ4BeyondSword.exe
	00000032   15
	00000009    0 <==
0000000c 
	0000001a    0
	00000019    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000016 
	0000001b    0
	00000018    0
	00000017    0
0000001c 
	0000001d    0
Backtrace:
=>1 0x7dbd144a in libglcore.so.1 (+0x81844a) (0x00000000)

```

---

### Post by jacksaff on 2008-07-25
I run Civ4BTS in 64bit hardy through wine. I had it installed before wine 1.0 though and use 1.1 now. Check wine appdb for any regressions. It might be that 1.0 didn't play too well with civ4 and could be fixed with a simple update.
It shouldn't make any difference but I have ia32-libs installed which kills most gremlins when running 32bit apps in a 64bit distro. Won't hurt, even if it doesn't help.

---

### Post by conjur3r on 2008-07-25
I don't have any issues with running civ4 on 64bits either.  My only recollection was that I needed to put those DLLs into the game folder (under program files) rather than in system32.

---

### Post by Celebloki on 2008-07-25
I have ia32-libs installed as well as the dlls in the game folder. The Beyond the Sword folder that is. I think I am going to do a complete uninstall of wine and Civ4 and redo everything. I may have messed too much up in the process of everything.

---

### Post by Celebloki on 2008-07-25
Were you guys using version 3.13 or 3.17?

---

### Post by Celebloki on 2008-07-25
Ok..........neither 3.13 or 3.17 worked, same error. Next Idea...VMware Workstation 6.5 and XP VM.

---

