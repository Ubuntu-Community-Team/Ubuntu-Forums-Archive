---
title: "Problem with Uplay"
date: 2016-02-03
forum: Wine
---

### Post by julia6 on 2016-02-03
I can't install the Uplay software, which is needed to play Ubisoft games. I tried install it with PlayOnLinux, but it crash after trying to open. After "debug" option, I have this message: ```
 __clone+0x5d() in libc.so.6 (0x00000000)
  161 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  162 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  163 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  164 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  165 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  166 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  167 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  168 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  169 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  170 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  171 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  172 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  173 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  174 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  175 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  176 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  177 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  178 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  179 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  180 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  181 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  182 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  183 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  184 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  185 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  186 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  187 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  188 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  189 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  190 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  191 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  192 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  193 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  194 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  195 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  196 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  197 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  198 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  199 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
  200 0xf74f1fde __clone+0x5d() in libc.so.6 (0x00000000)
0x0087a4f2: movl    %eax,0x0(%eax)
Modules:
Module    Address            Debug info    Name (128 modules)
PE      230000-  35d000    Deferred        libeay32
PE      360000-  3ae000    Deferred        ssleay32
PE      400000- 5537000    Export          uplay
PE    10000000-11816000    Deferred        libcef
PE    4ad00000-4b681000    Deferred        icudt
ELF    7b800000-7ba55000    Deferred        kernel32<elf>
  \-PE    7b810000-7ba55000    \               kernel32
ELF    7bc00000-7bcd9000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcd9000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7c599000-7c5db000    Deferred        rsaenh<elf>
  \-PE    7c5a0000-7c5db000    \               rsaenh
ELF    7cf09000-7cf10000    Deferred        libnss_dns.so.2
ELF    7cf10000-7cf82000    Deferred        d3dcompiler_43<elf>
  \-PE    7cf20000-7cf82000    \               d3dcompiler_43
ELF    7cfc8000-7cfdd000    Deferred        libgpg-error.so.0
ELF    7cfdd000-7cffb000    Deferred        libgcc_s.so.1
ELF    7cffb000-7d0ac000    Deferred        libgcrypt.so.20
ELF    7d0ac000-7d0d2000    Deferred        liblzma.so.5
ELF    7d0d2000-7d0db000    Deferred        librt.so.1
ELF    7d0db000-7d167000    Deferred        libsystemd.so.0
ELF    7d167000-7d171000    Deferred        libffi.so.6
ELF    7d171000-7d18a000    Deferred        libresolv.so.2
ELF    7d18a000-7d1e4000    Deferred        libdbus-1.so.3
ELF    7d1e4000-7d270000    Deferred        libgmp.so.10
ELF    7d270000-7d2a4000    Deferred        libhogweed.so.4
ELF    7d2a4000-7d2e0000    Deferred        libnettle.so.6
ELF    7d2e0000-7d2f4000    Deferred        libtasn1.so.6
ELF    7d2f4000-7d358000    Deferred        libp11-kit.so.0
ELF    7d358000-7d365000    Deferred        libkrb5support.so.0
ELF    7d365000-7d397000    Deferred        libk5crypto.so.3
ELF    7d397000-7d46e000    Deferred        libkrb5.so.3
ELF    7d46e000-7d482000    Deferred        libavahi-client.so.3
ELF    7d482000-7d5c5000    Deferred        libgnutls-deb0.so.28
ELF    7d5c5000-7d615000    Deferred        libgssapi_krb5.so.2
ELF    7d615000-7d69c000    Deferred        libcups.so.2
ELF    7d6a2000-7d6bc000    Deferred        d3dx9_43<elf>
  \-PE    7d6b0000-7d6bc000    \               d3dx9_43
ELF    7d6bc000-7d6f2000    Deferred        uxtheme<elf>
  \-PE    7d6c0000-7d6f2000    \               uxtheme
ELF    7d6f2000-7d6f9000    Deferred        libxfixes.so.3
ELF    7d6f9000-7d704000    Deferred        libxcursor.so.1
ELF    7d704000-7d716000    Deferred        libxi.so.6
ELF    7d716000-7d71a000    Deferred        libxcomposite.so.1
ELF    7d71a000-7d727000    Deferred        libxrandr.so.2
ELF    7d727000-7d733000    Deferred        libxrender.so.1
ELF    7d733000-7d73a000    Deferred        libxxf86vm.so.1
ELF    7d73a000-7d73e000    Deferred        libxinerama.so.1
ELF    7d73e000-7d745000    Deferred        libxdmcp.so.6
ELF    7d745000-7d749000    Deferred        libxau.so.6
ELF    7d749000-7d76e000    Deferred        libxcb.so.1
ELF    7d76e000-7d8b9000    Deferred        libx11.so.6
ELF    7d8b9000-7d8ce000    Deferred        libxext.so.6
ELF    7d8d4000-7d8d9000    Deferred        libkeyutils.so.1
ELF    7d8d9000-7d8de000    Deferred        libcom_err.so.2
ELF    7d8de000-7d8ec000    Deferred        libavahi-common.so.3
ELF    7d8ee000-7d97b000    Deferred        winex11<elf>
  \-PE    7d900000-7d97b000    \               winex11
ELF    7daee000-7db17000    Deferred        libexpat.so.1
ELF    7db17000-7db5a000    Deferred        libfontconfig.so.1
ELF    7db5a000-7db86000    Deferred        libpng12.so.0
ELF    7db86000-7dc33000    Deferred        libfreetype.so.6
ELF    7dc53000-7dcdd000    Deferred        gdiplus<elf>
  \-PE    7dc60000-7dcdd000    \               gdiplus
ELF    7dcdd000-7dd1e000    Deferred        usp10<elf>
  \-PE    7dce0000-7dd1e000    \               usp10
ELF    7dd1e000-7dde9000    Deferred        crypt32<elf>
  \-PE    7dd30000-7dde9000    \               crypt32
ELF    7dde9000-7de15000    Deferred        netapi32<elf>
  \-PE    7ddf0000-7de15000    \               netapi32
ELF    7de15000-7de3f000    Deferred        secur32<elf>
  \-PE    7de20000-7de3f000    \               secur32
ELF    7de3f000-7de66000    Deferred        mpr<elf>
  \-PE    7de50000-7de66000    \               mpr
ELF    7de66000-7de81000    Deferred        libz.so.1
ELF    7de81000-7def8000    Deferred        wininet<elf>
  \-PE    7de90000-7def8000    \               wininet
ELF    7def8000-7e023000    Deferred        oleaut32<elf>
  \-PE    7df10000-7e023000    \               oleaut32
ELF    7e023000-7e0be000    Deferred        urlmon<elf>
  \-PE    7e030000-7e0be000    \               urlmon
ELF    7e0be000-7e1a3000    Deferred        comdlg32<elf>
  \-PE    7e0c0000-7e1a3000    \               comdlg32
ELF    7e1c7000-7e1eb000    Deferred        imm32<elf>
  \-PE    7e1d0000-7e1eb000    \               imm32
ELF    7e1eb000-7e210000    Deferred        iphlpapi<elf>
  \-PE    7e1f0000-7e210000    \               iphlpapi
ELF    7e210000-7e24c000    Deferred        winspool<elf>
  \-PE    7e220000-7e24c000    \               winspool
ELF    7e24c000-7e276000    Deferred        msacm32<elf>
  \-PE    7e250000-7e276000    \               msacm32
ELF    7e276000-7e2f2000    Deferred        rpcrt4<elf>
  \-PE    7e280000-7e2f2000    \               rpcrt4
ELF    7e2f2000-7e41f000    Deferred        ole32<elf>
  \-PE    7e310000-7e41f000    \               ole32
ELF    7e41f000-7e4d7000    Deferred        winmm<elf>
  \-PE    7e430000-7e4d7000    \               winmm
ELF    7e4d7000-7e4eb000    Deferred        psapi<elf>
  \-PE    7e4e0000-7e4eb000    \               psapi
ELF    7e4eb000-7e520000    Deferred        ws2_32<elf>
  \-PE    7e4f0000-7e520000    \               ws2_32
ELF    7e520000-7e55b000    Deferred        winhttp<elf>
  \-PE    7e530000-7e55b000    \               winhttp
ELF    7e580000-7e678000    Deferred        comctl32<elf>
  \-PE    7e590000-7e678000    \               comctl32
ELF    7e678000-7e6ee000    Deferred        shlwapi<elf>
  \-PE    7e690000-7e6ee000    \               shlwapi
ELF    7e6ee000-7e917000    Deferred        shell32<elf>
  \-PE    7e700000-7e917000    \               shell32
ELF    7e917000-7e985000    Deferred        advapi32<elf>
  \-PE    7e920000-7e985000    \               advapi32
ELF    7e985000-7ea9d000    Deferred        gdi32<elf>
  \-PE    7e990000-7ea9d000    \               gdi32
ELF    7ea9d000-7ebeb000    Deferred        user32<elf>
  \-PE    7eab0000-7ebeb000    \               user32
ELF    7ef5d000-7ef6b000    Deferred        libnss_files.so.2
ELF    7ef6b000-7ef78000    Deferred        libnss_nis.so.2
ELF    7ef78000-7ef93000    Deferred        libnsl.so.1
ELF    7ef93000-7efe0000    Deferred        libm.so.6
ELF    7efe7000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    f7403000-f7408000    Deferred        libdl.so.2
ELF    f7408000-f75c3000    Dwarf           libc.so.6
ELF    f75c4000-f75e1000    Dwarf           libpthread.so.0
ELF    f75e6000-f75f0000    Deferred        libnss_compat.so.2
ELF    f7601000-f77b7000    Dwarf           libwine.so.1
ELF    f77b9000-f77dd000    Deferred        ld-linux.so.2
ELF    f77df000-f77e0000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Ubisoft\Ubisoft Game Launcher\Uplay.exe
    0000004e    0
    0000004c    0
    0000004b    0
    0000004a    0
    00000049    0
    00000048    0
    00000022    0
    00000023    0
    0000000b    0
    0000000d    0
    0000000c    0
    00000047    0
    00000046    0
    00000045    0
    00000044    0
    00000043    0
    0000003b    0
    0000003a    0
    00000039    0
    00000038    0
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
    0000002c    0 <==
    0000002b    0
    0000002a    0
    00000029    0
    00000028    0
    00000009    0
0000000e services.exe
    0000001f    0
    0000001e    0
    00000019    0
    00000018    0
    00000016    0
    00000014    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001d    0
    0000001a    0
    00000017    0
    00000013    0
0000001b plugplay.exe
    00000021    0
    00000020    0
    0000001c    0
0000003c explorer.exe
    00000042    0
    0000003d    0
[02/03/16 17:30:18] - Running wine- Uplay.exe (Working directory : /home/julia/.PlayOnLinux/wineprefix/Uplay/drive_c/Program Files/Ubisoft/Ubisoft Game Launcher)
err:secur32:SECUR32_initSchannelSP TLS library not found, SSL connections will fail
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:GetExplicitEntriesFromAclW 0x139034 0x121fc98 0x121fcac
fixme:winsock:WSAEnumNameSpaceProvidersA (0x5eba258 0x5ecdf9c) Stub!
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:winsock:WSALookupServiceBeginW (0x147ee64c 0x00000ff0 0x147ee694) Stub!
[0203/173020:ERROR:network_change_notifier_win.cc(160)] WSALookupServiceBegin failed with: 8
fixme:iphlpapi:NotifyAddrChange (Handle 0x147ee524, overlapped 0x64b6dc8): stub
fixme:winsock:WSALookupServiceBeginW (0x147ee68c 0x00000ff0 0x147ee6d4) Stub!
[0203/173020:ERROR:network_change_notifier_win.cc(160)] WSALookupServiceBegin failed with: 8
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
wine: Unhandled page fault on write access to 0x00000000 at address 0x87a4f2 (thread 002b), starting debugger...
Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x0087a4f2).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:0087a4f2 ESP:0998d524 EBP:0998d5d8 EFLAGS:00210246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:00000000 ECX:fbe08a2b EDX:00000000
 ESI:151af160 EDI:151ae138
Stack dump:
0x0998d524:  00e5511d fbe08ad3 00000000 1519f550
0x0998d534:  00000004 00000000 00000000 00000000
0x0998d544:  00000000 00000000 00000000 00000000
0x0998d554:  000000c0 00000000 00000000 00000000
0x0998d564:  00000018 00000000 4d430003 00000000
0x0998d574:  151af160 151ae138 00000000 00000000
000c: sel=0067 base=00000000 limit=00000000 32-bit r-x
Backtrace:
=>0 0x0087a4f2 in uplay (+0x47a4f2) (0x0998d5d8)
  1 0x00e554cf in uplay (+0xa554ce) (0x0998d654)
  2 0x00e5937d in uplay (+0xa5937c) (0x0998d6f4)
  3 0x00e4ab91 in uplay (+0xa4ab90) (0x0998d75c)
  4 0x00e4b947 in uplay (+0xa4b946) (0x0998ded0)
  5 0x00e4c8c1 in uplay (+0xa4c8c0) (0x0998dff8)
  6 0x009f96fa in uplay (+0x5f96f9) (0x0998e200)
  7 0x02f46390 in uplay (+0x2b4638f) (0x0998e480)
  8 0x009fb21d in uplay (+0x5fb21c) (0x0998e53c)
  9 0x009fb40f in uplay (+0x5fb40e) (0x0998e5c0)
  10 0x009e0417 in uplay (+0x5e0416) (0x0998e794)
  11 0x00fbc659 in uplay (+0xbbc658) (0x0998e89c)
  12 0x00f9c136 in uplay (+0xb9c135) (0x0998e92c)
  13 0x00f87afa in uplay (+0xb87af9) (0x0998e95c)
  14 0x008831b3 in uplay (+0x4831b2) (0x0998e980)
  15 0x00881e3a in uplay (+0x481e39) (0x0998e998)
  16 0x0089fb4c in uplay (+0x49fb4b) (0x0998e9b8)
  17 0x00ded928 in uplay (+0x9ed927) (0x0998e9f0)
  18 0x00ded9a6 in uplay (+0x9ed9a5) (0x0998e9f8)
  19 0x7bc74e90 call_thread_func_wrapper+0xb() in ntdll (0x0998ea08)
  20 0x7bc77c2f call_thread_func+0xce() in ntdll (0x0998eaf8)
  21 0x7bc74e6e RtlRaiseException+0x21() in ntdll (0x0998eb18)
  22 0x7bc7dedf in ntdll (+0x6dede) (0x0998f368)
  23 0xf75931aa start_thread+0xd9() in libpthread.so.0 (0x0998f428)
  24 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  25 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  26 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  27 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  28 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  29 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  30 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  31 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  32 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  33 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  34 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  35 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  36 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  37 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  38 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  39 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  40 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  41 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  42 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  43 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  44 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  45 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  46 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  47 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  48 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  49 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  50 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  51 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  52 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  53 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  54 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  55 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  56 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  57 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  58 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  59 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  60 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  61 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  62 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  63 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  64 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  65 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  66 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  67 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  68 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  69 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  70 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  71 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  72 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  73 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  74 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  75 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  76 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  77 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  78 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  79 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  80 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  81 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  82 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  83 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  84 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  85 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  86 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  87 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  88 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  89 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  90 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  91 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  92 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  93 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  94 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  95 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  96 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  97 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  98 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  99 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  100 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  101 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  102 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  103 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  104 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  105 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  106 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  107 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  108 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  109 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  110 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  111 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  112 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  113 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  114 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  115 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  116 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  117 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  118 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  119 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  120 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  121 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  122 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  123 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  124 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  125 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  126 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  127 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  128 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  129 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  130 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  131 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  132 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  133 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  134 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  135 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  136 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  137 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  138 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  139 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  140 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  141 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  142 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  143 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  144 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  145 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  146 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  147 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  148 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  149 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  150 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  151 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  152 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  153 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  154 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  155 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  156 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  157 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  158 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  159 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  160 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  161 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  162 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  163 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  164 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  165 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  166 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  167 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  168 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  169 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  170 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  171 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  172 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  173 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  174 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  175 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  176 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  177 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  178 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  179 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  180 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  181 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  182 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  183 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  184 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  185 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  186 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  187 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  188 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  189 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  190 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  191 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  192 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  193 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  194 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  195 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  196 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  197 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  198 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  199 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
  200 0xf74bafde __clone+0x5d() in libc.so.6 (0x00000000)
0x0087a4f2: movl    %eax,0x0(%eax)
Modules:
Module    Address            Debug info    Name (128 modules)
PE      230000-  35d000    Deferred        libeay32
PE      360000-  3ae000    Deferred        ssleay32
PE      400000- 5537000    Export          uplay
PE    10000000-11816000    Deferred        libcef
PE    4ad00000-4b681000    Deferred        icudt
ELF    7b800000-7ba55000    Deferred        kernel32<elf>
  \-PE    7b810000-7ba55000    \               kernel32
ELF    7bc00000-7bcd9000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcd9000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7c614000-7c656000    Deferred        rsaenh<elf>
  \-PE    7c620000-7c656000    \               rsaenh
ELF    7d039000-7d0ab000    Deferred        d3dcompiler_43<elf>
  \-PE    7d040000-7d0ab000    \               d3dcompiler_43
ELF    7d0f1000-7d106000    Deferred        libgpg-error.so.0
ELF    7d106000-7d124000    Deferred        libgcc_s.so.1
ELF    7d124000-7d1d5000    Deferred        libgcrypt.so.20
ELF    7d1d5000-7d1fb000    Deferred        liblzma.so.5
ELF    7d1fb000-7d204000    Deferred        librt.so.1
ELF    7d204000-7d290000    Deferred        libsystemd.so.0
ELF    7d290000-7d29a000    Deferred        libffi.so.6
ELF    7d29a000-7d2b3000    Deferred        libresolv.so.2
ELF    7d2b3000-7d30d000    Deferred        libdbus-1.so.3
ELF    7d30d000-7d399000    Deferred        libgmp.so.10
ELF    7d399000-7d3cd000    Deferred        libhogweed.so.4
ELF    7d3cd000-7d409000    Deferred        libnettle.so.6
ELF    7d409000-7d41d000    Deferred        libtasn1.so.6
ELF    7d41d000-7d481000    Deferred        libp11-kit.so.0
ELF    7d481000-7d48e000    Deferred        libkrb5support.so.0
ELF    7d48e000-7d4c0000    Deferred        libk5crypto.so.3
ELF    7d4c0000-7d597000    Deferred        libkrb5.so.3
ELF    7d597000-7d5ab000    Deferred        libavahi-client.so.3
ELF    7d5ab000-7d6ee000    Deferred        libgnutls-deb0.so.28
ELF    7d6ee000-7d73e000    Deferred        libgssapi_krb5.so.2
ELF    7d73e000-7d7c5000    Deferred        libcups.so.2
ELF    7d7cc000-7d7e6000    Deferred        d3dx9_43<elf>
  \-PE    7d7d0000-7d7e6000    \               d3dx9_43
ELF    7d7e6000-7d81c000    Deferred        uxtheme<elf>
  \-PE    7d7f0000-7d81c000    \               uxtheme
ELF    7d81c000-7d823000    Deferred        libxfixes.so.3
ELF    7d823000-7d82e000    Deferred        libxcursor.so.1
ELF    7d82e000-7d840000    Deferred        libxi.so.6
ELF    7d840000-7d844000    Deferred        libxcomposite.so.1
ELF    7d844000-7d851000    Deferred        libxrandr.so.2
ELF    7d851000-7d85d000    Deferred        libxrender.so.1
ELF    7d85d000-7d864000    Deferred        libxxf86vm.so.1
ELF    7d864000-7d868000    Deferred        libxinerama.so.1
ELF    7d868000-7d86f000    Deferred        libxdmcp.so.6
ELF    7d86f000-7d873000    Deferred        libxau.so.6
ELF    7d873000-7d898000    Deferred        libxcb.so.1
ELF    7d898000-7d9e3000    Deferred        libx11.so.6
ELF    7d9e3000-7d9f8000    Deferred        libxext.so.6
ELF    7d9f8000-7d9ff000    Deferred        libnss_dns.so.2
ELF    7d9ff000-7da04000    Deferred        libkeyutils.so.1
ELF    7da04000-7da09000    Deferred        libcom_err.so.2
ELF    7da09000-7da17000    Deferred        libavahi-common.so.3
ELF    7da19000-7daa6000    Deferred        winex11<elf>
  \-PE    7da20000-7daa6000    \               winex11
ELF    7db10000-7db39000    Deferred        libexpat.so.1
ELF    7db39000-7db7c000    Deferred        libfontconfig.so.1
ELF    7db7c000-7dba8000    Deferred        libpng12.so.0
ELF    7dba8000-7dc55000    Deferred        libfreetype.so.6
ELF    7dc55000-7dcdf000    Deferred        gdiplus<elf>
  \-PE    7dc60000-7dcdf000    \               gdiplus
ELF    7dcdf000-7dd03000    Deferred        imm32<elf>
  \-PE    7dcf0000-7dd03000    \               imm32
ELF    7dd03000-7dd44000    Deferred        usp10<elf>
  \-PE    7dd10000-7dd44000    \               usp10
ELF    7dd44000-7de0f000    Deferred        crypt32<elf>
  \-PE    7dd50000-7de0f000    \               crypt32
ELF    7de0f000-7de3b000    Deferred        netapi32<elf>
  \-PE    7de20000-7de3b000    \               netapi32
ELF    7de3b000-7de65000    Deferred        secur32<elf>
  \-PE    7de40000-7de65000    \               secur32
ELF    7de65000-7de8c000    Deferred        mpr<elf>
  \-PE    7de70000-7de8c000    \               mpr
ELF    7de8c000-7dea7000    Deferred        libz.so.1
ELF    7dec8000-7df3f000    Deferred        wininet<elf>
  \-PE    7ded0000-7df3f000    \               wininet
ELF    7df3f000-7e06a000    Deferred        oleaut32<elf>
  \-PE    7df50000-7e06a000    \               oleaut32
ELF    7e06a000-7e105000    Deferred        urlmon<elf>
  \-PE    7e080000-7e105000    \               urlmon
ELF    7e105000-7e12a000    Deferred        iphlpapi<elf>
  \-PE    7e110000-7e12a000    \               iphlpapi
ELF    7e12a000-7e20f000    Deferred        comdlg32<elf>
  \-PE    7e130000-7e20f000    \               comdlg32
ELF    7e20f000-7e24b000    Deferred        winspool<elf>
  \-PE    7e220000-7e24b000    \               winspool
ELF    7e24b000-7e275000    Deferred        msacm32<elf>
  \-PE    7e250000-7e275000    \               msacm32
ELF    7e275000-7e2f1000    Deferred        rpcrt4<elf>
  \-PE    7e280000-7e2f1000    \               rpcrt4
ELF    7e2f1000-7e41e000    Deferred        ole32<elf>
  \-PE    7e310000-7e41e000    \               ole32
ELF    7e41e000-7e4d6000    Deferred        winmm<elf>
  \-PE    7e430000-7e4d6000    \               winmm
ELF    7e4d6000-7e4ea000    Deferred        psapi<elf>
  \-PE    7e4e0000-7e4ea000    \               psapi
ELF    7e4ea000-7e51f000    Deferred        ws2_32<elf>
  \-PE    7e4f0000-7e51f000    \               ws2_32
ELF    7e51f000-7e55a000    Deferred        winhttp<elf>
  \-PE    7e530000-7e55a000    \               winhttp
ELF    7e57f000-7e677000    Deferred        comctl32<elf>
  \-PE    7e590000-7e677000    \               comctl32
ELF    7e677000-7e6ed000    Deferred        shlwapi<elf>
  \-PE    7e680000-7e6ed000    \               shlwapi
ELF    7e6ed000-7e916000    Deferred        shell32<elf>
  \-PE    7e700000-7e916000    \               shell32
ELF    7e916000-7e984000    Deferred        advapi32<elf>
  \-PE    7e920000-7e984000    \               advapi32
ELF    7e984000-7ea9c000    Deferred        gdi32<elf>
  \-PE    7e990000-7ea9c000    \               gdi32
ELF    7ea9c000-7ebea000    Deferred        user32<elf>
  \-PE    7eab0000-7ebea000    \               user32
ELF    7ef5c000-7ef6a000    Deferred        libnss_files.so.2
ELF    7ef6a000-7ef77000    Deferred        libnss_nis.so.2
ELF    7ef77000-7ef92000    Deferred        libnsl.so.1
ELF    7ef92000-7efdf000    Deferred        libm.so.6
ELF    7efe7000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    f73cc000-f73d1000    Deferred        libdl.so.2
ELF    f73d1000-f758c000    Dwarf           libc.so.6
ELF    f758d000-f75aa000    Dwarf           libpthread.so.0
ELF    f75c1000-f75cb000    Deferred        libnss_compat.so.2
ELF    f75cb000-f7781000    Dwarf           libwine.so.1
ELF    f7783000-f77a7000    Deferred        ld-linux.so.2
ELF    f77a9000-f77aa000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Ubisoft\Ubisoft Game Launcher\Uplay.exe
    00000040    0
    00000024    0
    0000003d    0
    0000003e    0
    00000021    0
    00000022    0
    0000000b    0
    0000000d    0
    0000000c    0
    00000047    0
    00000046    0
    00000045    0
    00000044    0
    00000043    0
    00000042    0
    0000003a    0
    00000039    0
    00000038    0
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
    0000002b    0 <==
    0000002a    0
    00000029    0
    00000028    0
    00000027    0
    00000009    0
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
0000003b explorer.exe
    00000041    0
    0000003c    0


```In some of webpages there is advice that needed is to install crypt32, but I can't do this. When I tried, it gives me message:```
sha1sum mismatch! Rename /home/julia/.cache/winetricks/win2ksp4/W2KSP4_EN.EXE and try again. 
```What I should do?

---

### Post by QIII on 2016-02-04
*Moved to **Wine***

Please use the default font and colors.  Enclose terminal output in code tags.

---

