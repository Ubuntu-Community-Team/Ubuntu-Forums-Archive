---
title: "Insanely Twisted Shadow Planet"
date: 2012-04-27
forum: Wine
---

### Post by SirDakkalot on 2012-04-27
So I recently purchased Insanely Twisted Shadow Planet on Steam (which  currently has no entry in the database) and it comes with GFWL. I know  there's a fix for GTA IV wherein you place the xlive.dll into the game's  folder, but it doesn't seem to work with this. It attempts to install  GFWL before crashing and stating that FCEngine-GFWL.exe has stopped  working. Using the latest wine and ubuntu versions.

Here's the terminal output:

```
fixme:gameux:GameExplorerImpl_VerifyAccess (0x5782b2d0, L"c:\\program files\\steam\\steamapps\\common\\insanely twisted shadow planet\\registergame.exe", 0x32d858)
fixme:dwmapi:DwmSetWindowAttribute (0x60132, 2, 0x32d570, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x60132, 3, 0x32d57c, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x60132, 4, 0x32d56c, 4) stub
fixme:process:GetLogicalProcessorInformation ((nil),0x33dba4): stub
fixme:process:GetLogicalProcessorInformation (0x20cbc20,0x33dba4): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:win:EnumDisplayDevicesW ((null),0,0x33f3d8,0x00000000), stub!
fixme:appbar:SHAppBarMessage unknown msg: 4
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=3): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=1): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=0): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=2): stub
fixme:appbar:SHAppBarMessage unknown msg: 4
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=3): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=1): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=0): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=2): stub
fixme:win:RegisterRawInputDevices (pRawInputDevices=0x1abdd6c, uiNumDevices=1, cbSize=12) stub!
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
wine: Call from 0x7bc4a970 to unimplemented function xlive.dll.64, aborting
wine: Unimplemented function xlive.dll.64 called at address 0x7bc4a970 (thread 0067), starting debugger...
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Audio",0x7b3ea1c): stub
Unhandled exception: unimplemented function xlive.dll.64 called in 32-bit code (0x7bc4a970).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7bc4a970 ESP:0033f998 EBP:0033f9fc EFLAGS:00200202(   - --  I   - - - )
 EAX:00000040 EBX:7bca7ff4 ECX:0033fa20 EDX:0033fa18
 ESI:0033f9a4 EDI:076c4218
Stack dump:
0x0033f998:  00000000 00000000 01a91000 80000100
0x0033f9a8:  00000001 00000000 7bc4a970 00000002
0x0033f9b8:  00661d9e 00000040 7bc48450 00000014
0x0033f9c8:  076c4218 0033f9ec 78583db8 01a91000
0x0033f9d8:  00000000 00000014 076c4218 00000000
0x0033f9e8:  076d89ac 0033fabc 004205e8 00000000
Backtrace:
=>0 0x7bc4a970 call_dll_entry_point+0x5f0() in ntdll (0x0033f9fc)
  1 0x0034000f (0x0033fabc)
  2 0x0040420d in fcengine-gfwl (+0x420c) (0x0033fe70)
  3 0x7b85a1ac call_process_entry+0xb() in kernel32 (0x0033fe88)
  4 0x7b85b41f in kernel32 (+0x4b41e) (0x0033fec8)
  5 0x7bc72f60 call_thread_func_wrapper+0xb() in ntdll (0x0033fed8)
  6 0x7bc759ed call_thread_func+0x7c() in ntdll (0x0033ffa8)
  7 0x7bc72f3e RtlRaiseException+0x21() in ntdll (0x0033ffc8)
  8 0x7bc4a99e call_dll_entry_point+0x61d() in ntdll (0x0033ffe8)
0x7bc4a970 call_dll_entry_point+0x5f0 in ntdll: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (130 modules)
PE      350000-  3a0000    Deferred        fmod_event
PE      3a0000-  3b6000    Deferred        xinput1_3
PE      400000-  917000    Export          fcengine-gfwl
PE      920000-  a28000    Deferred        fmodex
PE      a30000-  c2f000    Deferred        d3dx9_43
PE      c30000-  cc2000    Deferred        gameoverlayrenderer
PE    10000000-1001c000    Deferred        xlive
PE    78480000-7850e000    Deferred        msvcp90
PE    78520000-785c3000    Deferred        msvcr90
ELF    79eef000-7b800000    Deferred        libnvidia-glcore.so.280.13
ELF    7b800000-7ba16000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba16000    \               kernel32
ELF    7bc00000-7bcc4000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcc4000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7c600000-7c608000    Deferred        libogg.so.0
ELF    7c608000-7c633000    Deferred        libvorbis.so.0
ELF    7c633000-7c7ab000    Deferred        libvorbisenc.so.2
ELF    7c7ab000-7c7f9000    Deferred        libflac.so.8
ELF    7c7f9000-7c86a000    Deferred        libsndfile.so.1
ELF    7c86a000-7c8cf000    Deferred        libpulsecommon-1.0.so
ELF    7c8cf000-7c91d000    Deferred        libpulse.so.0
ELF    7c936000-7c93d000    Deferred        libasound_module_pcm_pulse.so
ELF    7c93d000-7ca2e000    Deferred        libasound.so.2
ELF    7ca32000-7ca39000    Deferred        libasyncns.so.0
ELF    7ca39000-7ca43000    Deferred        libwrap.so.0
ELF    7ca43000-7ca4b000    Deferred        libjson.so.0
ELF    7ca4e000-7ca7a000    Deferred        winealsa<elf>
  \-PE    7ca50000-7ca7a000    \               winealsa
ELF    7ca7a000-7cb6d000    Deferred        oleaut32<elf>
  \-PE    7ca90000-7cb6d000    \               oleaut32
ELF    7cb6d000-7cb90000    Deferred        mmdevapi<elf>
  \-PE    7cb70000-7cb90000    \               mmdevapi
ELF    7d119000-7d151000    Deferred        usp10<elf>
  \-PE    7d120000-7d151000    \               usp10
ELF    7d802000-7d8d4000    Deferred        libgl.so.1
ELF    7d8d4000-7d908000    Deferred        uxtheme<elf>
  \-PE    7d8e0000-7d908000    \               uxtheme
ELF    7d908000-7d911000    Deferred        librt.so.1
ELF    7d911000-7d928000    Deferred        libresolv.so.2
ELF    7d928000-7d971000    Deferred        libdbus-1.so.3
ELF    7d971000-7d9f6000    Deferred        libgcrypt.so.11
ELF    7d9f6000-7da08000    Deferred        libtasn1.so.3
ELF    7da08000-7da31000    Deferred        libk5crypto.so.3
ELF    7da31000-7dafa000    Deferred        libkrb5.so.3
ELF    7dafa000-7db0d000    Deferred        libavahi-client.so.3
ELF    7dc14000-7dc19000    Deferred        libgpg-error.so.0
ELF    7dc19000-7dcc9000    Deferred        libgnutls.so.26
ELF    7dcc9000-7dd07000    Deferred        libgssapi_krb5.so.2
ELF    7dd07000-7dd59000    Deferred        libcups.so.2
ELF    7ddde000-7dde9000    Deferred        libxcursor.so.1
ELF    7ddea000-7ddee000    Deferred        libkeyutils.so.1
ELF    7ddee000-7ddf7000    Deferred        libkrb5support.so.0
ELF    7ddf7000-7ddfb000    Deferred        libcom_err.so.2
ELF    7ddfb000-7de09000    Deferred        libavahi-common.so.3
ELF    7de60000-7de8a000    Deferred        libexpat.so.1
ELF    7de8a000-7debf000    Deferred        libfontconfig.so.1
ELF    7debf000-7decf000    Deferred        libxi.so.6
ELF    7decf000-7ded8000    Deferred        libxrandr.so.2
ELF    7ded8000-7dee3000    Deferred        libxrender.so.1
ELF    7dee3000-7dee9000    Deferred        libxxf86vm.so.1
ELF    7dee9000-7df08000    Deferred        libxcb.so.1
ELF    7df08000-7df22000    Deferred        libice.so.6
ELF    7df22000-7e058000    Deferred        libx11.so.6
ELF    7e058000-7e06b000    Deferred        libxext.so.6
ELF    7e06b000-7e0fe000    Deferred        winex11<elf>
  \-PE    7e080000-7e0fe000    \               winex11
ELF    7e0fe000-7e195000    Deferred        libfreetype.so.6
ELF    7e1d7000-7e1da000    Deferred        libnvidia-tls.so.280.13
ELF    7e1dc000-7e1e2000    Deferred        libxfixes.so.3
ELF    7e1f7000-7e20c000    Deferred        libz.so.1
ELF    7e20d000-7e211000    Deferred        libxcomposite.so.1
ELF    7e211000-7e215000    Deferred        libxinerama.so.1
ELF    7e215000-7e21c000    Deferred        libxdmcp.so.6
ELF    7e21c000-7e225000    Deferred        libsm.so.6
ELF    7e22c000-7e24e000    Deferred        imm32<elf>
  \-PE    7e230000-7e24e000    \               imm32
ELF    7e24e000-7e346000    Deferred        comctl32<elf>
  \-PE    7e260000-7e346000    \               comctl32
ELF    7e346000-7e3b0000    Deferred        shlwapi<elf>
  \-PE    7e350000-7e3b0000    \               shlwapi
ELF    7e3b0000-7e5c0000    Deferred        shell32<elf>
  \-PE    7e3c0000-7e5c0000    \               shell32
ELF    7e5c0000-7e5d4000    Deferred        psapi<elf>
  \-PE    7e5d0000-7e5d4000    \               psapi
ELF    7e5d4000-7e60e000    Deferred        winspool<elf>
  \-PE    7e5e0000-7e60e000    \               winspool
ELF    7e60e000-7e675000    Deferred        setupapi<elf>
  \-PE    7e620000-7e675000    \               setupapi
ELF    7e675000-7e7a9000    Deferred        wined3d<elf>
  \-PE    7e680000-7e7a9000    \               wined3d
ELF    7e7a9000-7e7e2000    Deferred        d3d9<elf>
  \-PE    7e7b0000-7e7e2000    \               d3d9
ELF    7e7e2000-7e86f000    Deferred        msvcrt<elf>
  \-PE    7e800000-7e86f000    \               msvcrt
ELF    7e86f000-7e897000    Deferred        msacm32<elf>
  \-PE    7e870000-7e897000    \               msacm32
ELF    7e897000-7e944000    Deferred        winmm<elf>
  \-PE    7e8a0000-7e944000    \               winmm
ELF    7e944000-7e966000    Deferred        iphlpapi<elf>
  \-PE    7e950000-7e966000    \               iphlpapi
ELF    7e966000-7e981000    Deferred        wsock32<elf>
  \-PE    7e970000-7e981000    \               wsock32
ELF    7e981000-7e9b3000    Deferred        ws2_32<elf>
  \-PE    7e990000-7e9b3000    \               ws2_32
ELF    7e9b3000-7ea29000    Deferred        rpcrt4<elf>
  \-PE    7e9c0000-7ea29000    \               rpcrt4
ELF    7ea29000-7eae6000    Deferred        gdi32<elf>
  \-PE    7ea40000-7eae6000    \               gdi32
ELF    7eae6000-7ec27000    Deferred        user32<elf>
  \-PE    7eb00000-7ec27000    \               user32
ELF    7ec27000-7ec88000    Deferred        advapi32<elf>
  \-PE    7ec30000-7ec88000    \               advapi32
ELF    7ec88000-7ed90000    Deferred        ole32<elf>
  \-PE    7eca0000-7ed90000    \               ole32
ELF    7ed90000-7ed9d000    Deferred        libnss_files.so.2
ELF    7ed9d000-7edb6000    Deferred        libnsl.so.1
ELF    7efb6000-7efe0000    Deferred        libm.so.6
ELF    7efe1000-7efe7000    Deferred        libuuid.so.1
ELF    7efe7000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    f73f3000-f73ff000    Deferred        libnss_nis.so.2
ELF    f7400000-f7405000    Deferred        libdl.so.2
ELF    f7405000-f757f000    Deferred        libc.so.6
ELF    f7580000-f759b000    Deferred        libpthread.so.0
ELF    f759c000-f75a0000    Deferred        libxau.so.6
ELF    f75b0000-f75ba000    Deferred        libnss_compat.so.2
ELF    f75bb000-f76fd000    Dwarf           libwine.so.1
ELF    f76ff000-f771f000    Deferred        ld-linux.so.2
ELF    f771f000-f7720000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 steam.exe
    00000017    0
    0000005a    0
    00000057    0
    00000050    0
    0000004f    0
    0000004d    0
    0000004c    0
    0000004b    1
    0000004a    1
    00000049    0
    00000048    0
    00000038    0
    00000025    0
    0000000d    0
    0000000b    0
    00000047    0
    00000046    0
    00000045    0
    00000044    0
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
    00000037    0
    00000036    0
    00000035    0
    00000034    0
    00000033    0
    00000032    0
    00000031    0
    00000030    0
    0000002f    0
    0000002e    0
    0000002d    0
    0000002c    0
    0000002b    0
    0000002a    0
    00000029    0
    00000028    0
    00000027    0
    00000026    0
    00000024    0
    00000023    0
    00000009    0
0000000e services.exe
    0000001e    0
    0000001d    0
    00000015    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001f    0
    00000019    0
    00000014    0
    00000013    0
0000001a plugplay.exe
    00000020    0
    0000001c    0
    0000001b    0
00000021 explorer.exe
    00000022    0
00000066 (D) C:\Program Files\Steam\steamapps\common\insanely twisted shadow planet\FCEngine-GFWL.exe
    0000005c   -2
    0000005d    2
    00000052    2
    00000058    0
    00000059    0
    00000054    0
    00000018    0
    00000067    0 <==

```

---

### Post by Vector_Matt on 2012-05-03
Unfortunately I also was not able to get the game to work in wine.

I was able to get it running in virtualbox though, so if you have a spare copy of windows floating around you could try that. (Note the game tended to run at about 1/2 - 2/3 of full speed most of the time, but it did seem to work fine otherwise.)

(When I tried it, I was using Gentoo x86_64 and wine 1.5, ignore the OS listed under my name, it's completely inaccurate and I can't seem to change it.)

---

