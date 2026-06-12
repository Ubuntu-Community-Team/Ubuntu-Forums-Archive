---
title: "(WINE) Full Tilt Poker doesn't open correctly"
date: 2007-09-06
forum: Wine
---

### Post by bohsocks on 2007-09-06
Hey guys.  I just did a fresh install of Feisty Fawn and installed WINE 0.9.41.  Everything goes swimmingly until I try to run Full Tilt Poker.  It installed perfectly, and I enabled the libraries recommended in this guide:

[http://www.mattahfahtu.com/2007/02/20/howto-install-and-use-poker-clients-under-linux-with-wine/](http://www.mattahfahtu.com/2007/02/20/howto-install-and-use-poker-clients-under-linux-with-wine/)

(oile32 and riche20)

The splash/connecting box for FTP comes up, then program abruptly closes.  I ran it in terminal, and this is what happens:

```

rob@rob-laptop:~$ env WINEPREFIX="/home/rob/.wine" wine "C:\Program Files\Full Tilt Poker\FullTiltPoker.exe"
fixme:actctx:FindActCtxSectionStringW 00000000 (null) 2 L"msvcr80.dll" 0x337b6c
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
wine: Unhandled page fault on write access to 0x00000000 at address 0xb7da734c (thread 000e), starting debugger...
Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0xb7da734c).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7da734c ESP:7b6062e0 EBP:7b60638c EFLAGS:00210202(   - 00      - -RI1)
 EAX:00000186 EBX:7e5b9714 ECX:00000062 EDX:000000c3
 ESI:0273e928 EDI:00000000
Stack dump:
0x7b6062e0:  7e598ddb 00000000 0273e928 00000188
0x7b6062f0:  00110000 0272c738 00000000 20020000
0x7b606300:  00000000 10060000 7b606358 7bc380ff
0x7b606310:  7bc7b498 2001e208 2001e238 2001ffe8
0x7b606320:  10060018 7fffffff 3007e228 00000000
0x7b606330:  00000000 00110000 02710000 7bc29ec1
Backtrace:
=>1 0xb7da734c memcpy+0x1c() in libc.so.6 (0x7b60638c)
  2 0x7e599f2d HttpQueryInfoW+0x1cd() in wininet (0x7b6063cc)
  3 0x7e59a420 HttpQueryInfoA+0xc0() in wininet (0x7b60641c)
  4 0x0047aaf6 in fulltiltpoker (+0x7aaf6) (0x02754f30)
  5 0x00110040 (0x00110050)
  6 0x00110040 (0x02754c28)
  7 0x00110050 (0x02779718)
  8 0x02754c28 (0x02744048)
  9 0x02779718 (0x00174288)
  10 0x02744048 (0x00110060)
  11 0x00174288 (0x02755068)
  12 0x00110060 (0x00110070)
  13 0x02755068 (0x027388f8)
  14 0x00110070 (0x0277ad78)
  15 0x027388f8 (0x00110080)
  16 0x0277ad78 (0x00110090)
  17 0x00110080 (0x001100a0)
  18 0x00110090 (0x02754df0)
  19 0x001100a0 (0x001100b0)
  20 0x02754df0 (0x02779768)
  21 0x001100b0 (0x02779928)
  22 0x02779768 (0x001100c0)
  23 0x02779928 (0x001100d0)
  24 0x001100c0 (0x001100e0)
  25 0x001100d0 (0x027551e8)
  26 0x001100e0 (0x0278bf50)
  27 0x027551e8 (0x00110040)
  28 0x0278bf50 (0x00110050)
  29 0x00110040 (0x02754c28)
  30 0x00110050 (0x02779718)
  31 0x02754c28 (0x02744048)
  32 0x02779718 (0x00174288)
  33 0x02744048 (0x00110060)
  34 0x00174288 (0x02755068)
  35 0x00110060 (0x00110070)
  36 0x02755068 (0x027388f8)
  37 0x00110070 (0x0277ad78)
  38 0x027388f8 (0x00110080)
  39 0x0277ad78 (0x00110090)
  40 0x00110080 (0x001100a0)
  41 0x00110090 (0x02754df0)
  42 0x001100a0 (0x001100b0)
  43 0x02754df0 (0x02779768)
  44 0x001100b0 (0x02779928)
  45 0x02779768 (0x001100c0)
  46 0x02779928 (0x001100d0)
  47 0x001100c0 (0x001100e0)
  48 0x001100d0 (0x027551e8)
  49 0x001100e0 (0x0278bf50)
  50 0x027551e8 (0x00110040)
  51 0x0278bf50 (0x00110050)
  52 0x00110040 (0x02754c28)
  53 0x00110050 (0x02779718)
  54 0x02754c28 (0x02744048)
  55 0x02779718 (0x00174288)
  56 0x02744048 (0x00110060)
  57 0x00174288 (0x02755068)
  58 0x00110060 (0x00110070)
  59 0x02755068 (0x027388f8)
  60 0x00110070 (0x0277ad78)
  61 0x027388f8 (0x00110080)
  62 0x0277ad78 (0x00110090)
  63 0x00110080 (0x001100a0)
  64 0x00110090 (0x02754df0)
  65 0x001100a0 (0x001100b0)
  66 0x02754df0 (0x02779768)
  67 0x001100b0 (0x02779928)
  68 0x02779768 (0x001100c0)
  69 0x02779928 (0x001100d0)
  70 0x001100c0 (0x001100e0)
  71 0x001100d0 (0x027551e8)
  72 0x001100e0 (0x0278bf50)
  73 0x027551e8 (0x00110040)
  74 0x0278bf50 (0x00110050)
  75 0x00110040 (0x02754c28)
  76 0x00110050 (0x02779718)
  77 0x02754c28 (0x02744048)
  78 0x02779718 (0x00174288)
  79 0x02744048 (0x00110060)
  80 0x00174288 (0x02755068)
  81 0x00110060 (0x00110070)
  82 0x02755068 (0x027388f8)
  83 0x00110070 (0x0277ad78)
  84 0x027388f8 (0x00110080)
  85 0x0277ad78 (0x00110090)
  86 0x00110080 (0x001100a0)
  87 0x00110090 (0x02754df0)
  88 0x001100a0 (0x001100b0)
  89 0x02754df0 (0x02779768)
  90 0x001100b0 (0x02779928)
  91 0x02779768 (0x001100c0)
  92 0x02779928 (0x001100d0)
  93 0x001100c0 (0x001100e0)
  94 0x001100d0 (0x027551e8)
  95 0x001100e0 (0x0278bf50)
  96 0x027551e8 (0x00110040)
  97 0x0278bf50 (0x00110050)
  98 0x00110040 (0x02754c28)
  99 0x00110050 (0x02779718)
  100 0x02754c28 (0x02744048)
  101 0x02779718 (0x00174288)
  102 0x02744048 (0x00110060)
  103 0x00174288 (0x02755068)
  104 0x00110060 (0x00110070)
  105 0x02755068 (0x027388f8)
  106 0x00110070 (0x0277ad78)
  107 0x027388f8 (0x00110080)
  108 0x0277ad78 (0x00110090)
  109 0x00110080 (0x001100a0)
  110 0x00110090 (0x02754df0)
  111 0x001100a0 (0x001100b0)
  112 0x02754df0 (0x02779768)
  113 0x001100b0 (0x02779928)
  114 0x02779768 (0x001100c0)
  115 0x02779928 (0x001100d0)
  116 0x001100c0 (0x001100e0)
  117 0x001100d0 (0x027551e8)
  118 0x001100e0 (0x0278bf50)
  119 0x027551e8 (0x00110040)
  120 0x0278bf50 (0x00110050)
  121 0x00110040 (0x02754c28)
  122 0x00110050 (0x02779718)
  123 0x02754c28 (0x02744048)
  124 0x02779718 (0x00174288)
  125 0x02744048 (0x00110060)
  126 0x00174288 (0x02755068)
  127 0x00110060 (0x00110070)
  128 0x02755068 (0x027388f8)
  129 0x00110070 (0x0277ad78)
  130 0x027388f8 (0x00110080)
  131 0x0277ad78 (0x00110090)
  132 0x00110080 (0x001100a0)
  133 0x00110090 (0x02754df0)
  134 0x001100a0 (0x001100b0)
  135 0x02754df0 (0x02779768)
  136 0x001100b0 (0x02779928)
  137 0x02779768 (0x001100c0)
  138 0x02779928 (0x001100d0)
  139 0x001100c0 (0x001100e0)
  140 0x001100d0 (0x027551e8)
  141 0x001100e0 (0x0278bf50)
  142 0x027551e8 (0x00110040)
  143 0x0278bf50 (0x00110050)
  144 0x00110040 (0x02754c28)
  145 0x00110050 (0x02779718)
  146 0x02754c28 (0x02744048)
  147 0x02779718 (0x00174288)
  148 0x02744048 (0x00110060)
  149 0x00174288 (0x02755068)
  150 0x00110060 (0x00110070)
  151 0x02755068 (0x027388f8)
  152 0x00110070 (0x0277ad78)
  153 0x027388f8 (0x00110080)
  154 0x0277ad78 (0x00110090)
  155 0x00110080 (0x001100a0)
  156 0x00110090 (0x02754df0)
  157 0x001100a0 (0x001100b0)
  158 0x02754df0 (0x02779768)
  159 0x001100b0 (0x02779928)
  160 0x02779768 (0x001100c0)
  161 0x02779928 (0x001100d0)
  162 0x001100c0 (0x001100e0)
  163 0x001100d0 (0x027551e8)
  164 0x001100e0 (0x0278bf50)
  165 0x027551e8 (0x00110040)
  166 0x0278bf50 (0x00110050)
  167 0x00110040 (0x02754c28)
  168 0x00110050 (0x02779718)
  169 0x02754c28 (0x02744048)
  170 0x02779718 (0x00174288)
  171 0x02744048 (0x00110060)
  172 0x00174288 (0x02755068)
  173 0x00110060 (0x00110070)
  174 0x02755068 (0x027388f8)
  175 0x00110070 (0x0277ad78)
  176 0x027388f8 (0x00110080)
  177 0x0277ad78 (0x00110090)
  178 0x00110080 (0x001100a0)
  179 0x00110090 (0x02754df0)
  180 0x001100a0 (0x001100b0)
  181 0x02754df0 (0x02779768)
  182 0x001100b0 (0x02779928)
  183 0x02779768 (0x001100c0)
  184 0x02779928 (0x001100d0)
  185 0x001100c0 (0x001100e0)
  186 0x001100d0 (0x027551e8)
  187 0x001100e0 (0x0278bf50)
  188 0x027551e8 (0x00110040)
  189 0x0278bf50 (0x00110050)
  190 0x00110040 (0x02754c28)
  191 0x00110050 (0x02779718)
  192 0x02754c28 (0x02744048)
  193 0x02779718 (0x00174288)
  194 0x02744048 (0x00110060)
  195 0x00174288 (0x02755068)
  196 0x00110060 (0x00110070)
  197 0x02755068 (0x027388f8)
  198 0x00110070 (0x0277ad78)
  199 0x027388f8 (0x00110080)
  200 0x0277ad78 (0x00110090)
  201 0x00110080 (0x001100a0)
0xb7da734c memcpy+0x1c in libc.so.6: repe movsl (%esi),%es:(%edi)
Modules:
Module  Address                 Debug info      Name (112 modules)
PE        340000-  3ea000       Deferred        libeay32
PE        400000-  56e000       Export          fulltiltpoker
PE        570000-  595000       Deferred        ssleay32
PE        5a0000-  5b3000       Deferred        zlib1-ft
PE        5c0000-  5e2000       Deferred        libpng
PE        5f0000-  60e000       Deferred        libjpeg
PE      10000000-10059000       Deferred        ftc_game
PE      78130000-781cb000       Deferred        msvcr80
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf22000-7bf3c000       Deferred        msrle32<elf>
  \-PE  7bf30000-7bf3c000       \               msrle32
ELF     7bf3c000-7bf63000       Deferred        msvfw32<elf>
  \-PE  7bf40000-7bf63000       \               msvfw32
ELF     7d487000-7d48d000       Deferred        libnss_dns.so.2
ELF     7d48d000-7d490000       Deferred        libnss_mdns4_minimal.so.2
ELF     7d490000-7d4d6000       Deferred        riched20<elf>
  \-PE  7d4a0000-7d4d6000       \               riched20
ELF     7d4d6000-7d4eb000       Deferred        midimap<elf>
  \-PE  7d4e0000-7d4eb000       \               midimap
ELF     7d4eb000-7d511000       Deferred        msacm32<elf>
  \-PE  7d4f0000-7d511000       \               msacm32
ELF     7d511000-7d529000       Deferred        msacm32<elf>
  \-PE  7d520000-7d529000       \               msacm32
ELF     7d529000-7d565000       Deferred        wineoss<elf>
  \-PE  7d530000-7d565000       \               wineoss
ELF     7d565000-7d5b6000       Deferred        libgcrypt.so.11
ELF     7d5b6000-7d5cb000       Deferred        libtasn1.so.3
ELF     7d5cb000-7d5f9000       Deferred        libcrypt.so.1
ELF     7d608000-7d678000       Deferred        libgnutls.so.13
ELF     7d678000-7d6a9000       Deferred        libcups.so.2
ELF     7d6d7000-7d6db000       Deferred        libgpg-error.so.0
ELF     7d765000-7d797000       Deferred        uxtheme<elf>
  \-PE  7d770000-7d797000       \               uxtheme
ELF     7d799000-7d79e000       Deferred        libxfixes.so.3
ELF     7d79e000-7d7a7000       Deferred        libxcursor.so.1
ELF     7d7a7000-7d7c4000       Deferred        imm32<elf>
  \-PE  7d7b0000-7d7c4000       \               imm32
ELF     7d7c4000-7d7ca000       Deferred        libxrandr.so.2
ELF     7d7ca000-7d7d2000       Deferred        libxrender.so.1
ELF     7d7d2000-7d7d5000       Deferred        libxinerama.so.1
ELF     7dec7000-7e13c000       Deferred        r200_dri.so
ELF     7e13c000-7e145000       Deferred        libdrm.so.2
ELF     7e145000-7e1a5000       Deferred        libgl.so.1
ELF     7e1a5000-7e1aa000       Deferred        libxdmcp.so.6
ELF     7e1aa000-7e1ad000       Deferred        libxau.so.6
ELF     7e1ad000-7e29e000       Deferred        libx11.so.6
ELF     7e29e000-7e2ac000       Deferred        libxext.so.6
ELF     7e2ac000-7e2b1000       Deferred        libxxf86vm.so.1
ELF     7e2b1000-7e2c9000       Deferred        libice.so.6
ELF     7e2c9000-7e2d2000       Deferred        libsm.so.6
ELF     7e2d2000-7e362000       Deferred        winex11<elf>
  \-PE  7e2e0000-7e362000       \               winex11
ELF     7e3e6000-7e406000       Deferred        libexpat.so.1
ELF     7e406000-7e431000       Deferred        libfontconfig.so.1
ELF     7e431000-7e445000       Deferred        libz.so.1
ELF     7e445000-7e4b5000       Deferred        libfreetype.so.6
ELF     7e4b5000-7e543000       Deferred        winmm<elf>
  \-PE  7e4c0000-7e543000       \               winmm
ELF     7e543000-7e557000       Deferred        msimg32<elf>
  \-PE  7e550000-7e557000       \               msimg32
ELF     7e557000-7e577000       Deferred        mpr<elf>
  \-PE  7e560000-7e577000       \               mpr
ELF     7e577000-7e5c0000       Export          wininet<elf>
  \-PE  7e580000-7e5c0000       \               wininet
ELF     7e5c0000-7e65e000       Deferred        oleaut32<elf>
  \-PE  7e5d0000-7e65e000       \               oleaut32
ELF     7e65e000-7e6b7000       Deferred        rpcrt4<elf>
  \-PE  7e670000-7e6b7000       \               rpcrt4
ELF     7e6b7000-7e756000       Deferred        ole32<elf>
  \-PE  7e6d0000-7e756000       \               ole32
ELF     7e756000-7e789000       Deferred        winspool<elf>
  \-PE  7e760000-7e789000       \               winspool
ELF     7e789000-7e7e2000       Deferred        shlwapi<elf>
  \-PE  7e7a0000-7e7e2000       \               shlwapi
ELF     7e7e2000-7e8e0000       Deferred        shell32<elf>
  \-PE  7e7f0000-7e8e0000       \               shell32
ELF     7e8e0000-7e981000       Deferred        comdlg32<elf>
  \-PE  7e8f0000-7e981000       \               comdlg32
ELF     7e981000-7e99b000       Deferred        wsock32<elf>
  \-PE  7e990000-7e99b000       \               wsock32
ELF     7e99b000-7e9c0000       Deferred        netapi32<elf>
  \-PE  7e9a0000-7e9c0000       \               netapi32
ELF     7e9c0000-7e9d3000       Deferred        libresolv.so.2
ELF     7e9d3000-7e9f1000       Deferred        iphlpapi<elf>
  \-PE  7e9e0000-7e9f1000       \               iphlpapi
ELF     7e9f1000-7ea1e000       Deferred        ws2_32<elf>
  \-PE  7ea00000-7ea1e000       \               ws2_32
ELF     7ea1e000-7ea85000       Deferred        msvcrt<elf>
  \-PE  7ea30000-7ea85000       \               msvcrt
ELF     7ea85000-7eacd000       Deferred        advapi32<elf>
  \-PE  7ea90000-7eacd000       \               advapi32
ELF     7eacd000-7ead9000       Deferred        libgcc_s.so.1
ELF     7ebd2000-7ec92000       Deferred        gdi32<elf>
  \-PE  7ebf0000-7ec92000       \               gdi32
ELF     7ec92000-7edcf000       Deferred        user32<elf>
  \-PE  7ecb0000-7edcf000       \               user32
ELF     7edcf000-7ee8c000       Deferred        comctl32<elf>
  \-PE  7ede0000-7ee8c000       \               comctl32
ELF     7ef9e000-7efa9000       Deferred        libnss_files.so.2
ELF     7efa9000-7efb3000       Deferred        libnss_nis.so.2
ELF     7efb3000-7efca000       Deferred        libnsl.so.1
ELF     7efca000-7eff1000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7d34000-b7d38000       Deferred        libdl.so.2
ELF     b7d38000-b7e79000       Export          libc.so.6
ELF     b7e7a000-b7e91000       Deferred        libpthread.so.0
ELF     b7ea0000-b7fb4000       Deferred        libwine.so.1
ELF     b7fb6000-b7fd1000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\Full Tilt Poker\FullTiltPoker.exe
        00000013    0
        00000012    0
        0000000f    0
        0000000e    0 <==
        0000000d    0
        00000009    0

```

Any thoughts?  

I search on these forums and didn't find anything similar to this... though I myself can't find the issue in that output that tells me the problem....

Please help!

---

### Post by bohsocks on 2007-09-07
bump

---

### Post by bohsocks on 2007-09-07
wine: Unhandled page fault on write access to 0x00000000 at address 0xb7da734c (thread 000e), starting debugger...
Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0xb7da734c).

?

---

### Post by bohsocks on 2007-09-07
Sigh.... am I blacklisted or something?  Almost all of my threads get the silent treatment

---

### Post by Hyperkill on 2007-09-08
I have FTP up and running pretty good without enabling those library files.  I just downloaded it and ran the install package using wine.  Then I installed the microsoft font package and now everything works pretty well.  The only problem I have is with sound going out every once in a while.

---

### Post by bohsocks on 2007-09-08
Well it worked fine in my last installs.... but for some reason now it won't open.....

it's the damndest thing....

anyone know what the error means?

---

### Post by bohsocks on 2007-09-10
Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump

---

