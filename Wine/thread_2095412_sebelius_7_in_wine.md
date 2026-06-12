---
title: "sebelius 7 in wine"
date: 2012-12-16
forum: Wine
---

### Post by icyisaac100 on 2012-12-16
When I installed sebelius 7, there were no hitches, but when I ran it it came up with a message box with - "A serious error occured" and there was a error text file. Anyone now how to fix this ?

```
Unhandled exception: unimplemented function KERNEL32.dll.InitializeConditionVariable called in 64-bit code (0x00007f3a1b948a9a).
Register dump:
 rip:00007f3a1b948a9a rsp:00000000002397a0 rbp:0000000000000004 eflags:00000206 (   - --  I   - -P- )
 rax:00007f3a1b948a50 rbx:0000000000a9e828 rcx:00000000002397c0 rdx:00000000014e4ab2
 rsi:0000000002368b1a rdi:000000000236930e  r8:0000000000000008  r9:0000000000239610 r10:0000000000000000
 r11:00000000002395e0 r12:0000000000a73720 r13:0000000000000003 r14:0000000000000000 r15:00000001417b62d0
Stack dump:
0x00000000002397a0:  00000000002397c0 ffff00ffffff0000
0x00000000002397b0:  0000000000000000 0020202000202000
0x00000000002397c0:  0000000180000100 0000000000000000
0x00000000002397d0:  00007f3a1b948a9a 0000000000000002
0x00000000002397e0:  000000000236930e 0000000002368b1a
0x00000000002397f0:  0000000000000000 0000000000000000
0x0000000000239800:  0000000000000000 0000000000000000
0x0000000000239810:  0000000000a9e828 0000000000000000
0x0000000000239820:  0000000000000000 0000000000000004
0x0000000000239830:  0000000000a73720 000000007b888dda
0x0000000000239840:  0000000000000000 0000000000a9e828
0x0000000000239850:  0000000000000000 0000000000000000
Backtrace:
=>0 0x00007f3a1b948a9a in ntdll (+0x38a9a) (0x0000000000000004)
  1 0x00000000014e4ab2 in plogueengine_x64 (+0x24ab1) (0x0000000000000004)
  2 0x00000000014ca1d8 in plogueengine_x64 (+0xa1d7) (0x0000000000000004)
  3 0x00000000014ca984 in plogueengine_x64 (+0xa983) (0x0000000000000004)
  4 0x00000000015575c1 in plogueengine_x64 (+0x975c0) (0x0000000000000004)
  5 0x0000000001558631 in plogueengine_x64 (+0x98630) (0x0000000000000004)
  6 0x00000000014d10d0 in plogueengine_x64 (+0x110cf) (0x0000000000a676d0)
0x00007f3a1b948a9a: jmp    0x00007f3a1b948a90
Modules:
Module    Address                    Debug info    Name (159 modules)
PE              250000-          2a7000    Deferred        phonon4
PE              2b0000-          2d1000    Deferred        qttest4
PE              2e0000-          674000    Deferred        qtxmlpatterns4
PE              680000-          68d000    Deferred        qgif4
PE              690000-          69b000    Deferred        qsvg4
PE              b50000-          de5000    Deferred        sarilib
PE              df0000-          e2f000    Deferred        qjpeg4
PE              e30000-          e83000    Deferred        qtiff4
PE             14c0000-         24d5000    Export          plogueengine_x64
PE             24e0000-         2519000    Deferred        portaudio_x64
PE            61000000-        61073000    Deferred        qtxml4
PE            64000000-        64111000    Deferred        qtnetwork4
PE            65000000-        65a05000    Deferred        qtgui4
PE            66000000-        6605a000    Deferred        qtsvg4
PE            67000000-        672c2000    Deferred        qtcore4
ELF            7b800000-        7bc5e000    Deferred        kernel32<elf>
  \-PE            7b820000-        7bc5e000    \               kernel32
ELF            7be00000-        7c103000    Deferred        <wine-loader>
PE           140000000-       142fb8000    Deferred        sibelius
PE           180000000-       180e08000    Deferred        qtwebkit4
ELF        7f3a0d101000-    7f3a0d36b000    Deferred        dbghelp<elf>
  \-PE        7f3a0d110000-    7f3a0d36b000    \               dbghelp
ELF        7f3a0d36b000-    7f3a0d57f000    Deferred        avrt<elf>
  \-PE        7f3a0d370000-    7f3a0d57f000    \               avrt
ELF        7f3a0d57f000-    7f3a0d7d0000    Deferred        dsound<elf>
  \-PE        7f3a0d590000-    7f3a0d7d0000    \               dsound
ELF        7f3a0d7d0000-    7f3a0d9ed000    Deferred        wsock32<elf>
  \-PE        7f3a0d7e0000-    7f3a0d9ed000    \               wsock32
ELF        7f3a0d9ed000-    7f3a0dc02000    Deferred        midimap<elf>
  \-PE        7f3a0d9f0000-    7f3a0dc02000    \               midimap
ELF        7f3a0dc02000-    7f3a0de1a000    Deferred        msacm32<elf>
  \-PE        7f3a0dc10000-    7f3a0de1a000    \               msacm32
ELF        7f3a0de1a000-    7f3a0e104000    Deferred        libasound.so.2
ELF        7f3a0e104000-    7f3a0e338000    Deferred        winealsa<elf>
  \-PE        7f3a0e110000-    7f3a0e338000    \               winealsa
ELF        7f3a0e338000-    7f3a0e53f000    Deferred        libogg.so.0
ELF        7f3a0e53f000-    7f3a0e76c000    Deferred        libvorbis.so.0
ELF        7f3a0e76c000-    7f3a0ec3b000    Deferred        libvorbisenc.so.2
ELF        7f3a0ec3b000-    7f3a0ee87000    Deferred        libflac.so.8
ELF        7f3a0ee87000-    7f3a0f08d000    Deferred        libasyncns.so.0
ELF        7f3a0f08d000-    7f3a0f2f3000    Deferred        libsndfile.so.1
ELF        7f3a0f2f3000-    7f3a0f4fd000    Deferred        libwrap.so.0
ELF        7f3a0f4fd000-    7f3a0f75a000    Deferred        libpulsecommon-2.1.so
ELF        7f3a0f75a000-    7f3a0f963000    Deferred        libjson.so.0
ELF        7f3a0f963000-    7f3a0fbab000    Deferred        libpulse.so.0
ELF        7f3a0fbc4000-    7f3a0fdef000    Deferred        winepulse<elf>
  \-PE        7f3a0fbd0000-    7f3a0fdef000    \               winepulse
ELF        7f3a0fdef000-    7f3a10013000    Deferred        mmdevapi<elf>
  \-PE        7f3a0fe00000-    7f3a10013000    \               mmdevapi
ELF        7f3a105bf000-    7f3a107e0000    Deferred        wintab32<elf>
  \-PE        7f3a105d0000-    7f3a107e0000    \               wintab32
ELF        7f3a1094c000-    7f3a10b60000    Deferred        gnome-keyring-pkcs11.so
ELF        7f3a10b60000-    7f3a10d68000    Deferred        librt.so.1
ELF        7f3a10d68000-    7f3a10f6c000    Deferred        libgpg-error.so.0
ELF        7f3a10f6c000-    7f3a11188000    Deferred        libresolv.so.2
ELF        7f3a11188000-    7f3a1138c000    Deferred        libkeyutils.so.1
ELF        7f3a1138c000-    7f3a115d0000    Deferred        libdbus-1.so.3
ELF        7f3a115d0000-    7f3a117e4000    Deferred        libp11-kit.so.0
ELF        7f3a117e4000-    7f3a11a62000    Deferred        libgcrypt.so.11
ELF        7f3a11a62000-    7f3a11c73000    Deferred        libtasn1.so.3
ELF        7f3a11c73000-    7f3a11e7b000    Deferred        libkrb5support.so.0
ELF        7f3a11e7b000-    7f3a1207f000    Deferred        libcom_err.so.2
ELF        7f3a1207f000-    7f3a122a8000    Deferred        libk5crypto.so.3
ELF        7f3a122a8000-    7f3a12576000    Deferred        libkrb5.so.3
ELF        7f3a12576000-    7f3a12787000    Deferred        libavahi-client.so.3
ELF        7f3a12787000-    7f3a12993000    Deferred        libavahi-common.so.3
ELF        7f3a12993000-    7f3a12c4f000    Deferred        libgnutls.so.26
ELF        7f3a12c4f000-    7f3a12e8d000    Deferred        libgssapi_krb5.so.2
ELF        7f3a12e8d000-    7f3a130ed000    Deferred        libcups.so.2
ELF        7f3a130ed000-    7f3a132f3000    Deferred        libxfixes.so.3
ELF        7f3a132f3000-    7f3a134fe000    Deferred        libxcursor.so.1
ELF        7f3a134fe000-    7f3a1370d000    Deferred        libxi.so.6
ELF        7f3a1370d000-    7f3a13910000    Deferred        libxcomposite.so.1
ELF        7f3a13910000-    7f3a13b1a000    Deferred        libxrandr.so.2
ELF        7f3a13b1a000-    7f3a13d24000    Deferred        libxrender.so.1
ELF        7f3a13d24000-    7f3a13f2a000    Deferred        libxxf86vm.so.1
ELF        7f3a13f2a000-    7f3a1412d000    Deferred        libxinerama.so.1
ELF        7f3a1412d000-    7f3a14333000    Deferred        libxdmcp.so.6
ELF        7f3a14333000-    7f3a14537000    Deferred        libxau.so.6
ELF        7f3a14537000-    7f3a14755000    Deferred        libxcb.so.1
ELF        7f3a14755000-    7f3a1495a000    Deferred        libuuid.so.1
ELF        7f3a1495a000-    7f3a14b76000    Deferred        libice.so.6
ELF        7f3a14b76000-    7f3a14eb0000    Deferred        libx11.so.6
ELF        7f3a14eb0000-    7f3a150c2000    Deferred        libxext.so.6
ELF        7f3a150c2000-    7f3a152ca000    Deferred        libsm.so.6
ELF        7f3a152ca000-    7f3a15563000    Deferred        winex11<elf>
  \-PE        7f3a152e0000-    7f3a15563000    \               winex11
ELF        7f3a15563000-    7f3a157ff000    Deferred        libfreetype.so.6
ELF        7f3a157ff000-    7f3a15a12000    Deferred        psapi<elf>
  \-PE        7f3a15800000-    7f3a15a12000    \               psapi
ELF        7f3a15a12000-    7f3a15c3b000    Deferred        iphlpapi<elf>
  \-PE        7f3a15a20000-    7f3a15c3b000    \               iphlpapi
ELF        7f3a15c3b000-    7f3a15e6c000    Deferred        netapi32<elf>
  \-PE        7f3a15c40000-    7f3a15e6c000    \               netapi32
ELF        7f3a15e6c000-    7f3a1609b000    Deferred        credui<elf>
  \-PE        7f3a15e70000-    7f3a1609b000    \               credui
ELF        7f3a1609b000-    7f3a162c6000    Deferred        mpr<elf>
  \-PE        7f3a160a0000-    7f3a162c6000    \               mpr
ELF        7f3a162c6000-    7f3a164dd000    Deferred        libz.so.1
ELF        7f3a164f6000-    7f3a1677a000    Deferred        wininet<elf>
  \-PE        7f3a16500000-    7f3a1677a000    \               wininet
ELF        7f3a1677a000-    7f3a169b3000    Deferred        uxtheme<elf>
  \-PE        7f3a16780000-    7f3a169b3000    \               uxtheme
ELF        7f3a169b3000-    7f3a16bdf000    Deferred        msacm32<elf>
  \-PE        7f3a169c0000-    7f3a16bdf000    \               msacm32
ELF        7f3a16bdf000-    7f3a16e9b000    Deferred        winmm<elf>
  \-PE        7f3a16bf0000-    7f3a16e9b000    \               winmm
ELF        7f3a16e9b000-    7f3a170e0000    Deferred        winspool<elf>
  \-PE        7f3a16ea0000-    7f3a170e0000    \               winspool
ELF        7f3a170e0000-    7f3a173e1000    Deferred        comctl32<elf>
  \-PE        7f3a170f0000-    7f3a173e1000    \               comctl32
ELF        7f3a173e1000-    7f3a17844000    Deferred        shell32<elf>
  \-PE        7f3a17400000-    7f3a17844000    \               shell32
ELF        7f3a17844000-    7f3a17b2f000    Deferred        comdlg32<elf>
  \-PE        7f3a17850000-    7f3a17b2f000    \               comdlg32
ELF        7f3a17b2f000-    7f3a17d56000    Deferred        imm32<elf>
  \-PE        7f3a17b40000-    7f3a17d56000    \               imm32
ELF        7f3a17d56000-    7f3a17f93000    Deferred        msvcr100<elf>
  \-PE        7f3a17d60000-    7f3a17f93000    \               msvcr100
ELF        7f3a17f93000-    7f3a181c5000    Deferred        msvcr90<elf>
  \-PE        7f3a17fa0000-    7f3a181c5000    \               msvcr90
ELF        7f3a181c5000-    7f3a18481000    Deferred        msvcrt<elf>
  \-PE        7f3a181e0000-    7f3a18481000    \               msvcrt
ELF        7f3a18481000-    7f3a18801000    Deferred        msvcp90<elf>
  \-PE        7f3a184c0000-    7f3a18801000    \               msvcp90
ELF        7f3a18801000-    7f3a18a3c000    Deferred        ws2_32<elf>
  \-PE        7f3a18810000-    7f3a18a3c000    \               ws2_32
ELF        7f3a18a3c000-    7f3a18cd1000    Deferred        rpcrt4<elf>
  \-PE        7f3a18a50000-    7f3a18cd1000    \               rpcrt4
ELF        7f3a18cd1000-    7f3a19057000    Deferred        ole32<elf>
  \-PE        7f3a18d00000-    7f3a19057000    \               ole32
ELF        7f3a19057000-    7f3a193db000    Deferred        oleaut32<elf>
  \-PE        7f3a19080000-    7f3a193db000    \               oleaut32
ELF        7f3a193db000-    7f3a195f4000    Deferred        version<elf>
  \-PE        7f3a193e0000-    7f3a195f4000    \               version
ELF        7f3a195f4000-    7f3a19877000    Deferred        advapi32<elf>
  \-PE        7f3a19600000-    7f3a19877000    \               advapi32
ELF        7f3a19877000-    7f3a19bd9000    Deferred        gdi32<elf>
  \-PE        7f3a19890000-    7f3a19bd9000    \               gdi32
ELF        7f3a19bd9000-    7f3a19f7b000    Deferred        user32<elf>
  \-PE        7f3a19c00000-    7f3a19f7b000    \               user32
ELF        7f3a19f7b000-    7f3a1a20e000    Deferred        shlwapi<elf>
  \-PE        7f3a19f90000-    7f3a1a20e000    \               shlwapi
ELF        7f3a1a20e000-    7f3a1a4c2000    Deferred        gdiplus<elf>
  \-PE        7f3a1a220000-    7f3a1a4c2000    \               gdiplus
ELF        7f3a1a4c2000-    7f3a1a6cf000    Deferred        libnss_files.so.2
ELF        7f3a1a6cf000-    7f3a1a8db000    Deferred        libnss_nis.so.2
ELF        7f3a1a8db000-    7f3a1aaf5000    Deferred        libnsl.so.1
ELF        7f3a1aaf5000-    7f3a1acfe000    Deferred        libnss_compat.so.2
ELF        7f3a1b3df000-    7f3a1b5f5000    Deferred        libgcc_s.so.1
ELF        7f3a1b5f5000-    7f3a1b8f1000    Deferred        libm.so.6
ELF        7f3a1b8f1000-    7f3a1bbe5000    Dwarf           ntdll<elf>
  \-PE        7f3a1b910000-    7f3a1bbe5000    \               ntdll
ELF        7f3a1bbe8000-    7f3a1bdec000    Deferred        libdl.so.2
ELF        7f3a1bdec000-    7f3a1c1ab000    Deferred        libc.so.6
ELF        7f3a1c1ac000-    7f3a1c3c9000    Deferred        libpthread.so.0
ELF        7f3a1c3e2000-    7f3a1c713000    Dwarf           libwine.so.1
ELF        7f3a1c715000-    7f3a1c93a000    Deferred        ld-linux-x86-64.so.2
ELF        7fff60fff000-    7fff61000000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    00000020    0
    0000001f    0
    00000019    0
    00000018    0
    00000017    0
    00000015    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001d    0
    0000001a    0
    00000014    0
    00000013    0
0000001b plugplay.exe
    00000021    0
    0000001e    0
    0000001c    0
00000022 explorer.exe
    00000023    0
00000024 (D) C:\Program Files\Avid\Sibelius 7\Sibelius.exe
    00000029    0
    00000028    0
    00000027    0
    00000026   15
    00000025    0 <==
System information:
    Wine build: wine-1.5.19
    Platform: x86_64
    Host system: Linux
    Host version: 3.5.0-19-generic
```

---

