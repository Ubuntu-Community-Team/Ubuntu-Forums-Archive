---
title: "How can I run Civilization 4: Colonization?"
date: 2008-09-27
forum: Wine
---

### Post by willz06jw on 2008-09-27
Howdy,

I know this may be a bit early, but I am trying to run the just released Civ4:Colonization.  I have Cedega and it doesn't support it yet.

How about Wine or CrossOver Games?  Any ideas?

Thanks,
Will

---

### Post by asdfoo on 2008-09-27
> **willz06jw said:**
> Howdy,

I know this may be a bit early, but I am trying to run the just released Civ4:Colonization.  I have Cedega and it doesn't support it yet.

How about Wine or CrossOver Games?  Any ideas?

Thanks,
Will

huh? not sure why you're posting here if you haven't attempted to install it with Wine.

just install wine and see if it works.

---

### Post by Levo on 2008-09-28
It installs & works perfectly! Take a look at my post [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=13961&iTestingId=31818").

---

### Post by willz06jw on 2008-09-28
Hmmm, strange.  When I open Colonization.exe with wine version 1.1.5 (w/winetricks installed with d3dx9_36.dll downloaded and put into system32) it gives me this error and doesn't start.

```
wine Colonization.exe
fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0x1f1a3b0,0x00000004,0x1f1a3ac) Unknown information class
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x1f1929c): Stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x1f190e8,0x00000000), stub!
fixme:psapi:EnumPageFilesA (0x138c8d0, 0x1ef988c) stub
fixme:psapi:EnumPageFilesA (0x138c8d0, 0x1ec41a8) stub
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQuerySystemInformation (0x00000007,0x1ef1db0,0x00000018,(nil)) stub
fixme:ntdll:server_ioctl_file Unsupported ioctl 4d0008 (device=4d access=0 func=2 method=0)
fixme:cursor:SetSystemCursor (0x10de,00007f00),stub!
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:SetSystemCursor (0x10de,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1126,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1136,00007f03),stub!
fixme:cursor:SetSystemCursor (0x113e,00007f01),stub!
fixme:cursor:SetSystemCursor (0x114e,00007f88),stub!
fixme:cursor:SetSystemCursor (0x115e,00007f86),stub!
fixme:cursor:SetSystemCursor (0x116e,00007f83),stub!
fixme:cursor:SetSystemCursor (0x117e,00007f85),stub!
fixme:cursor:SetSystemCursor (0x118e,00007f82),stub!
fixme:cursor:SetSystemCursor (0x119e,00007f84),stub!
fixme:cursor:SetSystemCursor (0x11ae,00007f04),stub!
fixme:cursor:SetSystemCursor (0x11be,00007f02),stub!
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x1f2f918): Stub!
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
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for C:\Program Files\2K Games\Firaxis Games\Sid Meier's Civilization IV Colonization\Logs.lnk
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for C:\Program Files\2K Games\Firaxis Games\Sid Meier's Civilization IV Colonization\Saves.lnk
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for C:\Program Files\2K Games\Firaxis Games\Sid Meier's Civilization IV Colonization\CivilizationIV.ini.lnk
fixme:shell:DllCanUnloadNow stub
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:msxml:schema_cache_add (0x1385a0)->(L"x-schema:CIV4GameInfoSchema.xml", var(vt 9)): stub
fixme:msxml:domdoc_putref_schemas (0x1385b8): semi-stub
fixme:msxml:domdoc_putref_schemas (0x1385b8): semi-stub
wine: Unhandled page fault on read access to 0x00000000 at address 0x439e8bd (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x0439e8bd).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0439e8bd ESP:01f2f400 EBP:0439d4c0 EFLAGS:00210202(   - 00      - -RI1)
 EAX:00000000 EBX:00000000 ECX:00000000 EDX:022e004c
 ESI:0238e6d8 EDI:00000000
Stack dump:
0x01f2f400:  004bc19f 00000000 00000005 0238d18c
0x01f2f410:  022e5178 008fbb9b 00411376 0238d1ec
0x01f2f420:  022e520c 022e520c 0238d188 01f2f444
0x01f2f430:  00a37efc 00000007 004bc131 0238e6d8
0x01f2f440:  0238e6d8 01f2f59c 00a4ce4b 00000000
0x01f2f450:  00407020 022e5178 022e5288 022e5178
Backtrace:
=>1 0x0439e8bd in cvgamecoredll (+0x8e8bd) (0x0439d4c0)
0x0439e8bd: movl	0x0(%eax),%eax
Modules:
Module	Address			Debug info	Name (119 modules)
PE	  230000-  243000	Deferred        zlib1
PE	  360000-  36e000	Deferred        hapdbg
PE	  400000- 1a27000	Deferred        colonization
PE	 1f30000- 22d9000	Deferred        d3dx9_36
PE	 4310000- 46c9000	Export          cvgamecoredll
PE	10000000-1002b000	Deferred        boost_python-vc71-mt-1_32
PE	18000000-18038000	Deferred        binkw32
PE	1e000000-1e1ca000	Deferred        python24
PE	21100000-2118c000	Deferred        mss32
ELF	7b800000-7b93c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93c000	\               kernel32
ELF	7bc00000-7bca6000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca6000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
PE	7c340000-7c396000	Deferred        msvcr71
PE	7c3a0000-7c41b000	Deferred        msvcp71
ELF	7c542000-7c591000	Deferred        wininet<elf>
  \-PE	7c550000-7c591000	\               wininet
ELF	7c591000-7c5d0000	Deferred        urlmon<elf>
  \-PE	7c5a0000-7c5d0000	\               urlmon
ELF	7c5d0000-7c6f0000	Deferred        libxml2.so.2
ELF	7c6f0000-7c73c000	Deferred        msxml3<elf>
  \-PE	7c700000-7c73c000	\               msxml3
ELF	7cff0000-7d012000	Deferred        mpr<elf>
  \-PE	7d000000-7d012000	\               mpr
ELF	7d019000-7d04c000	Deferred        libxslt.so.1
ELF	7d04c000-7d057000	Deferred        libgcc_s.so.1
ELF	7d066000-7d07b000	Deferred        psapi<elf>
  \-PE	7d070000-7d07b000	\               psapi
ELF	7d12b000-7de6b000	Deferred        libglcore.so.1
ELF	7de6b000-7df10000	Deferred        libgl.so.1
ELF	7df10000-7df91000	Deferred        opengl32<elf>
  \-PE	7df20000-7df91000	\               opengl32
ELF	7df91000-7e0a1000	Deferred        wined3d<elf>
  \-PE	7dfa0000-7e0a1000	\               wined3d
ELF	7e0a1000-7e0d1000	Deferred        d3d9<elf>
  \-PE	7e0b0000-7e0d1000	\               d3d9
ELF	7e0d1000-7e0e5000	Deferred        midimap<elf>
  \-PE	7e0e0000-7e0e5000	\               midimap
ELF	7e0e5000-7e10c000	Deferred        msacm32<elf>
  \-PE	7e0f0000-7e10c000	\               msacm32
ELF	7e10c000-7e123000	Deferred        msacm32<elf>
  \-PE	7e110000-7e123000	\               msacm32
ELF	7e123000-7e1e6000	Deferred        libasound.so.2
ELF	7e1f5000-7e22a000	Deferred        winealsa<elf>
  \-PE	7e200000-7e22a000	\               winealsa
ELF	7e276000-7e2a9000	Deferred        uxtheme<elf>
  \-PE	7e280000-7e2a9000	\               uxtheme
ELF	7e2a9000-7e2b2000	Deferred        libxcursor.so.1
ELF	7e2b2000-7e2b7000	Deferred        libxfixes.so.3
ELF	7e2b7000-7e2ba000	Deferred        libxcomposite.so.1
ELF	7e2ba000-7e2c0000	Deferred        libxrandr.so.2
ELF	7e2c0000-7e2c8000	Deferred        libxrender.so.1
ELF	7e2c8000-7e2cd000	Deferred        libxxf86vm.so.1
ELF	7e2cd000-7e2d0000	Deferred        libxinerama.so.1
ELF	7e2d0000-7e2f0000	Deferred        imm32<elf>
  \-PE	7e2e0000-7e2f0000	\               imm32
ELF	7e2f0000-7e308000	Deferred        libxcb.so.1
ELF	7e308000-7e3ef000	Deferred        libx11.so.6
ELF	7e3ef000-7e3fd000	Deferred        libxext.so.6
ELF	7e3fd000-7e415000	Deferred        libice.so.6
ELF	7e415000-7e41d000	Deferred        libsm.so.6
ELF	7e42c000-7e4c4000	Deferred        winex11<elf>
  \-PE	7e440000-7e4c4000	\               winex11
ELF	7e4c4000-7e4de000	Deferred        wsock32<elf>
  \-PE	7e4d0000-7e4de000	\               wsock32
ELF	7e4de000-7e528000	Deferred        dsound<elf>
  \-PE	7e4f0000-7e528000	\               dsound
ELF	7e548000-7e569000	Deferred        libexpat.so.1
ELF	7e569000-7e593000	Deferred        libfontconfig.so.1
ELF	7e593000-7e5a8000	Deferred        libz.so.1
ELF	7e5a8000-7e615000	Deferred        libfreetype.so.6
ELF	7e615000-7e62e000	Deferred        d3dx9_33<elf>
  \-PE	7e620000-7e62e000	\               d3dx9_33
ELF	7e62e000-7e715000	Deferred        oleaut32<elf>
  \-PE	7e650000-7e715000	\               oleaut32
ELF	7e715000-7e728000	Deferred        libresolv.so.2
ELF	7e728000-7e72a000	Deferred        libnvidia-tls.so.1
ELF	7e72a000-7e72f000	Deferred        libxdmcp.so.6
ELF	7e737000-7e756000	Deferred        iphlpapi<elf>
  \-PE	7e740000-7e756000	\               iphlpapi
ELF	7e756000-7e7bb000	Deferred        rpcrt4<elf>
  \-PE	7e760000-7e7bb000	\               rpcrt4
ELF	7e7bb000-7e8c4000	Deferred        ole32<elf>
  \-PE	7e7e0000-7e8c4000	\               ole32
ELF	7e8c4000-7e8d8000	Deferred        lz32<elf>
  \-PE	7e8d0000-7e8d8000	\               lz32
ELF	7e8d8000-7e8f1000	Deferred        version<elf>
  \-PE	7e8e0000-7e8f1000	\               version
ELF	7e8f1000-7e91d000	Deferred        ws2_32<elf>
  \-PE	7e900000-7e91d000	\               ws2_32
ELF	7e91d000-7e9af000	Deferred        winmm<elf>
  \-PE	7e930000-7e9af000	\               winmm
ELF	7e9af000-7ea19000	Deferred        msvcrt<elf>
  \-PE	7e9c0000-7ea19000	\               msvcrt
ELF	7ea19000-7eada000	Deferred        comctl32<elf>
  \-PE	7ea20000-7eada000	\               comctl32
ELF	7eada000-7eb34000	Deferred        shlwapi<elf>
  \-PE	7eaf0000-7eb34000	\               shlwapi
ELF	7eb34000-7ec4e000	Deferred        shell32<elf>
  \-PE	7eb40000-7ec4e000	\               shell32
ELF	7ec4e000-7eca2000	Deferred        advapi32<elf>
  \-PE	7ec60000-7eca2000	\               advapi32
ELF	7eca2000-7ed40000	Deferred        gdi32<elf>
  \-PE	7ecb0000-7ed40000	\               gdi32
ELF	7ed40000-7ee89000	Deferred        user32<elf>
  \-PE	7ed60000-7ee89000	\               user32
ELF	7efa9000-7efb4000	Deferred        libnss_files.so.2
ELF	7efb4000-7efcc000	Deferred        libnsl.so.1
ELF	7efcc000-7eff1000	Deferred        libm.so.6
ELF	7eff1000-7eff3000	Deferred        libxcb-xlib.so.0
ELF	7eff3000-7eff6000	Deferred        libxau.so.6
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	b7ce4000-b7ced000	Deferred        libnss_compat.so.2
ELF	b7cee000-b7cf2000	Deferred        libdl.so.2
ELF	b7cf2000-b7e41000	Deferred        libc.so.6
ELF	b7e42000-b7e5a000	Deferred        libpthread.so.0
ELF	b7e69000-b7f9f000	Deferred        libwine.so.1
ELF	b7fa1000-b7fbd000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\2K Games\Firaxis Games\Sid Meier's Civilization IV Colonization\Colonization.exe
	00000024    0
	00000009    0 <==
0000000c 
	00000017    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000021 
	00000022    0
Backtrace:
=>1 0x0439e8bd in cvgamecoredll (+0x8e8bd) (0x0439d4c0)

```

I wonder what could cause this...

Thanks,
Will

---

### Post by willz06jw on 2008-10-01
Sorry to bump, but what does this Wine message mean?

---

### Post by Bios Element on 2008-10-01
> **willz06jw said:**
> Sorry to bump, but what does this Wine message mean?

I've got your same error. No idea how to fix it though.

---

### Post by Levo on 2008-10-02
What's your wine configuration? I suggest using the ALSA sound driver, and set emulation "Windows XP"

---

### Post by willz06jw on 2008-10-02
Yep I am using both of those settings (and all default settings)

Thanks,
Will

---

### Post by Levo on 2008-10-04
Try installing the DirectX engine using winetricks or winedoors.

---

### Post by willz06jw on 2008-10-04
I installed directX 9 using wine doors and now I get this message (at least the error keeps changing!)

Thanks for your help!
Will

```
fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0x1f1a3b0,0x00000004,0x1f1a3ac) Unknown information class
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x1f1929c): Stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x1f190e8,0x00000000), stub!
fixme:psapi:EnumPageFilesA (0x138c8d0, 0x1ef988c) stub
fixme:psapi:EnumPageFilesA (0x138c8d0, 0x1ec41a8) stub
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQuerySystemInformation (0x00000007,0x1ef1db0,0x00000018,(nil)) stub
fixme:ntdll:server_ioctl_file Unsupported ioctl 4d0008 (device=4d access=0 func=2 method=0)
fixme:cursor:SetSystemCursor (0x10de,00007f00),stub!
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:SetSystemCursor (0x10de,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1126,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1136,00007f03),stub!
fixme:cursor:SetSystemCursor (0x113e,00007f01),stub!
fixme:cursor:SetSystemCursor (0x114e,00007f88),stub!
fixme:cursor:SetSystemCursor (0x115e,00007f86),stub!
fixme:cursor:SetSystemCursor (0x116e,00007f83),stub!
fixme:cursor:SetSystemCursor (0x117e,00007f85),stub!
fixme:cursor:SetSystemCursor (0x118e,00007f82),stub!
fixme:cursor:SetSystemCursor (0x119e,00007f84),stub!
fixme:cursor:SetSystemCursor (0x11ae,00007f04),stub!
fixme:cursor:SetSystemCursor (0x11be,00007f02),stub!
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x1f2f918): Stub!
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
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:msxml:schema_cache_add (0x1385a0)->(L"x-schema:CIV4GameInfoSchema.xml", var(vt 9)): stub
fixme:msxml:domdoc_putref_schemas (0x1385b8): semi-stub
fixme:msxml:domdoc_putref_schemas (0x1385b8): semi-stub
wine: Unhandled page fault on read access to 0x00000000 at address 0x438e8bd (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x0438e8bd).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0438e8bd ESP:01f2f400 EBP:0438d4c0 EFLAGS:00210202(   - 00      - -RI1)
 EAX:00000000 EBX:00000000 ECX:00000000 EDX:022e004c
 ESI:0238e6d0 EDI:00000000
Stack dump:
0x01f2f400:  004bc19f 00000000 00000005 0238d184
0x01f2f410:  022e5170 008fbb9b 00411376 0238d1e4
0x01f2f420:  022e5204 022e5204 0238d180 01f2f444
0x01f2f430:  00a37efc 00000007 004bc131 0238e6d0
0x01f2f440:  0238e6d0 01f2f59c 00a4ce4b 00000000
0x01f2f450:  00407020 022e5170 022e5280 022e5170
Backtrace:
=>1 0x0438e8bd in cvgamecoredll (+0x8e8bd) (0x0438d4c0)
0x0438e8bd: movl	0x0(%eax),%eax
Modules:
Module	Address			Debug info	Name (119 modules)
PE	  230000-  243000	Deferred        zlib1
PE	  360000-  36e000	Deferred        hapdbg
PE	  400000- 1a27000	Deferred        colonization
PE	 1f30000- 22d9000	Deferred        d3dx9_36
PE	 4300000- 46b9000	Export          cvgamecoredll
PE	10000000-1002b000	Deferred        boost_python-vc71-mt-1_32
PE	18000000-18038000	Deferred        binkw32
PE	1e000000-1e1ca000	Deferred        python24
PE	21100000-2118c000	Deferred        mss32
ELF	7b800000-7b93c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93c000	\               kernel32
ELF	7bc00000-7bca6000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca6000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
PE	7c340000-7c396000	Deferred        msvcr71
PE	7c3a0000-7c41b000	Deferred        msvcp71
ELF	7c52c000-7c57b000	Deferred        wininet<elf>
  \-PE	7c540000-7c57b000	\               wininet
ELF	7c57b000-7c5ba000	Deferred        urlmon<elf>
  \-PE	7c580000-7c5ba000	\               urlmon
ELF	7c5ba000-7c6da000	Deferred        libxml2.so.2
ELF	7c6da000-7c726000	Deferred        msxml3<elf>
  \-PE	7c6e0000-7c726000	\               msxml3
ELF	7cfda000-7cffc000	Deferred        mpr<elf>
  \-PE	7cfe0000-7cffc000	\               mpr
ELF	7d000000-7d033000	Deferred        libxslt.so.1
ELF	7d033000-7d03e000	Deferred        libgcc_s.so.1
ELF	7d04e000-7d063000	Deferred        psapi<elf>
  \-PE	7d050000-7d063000	\               psapi
ELF	7d112000-7de52000	Deferred        libglcore.so.1
ELF	7de52000-7def7000	Deferred        libgl.so.1
ELF	7def7000-7df78000	Deferred        opengl32<elf>
  \-PE	7df10000-7df78000	\               opengl32
ELF	7df78000-7e088000	Deferred        wined3d<elf>
  \-PE	7df90000-7e088000	\               wined3d
ELF	7e088000-7e0b8000	Deferred        d3d9<elf>
  \-PE	7e090000-7e0b8000	\               d3d9
ELF	7e0b8000-7e0cc000	Deferred        midimap<elf>
  \-PE	7e0c0000-7e0cc000	\               midimap
ELF	7e0cc000-7e0f3000	Deferred        msacm32<elf>
  \-PE	7e0d0000-7e0f3000	\               msacm32
ELF	7e0f3000-7e10a000	Deferred        msacm32<elf>
  \-PE	7e100000-7e10a000	\               msacm32
ELF	7e10a000-7e1cd000	Deferred        libasound.so.2
ELF	7e1dd000-7e212000	Deferred        winealsa<elf>
  \-PE	7e1f0000-7e212000	\               winealsa
ELF	7e25e000-7e291000	Deferred        uxtheme<elf>
  \-PE	7e260000-7e291000	\               uxtheme
ELF	7e291000-7e29a000	Deferred        libxcursor.so.1
ELF	7e29a000-7e29f000	Deferred        libxfixes.so.3
ELF	7e29f000-7e2a2000	Deferred        libxcomposite.so.1
ELF	7e2a2000-7e2a8000	Deferred        libxrandr.so.2
ELF	7e2a8000-7e2b0000	Deferred        libxrender.so.1
ELF	7e2b0000-7e2b5000	Deferred        libxxf86vm.so.1
ELF	7e2b5000-7e2b8000	Deferred        libxinerama.so.1
ELF	7e2b8000-7e2d8000	Deferred        imm32<elf>
  \-PE	7e2c0000-7e2d8000	\               imm32
ELF	7e2d8000-7e2dd000	Deferred        libxdmcp.so.6
ELF	7e2dd000-7e2f5000	Deferred        libxcb.so.1
ELF	7e2f5000-7e2f7000	Deferred        libxcb-xlib.so.0
ELF	7e2f7000-7e2fa000	Deferred        libxau.so.6
ELF	7e2fa000-7e3e1000	Deferred        libx11.so.6
ELF	7e3e1000-7e3ef000	Deferred        libxext.so.6
ELF	7e3ef000-7e407000	Deferred        libice.so.6
ELF	7e407000-7e40f000	Deferred        libsm.so.6
ELF	7e41b000-7e41d000	Deferred        libnvidia-tls.so.1
ELF	7e41f000-7e4b7000	Deferred        winex11<elf>
  \-PE	7e430000-7e4b7000	\               winex11
ELF	7e4b7000-7e4d1000	Deferred        wsock32<elf>
  \-PE	7e4c0000-7e4d1000	\               wsock32
ELF	7e4d1000-7e51b000	Deferred        dsound<elf>
  \-PE	7e4e0000-7e51b000	\               dsound
ELF	7e533000-7e554000	Deferred        libexpat.so.1
ELF	7e554000-7e57e000	Deferred        libfontconfig.so.1
ELF	7e57e000-7e593000	Deferred        libz.so.1
ELF	7e593000-7e600000	Deferred        libfreetype.so.6
ELF	7e600000-7e619000	Deferred        d3dx9_33<elf>
  \-PE	7e610000-7e619000	\               d3dx9_33
ELF	7e619000-7e700000	Deferred        oleaut32<elf>
  \-PE	7e630000-7e700000	\               oleaut32
ELF	7e700000-7e713000	Deferred        libresolv.so.2
ELF	7e723000-7e742000	Deferred        iphlpapi<elf>
  \-PE	7e730000-7e742000	\               iphlpapi
ELF	7e742000-7e7a7000	Deferred        rpcrt4<elf>
  \-PE	7e750000-7e7a7000	\               rpcrt4
ELF	7e7a7000-7e8b0000	Deferred        ole32<elf>
  \-PE	7e7c0000-7e8b0000	\               ole32
ELF	7e8b0000-7e8c4000	Deferred        lz32<elf>
  \-PE	7e8c0000-7e8c4000	\               lz32
ELF	7e8c4000-7e8dd000	Deferred        version<elf>
  \-PE	7e8d0000-7e8dd000	\               version
ELF	7e8dd000-7e909000	Deferred        ws2_32<elf>
  \-PE	7e8e0000-7e909000	\               ws2_32
ELF	7e909000-7e99b000	Deferred        winmm<elf>
  \-PE	7e910000-7e99b000	\               winmm
ELF	7e99b000-7ea05000	Deferred        msvcrt<elf>
  \-PE	7e9b0000-7ea05000	\               msvcrt
ELF	7ea05000-7eac6000	Deferred        comctl32<elf>
  \-PE	7ea10000-7eac6000	\               comctl32
ELF	7eac6000-7eb20000	Deferred        shlwapi<elf>
  \-PE	7ead0000-7eb20000	\               shlwapi
ELF	7eb20000-7ec3a000	Deferred        shell32<elf>
  \-PE	7eb30000-7ec3a000	\               shell32
ELF	7ec3a000-7ec8e000	Deferred        advapi32<elf>
  \-PE	7ec50000-7ec8e000	\               advapi32
ELF	7ec8e000-7ed2c000	Deferred        gdi32<elf>
  \-PE	7eca0000-7ed2c000	\               gdi32
ELF	7ed2c000-7ee75000	Deferred        user32<elf>
  \-PE	7ed50000-7ee75000	\               user32
ELF	7ef95000-7efa0000	Deferred        libnss_files.so.2
ELF	7efa0000-7efaa000	Deferred        libnss_nis.so.2
ELF	7efaa000-7efc2000	Deferred        libnsl.so.1
ELF	7efc2000-7efcb000	Deferred        libnss_compat.so.2
ELF	7efcb000-7eff0000	Deferred        libm.so.6
ELF	b7d04000-b7d08000	Deferred        libdl.so.2
ELF	b7d08000-b7e57000	Deferred        libc.so.6
ELF	b7e58000-b7e70000	Deferred        libpthread.so.0
ELF	b7e80000-b7fb6000	Deferred        libwine.so.1
ELF	b7fb8000-b7fd4000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\2K Games\Firaxis Games\Sid Meier's Civilization IV Colonization\Colonization.exe
	00000024    0
	00000009    0 <==
0000000c 
	00000017    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000021 
	00000022    0
Backtrace:
=>1 0x0438e8bd in cvgamecoredll (+0x8e8bd) (0x0438d4c0)

```

---

### Post by Levo on 2008-10-05
Try applying a animated cursor patch. Pick one here: [http://bugs.winehq.org/show_bug.cgi?id=10708](http://bugs.winehq.org/show_bug.cgi?id=10708)

---

### Post by willz06jw on 2008-10-05
None of these patches seem to work with Wine 1.1.5...I am going to go back and see what options were chosen in winetricks.  I am going to [re?]install directx9 msxml3 vcrun2003 dotnet11 --I'm worried I skipped a winetricks option when I did this the first time.  (BTW I determined which options to pick from [http://appdb.winehq.org/objectManager.php?sClass=version&iId=13896&iTestingId=31720](http://appdb.winehq.org/objectManager.php?sClass=version&iId=13896&iTestingId=31720)) 

For all: 

I did this by downloading the winetricks script:
[http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)

Then running it in terminal:
sh winetricks directx9 msxml3 vcrun2003 dotnet11

Thanks
Will

---

### Post by willz06jw on 2008-10-05
That worked -- Colonization now works!


Thanks for everyone's help (Levo),

Will Howard

---

### Post by *malagant* on 2008-10-05
The performance is very bad under Wine. Any tricks?

---

### Post by Levo on 2008-10-05
I don't have any performance issues. It runs just perfectly. What are your system specifications?

---

### Post by *malagant* on 2008-10-05
Q6600, GF 8800GT, 4 GB RAM. More then enough for this game ;P 

Well, Colo runs pefect under Windows, but under Wine every movement is bucking, as if the game would run with 2 fps.

---

### Post by Levo on 2008-10-05
Yes, your system specs are fine. What about your Wine Configuration?

---

### Post by *malagant* on 2008-10-05
Dunno what exactly you mean, but Wine version is 1.1.5, the game runs in  WinXP-mode, audio is set to ALSA and in the graphics tab the hardware vertex shader support is enabled.

---

### Post by Levo on 2008-10-05
Do you experience similar problems with other games?

---

### Post by *malagant* on 2008-10-05
When moving the camera around in World of Warcraft, there is a similar effect: the screen seems to flicker. This happens in Colo too, when moving aroung.

But I tried some graphics options in Colo, and now the game runs way better. I don't know exactly what i've changed, i think it has something to do with disabling animations / effects. Now it's playable, exept the annoying flickering.

---

### Post by esi on 2008-10-09
Hi all

I am trying to get colonization to work by following these instructions, but the application exits just after the intro. Does anyone have an idea of what could be wrong?

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
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for C:\Program Files\2K Games\Firaxis Games\Sid Meier's Civilization IV Colonization\Saves.lnk
fixme:shell:DllCanUnloadNow stub
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x4002a 0x00000000
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for C:\Program Files\2K Games\Firaxis Games\Sid Meier's Civilization IV Colonization\CivilizationIV.ini.lnk
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
'import site' failed; use -v for traceback
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x2ffefe0,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x2fff518,0x00000000), stub!
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
fixme:system:SystemParametersInfoW Unimplemented action: 55 (SPI_SETMOUSEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
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
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1e92f8) : stub
fixme:d3d:state_lastpixel Last Pixel Drawing Disabled, not handled yet
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1e92f8) : stub
wine: Unhandled page fault on read access to 0x00000000 at address 0x7b50344a (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7b50344a).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b50344a ESP:02fff338 EBP:00000000 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:00000060 ECX:00000000 EDX:00001000
 ESI:0000bd2c EDI:7c2bc0d4
Stack dump:
0x02fff338:  00017000 00000000 7c2bc0d4 00000000
0x02fff348:  00000000 00000000 084c05e0 00000020
0x02fff358:  00000001 fffff000 7c8a7000 00000000
0x02fff368:  00000000 00000000 7c8a7000 7c1dca30
0x02fff378:  00000004 00000060 00001403 7b5071f2
0x02fff388:  7c1dc960 00000060 00001403 00000000
Backtrace:
=>1 0x7b50344a in libglcore.so.1 (+0x81844a) (0x00000000)
0x7b50344a: movzwl	0x0(%ecx),%eax
Modules:
Module	Address			Debug info	Name (121 modules)
PE	  230000-  243000	Deferred        zlib1
PE	  250000-  25e000	Deferred        hapdbg
PE	  400000- 2af1538	Deferred        colonization
PE	 3000000- 336f000	Deferred        d3dx9_33
PE	 3b50000- 3f09000	Deferred        cvgamecoredll
PE	 4ff0000- 4ffa000	Deferred        mssdolby.flt
PE	 5110000- 5130000	Deferred        msseax.flt
PE	 79c0000- 7c27000	Deferred        d3dx9_31
PE	10000000-1002b000	Deferred        boost_python-vc71-mt-1_32
PE	18000000-18038000	Deferred        binkw32
PE	1e000000-1e1ca000	Deferred        python24
PE	21100000-2118c000	Deferred        mss32
PE	22300000-2230c000	Deferred        mssds3d.flt
PE	23000000-2300d000	Deferred        msssrs.flt
PE	24100000-2411e000	Deferred        mssdsp.flt
PE	26400000-2643a000	Deferred        mssvoice.asi
PE	26f00000-26f2e000	Deferred        mssmp3.asi
PE	69b10000-69c14000	Deferred        msxml3
ELF	7aceb000-7b800000	Export          libglcore.so.1
ELF	7b800000-7b93c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93c000	\               kernel32
ELF	7bc00000-7bca6000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca6000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
PE	7c340000-7c396000	Deferred        msvcr71
PE	7c3a0000-7c41b000	Deferred        msvcp71
ELF	7c881000-7c88c000	Deferred        libgcc_s.so.1
ELF	7c9b4000-7ca58000	Deferred        libgl.so.1
ELF	7ca6a000-7caeb000	Deferred        opengl32<elf>
  \-PE	7ca80000-7caeb000	\               opengl32
ELF	7caeb000-7cbfb000	Deferred        wined3d<elf>
  \-PE	7cb00000-7cbfb000	\               wined3d
ELF	7cbfb000-7cc6a000	Deferred        crypt32<elf>
  \-PE	7cc10000-7cc6a000	\               crypt32
ELF	7cc6a000-7cca5000	Deferred        rsaenh<elf>
  \-PE	7cc70000-7cca5000	\               rsaenh
ELF	7dc09000-7dc39000	Deferred        d3d9<elf>
  \-PE	7dc10000-7dc39000	\               d3d9
ELF	7e19e000-7e1b2000	Deferred        wtsapi32<elf>
  \-PE	7e1a0000-7e1b2000	\               wtsapi32
ELF	7e1b2000-7e1c6000	Deferred        midimap<elf>
  \-PE	7e1c0000-7e1c6000	\               midimap
ELF	7e1c6000-7e1ed000	Deferred        msacm32<elf>
  \-PE	7e1d0000-7e1ed000	\               msacm32
ELF	7e1ed000-7e204000	Deferred        msacm32<elf>
  \-PE	7e1f0000-7e204000	\               msacm32
ELF	7e204000-7e2c7000	Deferred        libasound.so.2
ELF	7e2c9000-7e2cb000	Deferred        libnvidia-tls.so.1
ELF	7e2d9000-7e30e000	Deferred        winealsa<elf>
  \-PE	7e2e0000-7e30e000	\               winealsa
ELF	7e35a000-7e38d000	Deferred        uxtheme<elf>
  \-PE	7e360000-7e38d000	\               uxtheme
ELF	7e38d000-7e396000	Deferred        libxcursor.so.1
ELF	7e396000-7e39b000	Deferred        libxfixes.so.3
ELF	7e39b000-7e39e000	Deferred        libxcomposite.so.1
ELF	7e39e000-7e3a4000	Deferred        libxrandr.so.2
ELF	7e3a4000-7e3ac000	Deferred        libxrender.so.1
ELF	7e3ac000-7e3b1000	Deferred        libxxf86vm.so.1
ELF	7e3b1000-7e3b4000	Deferred        libxinerama.so.1
ELF	7e3b4000-7e3d4000	Deferred        imm32<elf>
  \-PE	7e3c0000-7e3d4000	\               imm32
ELF	7e3d4000-7e3d9000	Deferred        libxdmcp.so.6
ELF	7e3d9000-7e3f1000	Deferred        libxcb.so.1
ELF	7e3f1000-7e3f3000	Deferred        libxcb-xlib.so.0
ELF	7e3f3000-7e3f6000	Deferred        libxau.so.6
ELF	7e3f6000-7e4dd000	Deferred        libx11.so.6
ELF	7e4dd000-7e4eb000	Deferred        libxext.so.6
ELF	7e4eb000-7e503000	Deferred        libice.so.6
ELF	7e503000-7e50b000	Deferred        libsm.so.6
ELF	7e517000-7e51a000	Deferred        iso8859-1.so
ELF	7e51d000-7e5b5000	Deferred        winex11<elf>
  \-PE	7e530000-7e5b5000	\               winex11
ELF	7e5e1000-7e602000	Deferred        libexpat.so.1
ELF	7e602000-7e62c000	Deferred        libfontconfig.so.1
ELF	7e62c000-7e641000	Deferred        libz.so.1
ELF	7e641000-7e6ae000	Deferred        libfreetype.so.6
ELF	7e6ae000-7e6c8000	Deferred        wsock32<elf>
  \-PE	7e6b0000-7e6c8000	\               wsock32
ELF	7e6c8000-7e712000	Deferred        dsound<elf>
  \-PE	7e6d0000-7e712000	\               dsound
ELF	7e712000-7e7f9000	Deferred        oleaut32<elf>
  \-PE	7e730000-7e7f9000	\               oleaut32
ELF	7e7f9000-7e80c000	Deferred        libresolv.so.2
ELF	7e81e000-7e83d000	Deferred        iphlpapi<elf>
  \-PE	7e820000-7e83d000	\               iphlpapi
ELF	7e83d000-7e8a2000	Deferred        rpcrt4<elf>
  \-PE	7e850000-7e8a2000	\               rpcrt4
ELF	7e8a2000-7e9ab000	Deferred        ole32<elf>
  \-PE	7e8c0000-7e9ab000	\               ole32
ELF	7e9ab000-7e9bf000	Deferred        lz32<elf>
  \-PE	7e9b0000-7e9bf000	\               lz32
ELF	7e9bf000-7e9d8000	Deferred        version<elf>
  \-PE	7e9c0000-7e9d8000	\               version
ELF	7e9d8000-7ea04000	Deferred        ws2_32<elf>
  \-PE	7e9e0000-7ea04000	\               ws2_32
ELF	7ea04000-7ea96000	Deferred        winmm<elf>
  \-PE	7ea10000-7ea96000	\               winmm
ELF	7ea96000-7eb00000	Deferred        msvcrt<elf>
  \-PE	7eab0000-7eb00000	\               msvcrt
ELF	7eb00000-7ebc1000	Deferred        comctl32<elf>
  \-PE	7eb10000-7ebc1000	\               comctl32
ELF	7ebc1000-7ec1b000	Deferred        shlwapi<elf>
  \-PE	7ebd0000-7ec1b000	\               shlwapi
ELF	7ec1b000-7ed35000	Deferred        shell32<elf>
  \-PE	7ec30000-7ed35000	\               shell32
ELF	7ed35000-7ed89000	Deferred        advapi32<elf>
  \-PE	7ed40000-7ed89000	\               advapi32
ELF	7ed89000-7ee27000	Deferred        gdi32<elf>
  \-PE	7eda0000-7ee27000	\               gdi32
ELF	7ee27000-7ef70000	Deferred        user32<elf>
  \-PE	7ee40000-7ef70000	\               user32
ELF	7efa6000-7efb1000	Deferred        libnss_files.so.2
ELF	7efb1000-7efc9000	Deferred        libnsl.so.1
ELF	7efc9000-7efee000	Deferred        libm.so.6
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	b7cc5000-b7cce000	Deferred        libnss_compat.so.2
ELF	b7ccf000-b7cd3000	Deferred        libdl.so.2
ELF	b7cd3000-b7e22000	Deferred        libc.so.6
ELF	b7e23000-b7e3b000	Deferred        libpthread.so.0
ELF	b7e4d000-b7f83000	Deferred        libwine.so.1
ELF	b7f85000-b7fa1000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\2K Games\Firaxis Games\Sid Meier's Civilization IV Colonization\colonization.exe
	00000035    0
	00000030    0
	0000002f   15
	0000002e   15
	0000002d    0
	00000009    0 <==
0000000c 
	00000014    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000016    0
	00000015    0
	00000011    0
	00000010    0
00000017 
	00000018    0
Backtrace:
=>1 0x7b50344a in libglcore.so.1 (+0x81844a) (0x00000000)

```

/esi

---

### Post by Levo on 2008-10-12
Which wine version do you use?
[This]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=13961") is my post in the Wine AppDB. Try following the steps.

---

### Post by willz06jw on 2008-10-19
Damn!  I am now trying to duplicate how I got Colo working previously and I am having a bit of trouble

I am using Wine 1.1.6 and it gives me a "Insert Original Disc instead of a backup" error...

Is this due to that I am no longer using 1.1.5?

Thanks,
Will

---

### Post by usererror on 2010-03-16
I am too trying to get this to work, but my issues are like everyone elses.  Just quits.  I wonder if its because I'm on a 64bit Ubuntu?

---

