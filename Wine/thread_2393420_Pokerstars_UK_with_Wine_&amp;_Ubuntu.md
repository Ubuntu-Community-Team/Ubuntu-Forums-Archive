---
title: "Pokerstars UK with Wine &amp; Ubuntu"
date: 2018-06-03
forum: Wine
---

### Post by davyk2 on 2018-06-03
Hi All,

quite new to linux as my home computer, so I was wondering if you could give me a hand on an error I am receiving.

I installed pokerstars and wine last month but all of a sudden it is causing an issue on log in and failing.

I am not sure if this is due to the new GDPR in Europe as it seems to fail after log in, but a terms and condition window cannot open correctly, then it crashes with the program error details below.

Anyone else got this issue??
or point me in the right direction for a fix?

System:
uname -a
Linux ubuntu 4.13.0-43-generic #48~16.04.1-Ubuntu SMP Thu May 17 12:56:46 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

PokerstarsInstallPM.exe is ran with wine
wine ./PokerStarsInstallUK.exe&

screenshot of problem:
attached

```
Error:
Unhandled exception: page fault on read access to 0x0000002c in 32-bit code (0x12ba77c1).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:12ba77c1 ESP:0033c154 EBP:0033c19c EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:4100a7d0 EBX:0033c1cf ECX:0000000c EDX:00000001
 ESI:00000000 EDI:00000440
Stack dump:
0x0033c154:  41a80000 00000000 41020ee4 46888018
0x0033c164:  4688801c 00000001 00000440 00000001
0x0033c174:  00000100 41020ee0 4686c6e8 00000440
0x0033c184:  00010100 00000100 53fce379 4686c6e8
0x0033c194:  46888000 00020803 0033c1ec 12b940f4
0x0033c1a4:  46888000 0033c2d0 0033c1d4 0033c1d0
Backtrace:
=>0 0x12ba77c1 in libcef (+0x2ba77c1) (0x0033c19c)
  1 0x12b940f4 in libcef (+0x2b940f3) (0x0033c1ec)
  2 0x12ba6680 in libcef (+0x2ba667f) (0x0033c274)
  3 0x12b174d3 in libcef (+0x2b174d2) (0x0033c2a8)
  4 0x12b1777f in libcef (+0x2b1777e) (0x0033c2fc)
  5 0x12b189a7 in libcef (+0x2b189a6) (0x0033d154)
  6 0x12b17b12 in libcef (+0x2b17b11) (0x0033d2c4)
  7 0x12b1b749 in libcef (+0x2b1b748) (0x0033d380)
  8 0x12af0f66 in libcef (+0x2af0f65) (0x0033d3f0)
  9 0x12af07b6 in libcef (+0x2af07b5) (0x0033d474)
  10 0x12b0f660 in libcef (+0x2b0f65f) (0x0033d490)
  11 0x12af31de in libcef (+0x2af31dd) (0x0033d4bc)
  12 0x12af363c in libcef (+0x2af363b) (0x0033d58c)
  13 0x12af24f5 in libcef (+0x2af24f4) (0x0033d5e8)
  14 0x12af0f58 in libcef (+0x2af0f57) (0x0033d660)
  15 0x12af07b6 in libcef (+0x2af07b5) (0x0033d6e4)
  16 0x12b0f660 in libcef (+0x2b0f65f) (0x0033d700)
  17 0x12af31de in libcef (+0x2af31dd) (0x0033d72c)
  18 0x12af363c in libcef (+0x2af363b) (0x0033d7fc)
  19 0x12af24f5 in libcef (+0x2af24f4) (0x0033d858)
  20 0x12af0f58 in libcef (+0x2af0f57) (0x0033d8d0)
  21 0x12af07b6 in libcef (+0x2af07b5) (0x0033d954)
  22 0x12b0f660 in libcef (+0x2b0f65f) (0x0033d970)
  23 0x12af31de in libcef (+0x2af31dd) (0x0033d99c)
  24 0x12af363c in libcef (+0x2af363b) (0x0033da6c)
  25 0x12af24f5 in libcef (+0x2af24f4) (0x0033dac8)
  26 0x12af0f58 in libcef (+0x2af0f57) (0x0033db40)
  27 0x12af07b6 in libcef (+0x2af07b5) (0x0033dbc4)
  28 0x12b0f660 in libcef (+0x2b0f65f) (0x0033dbe0)
  29 0x12af31de in libcef (+0x2af31dd) (0x0033dc0c)
  30 0x12af363c in libcef (+0x2af363b) (0x0033dcdc)
  31 0x12af24f5 in libcef (+0x2af24f4) (0x0033dd38)
  32 0x12af0f58 in libcef (+0x2af0f57) (0x0033ddb0)
  33 0x12af07b6 in libcef (+0x2af07b5) (0x0033de34)
  34 0x12b0f660 in libcef (+0x2b0f65f) (0x0033de50)
  35 0x12af31de in libcef (+0x2af31dd) (0x0033de7c)
  36 0x12af363c in libcef (+0x2af363b) (0x0033df4c)
  37 0x12af24f5 in libcef (+0x2af24f4) (0x0033dfa8)
  38 0x12af0f58 in libcef (+0x2af0f57) (0x0033e020)
  39 0x12af07b6 in libcef (+0x2af07b5) (0x0033e0a4)
  40 0x12b0f660 in libcef (+0x2b0f65f) (0x0033e0c0)
  41 0x12af31de in libcef (+0x2af31dd) (0x0033e0ec)
  42 0x12af363c in libcef (+0x2af363b) (0x0033e1bc)
  43 0x12af24f5 in libcef (+0x2af24f4) (0x0033e218)
  44 0x12af0f58 in libcef (+0x2af0f57) (0x0033e290)
  45 0x12af07b6 in libcef (+0x2af07b5) (0x0033e314)
  46 0x12b0f660 in libcef (+0x2b0f65f) (0x0033e330)
  47 0x12af31de in libcef (+0x2af31dd) (0x0033e35c)
  48 0x12af363c in libcef (+0x2af363b) (0x0033e42c)
  49 0x12af24f5 in libcef (+0x2af24f4) (0x0033e488)
  50 0x12af0f58 in libcef (+0x2af0f57) (0x0033e500)
  51 0x12af07b6 in libcef (+0x2af07b5) (0x0033e584)
  52 0x12b0f660 in libcef (+0x2b0f65f) (0x0033e5a0)
  53 0x12af31de in libcef (+0x2af31dd) (0x0033e5cc)
  54 0x12af363c in libcef (+0x2af363b) (0x0033e69c)
  55 0x12af24f5 in libcef (+0x2af24f4) (0x0033e6f8)
  56 0x12af0f58 in libcef (+0x2af0f57) (0x0033e770)
  57 0x12af07b6 in libcef (+0x2af07b5) (0x0033e7f4)
  58 0x12b0f660 in libcef (+0x2b0f65f) (0x0033e810)
  59 0x12af31de in libcef (+0x2af31dd) (0x0033e83c)
  60 0x12af363c in libcef (+0x2af363b) (0x0033e90c)
  61 0x12af24f5 in libcef (+0x2af24f4) (0x0033e968)
  62 0x12af0f58 in libcef (+0x2af0f57) (0x0033e9dc)
  63 0x12af07b6 in libcef (+0x2af07b5) (0x0033ea60)
  64 0x12b87fe1 in libcef (+0x2b87fe0) (0x0033ea94)
  65 0x12b0f660 in libcef (+0x2b0f65f) (0x0033eab0)
  66 0x12b88236 in libcef (+0x2b88235) (0x0033eb00)
  67 0x12941de6 in libcef (+0x2941de5) (0x0033eb64)
  68 0x12940423 in libcef (+0x2940422) (0x0033ec58)
  69 0x12948337 in libcef (+0x2948336) (0x0033ecb0)
  70 0x129472f9 in libcef (+0x29472f8) (0x0033ecf0)
  71 0x12946a87 in libcef (+0x2946a86) (0x0033ed48)
  72 0x129469d8 in libcef (+0x29469d7) (0x0033ed54)
  73 0x12c33e4c in libcef (+0x2c33e4b) (0x0033ed64)
  74 0x13a7a601 in libcef (+0x3a7a600) (0x0033ed70)
  75 0x139fe1b3 in libcef (+0x39fe1b2) (0x0033edc0)
  76 0x12e3b035 in libcef (+0x2e3b034) (0x0033edd0)
  77 0x11cca8f2 in libcef (+0x1cca8f1) (0x0033ee4c)
  78 0x1372fe26 in libcef (+0x372fe25) (0x0033ee68)
  79 0x11cd64e8 in libcef (+0x1cd64e7) (0x0033ee94)
  80 0x1123d297 in libcef (+0x123d296) (0x0033ef08)
  81 0x110510d0 in libcef (+0x10510cf) (0x0033f034)
  82 0x11050ab6 in libcef (+0x1050ab5) (0x0033f0e8)
  83 0x123e2aa1 in libcef (+0x23e2aa0) (0x0033f104)
  84 0x1123d297 in libcef (+0x123d296) (0x0033f178)
  85 0x1105346e in libcef (+0x105346d) (0x0033f1ec)
  86 0x133d4357 in libcef (+0x33d4356) (0x0033f204)
  87 0x1123d297 in libcef (+0x123d296) (0x0033f274)
  88 0x112465c3 in libcef (+0x12465c2) (0x0033f284)
  89 0x111efd96 in libcef (+0x11efd95) (0x0033f308)
  90 0x111f00db in libcef (+0x11f00da) (0x0033f328)
  91 0x111f01ee in libcef (+0x11f01ed) (0x0033f3e0)
  92 0x11248497 in libcef (+0x1248496) (0x0033f3fc)
  93 0x111efaef in libcef (+0x11efaee) (0x0033f40c)
  94 0x111d8b0e in libcef (+0x11d8b0d) (0x0033f420)
  95 0x12e242e0 in libcef (+0x2e242df) (0x0033f4cc)
  96 0x110efb77 in libcef (+0x10efb76) (0x0033f4e4)
  97 0x110effb3 in libcef (+0x10effb2) (0x0033f538)
  98 0x11f1ad61 in libcef (+0x1f1ad60) (0x0033f630)
  99 0x11f1b1e1 in libcef (+0x1f1b1e0) (0x0033f644)
  100 0x110efaa5 in libcef (+0x10efaa4) (0x0033f684)
  101 0x110f05cb in libcef (+0x10f05ca) (0x0033f758)
  102 0x100010e0 in libcef (+0x10df) (0x0033f788)
  103 0x0040d81c in pokerstarsbr (+0xd81b) (0x0033f7b4)
  104 0x00405ed8 in pokerstarsbr (+0x5ed7) (0x0033fe74)
  105 0x00430124 in pokerstarsbr (+0x30123) (0x0033fec0)
  106 0x7b461aac call_process_entry+0xb() in kernel32 (0x0033fed8)
  107 0x7b4633b2 in kernel32 (+0x533b1) (0x0033ffd8)
  108 0x7b461aba call_process_entry+0x19() in kernel32 (0x0033ffec)
0x12ba77c1: movl    0x2c(%esi),%eax
Modules:
Module    Address            Debug info    Name (170 modules)
PE      400000-  4ce000    Export          pokerstarsbr
PE     1c20000- 1c96000    Deferred        chrome_elf
PE    10000000-14edc000    Export          libcef
ELF    7a800000-7a93d000    Deferred        opengl32<elf>
  \-PE    7a820000-7a93d000    \               opengl32
ELF    7b400000-7b7ea000    Dwarf           kernel32<elf>
  \-PE    7b410000-7b7ea000    \               kernel32
ELF    7bc00000-7bcfa000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcfa000    \               ntdll
ELF    7c000000-7c004000    Deferred        <wine-loader>
PE    7c93b000-7c94f000    Deferred        api-ms-win-core-localization-obs
PE    7c940000-7c94f000    Deferred        api-ms-win-core-localization-obsC:\windows\system32\api-ms-win-core-localization-obsolete-l1-2-0.dll
ELF    7c953000-7c967000    Deferred        api-ms-win-core-datetime-l1-1-1<
PE    7c960000-7c967000    Deferred        api-ms-win-core-datetime-l1-1-1
ELF    7c96b000-7c97f000    Deferred        api-ms-win-core-string-l1-1-0<el
PE    7c970000-7c97f000    Deferred        api-ms-win-core-string-l1-1-0
PE    7c983000-7c997000    Deferred        api-ms-win-core-localization-l1-
PE    7c990000-7c997000    Deferred        api-ms-win-core-localization-l1-C:\windows\system32\api-ms-win-core-localization-l1-2-1.dll
ELF    7c99b000-7c9af000    Deferred        api-ms-win-core-fibers-l1-1-1<el
PE    7c9a0000-7c9af000    Deferred        api-ms-win-core-fibers-l1-1-1
ELF    7c9b3000-7c9c9000    Deferred        libgpg-error.so.0
ELF    7c9cb000-7ca40000    Deferred        libpcre.so.3
ELF    7ca43000-7ca60000    Deferred        libgcc_s.so.1
ELF    7ca63000-7cb12000    Deferred        libgcrypt.so.20
ELF    7cb13000-7cb39000    Deferred        liblzma.so.5
ELF    7cb3b000-7cb44000    Deferred        librt.so.1
ELF    7cb4b000-7cb71000    Deferred        libselinux.so.1
ELF    7cb73000-7cc01000    Deferred        libsystemd.so.0
ELF    7cc03000-7cc0c000    Deferred        libffi.so.6
ELF    7cc13000-7cc2c000    Deferred        libresolv.so.2
ELF    7cc33000-7cc38000    Deferred        libkeyutils.so.1
ELF    7cc3b000-7cc95000    Deferred        libdbus-1.so.3
ELF    7cc9b000-7cd27000    Deferred        libgmp.so.10
ELF    7cd2b000-7cd60000    Deferred        libhogweed.so.4
ELF    7cd63000-7cda0000    Deferred        libnettle.so.6
ELF    7cda3000-7cdb8000    Deferred        libtasn1.so.6
ELF    7cdbb000-7cdef000    Deferred        libidn.so.11
ELF    7cdf3000-7ce54000    Deferred        libp11-kit.so.0
ELF    7ce5b000-7ce68000    Deferred        libkrb5support.so.0
ELF    7ce6b000-7ce9c000    Deferred        libk5crypto.so.3
ELF    7cea3000-7cf79000    Deferred        libkrb5.so.3
ELF    7cf7b000-7cf8f000    Deferred        libavahi-client.so.3
ELF    7cf93000-7d0eb000    Deferred        libgnutls.so.30
ELF    7d0eb000-7d13d000    Deferred        libgssapi_krb5.so.2
ELF    7d143000-7d1ca000    Deferred        libcups.so.2
ELF    7d1d3000-7d1e7000    Deferred        api-ms-win-core-synch-l1-2-0<elf
PE    7d1e0000-7d1e7000    Deferred        api-ms-win-core-synch-l1-2-0
ELF    7d1eb000-7d223000    Deferred        uxtheme<elf>
  \-PE    7d1f0000-7d223000    \               uxtheme
ELF    7d223000-7d22a000    Deferred        libxfixes.so.3
ELF    7d22b000-7d237000    Deferred        libxcursor.so.1
ELF    7d23b000-7d240000    Deferred        libcom_err.so.2
ELF    7d243000-7d251000    Deferred        libavahi-common.so.3
ELF    7d25b000-7d268000    Deferred        libxrandr.so.2
ELF    7d26b000-7d27e000    Deferred        libxi.so.6
ELF    7d283000-7d287000    Deferred        libxcomposite.so.1
ELF    7d28b000-7d292000    Deferred        libxdmcp.so.6
ELF    7d293000-7d297000    Deferred        libxau.so.6
ELF    7d29b000-7d2c1000    Deferred        libxcb.so.1
ELF    7d2c3000-7d40e000    Deferred        libx11.so.6
ELF    7d413000-7d428000    Deferred        libxext.so.6
ELF    7d42b000-7d437000    Deferred        libxrender.so.1
ELF    7d43b000-7d442000    Deferred        libxxf86vm.so.1
ELF    7d443000-7d447000    Deferred        libxinerama.so.1
ELF    7d44b000-7d4d8000    Deferred        winex11<elf>
  \-PE    7d460000-7d4d8000    \               winex11
ELF    7d57b000-7d5a5000    Deferred        libexpat.so.1
ELF    7d5ab000-7d5f4000    Deferred        libfontconfig.so.1
ELF    7d61b000-7d646000    Deferred        libpng12.so.0
ELF    7d64b000-7d6fb000    Deferred        libfreetype.so.6
ELF    7d71b000-7d732000    Deferred        dxva2<elf>
  \-PE    7d720000-7d732000    \               dxva2
ELF    7d733000-7d772000    Deferred        d3d9<elf>
  \-PE    7d740000-7d772000    \               d3d9
ELF    7d773000-7d797000    Deferred        imm32<elf>
  \-PE    7d780000-7d797000    \               imm32
ELF    7d79b000-7d7b3000    Deferred        wtsapi32<elf>
  \-PE    7d7a0000-7d7b3000    \               wtsapi32
ELF    7d7b3000-7d81c000    Deferred        d3d11<elf>
  \-PE    7d7c0000-7d81c000    \               d3d11
ELF    7d823000-7d96b000    Deferred        wined3d<elf>
  \-PE    7d830000-7d96b000    \               wined3d
ELF    7d96b000-7d995000    Deferred        dxgi<elf>
  \-PE    7d970000-7d995000    \               dxgi
ELF    7d99b000-7da05000    Deferred        dwrite<elf>
  \-PE    7d9a0000-7da05000    \               dwrite
ELF    7da0b000-7da29000    Deferred        jsproxy<elf>
  \-PE    7da10000-7da29000    \               jsproxy
ELF    7da2b000-7da68000    Deferred        winhttp<elf>
  \-PE    7da30000-7da68000    \               winhttp
ELF    7da6b000-7da93000    Deferred        mpr<elf>
  \-PE    7da70000-7da93000    \               mpr
ELF    7da93000-7db0b000    Deferred        wininet<elf>
  \-PE    7daa0000-7db0b000    \               wininet
ELF    7db0b000-7dba9000    Deferred        urlmon<elf>
  \-PE    7db20000-7dba9000    \               urlmon
ELF    7dbab000-7dbc4000    Deferred        ncrypt<elf>
  \-PE    7dbb0000-7dbc4000    \               ncrypt
ELF    7dbcb000-7dbe1000    Deferred        dhcpcsvc<elf>
  \-PE    7dbd0000-7dbe1000    \               dhcpcsvc
ELF    7dbe3000-7dc0b000    Deferred        propsys<elf>
  \-PE    7dbf0000-7dc0b000    \               propsys
ELF    7dc0b000-7dcfb000    Deferred        cryptui<elf>
  \-PE    7dc10000-7dcfb000    \               cryptui
ELF    7dcfb000-7dd41000    Deferred        usp10<elf>
  \-PE    7dd00000-7dd41000    \               usp10
ELF    7dd43000-7dd5e000    Deferred        libz.so.1
ELF    7dd6b000-7dd82000    Deferred        dwmapi<elf>
  \-PE    7dd70000-7dd82000    \               dwmapi
ELF    7dd83000-7dde9000    Deferred        dbghelp<elf>
  \-PE    7dd90000-7dde9000    \               dbghelp
ELF    7ddeb000-7de04000    Deferred        hid<elf>
  \-PE    7ddf0000-7de04000    \               hid
ELF    7de0b000-7deda000    Deferred        crypt32<elf>
  \-PE    7de10000-7deda000    \               crypt32
ELF    7dedb000-7df11000    Deferred        wintrust<elf>
  \-PE    7dee0000-7df11000    \               wintrust
ELF    7df13000-7df71000    Deferred        oleacc<elf>
  \-PE    7df20000-7df71000    \               oleacc
ELF    7df73000-7dfa7000    Deferred        secur32<elf>
  \-PE    7df80000-7dfa7000    \               secur32
ELF    7dfab000-7dfc3000    Deferred        userenv<elf>
  \-PE    7dfb0000-7dfc3000    \               userenv
ELF    7dfc3000-7dfec000    Deferred        iphlpapi<elf>
  \-PE    7dfd0000-7dfec000    \               iphlpapi
ELF    7dff3000-7e022000    Deferred        netapi32<elf>
  \-PE    7e000000-7e022000    \               netapi32
ELF    7e023000-7e05c000    Deferred        ws2_32<elf>
  \-PE    7e030000-7e05c000    \               ws2_32
ELF    7e063000-7e08e000    Deferred        msacm32<elf>
  \-PE    7e070000-7e08e000    \               msacm32
ELF    7e093000-7e14b000    Deferred        winmm<elf>
  \-PE    7e0a0000-7e14b000    \               winmm
ELF    7e14b000-7e15f000    Deferred        psapi<elf>
  \-PE    7e150000-7e15f000    \               psapi
ELF    7e163000-7e295000    Deferred        oleaut32<elf>
  \-PE    7e180000-7e295000    \               oleaut32
ELF    7e29b000-7e31c000    Deferred        rpcrt4<elf>
  \-PE    7e2b0000-7e31c000    \               rpcrt4
ELF    7e323000-7e47e000    Deferred        ole32<elf>
  \-PE    7e340000-7e47e000    \               ole32
ELF    7e483000-7e4c2000    Deferred        winspool<elf>
  \-PE    7e490000-7e4c2000    \               winspool
ELF    7e4c3000-7e5e2000    Deferred        comctl32<elf>
  \-PE    7e4d0000-7e5e2000    \               comctl32
ELF    7e5e3000-7e659000    Deferred        shlwapi<elf>
  \-PE    7e5f0000-7e659000    \               shlwapi
ELF    7e65b000-7e8ab000    Deferred        shell32<elf>
  \-PE    7e670000-7e8ab000    \               shell32
ELF    7e8ab000-7e996000    Deferred        comdlg32<elf>
  \-PE    7e8b0000-7e996000    \               comdlg32
ELF    7e99b000-7eaca000    Deferred        gdi32<elf>
  \-PE    7e9b0000-7eaca000    \               gdi32
ELF    7eacb000-7ecab000    Deferred        user32<elf>
  \-PE    7eae0000-7ecab000    \               user32
ELF    7ecab000-7ed23000    Deferred        advapi32<elf>
  \-PE    7ecc0000-7ed23000    \               advapi32
ELF    7ed23000-7ed36000    Deferred        libnss_files.so.2
ELF    7ed3b000-7ed48000    Deferred        libnss_nis.so.2
ELF    7ed4b000-7ed66000    Deferred        libnsl.so.1
ELF    7ed6b000-7ed85000    Deferred        version<elf>
  \-PE    7ed70000-7ed85000    \               version
ELF    7ef8b000-7efe0000    Deferred        libm.so.6
ELF    7eff3000-7effd000    Deferred        libnss_compat.so.2
ELF    f7bcb000-f7bd0000    Deferred        libdl.so.2
ELF    f7bd3000-f7d89000    Deferred        libc.so.6
ELF    f7d8b000-f7da8000    Deferred        libpthread.so.0
ELF    f7dcb000-f7f82000    Dwarf           libwine.so.1
ELF    f7f83000-f7fa8000    Deferred        ld-linux.so.2
ELF    f7fae000-f7faf000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    00000022    0
    0000001d    0
    00000013    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    0000001c    0
    00000017    0
    00000016    0
    00000012    0
0000001a plugplay.exe
    0000001f    0
    0000001e    0
    0000001b    0
00000020 winedevice.exe
    00000029    0
    00000024    0
    00000023    0
    00000021    0
00000027 explorer.exe
    0000002c    0
    0000002b    0
    0000002a    0
    00000028    0
00000032 PokerStars.exe
    0000003c    0
    0000003b    0
    0000003a    0
    00000039    0
    00000038    0
    00000037    0
    00000036    0
    00000035    0
    00000034    0
    00000033    0
0000003d gameutil1.exe
    00000040    0
    0000003f    0
    0000003e    0
00000041 PokerStarsBr.exe
    00000124   -2
    00000065    0
    00000064    0
    00000063    0
    00000062    0
    00000061    0
    00000060    0
    0000005f    0
    0000005d    0
    00000059    0
    00000058    0
    00000057    0
    00000056   -2
    00000055    0
    00000054    0
    00000053    0
    00000052    0
    00000051    0
    00000050    0
    0000004e    0
    0000004c    0
    0000004b   -2
    0000004a   -2
    00000049    0
    00000048    0
    00000047    0
    00000046    0
    00000045    0
    00000044    0
    00000043    0
    00000042    0
00000066 PokerStarsBr.exe
    000000a9    0
    00000084   -2
    00000083    0
    00000082    0
    00000081    0
    00000080    0
    0000007f    0
    0000007e    0
    0000007d    0
    0000007c    0
    0000007b    0
    0000007a    0
    00000079    0
    00000078    0
    00000077   -2
    00000076   -2
    00000075    0
    00000074    0
    00000067    0
000000b7 PokerStarsBr.exe
    00000125   -2
    00000120    0
    000000db    0
    000000da    0
    000000d9    0
    000000d8    0
    000000d7    0
    000000d6    0
    000000d5    0
    000000d3    0
    000000cf    0
    000000ce    0
    000000cd    0
    000000cc   -2
    000000cb    0
    000000ca    0
    000000c9    0
    000000c8    0
    000000c7    0
    000000c6    0
    000000c5    0
    000000c4    0
    000000c3    0
    000000c2    0
    000000c1   -2
    000000c0   -2
    000000bf    0
    000000be    0
    000000bd    0
    000000bc    0
    000000bb    0
    000000ba    0
    000000b9    0
    000000b8    0
000000dc (D) C:\Program Files (x86)\PokerStars.UK\br\PokerStarsBr.exe
    0000011f    0
    0000011e    0
    000000fa   -2
    000000f9    0
    000000f8    0
    000000f7    0
    000000f6    0
    000000f5    0
    000000f4    0
    000000f3    0
    000000f2    0
    000000f1    0
    000000f0    0
    000000ef    0
    000000ee    0
    000000ed   -2
    000000ec   -2
    000000eb    0
    000000ea    0
    000000dd    0 <==
```
System information:
    Wine build: wine-3.0.1
    Platform: i386 (WOW64)
    Version: Windows 7
    Host system: Linux
    Host version: 4.13.0-43-generic

---

### Post by jeremy31 on 2018-06-03
Moved to Wine subforum

---

