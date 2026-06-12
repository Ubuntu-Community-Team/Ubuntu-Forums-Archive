---
title: "Macromedia games"
date: 2007-12-27
forum: Wine
---

### Post by motorbreath on 2007-12-27
Firstly, I have never been able to get anything to work in wine so I am a complete noob but my kids got some educational games for Christmas from their Pop and I would like to get them to run in Ubuntu. I dual boot with Vista but would rather not use it.

Any way the games are put together using macromedia and I managed to get them  installed but when I try to run them it I get starting ..... then it crashes. Terminal output as follows

```
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias -480, std (d/m/y): 25/03/2007, dlt (d/m/y): 28/10/2007
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
wine: Unhandled page fault on read access to 0x000006f8 at address 0x7cd1b856 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x000006f8 in 32-bit code (0x7cd1b856).
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7cd1b856 ESP:0034ec70 EBP:0034ec98 EFLAGS:00210202(   - 00      - -RI1)
 EAX:00000000 EBX:7cdc687c ECX:7ee34860 EDX:7cdc22e0
 ESI:001d6480 EDI:05670240
Stack dump:
0x0034ec70:  00000000 00000000 20000000 00000000
0x0034ec80:  00000000 00000054 00000000 05670444
0x0034ec90:  7ce1c3d4 05670444 0034ed08 7cdfaa56
0x0034eca0:  001d6480 7ce11bd5 05670240 00000000
0x0034ecb0:  00000000 0034ecf8 05670240 0034ed58
0x0034ecc0:  7dd921fe ab492707 00000001 00000000
Backtrace:
=>1 0x7cd1b856 IWineD3DDeviceImpl_GetAvailableTextureMem+0x26(iface=0x1d6480) [/build/buildd/wine-0.9.46/dlls/wined3d/device.c:2300] in wined3d (0x0034ec98)
  2 0x7cdfaa56 DDRAW_Create+0x4f6(guid=<is not available>, DD=0x34eea8, UnkOuter=0x0, iid=0x7ce16ed8) [/build/buildd/wine-0.9.46/dlls/ddraw/main.c:264] in ddraw (0x0034ed08)
  3 0x7cdfae42 DirectDrawCreate+0x102(GUID=<register EDI not in topmost frame>, DD=0x34eea8, UnkOuter=0x0) [/build/buildd/wine-0.9.46/dlls/ddraw/main.c:356] in ddraw (0x0034ed58)
  4 0x66851857 in quicktime.qts (+0x51857) (0x0034efd4)
  5 0x66857926 in quicktime.qts (+0x57926) (0x0034f0a4)
  6 0x668579f1 in quicktime.qts (+0x579f1) (0x0abe92f2)
  7 0x0abe92f2 (0x0abf9c20)
  8 0x00000000 (0x00000000)
0x7cd1b856 IWineD3DDeviceImpl_GetAvailableTextureMem+0x26 [/build/buildd/wine-0.9.46/dlls/wined3d/device.c:2300] in wined3d: movl       0x6f8(%eax),%edx
Unable to open file '/build/buildd/wine-0.9.46/dlls/wined3d/device.c'
Modules:
Module  Address                 Debug info      Name (182 modules)
PE        680000-  68e000       Deferred        sound control.x32
PE       7440000- 745f000       Deferred        filextra.x32
PE       7e80000- 7ed8000       Deferred        zipxtra.x32
PE       7ee0000- 7ee7000       Deferred        bitdreader.x32
PE       7ef0000- 7ef6000       Deferred        gif agent.x32
PE       7f00000- 7f0b000       Deferred        image translator helper.x32
PE       7f10000- 7f16000       Deferred        jpeg agent.x32
PE       7f20000- 7f3a000       Deferred        jpeg export.x32
PE       8660000- 8666000       Deferred        quicktime agent.x32
PE       89a0000- 89d6000       Deferred        budapi.x32
PE       8af0000- 8b05000       Deferred        dmpack1.x32
PE       9020000- 9036000       Deferred        dmpack2.x32
PE       9550000- 9562000       Deferred        dmstars.x32
PE       9a80000- 9a96000       Deferred        dmwaves.x32
PE       9fb0000- 9fca000       Deferred        dmxtremepack.x32
PE       a4e0000- a53e000       Deferred        pmatic.x32
PE       a650000- a661000       Deferred        resolution.x32
PE       a780000- a78b000       Deferred        smxtra.x32
PE      10000000-10021000       Deferred        proj
PE      20000000-2000d000       Deferred        naphd
PE      66800000-674cd000       Export          quicktime.qts
PE      68000000-68131000       Deferred        dirapi
PE      69000000-69097000       Deferred        iml32
PE      6a000000-6a064000       Deferred        textxtra.x32
PE      6a100000-6a146000       Deferred        font xtra.x32
PE      6a200000-6a261000       Deferred        flash asset.x32
PE      6a300000-6a342000       Deferred        mui dialog.x32
PE      6a400000-6a449000       Deferred        qtauth.x32
PE      6a500000-6a5b5000       Deferred        import xtra for powerpoint.x32
PE      6a700000-6a778000       Deferred        swacnvrt.x32
PE      6c080000-6c0a2000       Deferred        qt3asset.x32
PE      6c180000-6c1fe000       Deferred        swacmpr.x32
PE      6c280000-6c2a2000       Deferred        qtexport.x32
PE      6c300000-6c342000       Deferred        flash asset options.x32
PE      6c380000-6c3de000       Deferred        vector editor xtra.x32
PE      6d000000-6d013000       Deferred        text asset.x32
PE      6d040000-6d054000       Deferred        font asset.x32
PE      6d080000-6d0a1000       Deferred        font asset dialog.x32
PE      6d0c0000-6d0e8000       Deferred        xmlparser.x32
PE      6d100000-6d113000       Deferred        cursor asset.x32
PE      6d140000-6d155000       Deferred        swaopt.x32
PE      6d1c0000-6d1d8000       Deferred        textauth.x32
PE      6d200000-6d21f000       Deferred        cursor options.x32
PE      6d240000-6d259000       Deferred        animated gif options.x32
PE      6d280000-6d298000       Deferred        mix services.x32
PE      6d2c0000-6d2d6000       Deferred        sound import export.x32
PE      6d300000-6d327000       Deferred        png import export.x32
PE      6d340000-6d352000       Deferred        swadcmpr.x32
PE      6d440000-6d478000       Deferred        tiff import export.x32
PE      6e000000-6e00f000       Deferred        netfile.x32
PE      6e020000-6e02d000       Deferred        netlingo.x32
PE      6e060000-6e06f000       Deferred        swastrm.x32
PE      6e080000-6e08d000       Deferred        ineturl.x32
PE      6e0a0000-6e0ab000       Deferred        animated gif asset.x32
PE      6e0c0000-6e0d0000       Deferred        actor control.x32
PE      6e120000-6e126000       Deferred        bmp agent.x32
PE      6e140000-6e14e000       Deferred        macromix.x32
PE      6e160000-6e16a000       Deferred        fileio.x32
PE      6e180000-6e18c000       Deferred        squish.x32
PE      6e1a0000-6e1ad000       Deferred        lzcomprs.x32
PE      6e1c0000-6e1ca000       Deferred        sun au import export.x32
PE      6e1e0000-6e1ec000       Deferred        swa import export.x32
PE      6e240000-6e252000       Deferred        lrg import export.x32
PE      6f020000-6f02d000       Deferred        targa import export.x32
PE      6f030000-6f03c000       Deferred        xresagt.x32
PE      6f060000-6f066000       Deferred        avi agent.x32
PE      6f070000-6f076000       Deferred        photoshop clut import.x32
PE      6f080000-6f087000       Deferred        macpaint import.x32
PE      6f0a0000-6f0b4000       Deferred        mpeg 3 import export.x32
PE      6f0c0000-6f0c7000       Deferred        palette import.x32
PE      6f0d0000-6f0d6000       Deferred        pict agent.x32
PE      6f0e0000-6f0e9000       Deferred        photoshop 3.0 import.x32
PE      6f0f0000-6f0f6000       Deferred        script agent.x32
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7cce9000-7cdc9000       Dwarf           wined3d<elf>
  \-PE  7cd00000-7cdc9000       \               wined3d
ELF     7cdc9000-7ce1e000       Dwarf           ddraw<elf>
  \-PE  7cdd0000-7ce1e000       \               ddraw
ELF     7d040000-7d0a1000       Deferred        crypt32<elf>
  \-PE  7d050000-7d0a1000       \               crypt32
ELF     7d0a1000-7d0d6000       Deferred        rsaenh<elf>
  \-PE  7d0b0000-7d0d6000       \               rsaenh
ELF     7d0d6000-7d120000       Deferred        wininet<elf>
  \-PE  7d0e0000-7d120000       \               wininet
ELF     7d120000-7d1be000       Deferred        oleaut32<elf>
  \-PE  7d130000-7d1be000       \               oleaut32
ELF     7d1be000-7d1eb000       Deferred        ws2_32<elf>
  \-PE  7d1d0000-7d1eb000       \               ws2_32
ELF     7d317000-7d322000       Deferred        libgcc_s.so.1
ELF     7d49e000-7d4be000       Deferred        mpr<elf>
  \-PE  7d4b0000-7d4be000       \               mpr
ELF     7d4be000-7d508000       Deferred        dsound<elf>
  \-PE  7d4d0000-7d508000       \               dsound
ELF     7d509000-7d530000       Deferred        msacm32<elf>
  \-PE  7d510000-7d530000       \               msacm32
ELF     7d530000-7d548000       Deferred        msacm32<elf>
  \-PE  7d540000-7d548000       \               msacm32
ELF     7d548000-7d582000       Deferred        wineoss<elf>
  \-PE  7d550000-7d582000       \               wineoss
ELF     7d582000-7d5d3000       Deferred        libgcrypt.so.11
ELF     7d5d3000-7d5d7000       Deferred        libgpg-error.so.0
ELF     7d5d7000-7d5e7000       Deferred        libtasn1.so.3
ELF     7d5e7000-7d5ef000       Deferred        libkrb5support.so.0
ELF     7d5ef000-7d61d000       Deferred        libcrypt.so.1
ELF     7d61d000-7d68d000       Deferred        libgnutls.so.13
ELF     7d68d000-7d6b2000       Deferred        libk5crypto.so.3
ELF     7d6b2000-7d73a000       Deferred        libkrb5.so.3
ELF     7d73a000-7d763000       Deferred        libgssapi_krb5.so.2
ELF     7d763000-7d798000       Deferred        libcups.so.2
ELF     7d79a000-7d7af000       Deferred        midimap<elf>
  \-PE  7d7a0000-7d7af000       \               midimap
ELF     7d7dd000-7d7e0000       Deferred        libcom_err.so.2
ELF     7d86a000-7d89c000       Deferred        uxtheme<elf>
  \-PE  7d870000-7d89c000       \               uxtheme
ELF     7d89c000-7d8b0000       Deferred        lz32<elf>
  \-PE  7d8a0000-7d8b0000       \               lz32
ELF     7d8b0000-7d8ca000       Deferred        version<elf>
  \-PE  7d8c0000-7d8ca000       \               version
ELF     7d8ca000-7d8e8000       Deferred        iphlpapi<elf>
  \-PE  7d8d0000-7d8e8000       \               iphlpapi
ELF     7d8e8000-7d941000       Deferred        rpcrt4<elf>
  \-PE  7d8f0000-7d941000       \               rpcrt4
ELF     7d941000-7d9e2000       Deferred        ole32<elf>
  \-PE  7d950000-7d9e2000       \               ole32
ELF     7d9e2000-7da70000       Deferred        winmm<elf>
  \-PE  7d9f0000-7da70000       \               winmm
ELF     7da70000-7daa5000       Deferred        winspool<elf>
  \-PE  7da80000-7daa5000       \               winspool
ELF     7daa5000-7db63000       Deferred        comctl32<elf>
  \-PE  7dab0000-7db63000       \               comctl32
ELF     7db63000-7dbbc000       Deferred        shlwapi<elf>
  \-PE  7db70000-7dbbc000       \               shlwapi
ELF     7dbbc000-7dcbf000       Deferred        shell32<elf>
  \-PE  7dbd0000-7dcbf000       \               shell32
ELF     7dcbf000-7dd60000       Deferred        comdlg32<elf>
  \-PE  7dcd0000-7dd60000       \               comdlg32
ELF     7dd60000-7ddc8000       Deferred        msvcrt<elf>
  \-PE  7dd70000-7ddc8000       \               msvcrt
ELF     7ddc8000-7dde5000       Deferred        imm32<elf>
  \-PE  7ddd0000-7dde5000       \               imm32
ELF     7dde5000-7dded000       Deferred        libxrender.so.1
ELF     7dded000-7ddef000       Deferred        libkeyutils.so.1
ELF     7ddef000-7de02000       Deferred        libresolv.so.2
ELF     7de5f000-7de61000       Deferred        libnvidia-tls.so.1
ELF     7de61000-7e7f9000       Deferred        libglcore.so.1
ELF     7e7f9000-7e88f000       Deferred        libgl.so.1
ELF     7e88f000-7e894000       Deferred        libxdmcp.so.6
ELF     7e894000-7e897000       Deferred        libxau.so.6
ELF     7e897000-7e988000       Deferred        libx11.so.6
ELF     7e988000-7e996000       Deferred        libxext.so.6
ELF     7e996000-7e99b000       Deferred        libxxf86vm.so.1
ELF     7e99b000-7e9b3000       Deferred        libice.so.6
ELF     7e9b3000-7e9bb000       Deferred        libsm.so.6
ELF     7e9bc000-7e9c1000       Deferred        libxfixes.so.3
ELF     7e9c1000-7e9ca000       Deferred        libxcursor.so.1
ELF     7e9ca000-7e9d0000       Deferred        libxrandr.so.2
ELF     7e9d2000-7ea5d000       Deferred        winex11<elf>
  \-PE  7e9e0000-7ea5d000       \               winex11
ELF     7eb66000-7eb86000       Deferred        libexpat.so.1
ELF     7eb86000-7ebb1000       Deferred        libfontconfig.so.1
ELF     7ebb1000-7ebc6000       Deferred        libz.so.1
ELF     7ebc6000-7ec36000       Deferred        libfreetype.so.6
ELF     7ec4d000-7ec96000       Deferred        advapi32<elf>
  \-PE  7ec60000-7ec96000       \               advapi32
ELF     7ec96000-7ed31000       Deferred        gdi32<elf>
  \-PE  7ecb0000-7ed31000       \               gdi32
ELF     7ed31000-7ee6f000       Deferred        user32<elf>
  \-PE  7ed50000-7ee6f000       \               user32
ELF     7ef8e000-7ef99000       Deferred        libnss_files.so.2
ELF     7ef99000-7efa3000       Deferred        libnss_nis.so.2
ELF     7efa3000-7efbb000       Deferred        libnsl.so.1
ELF     7efbb000-7efc4000       Deferred        libnss_compat.so.2
ELF     7efc4000-7efe9000       Deferred        libm.so.6
ELF     b7c84000-b7c88000       Deferred        libdl.so.2
ELF     b7c88000-b7dd2000       Deferred        libc.so.6
ELF     b7dd3000-b7deb000       Deferred        libpthread.so.0
ELF     b7e02000-b7f16000       Deferred        libwine.so.1
ELF     b7f18000-b7f34000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\Eureka\Numbers & Puzzles\Naphd.exe
        00000012   15
        0000000f    1
        00000009    0 <==

```

No idea what it all means so any help would be appreciated.

---

### Post by JarvidLol on 2007-12-27
If they are just flash files then you can open them with firefox with no problem if you have flash installed.

---

### Post by markharding557 on 2007-12-27
try installing flash for windows into wine
if it needs ie you may have to install that
also if you have an older copy of windows you could try to run this in virtualbox or vmware

---

### Post by airtonix on 2007-12-27
macromedia games? thats a new name for it.... i guess coming from a brand identification based operating system that turns your computer into a remote shop front for distant megacorps does that to ones association of protocols and devices.

If you want to identify products by their corporate owner, you should be calling it 'Adobe Games'.

since Adobe now own Macromedia. This is funny, since the original Macromedia team used to work for Adobe.

Flash Player version 9 is in the repos for ubuntu. You most likely need to have the multiverse and universe repos enabled, then you can : 

> sudo apt-get install flashplugin-nonfree

Edit: 

Just tried installing it on my recently installed ubuntu feisty, and i get this error...(it looks like adobes fault)

> 13:19:55 (52.52 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

---

### Post by davidforehand on 2007-12-28
it may be possible that they may need macromedia shockwave which is not supported in Linux. Some internet games require this. However I have been able to get shockwave to work by installing the windows version using Crossover Office which is a commercial piece of software that would cost you some money. I am not sure if you would be able to use Wine. I tried it awhile ago with wine and couldnt get it to install, but maybe newer versions will work.

---

### Post by volkswagner on 2007-12-30
Wow Linux users left in the dark again.  Bummer!  Is there any chance shockwave will ever work in Linux running FireFox?

Things like this make Linux a hard sell to even the most basic computer user if the kids cant play their favorite games at Noggin.com and many others.

---

