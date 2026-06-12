---
title: "Red Alert 3 - Comprehensive How to Needed"
date: 2012-07-28
forum: Wine
---

### Post by Daddyo-613 on 2012-07-28
**The Problem:** 

I'm trying to run RA3 retail in WINE 1.4 without success. WINE HQ does not have a coherent "How to" describing how to install and configure RA3 in WINE to get it to run. I've managed to install RA3 from the retail disk but I've been unable to get the game to run.

**My System:**

Wine build: wine-1.4
    Platform: i386 - Intel(R) Core(TM)2 Quad CPU @ 2.40GHz
    Host system: OS Type: Linux, GCC Version:  4.5.2 (i686-linux-gnu)
                              Xorg Version: 1.10.1 (13 October 2011  05:38:22PM)
    Host version: 2.6.38-15-generic-pae - Ubuntu 11.04 (natty)

When I launch the "RA3.exe" I get an error message. The details of the error are as follows:

```
Unhandled exception: unimplemented function msvcrt.dll._localtime64 called in 32-bit code (0x7bc4a020).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc4a020 ESP:0201d7c4 EBP:0201d828 EFLAGS:00200202(   - --  I   - - - )
 EAX:6177074c EBX:7bca6ff4 ECX:00000000 EDX:00000002
 ESI:0201d7d0 EDI:61764604
Stack dump:
0x0201d7c4:  100bd96e 7bc350c1 00000004 80000100
0x0201d7d4:  00000001 00000000 7bc4a020 00000002
0x0201d7e4:  61770970 6177074c 0000c101 61764604
0x0201d7f4:  0201d814 617118c5 6176d3e0 0000c101
0x0201d804:  00004e20 00000000 00000004 0d78ab6e
0x0201d814:  0201d834 61701c44 6176d3e0 0d78ab6e
Backtrace:
=>0 0x7bc4a020 call_dll_entry_point+0x5f0() in ntdll (0x0201d828)
  1 0x0037000f (0x0201d8d4)
  2 0x61722191 in mozsqlite3 (+0x22190) (0x0201d9f4)
  3 0x61724741 in mozsqlite3 (+0x24740) (0x0201db24)
  4 0x6173fa81 in mozsqlite3 (+0x3fa80) (0x0201de04)
  5 0x61746e65 in mozsqlite3 (+0x46e64) (0x0201df84)
  6 0x6a5568da in xul (+0x9168d9) (0x0201dfc4)
  7 0x6a5507b6 in xul (+0x9107b5) (0x0201e004)
  8 0x6a5f5f5b in xul (+0x9b5f5a) (0x0201e194)
  9 0x6a54e01d in xul (+0x90e01c) (0x0201e1e4)
  10 0x6173fa81 in mozsqlite3 (+0x3fa80) (0x0201e4c4)
  11 0x61746e65 in mozsqlite3 (+0x46e64) (0x0201e644)
  12 0x6a5568da in xul (+0x9168d9) (0x0201e684)
  13 0x6a5507b6 in xul (+0x9107b5) (0x0201e6c4)
  14 0x6a550176 in xul (+0x910175) (0x0201e6f4)
  15 0x6a5face6 in xul (+0x9bace5) (0x0201e824)
  16 0x6a5fba84 in xul (+0x9bba83) (0x0201e8e4)
  17 0x6a7a7e9e in xul (+0xb67e9d) (0x0201e944)
  18 0x6a771b2c in xul (+0xb31b2b) (0x0201e974)
  19 0x6a7a81cf in xul (+0xb681ce) (0x0201e9b4)
  20 0x64f58fc8 in nspr4 (+0x18fc7) (0x0201e9f4)
  21 0x64f5b57a in nspr4 (+0x1b579) (0x0201ea14)
  22 0x78003820 in msvcrt (+0x381f) (0x0201ea48)
  23 0x7bc71e90 call_thread_func_wrapper+0xb() in ntdll (0x0201ea58)
  24 0x7bc7494d call_thread_func+0x7c() in ntdll (0x0201eb28)
  25 0x7bc71e6e RtlRaiseException+0x21() in ntdll (0x0201eb48)
  26 0x7bc7a818 in ntdll (+0x6a817) (0x0201f398)
  27 0xb7595e99 start_thread+0xd8() in libpthread.so.0 (0x0201f498)
0x7bc4a020 call_dll_entry_point+0x5f0 in ntdll: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (133 modules)
PE      400000-  536000    Deferred        ra3
PE    61700000-61777000    Export          mozsqlite3
PE    61e40000-61e4c000    Deferred        mozalloc
PE    622c0000-622cd000    Deferred        plds4
PE    62e40000-62e67000    Deferred        smime3
PE    64f40000-64f75000    Export          nspr4
PE    68400000-684ea000    Deferred        nss3
PE    68780000-6879a000    Deferred        nssutil3
PE    69c40000-6b009000    Export          xul
PE    6c800000-6c832000    Deferred        ssl3
PE    6ce40000-6ce4d000    Deferred        plc4
PE    70180000-704b9000    Deferred        mozjs
PE    78000000-78044000    Export          msvcrt
ELF    7b800000-7ba16000    Deferred        kernel32<elf>
  \-PE    7b810000-7ba16000    \               kernel32
ELF    7bc00000-7bcc3000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcc3000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7d487000-7d4bf000    Deferred        usp10<elf>
  \-PE    7d490000-7d4bf000    \               usp10
ELF    7d4bf000-7d4d3000    Deferred        msimg32<elf>
  \-PE    7d4c0000-7d4d3000    \               msimg32
ELF    7d4d3000-7d531000    Deferred        dbghelp<elf>
  \-PE    7d4e0000-7d531000    \               dbghelp
ELF    7d531000-7d553000    Deferred        iphlpapi<elf>
  \-PE    7d540000-7d553000    \               iphlpapi
ELF    7d553000-7d585000    Deferred        ws2_32<elf>
  \-PE    7d560000-7d585000    \               ws2_32
ELF    7d585000-7d5a0000    Deferred        wsock32<elf>
  \-PE    7d590000-7d5a0000    \               wsock32
ELF    7d5a0000-7d696000    Deferred        mshtml<elf>
  \-PE    7d5b0000-7d696000    \               mshtml
ELF    7d696000-7d69c000    Deferred        libnss_dns.so.2
ELF    7d69c000-7d6a0000    Deferred        libnss_mdns4_minimal.so.2
ELF    7d6a4000-7d6b8000    Deferred        psapi<elf>
  \-PE    7d6b0000-7d6b8000    \               psapi
ELF    7d6b8000-7d73c000    Deferred        urlmon<elf>
  \-PE    7d6c0000-7d73c000    \               urlmon
ELF    7d73c000-7d79f000    Deferred        ieframe<elf>
  \-PE    7d740000-7d79f000    \               ieframe
ELF    7d7ef000-7d80a000    Deferred        spoolss<elf>
  \-PE    7d7f0000-7d80a000    \               spoolss
ELF    7d80a000-7d82b000    Deferred        localspl<elf>
  \-PE    7d810000-7d82b000    \               localspl
ELF    7d960000-7d96c000    Deferred        libnss_files.so.2
ELF    7d96c000-7d977000    Deferred        libnss_nis.so.2
ELF    7d977000-7d98e000    Deferred        libnsl.so.1
ELF    7d98e000-7d996000    Deferred        libnss_compat.so.2
ELF    7d996000-7d99f000    Deferred        librt.so.1
ELF    7d99f000-7d9dc000    Deferred        libdbus-1.so.3
ELF    7d9dc000-7d9e1000    Deferred        libgpg-error.so.0
ELF    7d9e1000-7d9f2000    Deferred        libtasn1.so.3
ELF    7d9f2000-7da07000    Deferred        libresolv.so.2
ELF    7da07000-7da0b000    Deferred        libkeyutils.so.1
ELF    7da0b000-7da1b000    Deferred        libavahi-client.so.3
ELF    7da1b000-7da8f000    Deferred        libgcrypt.so.11
ELF    7da8f000-7db25000    Deferred        libgnutls.so.26
ELF    7db25000-7db49000    Deferred        libk5crypto.so.3
ELF    7db49000-7dbf7000    Deferred        libkrb5.so.3
ELF    7dbf7000-7dc27000    Deferred        libgssapi_krb5.so.2
ELF    7dc27000-7dc71000    Deferred        libcups.so.2
ELF    7dc89000-7dcbd000    Deferred        uxtheme<elf>
  \-PE    7dc90000-7dcbd000    \               uxtheme
ELF    7dcbd000-7dcc3000    Deferred        libxfixes.so.3
ELF    7dcc3000-7dccd000    Deferred        libxcursor.so.1
ELF    7dccf000-7dcd7000    Deferred        libkrb5support.so.0
ELF    7dcd7000-7dce3000    Deferred        libavahi-common.so.3
ELF    7dd4b000-7dd75000    Deferred        libexpat.so.1
ELF    7dd75000-7dda4000    Deferred        libfontconfig.so.1
ELF    7dda4000-7ddb3000    Deferred        libxi.so.6
ELF    7ddb3000-7ddb7000    Deferred        libxcomposite.so.1
ELF    7ddb7000-7ddbf000    Deferred        libxrandr.so.2
ELF    7ddbf000-7ddc9000    Deferred        libxrender.so.1
ELF    7ddc9000-7ddcf000    Deferred        libxxf86vm.so.1
ELF    7ddcf000-7ddd3000    Deferred        libxinerama.so.1
ELF    7ddd3000-7ddf5000    Deferred        imm32<elf>
  \-PE    7dde0000-7ddf5000    \               imm32
ELF    7ddf5000-7ddfb000    Deferred        libxdmcp.so.6
ELF    7ddfb000-7de14000    Deferred        libxcb.so.1
ELF    7de14000-7df2f000    Deferred        libx11.so.6
ELF    7df2f000-7df3e000    Deferred        libxext.so.6
ELF    7df3e000-7df56000    Deferred        libice.so.6
ELF    7df56000-7dfea000    Deferred        winex11<elf>
  \-PE    7df60000-7dfea000    \               winex11
ELF    7e062000-7e066000    Deferred        libxau.so.6
ELF    7e066000-7e0ec000    Deferred        libfreetype.so.6
ELF    7e0ec000-7e10c000    Deferred        oleacc<elf>
  \-PE    7e0f0000-7e10c000    \               oleacc
ELF    7e10c000-7e132000    Deferred        mpr<elf>
  \-PE    7e110000-7e132000    \               mpr
ELF    7e132000-7e147000    Deferred        libz.so.1
ELF    7e147000-7e1b6000    Deferred        wininet<elf>
  \-PE    7e150000-7e1b6000    \               wininet
ELF    7e1b6000-7e22a000    Deferred        gdiplus<elf>
  \-PE    7e1c0000-7e22a000    \               gdiplus
ELF    7e22a000-7e31c000    Deferred        oleaut32<elf>
  \-PE    7e240000-7e31c000    \               oleaut32
ELF    7e31c000-7e386000    Deferred        shlwapi<elf>
  \-PE    7e330000-7e386000    \               shlwapi
ELF    7e386000-7e596000    Deferred        shell32<elf>
  \-PE    7e390000-7e596000    \               shell32
ELF    7e596000-7e675000    Deferred        comdlg32<elf>
  \-PE    7e5a0000-7e675000    \               comdlg32
ELF    7e675000-7e6af000    Deferred        winspool<elf>
  \-PE    7e680000-7e6af000    \               winspool
ELF    7e6af000-7e6d7000    Deferred        msacm32<elf>
  \-PE    7e6b0000-7e6d7000    \               msacm32
ELF    7e6d7000-7e74c000    Deferred        rpcrt4<elf>
  \-PE    7e6e0000-7e74c000    \               rpcrt4
ELF    7e74c000-7e852000    Deferred        ole32<elf>
  \-PE    7e760000-7e852000    \               ole32
ELF    7e852000-7e8ff000    Deferred        winmm<elf>
  \-PE    7e860000-7e8ff000    \               winmm
ELF    7e8ff000-7e918000    Deferred        version<elf>
  \-PE    7e900000-7e918000    \               version
ELF    7e918000-7e978000    Deferred        advapi32<elf>
  \-PE    7e920000-7e978000    \               advapi32
ELF    7e978000-7ea35000    Deferred        gdi32<elf>
  \-PE    7e980000-7ea35000    \               gdi32
ELF    7ea35000-7eb75000    Deferred        user32<elf>
  \-PE    7ea50000-7eb75000    \               user32
ELF    7eb75000-7ec6d000    Deferred        comctl32<elf>
  \-PE    7eb80000-7ec6d000    \               comctl32
ELF    7efc2000-7efe8000    Deferred        libm.so.6
ELF    7efe9000-7efed000    Deferred        libcom_err.so.2
ELF    b7420000-b7428000    Deferred        libsm.so.6
ELF    b7429000-b742d000    Deferred        libdl.so.2
ELF    b742d000-b758f000    Dwarf           libc.so.6
ELF    b7590000-b75a9000    Dwarf           libpthread.so.0
ELF    b75ab000-b75b0000    Deferred        libuuid.so.1
ELF    b75c1000-b7702000    Dwarf           libwine.so.1
ELF    b7704000-b7722000    Deferred        ld-linux.so.2
ELF    b7722000-b7723000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Electronic Arts\Red Alert 3\RA3.exe
    0000003a    0
    00000035    0
    00000034    0 <==
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
    00000009    0
0000000e services.exe
    00000039    0
    00000038    0
    00000024    0
    0000001e    0
    00000018    0
    00000017    0
    00000015    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001c    0
    00000019    0
    00000014    0
    00000013    0
0000001a plugplay.exe
    00000020    0
    0000001d    0
    0000001b    0
00000021 winedevice.exe
    00000026    0
    00000023    0
    00000022    0
00000027 explorer.exe
    00000028    0
System information:
    Wine build: wine-1.4
    Platform: i386
    Host system: Linux
    Host version: 2.6.38-15-generic-pae
```Please don't direct me to the general WINE HQ Appdb. I've scoured that site and I've been unable to find any helpful information. 

If there is a specific page I've missed, I'd be pleased to see that reference.

Any help would be appreciated.

---

### Post by sffvba[e0rt on 2012-07-28
*Thread moved to **Wine**.*


404

---

### Post by ergo-proxy on 2012-07-29
Did you install wine from ppa? Try with a different  wine versions too. It did fully work me without any tricks and afair I did use 1.3* version (dont really remember which one). 

The problem you faced might be related to securom which often is not properly recognized by wine even if you own original disks so perhaps try applying *cough* a vitamin...

---

