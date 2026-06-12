---
title: "How to get Cinema 4D to work (A 3D Animation Tool)"
date: 2013-07-09
forum: Wine
---

### Post by GrassThatCowsEat on 2013-07-09
I Have never been able to get this to work and since this is the first on the forums it looks unlikely anyone else can get it to work
I have wine 1.6 and the latest OpenGL

When I try to open Cinema 4D.exe with wine it comes up with this very long message
Please help me!

-----------------------------------------------------------------------------------------------------------------------------------------------------

```
Unhandled exception: 0xc06d007e in 32-bit code (0x7b83bbd5).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7b83bbd5 ESP:0033f874 EBP:0033f8e8 EFLAGS:00000287(   - --  I S - -P-C)
 EAX:7b8267d5 EBX:7b8b4ff4 ECX:0033f918 EDX:0033f894
 ESI:00000001 EDI:c06d007e
Stack dump:
0x0033f874:  0033f910 00000004 0033f8a0 c06d007e
0x0033f884:  00000000 00000000 7b83bbd5 00000001
0x0033f894:  0033f918 0033f8c8 7b858f2d 7ffd8c00
0x0033f8a4:  00000000 00000000 0106232c 01f02a60
0x0033f8b4:  010b7758 0033f8e0 7b8b4ff4 00000038
0x0033f8c4:  010b7758 0033f8f8 7b858fa1 00000000
Backtrace:
=>0 0x7b83bbd5 in kernel32 (+0x2bbd5) (0x0033f8e8)
  1 0x0040142f in cinema 4d (+0x142e) (0x0033f958)
  2 0x00c40caf in cinema 4d (+0x840cae) (0x0033fd78)
  3 0x00c24614 in cinema 4d (+0x824613) (0x0033fe60)
  4 0x7b85f22c call_process_entry+0xb() in kernel32 (0x0033fe78)
  5 0x7b8604ab in kernel32 (+0x504aa) (0x0033feb8)
  6 0x7bc78e30 call_thread_func_wrapper+0xb() in ntdll (0x0033fed8)
  7 0x7bc7be3d call_thread_func+0x7c() in ntdll (0x0033ffa8)
  8 0x7bc78e0e RtlRaiseException+0x21() in ntdll (0x0033ffc8)
  9 0x7bc4e0ce call_dll_entry_point+0x33d() in ntdll (0x0033ffe8)
  10 0xf755166d wine_call_on_stack+0x1c() in libwine.so.1 (0x00000000)
  11 0xf755172b wine_switch_to_stack+0x2a() in libwine.so.1 (0xffc2a5b8)
  12 0x7bc53f30 LdrInitializeThunk+0x3af() in ntdll (0xffc2a628)
  13 0x7b866a62 __wine_kernel_init+0xa21() in kernel32 (0xffc2b7d8)
  14 0x7bc546eb __wine_process_init+0x25a() in ntdll (0xffc2b868)
  15 0xf754ebcc wine_init+0x2db() in libwine.so.1 (0xffc2b8d8)
  16 0x7bf00d0b main+0x8a() in <wine-loader> (0xffc2bd28)
  17 0xf73814d3 __libc_start_main+0xf2() in libc.so.6 (0x00000000)
0x7b83bbd5: movl    0xfffffff0(%ebp),%ecx
Modules:
Module    Address            Debug info    Name (116 modules)
PE      400000- 1ce2000    Export          cinema 4d
ELF    7b800000-7ba51000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba51000    \               kernel32
ELF    7bc00000-7bcd9000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcd9000    \               ntdll
ELF    7bf00000-7bf04000    Dwarf           <wine-loader>
ELF    7d1a4000-7d1a9000    Deferred        libgpg-error.so.0
ELF    7d1a9000-7d1c0000    Deferred        libresolv.so.2
ELF    7d1c0000-7d20a000    Deferred        libdbus-1.so.3
ELF    7d20a000-7d21e000    Deferred        libp11-kit.so.0
ELF    7d21e000-7d2a2000    Deferred        libgcrypt.so.11
ELF    7d2a2000-7d2b4000    Deferred        libtasn1.so.3
ELF    7d2b4000-7d2bd000    Deferred        libkrb5support.so.0
ELF    7d2bd000-7d2c2000    Deferred        libcom_err.so.2
ELF    7d2c2000-7d2ea000    Deferred        libk5crypto.so.3
ELF    7d2ea000-7d3b8000    Deferred        libkrb5.so.3
ELF    7d3b8000-7d3ca000    Deferred        libavahi-client.so.3
ELF    7d3ca000-7d3d8000    Deferred        libavahi-common.so.3
ELF    7d3d8000-7d49c000    Deferred        libgnutls.so.26
ELF    7d49c000-7d4d9000    Deferred        libgssapi_krb5.so.2
ELF    7d4d9000-7d538000    Deferred        libcups.so.2
ELF    7d538000-7d56e000    Deferred        uxtheme<elf>
  \-PE    7d540000-7d56e000    \               uxtheme
ELF    7d56e000-7d579000    Deferred        libxcursor.so.1
ELF    7d579000-7d589000    Deferred        libxi.so.6
ELF    7d589000-7d594000    Deferred        libxrandr.so.2
ELF    7d594000-7d59e000    Deferred        libxrender.so.1
ELF    7d59e000-7d5b8000    Deferred        libice.so.6
ELF    7d5b8000-7d5c1000    Deferred        libsm.so.6
ELF    7d5db000-7d66d000    Deferred        winex11<elf>
  \-PE    7d5f0000-7d66d000    \               winex11
ELF    7d7cc000-7d7f4000    Deferred        libexpat.so.1
ELF    7d7f4000-7d82c000    Deferred        libfontconfig.so.1
ELF    7d82c000-7d8c6000    Deferred        libfreetype.so.6
ELF    7d8c6000-7d8fc000    Deferred        ws2_32<elf>
  \-PE    7d8d0000-7d8fc000    \               ws2_32
ELF    7d8fc000-7d943000    Deferred        avifil32<elf>
  \-PE    7d900000-7d943000    \               avifil32
ELF    7d943000-7da7a000    Deferred        libx11.so.6
ELF    7da7a000-7da8c000    Deferred        libxext.so.6
ELF    7da8c000-7daa2000    Deferred        libglapi.so.0
ELF    7daa2000-7dac0000    Deferred        libgcc_s.so.1
ELF    7dbcd000-7dbd1000    Deferred        libkeyutils.so.1
ELF    7dbd1000-7dbd5000    Deferred        libxcomposite.so.1
ELF    7dbd5000-7dbd9000    Deferred        libxinerama.so.1
ELF    7dbd9000-7dbdf000    Deferred        libuuid.so.1
ELF    7dbe9000-7dbf0000    Deferred        libxdmcp.so.6
ELF    7dbf0000-7dbf4000    Deferred        libxau.so.6
ELF    7dbf4000-7dc01000    Deferred        libdrm.so.2
ELF    7dc01000-7dc07000    Deferred        libxxf86vm.so.1
ELF    7dc07000-7dc29000    Deferred        libxcb.so.1
ELF    7dc29000-7dc41000    Deferred        libxcb-glx.so.0
ELF    7dc41000-7dc48000    Deferred        libxfixes.so.3
ELF    7dc48000-7dca6000    Deferred        libgl.so.1
ELF    7dca6000-7dd2d000    Deferred        libglu.so.1
ELF    7dd47000-7dd6d000    Deferred        iphlpapi<elf>
  \-PE    7dd50000-7dd6d000    \               iphlpapi
ELF    7dd6d000-7ddad000    Deferred        winspool<elf>
  \-PE    7dd70000-7ddad000    \               winspool
ELF    7ddad000-7dfde000    Deferred        shell32<elf>
  \-PE    7ddc0000-7dfde000    \               shell32
ELF    7dfde000-7e0c9000    Deferred        comdlg32<elf>
  \-PE    7dfe0000-7e0c9000    \               comdlg32
ELF    7e0c9000-7e139000    Deferred        setupapi<elf>
  \-PE    7e0d0000-7e139000    \               setupapi
ELF    7e139000-7e247000    Deferred        opengl32<elf>
  \-PE    7e150000-7e247000    \               opengl32
ELF    7e247000-7e34f000    Deferred        comctl32<elf>
  \-PE    7e250000-7e34f000    \               comctl32
ELF    7e34f000-7e37b000    Deferred        msvfw32<elf>
  \-PE    7e350000-7e37b000    \               msvfw32
ELF    7e37b000-7e3a6000    Deferred        msacm32<elf>
  \-PE    7e380000-7e3a6000    \               msacm32
ELF    7e3a6000-7e45c000    Deferred        winmm<elf>
  \-PE    7e3b0000-7e45c000    \               winmm
ELF    7e45c000-7e4dd000    Deferred        rpcrt4<elf>
  \-PE    7e470000-7e4dd000    \               rpcrt4
ELF    7e4dd000-7e619000    Deferred        ole32<elf>
  \-PE    7e4f0000-7e619000    \               ole32
ELF    7e619000-7e74d000    Deferred        oleaut32<elf>
  \-PE    7e630000-7e74d000    \               oleaut32
ELF    7e74d000-7e7bc000    Deferred        advapi32<elf>
  \-PE    7e760000-7e7bc000    \               advapi32
ELF    7e7bc000-7e8d9000    Deferred        gdi32<elf>
  \-PE    7e7d0000-7e8d9000    \               gdi32
ELF    7e8d9000-7ea34000    Deferred        user32<elf>
  \-PE    7e8f0000-7ea34000    \               user32
ELF    7ea34000-7eaae000    Deferred        shlwapi<elf>
  \-PE    7ea40000-7eaae000    \               shlwapi
ELF    7eaae000-7eb3a000    Deferred        gdiplus<elf>
  \-PE    7eac0000-7eb3a000    \               gdiplus
ELF    7eb3a000-7eb4e000    Deferred        psapi<elf>
  \-PE    7eb40000-7eb4e000    \               psapi
ELF    7eb4e000-7eb67000    Deferred        libz.so.1
ELF    7eb69000-7eb81000    Deferred        glu32<elf>
  \-PE    7eb70000-7eb81000    \               glu32
ELF    7eb81000-7ebe9000    Deferred        dbghelp<elf>
  \-PE    7eb90000-7ebe9000    \               dbghelp
ELF    7ebe9000-7ec03000    Deferred        imagehlp<elf>
  \-PE    7ebf0000-7ec03000    \               imagehlp
ELF    7ec03000-7ec1d000    Deferred        libnsl.so.1
ELF    7ec1d000-7ec26000    Deferred        libnss_compat.so.2
ELF    7ec26000-7ec40000    Deferred        version<elf>
  \-PE    7ec30000-7ec40000    \               version
ELF    7efb1000-7efdd000    Deferred        libm.so.6
ELF    7efdd000-7efe6000    Deferred        librt.so.1
ELF    7efe7000-7eff4000    Deferred        libnss_files.so.2
ELF    7eff4000-7f000000    Deferred        libnss_nis.so.2
ELF    f7363000-f7368000    Deferred        libdl.so.2
ELF    f7368000-f7512000    Dwarf           libc.so.6
ELF    f7513000-f752e000    Deferred        libpthread.so.0
ELF    f7541000-f7544000    Deferred        libx11-xcb.so.1
ELF    f7544000-f7548000    Deferred        libxdamage.so.1
ELF    f7548000-f76fe000    Dwarf           libwine.so.1
ELF    f7700000-f7722000    Deferred        ld-linux.so.2
ELF    f7722000-f7723000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000c winemenubuilder.exe
    0000000d    0
0000000e services.exe
    0000001e    0
    0000001d    0
    00000018    0
    00000016    0
    00000014    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001c    0
    00000019    0
    00000017    0
    00000013    0
0000001a plugplay.exe
    00000020    0
    0000001f    0
    0000001b    0
00000021 explorer.exe
    00000023    0
    00000022    0
00000024 (D) E:\media\nathan\BACKUPS\C4D\MAXON\Cinema 4D R13\CINEMA 4D.exe
    00000025    0 <==
0000002b CINEMA 4D.exe
    0000002c    0
0000002d winedbg.exe
    0000002e    0
System information:
    Wine build: wine-1.6-rc4
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 3.5.0-34-generic
```

---

### Post by Grafens on 2013-07-09
I don't use cinema4d myself but a few things may help.
What video card are you using usually these types of programs require highend GTX or quadro like cards.
Have to tried configuring wine to use windows7 or XP  in the settings.
Under your specks it says 'Platform: i386 (WOW64)' your OS is 64bit right? If it is 64bit you can use either 64bit or 32bit programs on it.
Over on winehq a couple of people have got C4D r14 running with wine 1.5.30 maybe you'll have better luck with that wine version [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1418](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1418)

Best of luck

---

### Post by GrassThatCowsEat on 2013-07-11
I have an Intel HD Graphics 2000 chip and have been able to successfully run Cinema 4D before. I have not tried to configure wine as I do not know how or even the right settings to do so. My OS is 64 bit. I will check the link you have given me.

---

### Post by GrassThatCowsEat on 2013-07-11
When I click the link I am unsure of what to do next.

---

### Post by oldos2er on 2013-07-11
Moved to Wine.

---

