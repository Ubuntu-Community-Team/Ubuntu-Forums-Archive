---
title: "[GTA SAN ANDREAS]Crash &amp; Stuff"
date: 2016-06-09
forum: Wine
---

### Post by EpicSides on 2016-06-09
Hello guys!!

I'm in trouble with my GTA San Andreas installation on Wine...

After hard days of installation and configuration, i've finally managed to make the game launch through PlayOnLinux, but then appears an ugly menu through a black screen. I'm tryin to launch the game anyway but after loading complete it crashes right before starting the "graphical" part.

So it seems i'm in trouble to make the game work after multiple configurations and driver updates :/

I've tried basically everything on the internet but still unable to make the game run properly :(

Any hints? Here's my crashing log:

```
[06/09/16 20:47:42] - Running wine-1.8.1 gta_sa.exe (Working directory : /home/macaquepc1/.PlayOnLinux/wineprefix/GTASA/drive_c/Program Files/Rockstar Games/GTA San Andreas)
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
fixme:process:SetProcessDEPPolicy (1): stub
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
fixme:service:scmdatabase_autostart_services Auto-start service L"clr_optimization_v4.0.30319_32" failed to start: 1053
fixme:d3d:wined3d_adapter_find_polyoffset_scale No FBOs, assuming polyoffset scale of 2^23.
fixme:win:EnumDisplayDevicesW ((null),0,0x33f538,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d:wined3d_adapter_find_polyoffset_scale No FBOs, assuming polyoffset scale of 2^23.
fixme:win:EnumDisplayDevicesW ((null),0,0x33f528,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d:wined3d_adapter_find_polyoffset_scale No FBOs, assuming polyoffset scale of 2^23.
fixme:win:EnumDisplayDevicesW ((null),0,0x33f308,0x00000000), stub!
fixme:d3d:wined3d_adapter_find_polyoffset_scale No FBOs, assuming polyoffset scale of 2^23.
fixme:win:EnumDisplayDevicesW ((null),0,0x33f7a8,0x00000000), stub!
fixme:d3d:resource_check_usage Unhandled usage flags 0x20.
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:d3d:buffer_internal_preload Too many declaration changes or converting dynamic buffer, stopping converting
fixme:d3d:resource_check_usage Unhandled usage flags 0x20.
fixme:d3d:buffer_internal_preload Too many declaration changes or converting dynamic buffer, stopping converting
fixme:d3d:buffer_internal_preload Too many declaration changes or converting dynamic buffer, stopping converting
fixme:d3d:buffer_internal_preload Too many declaration changes or converting dynamic buffer, stopping converting
fixme:d3d:buffer_internal_preload Too many declaration changes or converting dynamic buffer, stopping converting
fixme:wmvcore:WMCreateSyncReader ((nil), 0, 0x33fc64): stub
fixme:d3d:wined3d_swapchain_set_gamma_ramp Ignoring flags 0x1.
err:xvidmode:ComputeGammaFromRamp low-biased gamma ramp (588), rejected
fixme:d3d:wined3d_swapchain_set_gamma_ramp Ignoring flags 0x1.
fixme:d3d:wined3d_device_uninit_3d Something's still holding the implicit swapchain.
fixme:d3d:wined3d_device_decref Device released with resources still bound, acceptable but unexpected.
fixme:d3d:wined3d_device_decref Leftover resource 0x1abee8 with type WINED3D_RTYPE_SURFACE (0x1).
fixme:d3d:wined3d_device_decref Leftover resource 0x1abd48 with type WINED3D_RTYPE_TEXTURE (0x3).
fixme:d3d:wined3d_device_decref Leftover resource 0x1aba48 with type WINED3D_RTYPE_SURFACE (0x1).
fixme:d3d:wined3d_device_decref Leftover resource 0x1ab8a8 with type WINED3D_RTYPE_TEXTURE (0x3).
fixme:d3d:wined3d_device_decref Leftover resource 0x1ab790 with type WINED3D_RTYPE_SURFACE (0x1).
fixme:d3d:wined3d_device_decref Leftover resource 0x1ab5f0 with type WINED3D_RTYPE_TEXTURE (0x3).
fixme:d3d:wined3d_device_decref Leftover resource 0x13c740 with type WINED3D_RTYPE_SURFACE (0x1).
fixme:d3d:wined3d_device_decref Leftover resource 0x1a9dd0 with type WINED3D_RTYPE_TEXTURE (0x3).
err:d3d:wined3d_device_decref Context array not freed!
Initialised SoundManager 
```

Thanks for help ^^

---

### Post by QDR06VV9 on 2016-06-09
Hi EpicSides Please do not create multiple threads for the same request it dilutes the community in helping you.
Thanks

---

### Post by EpicSides on 2016-06-09
No problem :)

Deleting the other topic right now.

---

### Post by EpicSides on 2016-06-09
New launching test with most recent version of Wine.

Ugly Graphics Bug Menu problem solved but still unable to run the game after menus (graphical part)
It seems like it's the best version for me to run SA, but it looks like i'm missing some components or something wrong in configuration :(
New report:

```
[06/09/16 22:34:37] - Running wine-1.9.11 gta_sa.exe (Working directory : /home/macaquepc1/.PlayOnLinux/wineprefix/GTASA/drive_c/Program Files/Rockstar Games/GTA San Andreas)
wine: Unhandled page fault on write access to 0x00000000 at address 0x6a5824e2 (thread 0029), starting debugger...
err:dbghelp:pe_load_msc_debug_info -Debug info stripped, but no .DBG file in module L"xul"
wine: configuration in '/home/macaquepc1/.PlayOnLinux//wineprefix/GTASA' has been updated.
wine: Unhandled page fault on read access to 0x00000020 at address 0x7d4ecd05 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000020 in 32-bit code (0x7d4ecd05).
err:dbghelp_msc:codeview_process_info Unknown CODEVIEW signature 8c2e96f8 in module L"gta_sa"
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7d4ecd05 ESP:0177f7d0 EBP:00000020 EFLAGS:00210202(  R- --  I   - - - )
 EAX:7dc60a80 EBX:7d96b000 ECX:00000018 EDX:00000008
 ESI:7dc60a20 EDI:7db7fcfc
Stack dump:
0x0177f7d0:  00000002 00001406 7d85d0d0 00000018
0x0177f7e0:  0013a3a8 00174e8c 7d4ecc99 7e26b32c
0x0177f7f0:  00000007 000000a1 0177fa78 7e183b1a
0x0177f800:  00000007 00000020 ffffffbf 00000258
0x0177f810:  0177f830 7bcd97b0 0177f898 7bc532ae
0x0177f820:  00000002 0332ec00 0177f898 7bc532ae
Backtrace:
=>0 0x7d4ecd05 in i915_dri.so (+0x179d05) (0x00000020)
  1 0x7e183b1a in wined3d (+0x63b19) (0x0177fa78)
  2 0x7e15ef94 in wined3d (+0x3ef93) (0x0177faa8)
  3 0x7e15e53b in wined3d (+0x3e53a) (0x0177fac8)
  4 0x7e15f675 in wined3d (+0x3f674) (0x0177fae8)
  5 0x7e171925 wined3d_device_draw_indexed_primitive+0xa4() in wined3d (0x0177fb28)
  6 0x7c6d2de9 in d3d9 (+0x12de8) (0x0177fb74)
  7 0x007fa391 in gta_sa (+0x3fa390) (0x02d9a238)
0x7d4ecd05: flds    0x0(%ebp)
Modules:
Module    Address            Debug info    Name (127 modules)
PE      240000-  249000    Deferred        ogg
PE      250000-  358000    Deferred        vorbis
PE      360000-  390000    Deferred        eax
PE      400000- 1577000    Export          gta_sa
PE    10000000-10011000    Deferred        vorbisfile
PE    35500000-35708000    Deferred        quartz
ELF    7a800000-7a932000    Deferred        opengl32<elf>
  \-PE    7a820000-7a932000    \               opengl32
ELF    7b400000-7b7ea000    Deferred        kernel32<elf>
  \-PE    7b420000-7b7ea000    \               kernel32
ELF    7bc00000-7bcf7000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcf7000    \               ntdll
ELF    7c000000-7c003000    Deferred        <wine-loader>
ELF    7c483000-7c49e000    Deferred        wmvcore<elf>
  \-PE    7c490000-7c49e000    \               wmvcore
ELF    7c6b6000-7c6f4000    Dwarf           d3d9<elf>
  \-PE    7c6c0000-7c6f4000    \               d3d9
ELF    7c6f4000-7c800000    Deferred        comctl32<elf>
  \-PE    7c700000-7c800000    \               comctl32
ELF    7cb08000-7cb41000    Deferred        uxtheme<elf>
  \-PE    7cb10000-7cb41000    \               uxtheme
ELF    7cb41000-7cb8c000    Deferred        dinput<elf>
  \-PE    7cb50000-7cb8c000    \               dinput
ELF    7cb8c000-7cba7000    Deferred        dinput8<elf>
  \-PE    7cb90000-7cba7000    \               dinput8
ELF    7cba7000-7cbbf000    Deferred        libresolv.so.2
ELF    7cbbf000-7cd37000    Deferred        libvorbisenc.so.2
ELF    7cd37000-7cd6b000    Deferred        libflac.so.8
ELF    7cd6b000-7cddd000    Deferred        libsndfile.so.1
ELF    7cddd000-7ce4c000    Deferred        libpulsecommon-4.0.so
ELF    7ce4c000-7ce9b000    Deferred        libpulse.so.0
ELF    7ce9b000-7cf91000    Deferred        libasound.so.2
ELF    7cf91000-7cfc2000    Deferred        winealsa<elf>
  \-PE    7cfa0000-7cfc2000    \               winealsa
ELF    7d0c5000-7d0f1000    Deferred        libvorbis.so.0
ELF    7d0f1000-7d236000    Deferred        oleaut32<elf>
  \-PE    7d110000-7d236000    \               oleaut32
ELF    7d236000-7d281000    Deferred        dsound<elf>
  \-PE    7d240000-7d281000    \               dsound
ELF    7d281000-7d33e000    Deferred        msvcrt<elf>
  \-PE    7d2a0000-7d33e000    \               msvcrt
ELF    7d351000-7d373000    Deferred        mmdevapi<elf>
  \-PE    7d360000-7d373000    \               mmdevapi
ELF    7d373000-7d976000    Dwarf           i915_dri.so
ELF    7dd79000-7dd82000    Deferred        libogg.so.0
ELF    7ddd7000-7de0e000    Deferred        libtxc_dxtn.so
ELF    7de0f000-7de16000    Deferred        libasyncns.so.0
ELF    7de1c000-7de23000    Deferred        libasound_module_pcm_pulse.so
ELF    7de2f000-7de3a000    Deferred        libpciaccess.so.0
ELF    7de3a000-7de57000    Deferred        libgcc_s.so.1
ELF    7df3f000-7df4c000    Deferred        libdrm_radeon.so.1
ELF    7df4c000-7df54000    Deferred        libdrm_nouveau.so.2
ELF    7df54000-7df76000    Deferred        libdrm_intel.so.1
ELF    7df76000-7dfc1000    Deferred        libdbus-1.so.3
ELF    7dfc1000-7dfcb000    Deferred        libnih-dbus.so.1
ELF    7dfcb000-7dfe4000    Deferred        libnih.so.1
ELF    7dfe4000-7e008000    Deferred        libcgmanager.so.0
ELF    7e008000-7e01b000    Deferred        libudev.so.1
ELF    7e01b000-7e02a000    Deferred        libdrm.so.2
ELF    7e02a000-7e02d000    Deferred        libxshmfence.so.1
ELF    7e02d000-7e034000    Deferred        libxcb-sync.so.1
ELF    7e034000-7e04c000    Deferred        libxcb-glx.so.0
ELF    7e04c000-7e067000    Deferred        libglapi.so.0
ELF    7e067000-7e0f9000    Deferred        libgl.so.1
ELF    7e0f9000-7e103000    Deferred        libwrap.so.0
ELF    7e103000-7e10e000    Deferred        libjson-c.so.2
ELF    7e112000-7e270000    Dwarf           wined3d<elf>
  \-PE    7e120000-7e270000    \               wined3d
ELF    7e270000-7e2e7000    Deferred        ddraw<elf>
  \-PE    7e280000-7e2e7000    \               ddraw
ELF    7e2e7000-7e2ed000    Deferred        libxfixes.so.3
ELF    7e2ed000-7e2f8000    Deferred        libxcursor.so.1
ELF    7e2f8000-7e308000    Deferred        libxi.so.6
ELF    7e308000-7e30c000    Deferred        libxcomposite.so.1
ELF    7e30c000-7e317000    Deferred        libxrandr.so.2
ELF    7e317000-7e322000    Deferred        libxrender.so.1
ELF    7e322000-7e328000    Deferred        libxxf86vm.so.1
ELF    7e328000-7e32c000    Deferred        libxinerama.so.1
ELF    7e32c000-7e333000    Deferred        libxdmcp.so.6
ELF    7e333000-7e337000    Deferred        libxau.so.6
ELF    7e337000-7e359000    Deferred        libxcb.so.1
ELF    7e359000-7e48d000    Deferred        libx11.so.6
ELF    7e48d000-7e4a0000    Deferred        libxext.so.6
ELF    7e4a2000-7e4a6000    Deferred        libxcb-present.so.0
ELF    7e4a6000-7e4aa000    Deferred        libxcb-dri3.so.0
ELF    7e4aa000-7e4b0000    Deferred        libxcb-dri2.so.0
ELF    7e4b0000-7e4b3000    Deferred        libx11-xcb.so.1
ELF    7e4b3000-7e4b7000    Deferred        libxdamage.so.1
ELF    7e4b9000-7e54d000    Deferred        winex11<elf>
  \-PE    7e4c0000-7e54d000    \               winex11
ELF    7e54d000-7e571000    Deferred        imm32<elf>
  \-PE    7e550000-7e571000    \               imm32
ELF    7e5f2000-7e61b000    Deferred        libexpat.so.1
ELF    7e61b000-7e656000    Deferred        libfontconfig.so.1
ELF    7e656000-7e67e000    Deferred        libpng12.so.0
ELF    7e67e000-7e697000    Deferred        libz.so.1
ELF    7e697000-7e737000    Deferred        libfreetype.so.6
ELF    7e750000-7e78b000    Deferred        ws2_32<elf>
  \-PE    7e760000-7e78b000    \               ws2_32
ELF    7e7b1000-7e7db000    Deferred        msacm32<elf>
  \-PE    7e7c0000-7e7db000    \               msacm32
ELF    7e7db000-7e861000    Deferred        rpcrt4<elf>
  \-PE    7e7f0000-7e861000    \               rpcrt4
ELF    7e861000-7e9a8000    Deferred        ole32<elf>
  \-PE    7e880000-7e9a8000    \               ole32
ELF    7e9a8000-7e9c1000    Deferred        version<elf>
  \-PE    7e9b0000-7e9c1000    \               version
ELF    7e9c1000-7ea3c000    Deferred        advapi32<elf>
  \-PE    7e9d0000-7ea3c000    \               advapi32
ELF    7ea3c000-7eb5e000    Deferred        gdi32<elf>
  \-PE    7ea50000-7eb5e000    \               gdi32
ELF    7eb5e000-7ecbd000    Deferred        user32<elf>
  \-PE    7eb70000-7ecbd000    \               user32
ELF    7ecbd000-7ed77000    Deferred        winmm<elf>
  \-PE    7ecd0000-7ed77000    \               winmm
ELF    7ef77000-7ef83000    Deferred        libnss_files.so.2
ELF    7ef83000-7ef8f000    Deferred        libnss_nis.so.2
ELF    7ef8f000-7efa8000    Deferred        libnsl.so.1
ELF    7efa8000-7efb1000    Deferred        libnss_compat.so.2
ELF    7efb1000-7eff7000    Deferred        libm.so.6
ELF    7eff7000-7f000000    Deferred        librt.so.1
ELF    b7361000-b7366000    Deferred        libdl.so.2
ELF    b7366000-b7515000    Deferred        libc.so.6
ELF    b7515000-b7531000    Deferred        libpthread.so.0
ELF    b754b000-b7701000    Dwarf           libwine.so.1
ELF    b7703000-b7725000    Deferred        ld-linux.so.2
ELF    b7727000-b7728000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Rockstar Games\GTA San Andreas\gta_sa.exe
    00000047    0
    00000046    0
    00000045   15
    00000042    0
    00000040    0
    0000003f    0
    00000009    0 <==
0000000e services.exe
    00000025    0
    00000024    0
    0000001d    0
    00000014    0
    00000010    0
    0000000f    0
00000012 mscorsvw.exe
    0000001a    0
    00000019    0
    00000018    0
    00000013    0
0000001b winedevice.exe
    00000021    0
    00000020    0
    0000001f    0
    0000001c    0
00000022 plugplay.exe
    00000027    0
    00000026    0
    00000023    0
0000002a explorer.exe
    00000034    0
    00000032    0
    00000031    0
    0000002e    0
    0000002b    0
System information:
    Wine build: wine-1.9.11
    Platform: i386
    Version: Windows XP
    Host system: Linux
    Host version: 4.2.0-36-generic
../nptl/pthread_mutex_lock.c :359 : __pthread_mutex_lock_full:  l'assertion « robust || (oldval & 0x40000000) == 0 » a échoué.
[06/09/16 22:36:02] - Running wine-1.9.11 gta_sa.exe (Working directory : /home/macaquepc1/.PlayOnLinux/wineprefix/GTASA/drive_c/Program Files/Rockstar Games/GTA San Andreas)
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
fixme:process:SetProcessDEPPolicy (1): stub
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
fixme:process:SetProcessShutdownParameters (00000380, 00000000): partial stub.
fixme:d3d:wined3d_adapter_find_polyoffset_scale No FBOs, assuming polyoffset scale of 2^23.
fixme:win:EnumDisplayDevicesW ((null),0,0x177f538,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d:wined3d_adapter_find_polyoffset_scale No FBOs, assuming polyoffset scale of 2^23.
fixme:win:EnumDisplayDevicesW ((null),0,0x177f528,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d:wined3d_adapter_find_polyoffset_scale No FBOs, assuming polyoffset scale of 2^23.
fixme:win:EnumDisplayDevicesW ((null),0,0x177f318,0x00000000), stub!
fixme:d3d:wined3d_adapter_find_polyoffset_scale No FBOs, assuming polyoffset scale of 2^23.
fixme:win:EnumDisplayDevicesW ((null),0,0x177f7a8,0x00000000), stub!
fixme:d3d:resource_check_usage Unhandled usage flags 0x20.
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
err:d3d:wined3d_texture_prepare_location Texture 0x153660 does not have a drawable.
fixme:d3d:buffer_internal_preload Too many declaration changes or converting dynamic buffer, stopping converting
fixme:d3d_perf:draw_primitive_immediate_mode Drawing using immediate mode.
err:d3d:wined3d_texture_prepare_location Texture 0x153660 does not have a drawable.
fixme:d3d:resource_check_usage Unhandled usage flags 0x20.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
fixme:d3d:buffer_internal_preload Too many declaration changes or converting dynamic buffer, stopping converting
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
fixme:d3d:buffer_internal_preload Too many declaration changes or converting dynamic buffer, stopping converting
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
fixme:d3d:buffer_internal_preload Too many declaration changes or converting dynamic buffer, stopping converting
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
fixme:d3d:buffer_internal_preload Too many declaration changes or converting dynamic buffer, stopping converting
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
fixme:wmvcore:WMCreateSyncReader ((nil), 0, 0x177fc68): stub
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
fixme:d3d:wined3d_swapchain_set_gamma_ramp Ignoring flags 0x1.
err:xvidmode:ComputeGammaFromRamp low-biased gamma ramp (588), rejected
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
fixme:d3d:wined3d_swapchain_set_gamma_ramp Ignoring flags 0x1.
err:xvidmode:ComputeGammaFromRamp low-biased gamma ramp (588), rejected
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x31e9240 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
err:d3d:wined3d_texture_prepare_location Texture 0x139e88 does not have a drawable.
fixme:d3d:buffer_internal_preload Too many declaration changes or converting dynamic buffer, stopping converting
wine: Unhandled page fault on read access to 0x00000020 at address 0x7daead05 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000020 in 32-bit code (0x7daead05).
err:dbghelp_msc:codeview_process_info Unknown CODEVIEW signature 8c2e96f8 in module L"gta_sa"
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7daead05 ESP:0177f7d0 EBP:00000020 EFLAGS:00210202(  R- --  I   - - - )
 EAX:7cea7880 EBX:7df69000 ECX:00000018 EDX:00000008
 ESI:7cea7820 EDI:7cd64a44
Stack dump:
0x0177f7d0:  00000002 00001406 7de5b0d0 00000018
0x0177f7e0:  0013a3e8 00174e8c 7daeac99 7e26932c
0x0177f7f0:  00000007 000000a1 0177fa78 7e181b1a
0x0177f800:  00000007 00000020 ffffffbf 00000258
0x0177f810:  0177f830 7bcd97b0 0177f898 7bc532ae
0x0177f820:  00000002 0332f850 0177f898 7bc532ae
Backtrace:
=>0 0x7daead05 in i915_dri.so (+0x179d05) (0x00000020)
  1 0x7e181b1a in wined3d (+0x61b19) (0x0177fa78)
  2 0x7e15cf94 in wined3d (+0x3cf93) (0x0177faa8)
  3 0x7e15c53b in wined3d (+0x3c53a) (0x0177fac8)
  4 0x7e15d675 in wined3d (+0x3d674) (0x0177fae8)
  5 0x7e16f925 wined3d_device_draw_indexed_primitive+0xa4() in wined3d (0x0177fb28)
  6 0x7cff3de9 in d3d9 (+0x13de8) (0x0177fb74)
  7 0x007fa391 in gta_sa (+0x3fa390) (0x02d9a238)
0x7daead05: flds    0x0(%ebp)
Modules:
Module    Address            Debug info    Name (127 modules)
PE      240000-  249000    Deferred        ogg
PE      250000-  358000    Deferred        vorbis
PE      360000-  390000    Deferred        eax
PE      400000- 1577000    Export          gta_sa
PE    10000000-10011000    Deferred        vorbisfile
PE    35500000-35708000    Deferred        quartz
ELF    7a800000-7a932000    Deferred        opengl32<elf>
  \-PE    7a820000-7a932000    \               opengl32
ELF    7b400000-7b7ea000    Deferred        kernel32<elf>
  \-PE    7b420000-7b7ea000    \               kernel32
ELF    7bc00000-7bcf7000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcf7000    \               ntdll
ELF    7c000000-7c003000    Deferred        <wine-loader>
ELF    7c5f4000-7c700000    Deferred        comctl32<elf>
  \-PE    7c600000-7c700000    \               comctl32
ELF    7cfa2000-7cfbd000    Deferred        wmvcore<elf>
  \-PE    7cfb0000-7cfbd000    \               wmvcore
ELF    7cfd7000-7d015000    Dwarf           d3d9<elf>
  \-PE    7cfe0000-7d015000    \               d3d9
ELF    7d015000-7d04e000    Deferred        uxtheme<elf>
  \-PE    7d020000-7d04e000    \               uxtheme
ELF    7d04e000-7d099000    Deferred        dinput<elf>
  \-PE    7d060000-7d099000    \               dinput
ELF    7d099000-7d0b4000    Deferred        dinput8<elf>
  \-PE    7d0a0000-7d0b4000    \               dinput8
ELF    7d0b4000-7d0cc000    Deferred        libresolv.so.2
ELF    7d0cc000-7d0f8000    Deferred        libvorbis.so.0
ELF    7d0f8000-7d270000    Deferred        libvorbisenc.so.2
ELF    7d270000-7d2a4000    Deferred        libflac.so.8
ELF    7d2a4000-7d316000    Deferred        libsndfile.so.1
ELF    7d316000-7d385000    Deferred        libpulsecommon-4.0.so
ELF    7d385000-7d3d4000    Deferred        libpulse.so.0
ELF    7d3d4000-7d4ca000    Deferred        libasound.so.2
ELF    7d4ca000-7d4fb000    Deferred        winealsa<elf>
  \-PE    7d4d0000-7d4fb000    \               winealsa
ELF    7d4fb000-7d640000    Deferred        oleaut32<elf>
  \-PE    7d510000-7d640000    \               oleaut32
ELF    7d640000-7d68b000    Deferred        dsound<elf>
  \-PE    7d650000-7d68b000    \               dsound
ELF    7d68b000-7d748000    Deferred        msvcrt<elf>
  \-PE    7d6a0000-7d748000    \               msvcrt
ELF    7d752000-7d75b000    Deferred        libogg.so.0
ELF    7d75b000-7d77d000    Deferred        mmdevapi<elf>
  \-PE    7d760000-7d77d000    \               mmdevapi
ELF    7d7d2000-7d809000    Deferred        libtxc_dxtn.so
ELF    7d80a000-7d811000    Deferred        libasyncns.so.0
ELF    7d817000-7d81e000    Deferred        libasound_module_pcm_pulse.so
ELF    7d82a000-7d835000    Deferred        libpciaccess.so.0
ELF    7d835000-7d852000    Deferred        libgcc_s.so.1
ELF    7d93a000-7d947000    Deferred        libdrm_radeon.so.1
ELF    7d947000-7d94f000    Deferred        libdrm_nouveau.so.2
ELF    7d94f000-7d971000    Deferred        libdrm_intel.so.1
ELF    7d971000-7df74000    Dwarf           i915_dri.so
ELF    7df74000-7dfbf000    Deferred        libdbus-1.so.3
ELF    7dfbf000-7dfc9000    Deferred        libnih-dbus.so.1
ELF    7dfc9000-7dfe2000    Deferred        libnih.so.1
ELF    7dfe2000-7e006000    Deferred        libcgmanager.so.0
ELF    7e006000-7e019000    Deferred        libudev.so.1
ELF    7e019000-7e028000    Deferred        libdrm.so.2
ELF    7e028000-7e02b000    Deferred        libxshmfence.so.1
ELF    7e02b000-7e032000    Deferred        libxcb-sync.so.1
ELF    7e032000-7e04a000    Deferred        libxcb-glx.so.0
ELF    7e04a000-7e065000    Deferred        libglapi.so.0
ELF    7e065000-7e0f7000    Deferred        libgl.so.1
ELF    7e0f7000-7e101000    Deferred        libwrap.so.0
ELF    7e101000-7e10c000    Deferred        libjson-c.so.2
ELF    7e110000-7e26e000    Dwarf           wined3d<elf>
  \-PE    7e120000-7e26e000    \               wined3d
ELF    7e26e000-7e2e5000    Deferred        ddraw<elf>
  \-PE    7e280000-7e2e5000    \               ddraw
ELF    7e2e5000-7e2eb000    Deferred        libxfixes.so.3
ELF    7e2eb000-7e2f6000    Deferred        libxcursor.so.1
ELF    7e2f6000-7e306000    Deferred        libxi.so.6
ELF    7e306000-7e30a000    Deferred        libxcomposite.so.1
ELF    7e30a000-7e315000    Deferred        libxrandr.so.2
ELF    7e315000-7e320000    Deferred        libxrender.so.1
ELF    7e320000-7e326000    Deferred        libxxf86vm.so.1
ELF    7e326000-7e32a000    Deferred        libxinerama.so.1
ELF    7e32a000-7e331000    Deferred        libxdmcp.so.6
ELF    7e331000-7e335000    Deferred        libxau.so.6
ELF    7e335000-7e357000    Deferred        libxcb.so.1
ELF    7e357000-7e48b000    Deferred        libx11.so.6
ELF    7e48b000-7e49e000    Deferred        libxext.so.6
ELF    7e4a0000-7e4a4000    Deferred        libxcb-present.so.0
ELF    7e4a4000-7e4a8000    Deferred        libxcb-dri3.so.0
ELF    7e4a8000-7e4ae000    Deferred        libxcb-dri2.so.0
ELF    7e4ae000-7e4b1000    Deferred        libx11-xcb.so.1
ELF    7e4b1000-7e4b5000    Deferred        libxdamage.so.1
ELF    7e4b7000-7e54b000    Deferred        winex11<elf>
  \-PE    7e4c0000-7e54b000    \               winex11
ELF    7e54b000-7e56f000    Deferred        imm32<elf>
  \-PE    7e550000-7e56f000    \               imm32
ELF    7e5fd000-7e626000    Deferred        libexpat.so.1
ELF    7e626000-7e661000    Deferred        libfontconfig.so.1
ELF    7e661000-7e689000    Deferred        libpng12.so.0
ELF    7e689000-7e6a2000    Deferred        libz.so.1
ELF    7e6a2000-7e742000    Deferred        libfreetype.so.6
ELF    7e75b000-7e796000    Deferred        ws2_32<elf>
  \-PE    7e760000-7e796000    \               ws2_32
ELF    7e7c3000-7e7ed000    Deferred        msacm32<elf>
  \-PE    7e7d0000-7e7ed000    \               msacm32
ELF    7e7ed000-7e873000    Deferred        rpcrt4<elf>
  \-PE    7e800000-7e873000    \               rpcrt4
ELF    7e873000-7e9ba000    Deferred        ole32<elf>
  \-PE    7e890000-7e9ba000    \               ole32
ELF    7e9ba000-7ea35000    Deferred        advapi32<elf>
  \-PE    7e9d0000-7ea35000    \               advapi32
ELF    7ea35000-7eb57000    Deferred        gdi32<elf>
  \-PE    7ea40000-7eb57000    \               gdi32
ELF    7eb57000-7ecb6000    Deferred        user32<elf>
  \-PE    7eb70000-7ecb6000    \               user32
ELF    7ecb6000-7ed70000    Deferred        winmm<elf>
  \-PE    7ecc0000-7ed70000    \               winmm
ELF    7ef70000-7ef7c000    Deferred        libnss_files.so.2
ELF    7ef7c000-7ef88000    Deferred        libnss_nis.so.2
ELF    7ef88000-7efa1000    Deferred        libnsl.so.1
ELF    7efa1000-7efe7000    Deferred        libm.so.6
ELF    7efe7000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    b7335000-b733e000    Deferred        libnss_compat.so.2
ELF    b733f000-b7344000    Deferred        libdl.so.2
ELF    b7344000-b74f3000    Deferred        libc.so.6
ELF    b74f3000-b750f000    Deferred        libpthread.so.0
ELF    b7520000-b7529000    Deferred        librt.so.1
ELF    b7529000-b76df000    Dwarf           libwine.so.1
ELF    b76e1000-b7703000    Deferred        ld-linux.so.2
ELF    b7705000-b7706000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Rockstar Games\GTA San Andreas\gta_sa.exe
    00000036    0
    00000035    0
    00000034   15
    00000031    0
    0000002f    0
    00000028    0
    00000009    0 <==
0000000e services.exe
    00000025    0
    00000024    0
    0000001d    0
    00000014    0
    00000010    0
    0000000f    0
00000012 mscorsvw.exe
    0000001a    0
    00000019    0
    00000018    0
    00000013    0
0000001b winedevice.exe
    00000023    0
    00000020    0
    0000001f    0
    0000001c    0
00000021 plugplay.exe
    00000027    0
    00000026    0
    00000022    0
00000029 explorer.exe
    0000002e    0
    0000002d    0
    0000002c    0
    0000002b    0
    0000002a    0
System information:
    Wine build: wine-1.9.11
    Platform: i386
    Version: Windows XP
    Host system: Linux
    Host version: 4.2.0-36-generic
```

---

