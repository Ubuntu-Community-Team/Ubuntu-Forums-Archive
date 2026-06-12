---
title: "Help with battlefield 2."
date: 2013-12-24
forum: Wine
---

### Post by itsneroo11 on 2013-12-24
I launch it with wine emulated desktop + i installed d3dx9_24 and 25 into my system 32 folder and i tried launching it with terminal thats what teminal spits out.

```

fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 53 (SPI_SETTOGGLEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33f85c 1 C) semi-stub
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33f6ec 1 C) semi-stub
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33ef78 1 C) semi-stub
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33efdc 1 C) semi-stub
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33e458 1 C) semi-stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33ec50,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x33ec50,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ec50,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x33ec50,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ea60,0x00000000), stub!
wine: Call from 0x7bc54610 to unimplemented function GDI32.dll.GdiEntry1, aborting
wine: Unimplemented function GDI32.dll.GdiEntry1 called at address 0x7bc54610 (thread 0050), starting debugger...
Unhandled exception: unimplemented function GDI32.dll.GdiEntry1 called in 32-bit code (0x7bc54610).
err:dbghelp_msc:codeview_process_info Unknown CODEVIEW signature 00750030 in module L"bf2"
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc54610 ESP:0033e340 EBP:0033e3a4 EFLAGS:00000202(   - --  I   - - - )
 EAX:0391abbe EBX:7bcc6ff4 ECX:023f7308 EDX:023f7344
 ESI:0033e34c EDI:00000000
Stack dump:
0x0033e340:  00303fa5 00000078 7bc9e835 80000100
0x0033e350:  00000001 00000000 7bc54610 00000002
0x0033e360:  0391abf4 0391abbe 7ec51656 00000000
0x0033e370:  0033e7df b73cd6c0 00000026 b75c9c2a
0x0033e380:  00000000 7bcc6ff4 7ec5166e 0033ea00
0x0033e390:  0033e3ac 00000000 bf8b6048 023f733c
Backtrace:
=>0 0x7bc54610 call_dll_entry_point+0x310() in ntdll (0x0033e3a4)
  1 0x03150357 (0x0033ec00)
  2 0x037bae42 in d3d9 (+0x2ae41) (0x0033efb4)
  3 0x037bc445 in d3d9 (+0x2c444) (0x0033efdc)
  4 0x037b9f35 in d3d9 (+0x29f34) (0x0033f1e0)
  5 0x037ba5dd in d3d9 (+0x2a5dc) (0x0033f2f8)
  6 0x0330bcf8 in renddx9 (+0xbcf7) (0x0033f330)
  7 0x033298ba in renddx9 (+0x298b9) (0x0033f384)
  8 0x00611d9e in bf2 (+0x211d9d) (0x0033f3d8)
  9 0x00613bb4 in bf2 (+0x213bb3) (0x0033f42c)
  10 0x00614170 in bf2 (+0x21416f) (0x0033f6a8)
  11 0x03355980 in renddx9 (+0x5597f) (0x0033f6d8)
  12 0x0061b0d4 in bf2 (+0x21b0d3) (0x0033f7f8)
  13 0x00436776 in bf2 (+0x36775) (0x0033f9ac)
  14 0x0042e3f1 in bf2 (+0x2e3f0) (0x0033fac4)
  15 0x0040b19e in bf2 (+0xb19d) (0x0033fca8)
  16 0x00401e33 in bf2 (+0x1e32) (0x0033fcf8)
  17 0x004028f4 in bf2 (+0x28f3) (0x0033fd60)
  18 0x00402b98 in bf2 (+0x2b97) (0x0033fda8)
  19 0x00402c39 in bf2 (+0x2c38) (0x0033fdb8)
  20 0x007dc76d in bf2 (+0x3dc76c) (0x0033fe60)
  21 0x7b85f9fc call_process_entry+0xb() in kernel32 (0x0033fe78)
  22 0x7b860c7b in kernel32 (+0x50c7a) (0x0033feb8)
  23 0x7bc80790 call_thread_func_wrapper+0xb() in ntdll (0x0033fed8)
  24 0x7bc8379d call_thread_func+0x7c() in ntdll (0x0033ffa8)
  25 0x7bc8076e RtlRaiseException+0x21() in ntdll (0x0033ffc8)
  26 0x7bc5463e call_dll_entry_point+0x33d() in ntdll (0x0033ffe8)
  27 0xb75c88ed wine_call_on_stack+0x1c() in libwine.so.1 (0x00000000)
  28 0xb75c89ab wine_switch_to_stack+0x2a() in libwine.so.1 (0xbfcd63c8)
  29 0x7bc5a500 LdrInitializeThunk+0x3af() in ntdll (0xbfcd6438)
  30 0x7b867458 __wine_kernel_init+0xa27() in kernel32 (0xbfcd75e8)
  31 0x7bc5af3b __wine_process_init+0x25a() in ntdll (0xbfcd7678)
  32 0xb75c5e50 wine_init+0x2ef() in libwine.so.1 (0xbfcd76e8)
  33 0x7bf00f8b main+0xfa() in <wine-loader> (0xbfcd7b38)
  34 0xb73e7935 __libc_start_main+0xf4() in libc.so.6 (0x00000000)
0x7bc54610 call_dll_entry_point+0x310 in ntdll: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (119 modules)
PE      340000-  359000    Deferred        zlib122
PE      360000-  399000    Deferred        bf2voipserver
PE      3a0000-  3ed000    Deferred        bf2audio
PE      3f0000-  3f6000    Deferred        d3d8thk
PE      400000-  9c3000    Export          bf2
PE      9d0000-  b50000    Deferred        dice_py
PE     2d20000- 2ee6000    Deferred        bf2openal
PE     3100000- 3142000    Deferred        textureatlasbuilder
PE     3160000- 3173000    Deferred        pcregexp
PE     3300000- 352d000    Export          renddx9
PE     3530000- 3783000    Deferred        d3dx9_25
PE     3790000- 3939000    Export          d3d9
PE    10000000-10122000    Deferred        memory
PE    30000000-3006d000    Deferred        binkw32
PE    51080000-510e1000    Deferred        dsound
PE    6ce10000-6cebf000    Deferred        dinput8
PE    77f60000-77fd6000    Deferred        shlwapi
ELF    7b800000-7ba5b000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba5b000    \               kernel32
ELF    7bc00000-7bce4000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bce4000    \               ntdll
ELF    7bf00000-7bf04000    Dwarf           <wine-loader>
PE    7c340000-7c396000    Deferred        msvcr71
ELF    7cfe6000-7d01c000    Deferred        uxtheme<elf>
  \-PE    7cff0000-7d01c000    \               uxtheme
ELF    7d01c000-7d125000    Deferred        comctl32<elf>
  \-PE    7d020000-7d125000    \               comctl32
ELF    7d50b000-7d552000    Deferred        avifil32<elf>
  \-PE    7d510000-7d552000    \               avifil32
ELF    7d5b7000-7d5e3000    Deferred        msvfw32<elf>
  \-PE    7d5c0000-7d5e3000    \               msvfw32
ELF    7d5e3000-7d600000    Deferred        libgcc_s.so.1
ELF    7d702000-7d727000    Deferred        imm32<elf>
  \-PE    7d710000-7d727000    \               imm32
ELF    7d727000-7d73e000    Deferred        libresolv.so.2
ELF    7d73e000-7d746000    Deferred        libogg.so.0
ELF    7d746000-7d772000    Deferred        libvorbis.so.0
ELF    7d772000-7d8ea000    Deferred        libvorbisenc.so.2
ELF    7d8ea000-7d93a000    Deferred        libflac.so.8
ELF    7d93a000-7d941000    Deferred        libasyncns.so.0
ELF    7d941000-7d9b5000    Deferred        libsndfile.so.1
ELF    7d9b5000-7d9ff000    Deferred        libdbus-1.so.3
ELF    7d9ff000-7da6a000    Deferred        libpulsecommon-3.0.so
ELF    7da6a000-7dab9000    Deferred        libpulse.so.0
ELF    7dad5000-7dafd000    Deferred        winepulse<elf>
  \-PE    7dae0000-7dafd000    \               winepulse
ELF    7dafd000-7dc31000    Deferred        oleaut32<elf>
  \-PE    7db10000-7dc31000    \               oleaut32
ELF    7dc31000-7dc53000    Deferred        mmdevapi<elf>
  \-PE    7dc40000-7dc53000    \               mmdevapi
ELF    7dd99000-7dda0000    Deferred        libxfixes.so.3
ELF    7dda0000-7ddab000    Deferred        libxcursor.so.1
ELF    7ddab000-7ddbb000    Deferred        libxi.so.6
ELF    7ddbb000-7ddbf000    Deferred        libxcomposite.so.1
ELF    7ddbf000-7ddca000    Deferred        libxrandr.so.2
ELF    7ddca000-7ddd4000    Deferred        libxrender.so.1
ELF    7ddd4000-7ddda000    Deferred        libxxf86vm.so.1
ELF    7ddda000-7ddde000    Deferred        libxinerama.so.1
ELF    7ddde000-7dde5000    Deferred        libxdmcp.so.6
ELF    7dde5000-7dde9000    Deferred        libxau.so.6
ELF    7dde9000-7de0b000    Deferred        libxcb.so.1
ELF    7de0b000-7df42000    Deferred        libx11.so.6
ELF    7df42000-7df54000    Deferred        libxext.so.6
ELF    7df5a000-7df64000    Deferred        libwrap.so.0
ELF    7df64000-7df6e000    Deferred        libjson.so.0
ELF    7df70000-7e004000    Deferred        winex11<elf>
  \-PE    7df80000-7e004000    \               winex11
ELF    7e066000-7e101000    Deferred        libfreetype.so.6
ELF    7e146000-7e16e000    Deferred        libexpat.so.1
ELF    7e16e000-7e1a7000    Deferred        libfontconfig.so.1
ELF    7e1a7000-7e1c6000    Deferred        libtinfo.so.5
ELF    7e1c6000-7e1e8000    Deferred        libncurses.so.5
ELF    7e204000-7e439000    Deferred        shell32<elf>
  \-PE    7e210000-7e439000    \               shell32
ELF    7e439000-7e508000    Deferred        crypt32<elf>
  \-PE    7e440000-7e508000    \               crypt32
ELF    7e508000-7e52e000    Deferred        iphlpapi<elf>
  \-PE    7e510000-7e52e000    \               iphlpapi
ELF    7e52e000-7e54a000    Deferred        wsock32<elf>
  \-PE    7e530000-7e54a000    \               wsock32
ELF    7e54a000-7e575000    Deferred        msacm32<elf>
  \-PE    7e550000-7e575000    \               msacm32
ELF    7e575000-7e5f8000    Deferred        rpcrt4<elf>
  \-PE    7e580000-7e5f8000    \               rpcrt4
ELF    7e5f8000-7e736000    Deferred        ole32<elf>
  \-PE    7e610000-7e736000    \               ole32
ELF    7e736000-7e7ef000    Deferred        winmm<elf>
  \-PE    7e740000-7e7ef000    \               winmm
ELF    7e7ef000-7e825000    Deferred        ws2_32<elf>
  \-PE    7e800000-7e825000    \               ws2_32
ELF    7e825000-7e8cf000    Deferred        msvcrt<elf>
  \-PE    7e840000-7e8cf000    \               msvcrt
ELF    7e8cf000-7e9fc000    Deferred        msvcp71<elf>
  \-PE    7e900000-7e9fc000    \               msvcp71
ELF    7e9fc000-7ea6c000    Deferred        advapi32<elf>
  \-PE    7ea10000-7ea6c000    \               advapi32
ELF    7ea6c000-7eb8a000    Deferred        gdi32<elf>
  \-PE    7ea80000-7eb8a000    \               gdi32
ELF    7eb8a000-7ece5000    Deferred        user32<elf>
  \-PE    7eba0000-7ece5000    \               user32
ELF    7ece5000-7ecfe000    Deferred        libz.so.1
ELF    7ed00000-7ed1a000    Deferred        version<elf>
  \-PE    7ed10000-7ed1a000    \               version
ELF    7ed1a000-7ed82000    Deferred        dbghelp<elf>
  \-PE    7ed20000-7ed82000    \               dbghelp
ELF    7ef82000-7ef8f000    Deferred        libnss_files.so.2
ELF    7ef8f000-7ef9b000    Deferred        libnss_nis.so.2
ELF    7ef9b000-7efb4000    Deferred        libnsl.so.1
ELF    7efb4000-7efbd000    Deferred        libnss_compat.so.2
ELF    7efbd000-7f000000    Deferred        libm.so.6
ELF    b73c4000-b73cd000    Deferred        librt.so.1
ELF    b73ce000-b7582000    Dwarf           libc.so.6
ELF    b7582000-b7587000    Deferred        libdl.so.2
ELF    b7588000-b75a3000    Deferred        libpthread.so.0
ELF    b75aa000-b75be000    Deferred        psapi<elf>
  \-PE    b75b0000-b75be000    \               psapi
ELF    b75bf000-b7775000    Dwarf           libwine.so.1
ELF    b7777000-b7799000    Deferred        ld-linux.so.2
ELF    b7799000-b779a000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    00000023    0
    00000022    0
    0000001c    0
    00000010    0
    0000000f    0
0000001a winedevice.exe
    00000026    0
    0000001f    0
    0000001e    0
    0000001b    0
00000020 plugplay.exe
    00000025    0
    00000024    0
    00000021    0
00000027 explorer.exe
    0000002b    0
    00000028    0
00000029 Steam.exe
    0000006e    0
    00000016    0
    00000052    0
    0000004f    0
    0000004e    0
    0000004c    0
    0000004b    0
    0000004a    0
    00000049    0
    00000048    0
    00000035    0
    0000002c    0
    0000002d    0
    0000002e    0
    00000034    0
    00000032    0
    00000031    0
    0000000d    0
    0000000b    0
    00000014    0
    00000011    0
    00000013   15
    00000019    0
    00000017    0
    00000047    0
    00000046    0
    00000045    0
    00000043    0
    00000042    0
    00000041    0
    00000040    0
    0000003f    0
    0000003e    0
    0000003d    0
    0000003c    0
    0000003b    0
    0000003a    0
    00000039    0
    00000038    0
    00000037    0
    00000036    0
    00000033    0
    00000030    0
    0000002f    0
    0000002a    0
00000069 (D) Z:\home\vaio\Desktop\Games\BF2.exe
    00000087    0
    00000082    0
    00000073    0
    00000072    0
    00000074    0
    0000005d   15
    00000050    0 <==
0000005f explorer.exe
    0000005e    0
    00000062    0

```

---

