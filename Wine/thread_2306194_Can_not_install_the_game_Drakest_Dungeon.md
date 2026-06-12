---
title: "Can not install the game Drakest Dungeon"
date: 2015-12-13
forum: Wine
---

### Post by aron3 on 2015-12-13
Hello. So I've been trying to get Darkest dungeon working trough wine 1.7.55, it woked on my previrious computer and i installed the same wine version wih the same configuration and the same dll componets(I'm not too sure on that one).he
here is the log:
Unhandled exception: unimplemented function msvcp120.dll.??0_Pad@std@@QAE@XZ called in 32-bit code (0x7b83c3de).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7b83c3de ESP:0033f254 EBP:0033f2c8 EFLAGS:00000246(   - --  I  Z- -P- )
 EAX:7b827a69 EBX:7b8c0000 ECX:00000000 EDX:80000100
 ESI:80000100 EDI:7d6f4db8
Stack dump:
0x0033f254:  0033f2f8 00000008 00000000 80000100
0x0033f264:  00000001 00000000 7b83c3de 00000002
0x0033f274:  7d7527e0 7d752f51 7d80c9e6 01d20000
0x0033f284:  00000000 7d7f0149 7d80c9e6 01d20000
0x0033f294:  00000000 0033f2c0 7d881000 00000400
0x0033f2a4:  7d6f4db8 0033f2d8 7d80c9e6 00000001
000c: sel=0067 base=00000000 limit=00000000 32-bit r-x
Backtrace:
=>0 0x7b83c3de in kernel32 (+0x2c3de) (0x0033f2c8)
  1 0x7d752458 in msvcp120 (+0x62457) (0x0033f308)
  2 0x7d6f354d in msvcp120 (+0x354c) (0x0033f360)
  3 0x008d6160 in darkest (+0x4d615f) (0x0033f360)
  4 0x008d5f39 in darkest (+0x4d5f38) (0x0033f380)
  5 0x00a525a3 in darkest (+0x6525a2) (0x0033fbf0)
  6 0x00a51ec2 in darkest (+0x651ec1) (0x0033fe14)
  7 0x00cd0b7b in darkest (+0x8d0b7a) (0x0033fe60)
  8 0x7b861e9c call_process_entry+0xb() in kernel32 (0x0033fe78)
  9 0x7b862f73 in kernel32 (+0x52f72) (0x0033feb8)
  10 0x7bc84470 call_thread_func_wrapper+0xb() in ntdll (0x0033fed8)
  11 0x7bc8763d call_thread_func+0x7c() in ntdll (0x0033ffa8)
  12 0x7bc8444e RtlRaiseException+0x21() in ntdll (0x0033ffc8)
  13 0x7bc564ce call_dll_entry_point+0x3fd() in ntdll (0x0033ffe8)
  14 0xf760561d wine_call_on_stack+0x1c() in libwine.so.1 (0x00000000)
  15 0xf76056db wine_switch_to_stack+0x2a() in libwine.so.1 (0xffbe27d8)
  16 0x7bc5c809 LdrInitializeThunk+0x238() in ntdll (0xffbe2818)
  17 0x7b869863 __wine_kernel_init+0xa12() in kernel32 (0xffbe3938)
  18 0x7bc5d733 __wine_process_init+0x192() in ntdll (0xffbe39c8)
  19 0xf7602d80 wine_init+0x30f() in libwine.so.1 (0xffbe3a28)
  20 0x7bf0100c main+0xfb() in <wine-loader> (0xffbe3e78)
  21 0xf741da83 __libc_start_main+0xf2() in libc.so.6 (0x00000000)
0x7b83c3de: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (96 modules)
PE      340000-  3b8000    Deferred        steam_api
PE      400000- 12e3000    Export          darkest
PE     12f0000- 14d4000    Deferred        fmod
PE     14e0000- 16fa000    Deferred        fmodstudio
PE     1700000- 1749000    Deferred        libcurl
PE     1750000- 188d000    Deferred        libeay32
PE     1890000- 18d6000    Deferred        ssleay32
PE    10000000-100b4000    Deferred        sdl2
PE    62aa0000-62b08000    Deferred        glew32
ELF    7a800000-7a91f000    Deferred        opengl32<elf>
  \-PE    7a820000-7a91f000    \               opengl32
ELF    7b800000-7ba6a000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba6a000    \               kernel32
ELF    7bc00000-7bcf3000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcf3000    \               ntdll
ELF    7bf00000-7bf04000    Dwarf           <wine-loader>
ELF    7d583000-7d5ac000    Deferred        libexpat.so.1
ELF    7d5ac000-7d5e7000    Deferred        libfontconfig.so.1
ELF    7d5e7000-7d60f000    Deferred        libpng12.so.0
ELF    7d60f000-7d6af000    Deferred        libfreetype.so.6
ELF    7d6af000-7d7bd000    Dwarf           msvcp120<elf>
  \-PE    7d6f0000-7d7bd000    \               msvcp120
ELF    7d7bd000-7d892000    Deferred        msvcr120<elf>
  \-PE    7d7e0000-7d892000    \               msvcr120
ELF    7d892000-7d963000    Deferred        crypt32<elf>
  \-PE    7d8a0000-7d963000    \               crypt32
ELF    7d963000-7d994000    Deferred        libcrypt.so.1
ELF    7d994000-7da51000    Deferred        libsqlite3.so.0
ELF    7da51000-7da98000    Deferred        libhx509.so.5
ELF    7da98000-7daa7000    Deferred        libheimbase.so.1
ELF    7daa7000-7dad0000    Deferred        libwind.so.0
ELF    7dad0000-7db0c000    Deferred        libp11-kit.so.0
ELF    7db0c000-7db20000    Deferred        libtasn1.so.6
ELF    7db20000-7db36000    Deferred        libroken.so.18
ELF    7db36000-7db6b000    Deferred        libhcrypto.so.4
ELF    7db6b000-7dc11000    Deferred        libasn1.so.8
ELF    7dc11000-7dc97000    Deferred        libkrb5.so.26
ELF    7dc97000-7dd1d000    Deferred        libgcrypt.so.11
ELF    7dd1d000-7dde3000    Deferred        libgnutls.so.26
ELF    7dde3000-7de1f000    Deferred        libgssapi.so.3
ELF    7de1f000-7de3a000    Deferred        libsasl2.so.2
ELF    7de3a000-7de52000    Deferred        libresolv.so.2
ELF    7de52000-7dea4000    Deferred        libldap_r-2.4.so.2
ELF    7decc000-7df30000    Deferred        wldap32<elf>
  \-PE    7ded0000-7df30000    \               wldap32
ELF    7df30000-7df59000    Deferred        iphlpapi<elf>
  \-PE    7df40000-7df59000    \               iphlpapi
ELF    7df59000-7df95000    Deferred        ws2_32<elf>
  \-PE    7df60000-7df95000    \               ws2_32
ELF    7df95000-7e0db000    Deferred        oleaut32<elf>
  \-PE    7dfb0000-7e0db000    \               oleaut32
ELF    7e0fe000-7e105000    Deferred        libffi.so.6
ELF    7e105000-7e10a000    Deferred        libgpg-error.so.0
ELF    7e10a000-7e119000    Deferred        liblber-2.4.so.2
ELF    7e119000-7e12d000    Deferred        psapi<elf>
  \-PE    7e120000-7e12d000    \               psapi
ELF    7e12d000-7e147000    Deferred        libz.so.1
ELF    7e14a000-7e153000    Deferred        libheimntlm.so.0
ELF    7e153000-7e16f000    Deferred        wsock32<elf>
  \-PE    7e160000-7e16f000    \               wsock32
ELF    7e16f000-7e1d8000    Deferred        dbghelp<elf>
  \-PE    7e180000-7e1d8000    \               dbghelp
ELF    7e1d8000-7e253000    Deferred        shlwapi<elf>
  \-PE    7e1f0000-7e253000    \               shlwapi
ELF    7e253000-7e4a1000    Deferred        shell32<elf>
  \-PE    7e260000-7e4a1000    \               shell32
ELF    7e4a1000-7e4c6000    Deferred        imm32<elf>
  \-PE    7e4b0000-7e4c6000    \               imm32
ELF    7e4c6000-7e4f1000    Deferred        msacm32<elf>
  \-PE    7e4d0000-7e4f1000    \               msacm32
ELF    7e4f1000-7e576000    Deferred        rpcrt4<elf>
  \-PE    7e500000-7e576000    \               rpcrt4
ELF    7e576000-7e6bb000    Deferred        ole32<elf>
  \-PE    7e590000-7e6bb000    \               ole32
ELF    7e6bb000-7e6d5000    Deferred        version<elf>
  \-PE    7e6c0000-7e6d5000    \               version
ELF    7e6d5000-7e831000    Deferred        user32<elf>
  \-PE    7e6f0000-7e831000    \               user32
ELF    7e831000-7e8eb000    Deferred        winmm<elf>
  \-PE    7e840000-7e8eb000    \               winmm
ELF    7e8eb000-7e967000    Deferred        advapi32<elf>
  \-PE    7e900000-7e967000    \               advapi32
ELF    7e967000-7ea88000    Deferred        gdi32<elf>
  \-PE    7e970000-7ea88000    \               gdi32
ELF    7ea88000-7ea95000    Deferred        libnss_files.so.2
ELF    7ea95000-7eaae000    Deferred        libnsl.so.1
ELF    7ef92000-7efd8000    Deferred        libm.so.6
ELF    7efdb000-7efe0000    Deferred        libcom_err.so.2
ELF    f7404000-f75b2000    Dwarf           libc.so.6
ELF    f75b2000-f75b7000    Deferred        libdl.so.2
ELF    f75b8000-f75d4000    Deferred        libpthread.so.0
ELF    f75d4000-f75e0000    Deferred        libnss_nis.so.2
ELF    f75f3000-f75fc000    Deferred        libnss_compat.so.2
ELF    f75fc000-f77b2000    Dwarf           libwine.so.1
ELF    f77b4000-f77d6000    Deferred        ld-linux.so.2
ELF    f77d6000-f77d7000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000002a    0
    0000001d    0
    00000014    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001c    0
    00000019    0
    00000018    0
    00000013    0
0000001a plugplay.exe
    00000020    0
    0000001f    0
    0000001b    0
00000021 explorer.exe
    00000025    0
    00000024    0
    00000023    0
    00000022    0
0000002b (D) Z:\home\mcaron\Asztal\DarkestDungeon\_windows\Darkest.exe
    0000002c    0 <==
System information:
    Wine build: wine-1.7.55
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 3.13.0-37-generic

---

### Post by AlexHudghton on 2016-01-08
You may want to look at this [https://appdb.winehq.org/objectManager.php?sClass=version&iId=32518](https://appdb.winehq.org/objectManager.php?sClass=version&iId=32518)

---

