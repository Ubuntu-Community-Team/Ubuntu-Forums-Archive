---
title: "&quot;Terraria has encountered a serious problem&quot;"
date: 2012-05-05
forum: Wine
---

### Post by samiscool30 on 2012-05-05
After i installed dotnet40 for Terraria, it got this error after i tried to play it:

Unhandled exception: 0xe0434352 in 32-bit code (0x7b839cf2).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b839cf2 ESP:0033e100 EBP:0033e164 EFLAGS:00200203(   - --  I   - - -C)
 EAX:7b826245 EBX:7b895ff4 ECX:79140000 EDX:0033e134
 ESI:e0434352 EDI:0013cbd8
Stack dump:
0x0033e100:  0033e1c0 00000014 79157a53 e0434352
0x0033e110:  00000001 00000000 7b839cf2 00000005
0x0033e120:  80070002 00000000 00000000 00000000
0x0033e130:  79140000 79150579 0033e148 02000059
0x0033e140:  0033e14c 7915bc5e 003fc828 0033e15c
0x0033e150:  791ca99c 038a79e8 7b839caa 00000005
Backtrace:
=>0 0x7b839cf2 in kernel32 (+0x29cf2) (0x0033e164)
  1 0x791cac08 in clr (+0x8ac07) (0x0033e1f4)
  2 0x7923ab0b in clr (+0xfab0a) (0x0033e230)
  3 0x7940bc8d in clr (+0x2cbc8c) (0x0033e288 )
  4 0x79817e0e in clrjit (+0x7e0d) (0x0033e2b0)
  5 0x7982d342 in clrjit (+0x1d341) (0x0033e9a 8 )
  6 0x79812d28 in clrjit (+0x2d27) (0x0033ea24)
  7 0x79812e58 in clrjit (+0x2e57) (0x0033ea3c)
  8 0x79812ea2 in clrjit (+0x2ea1) (0x0033ea58)
  9 0x798132a2 in clrjit (+0x32a1) (0x0033ea94)
  10 0x79813396 in clrjit (+0x3395) (0x0033eb04)
  11 0x798134c9 in clrjit (+0x34c8 ) (0x0033ebe0)
  12 0x79815e4b in clrjit (+0x5e4a) (0x0033ec04)
  13 0x791af7f1 in clr (+0x6f7f0) (0x0033ec6c)
  14 0x791af87d in clr (+0x6f87c) (0x0033ecb4)
  15 0x791af8c3 in clr (+0x6f8c2) (0x0033ed1c)
  16 0x791af698 in clr (+0x6f697) (0x0033f0d8)
  17 0x792137d3 in clr (+0xd37d2) (0x0033f1b8)
  18 0x79213980 in clr (+0xd397f) (0x0033f228)
  19 0x79161f55 in clr (+0x21f54) (0x0033f28c)
  20 0x00b1c1c2 (0x0033f2a4)
  21 0x791421db in clr (+0x21da) (0x0033f2d4)
  22 0x79164a2a in clr (+0x24a29) (0x0033f350)
  23 0x79164bcc in clr (+0x24bcb) (0x0033f490)
  24 0x79164c01 in clr (+0x24c00) (0x0033f4ac)
  25 0x79164c21 in clr (+0x24c20) (0x0033f4c4)
  26 0x7922ce82 in clr (+0xece81) (0x0033f628)
  27 0x7922cf90 in clr (+0xecf8f) (0x0033f890)
  28 0x7922cda4 in clr (+0xecda3) (0x0033fd74)
  29 0x7922d199 in clr (+0xed198) (0x0033fdc8)
  30 0x7922d09a in clr (+0xed099) (0x0033fe14)
  31 0x792aaf00 in clr (+0x16aeff) (0x0033fe4c)
  32 0x603b55ab in mscoreei (+0x55aa) (0x0033fe58 )
  33 0x79007f16 in mscoree (+0x7f15) (0x0033fe68)
  34 0x79004de3 in mscoree (+0x4de2) (0x0033fe88 )
  35 0x7b85af4f in kernel32 (+0x4af4e) (0x0033fec8 )
  36 0x7bc71da0 call_thread_func_wrapper+0xb() in ntdll (0x0033fed8 )
  37 0x7bc7485d call_thread_func+0x7c() in ntdll (0x0033ffa8 )
  38 0x7bc71d7e RtlRaiseException+0x21() in ntdll (0x0033ffc8 )
  39 0x7bc49f4e call_dll_entry_point+0x61d() in ntdll (0x0033ffe8 )
0x7b839cf2: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (63 modules)
PE      400000-  5cc000    Deferred        terraria
ELF    20000000-2008d000    Deferred        msvcrt<elf>
  \-PE    20010000-2008d000    \               msvcrt
ELF    2008d000-201c3000    Deferred        libx11.so.6
ELF    201c3000-201dd000    Deferred        libice.so.6
ELF    201dd000-201e3000    Deferred        libuuid.so.1
ELF    201e3000-20202000    Deferred        libxcb.so.1
ELF    20202000-20237000    Deferred        libfontconfig.so.1
ELF    20237000-20242000    Deferred        libxcursor.so.1
ELF    20242000-20248000    Deferred        libxfixes.so.3
ELF    20248000-20350000    Deferred        ole32<elf>
  \-PE    20260000-20350000    \               ole32
ELF    22d1c000-22e5c000    Deferred        user32<elf>
  \-PE    22d30000-22e5c000    \               user32
ELF    28f10000-28f14000    Deferred        libxcomposite.so.1
ELF    3192c000-31941000    Deferred        libz.so.1
ELF    32891000-32895000    Deferred        libxau.so.6
ELF    3d3b3000-3d3bc000    Deferred        libsm.so.6
ELF    44765000-44775000    Deferred        libxi.so.6
ELF    447d9000-447dd000    Deferred        libxinerama.so.1
ELF    4a720000-4a729000    Deferred        libxrandr.so.2
ELF    4c66c000-4c67f000    Deferred        libxext.so.6
ELF    51cb9000-51cc4000    Deferred        libxrender.so.1
ELF    5244b000-524de000    Deferred        winex11<elf>
  \-PE    52460000-524de000    \               winex11
ELF    5743b000-57442000    Deferred        libxdmcp.so.6
ELF    5b841000-5b8d8000    Deferred        libfreetype.so.6
PE    5e0d0000-5e17a000    Deferred        diasymreader
PE    60340000-6034d000    Deferred        culture
PE    603b0000-60416000    Export          mscoreei
PE    60930000-60940000    Deferred        nlssorting
ELF    67754000-6777e000    Deferred        libexpat.so.1
ELF    68000000-68020000    Deferred        ld-linux.so.2
ELF    68020000-68162000    Dwarf           libwine.so.1
ELF    68162000-6817d000    Deferred        libpthread.so.0
ELF    6817d000-68182000    Deferred        libdl.so.2
ELF    68182000-6819b000    Deferred        libnsl.so.1
ELF    6819b000-681a8000    Deferred        libnss_files.so.2
ELF    696c8000-69846000    Deferred        libc.so.6
ELF    69a2a000-69a30000    Deferred        libxxf86vm.so.1
ELF    6ade9000-6ae0b000    Deferred        imm32<elf>
  \-PE    6adf0000-6ae0b000    \               imm32
ELF    6df66000-6dfc7000    Deferred        advapi32<elf>
  \-PE    6df70000-6dfc7000    \               advapi32
PE    70bd0000-70c34000    Deferred        shlwapi
ELF    712f4000-7130d000    Deferred        version<elf>
  \-PE    71300000-7130d000    \               version
ELF    71ff5000-71fff000    Deferred        libnss_compat.so.2
ELF    72c6c000-72d29000    Deferred        gdi32<elf>
  \-PE    72c80000-72d29000    \               gdi32
ELF    73c0c000-73c18000    Deferred        libnss_nis.so.2
ELF    76075000-760eb000    Deferred        rpcrt4<elf>
  \-PE    76080000-760eb000    \               rpcrt4
ELF    7856b000-78595000    Deferred        libm.so.6
PE    79000000-7904a000    Export          mscoree
PE    79060000-7911e000    Deferred        msvcr100_clr0400
PE    79140000-797af000    Export          clr
PE    79810000-79870000    Export          clrjit
ELF    7b800000-7ba16000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba16000    \               kernel32
ELF    7bc00000-7bcc3000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcc3000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    00000027    0
    00000026    0
    0000001f    0
    0000001b    0
    00000019    0
    00000010    0
    0000000f    0
00000014 explorer.exe
    00000015    0
0000001c winedevice.exe
    00000024    0
    00000021    0
    0000001e    0
    0000001d    0
00000022 plugplay.exe
    00000028    0
    00000025    0
    00000023    0
00000029 (D) C:\Program Files\Terraria 1.1.2\Terraria.exe
    0000002c    2
    0000002b    0
    0000002a    0 <==
0000002f wineconsole.exe
    00000030    0
System information:
    Wine build: wine-1.4
    Platform: i386
    Host system: Linux
    Host version: 3.0.0-19-generic

Any help would be great. Plus the smileys is the numbers 8 and ) since the forums automatically recognizes it as a smiley.

---

### Post by *^kyfds( on 2012-05-05
that's a kernel panic, isn't it?

which version of ubuntu are you running?

---

### Post by samiscool30 on 2012-05-05
> **Thehumorouscheese said:**
> that's a kernel panic, isn't it?

which version of ubuntu are you running?
 I am using 11.10

---

### Post by samiscool30 on 2012-05-05
I now get the error "CLR error: 80004005   The Program will now terminate"  I got this error when i tried to run it through dosdevices, before i tried running it through drive_c

---

### Post by AlwaysLearning on 2012-05-13
> **samiscool30 said:**
> After i installed dotnet40 for Terraria, it got this error after i tried to play it:

Unhandled exception: 0xe0434352 in 32-bit code (0x7b839cf2).
Register dump:
...
Any help would be great. Plus the smileys is the numbers 8 and ) since the forums automatically recognizes it as a smiley.

I had the exact error message today.

Turns out that in the last couple of months where I haven't been playing Terraria I'd moved my Steam's WINEPREFIX to a new folder. As a result, all of the softlinks I'd created to .NET Framework 4.0 files and the XNA files in the $WINEPREFIX/drive_c/Program Files/Steam/steamapps/common/terraria folder were broken. Once I deleted the softlinks and recreated them pointing at the new locations everything started working again.

Hope this helps,
A.L.

---

