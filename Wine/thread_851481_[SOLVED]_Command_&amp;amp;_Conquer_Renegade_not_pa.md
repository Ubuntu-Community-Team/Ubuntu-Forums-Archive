---
title: "[SOLVED] Command &amp;amp; Conquer: Renegade not patching in wine"
date: 2008-07-06
forum: Wine
---

### Post by vandorjw on 2008-07-06
Can anyone help me sort this out?
Ubuntu Version: Feisty Fawn 7.04 (kernal (whole bunch of numbers).17
Wine Version 1.0

Renegade installed correctly from the cd-rom,  however I cannot update the game to version 1.037.

This is the error I get when I try and run the file using "wine Renegade_1037_English.exe"

> wine: Call from 0x7b841748 to unimplemented function msvcirt.dll.??0streambuf@@IAE@XZ, aborting
wine: Unimplemented function msvcirt.dll.??0streambuf@@IAE@XZ called at address 0x7b841748 (thread 0009), starting debugger...
Unhandled exception: unimplemented function msvcirt.dll.??0streambuf@@IAE@XZ called in 32-bit code (0x7b8417c2).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b8417c2 ESP:0032fd78 EBP:0032fddc EFLAGS:00200212(   - 00      - -IA1)
 EAX:7b82c1b9 EBX:7b8ae95c ECX:00000000 EDX:0032fdf4
 ESI:0032fdf4 EDI:00404014
Stack dump:
0x0032fd78:  0032fdf4 00000008 7ffd8000 80000100
0x0032fd88:  00000001 00000000 7b841748 00000002
0x0032fd98:  7eb439a4 7eb43efb 00000000 7bc32f4d
0x0032fda8:  7bc3258f 7eb95298 0032fdc0 7eb95298
0x0032fdb8:  00000009 000000fc 0032fe00 7eb7b204
0x0032fdc8:  7bc33013 7eb95298 7b841752 7eb95298
Backtrace:
=>1 0x7b8417c2 RaiseException+0x7a() in kernel32 (0x0032fddc)
  2 0x7eb43951 in msvcirt (+0x13951) (0x0032fdfc)
  3 0x7eb408a4 in msvcirt (+0x108a4) (0x0032fe58)
  4 0x0040200c in renegade_1037_english (+0x200c) (0x0032ff08)
  5 0x7b87087c in kernel32 (+0x5087c) (0x0032ffe8)
  6 0xb7dfe2af wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7b8417c2 RaiseException+0x7a in kernel32: subl        $4,%esp
Modules:
Module  Address                 Debug info      Name (50 modules)
PE        400000-  43e000       Export          renegade_1037_english
ELF     7b800000-7b929000       Export          kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca2000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca2000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e7a4000-7e7d7000       Deferred        uxtheme<elf>
  \-PE  7e7b0000-7e7d7000       \               uxtheme
ELF     7e7d7000-7e7e0000       Deferred        libxcursor.so.1
ELF     7e7e0000-7e7e5000       Deferred        libxfixes.so.3
ELF     7e7e5000-7e7e8000       Deferred        libxcomposite.so.1
ELF     7e7e8000-7e7ee000       Deferred        libxrandr.so.2
ELF     7e7ee000-7e7f6000       Deferred        libxrender.so.1
ELF     7e7f6000-7e816000       Deferred        imm32<elf>
  \-PE  7e800000-7e816000       \               imm32
ELF     7e816000-7e81b000       Deferred        libxdmcp.so.6
ELF     7e81b000-7e81e000       Deferred        libxau.so.6
ELF     7e81e000-7e90f000       Deferred        libx11.so.6
ELF     7e90f000-7e91d000       Deferred        libxext.so.6
ELF     7e91d000-7e922000       Deferred        libxxf86vm.so.1
ELF     7e922000-7e93a000       Deferred        libice.so.6
ELF     7e93a000-7e943000       Deferred        libsm.so.6
ELF     7e94f000-7e9e3000       Deferred        winex11<elf>
  \-PE  7e960000-7e9e3000       \               winex11
ELF     7ea4c000-7ea6c000       Deferred        libexpat.so.1
ELF     7ea6c000-7ea97000       Deferred        libfontconfig.so.1
ELF     7eaa3000-7eab7000       Deferred        libz.so.1
ELF     7eab7000-7eb22000       Deferred        libfreetype.so.6
ELF     7eb2e000-7eb4b000       Export          msvcirt<elf>
  \-PE  7eb30000-7eb4b000       \               msvcirt
ELF     7eb4b000-7ebb0000       Deferred        msvcrt<elf>
  \-PE  7eb60000-7ebb0000       \               msvcrt
ELF     7ebb0000-7ec70000       Deferred        comctl32<elf>
  \-PE  7ebc0000-7ec70000       \               comctl32
ELF     7ec70000-7ecbf000       Deferred        advapi32<elf>
  \-PE  7ec80000-7ecbf000       \               advapi32
ELF     7ecbf000-7ed58000       Deferred        gdi32<elf>
  \-PE  7ecd0000-7ed58000       \               gdi32
ELF     7ed58000-7ee99000       Deferred        user32<elf>
  \-PE  7ed70000-7ee99000       \               user32
ELF     7efab000-7efb6000       Deferred        libnss_files.so.2
ELF     7efb6000-7efcd000       Deferred        libnsl.so.1
ELF     7efcd000-7eff4000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7c84000-b7c8d000       Deferred        libnss_compat.so.2
ELF     b7c8e000-b7c92000       Deferred        libdl.so.2
ELF     b7c92000-b7dd3000       Deferred        libc.so.6
ELF     b7dd4000-b7deb000       Deferred        libpthread.so.0
ELF     b7df7000-b7f2c000       Export          libwine.so.1
ELF     b7f2e000-b7f49000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Westwood\Renegade_1037_English.exe
        00000009    0 <==
0000000c 
        00000013    0
        00000012    0
        0000000e    0
        0000000d    0
0000000f 
        00000015    0
        00000014    0
        00000011    0
        00000010    0
Backtrace:
=>1 0x7b8417c2 RaiseException+0x7a() in kernel32 (0x0032fddc)
  2 0x7eb43951 in msvcirt (+0x13951) (0x0032fdfc)
  3 0x7eb408a4 in msvcirt (+0x108a4) (0x0032fe58)
  4 0x0040200c in renegade_1037_english (+0x200c) (0x0032ff08)
  5 0x7b87087c in kernel32 (+0x5087c) (0x0032ffe8)
  6 0xb7dfe2af wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
wine: Call from 0x7b841748 to unimplemented function msvcirt.dll.??0streambuf@@QAE@ABV0@@Z, aborting



Thanks in advance

PS: I know that this game works on Ubuntu, because my brother has it on is laptop using Xubuntu 8.04, however, he doesn't know how to fix this problem either.

---

### Post by vandorjw on 2008-07-08
hey,
It is working now,

To get this bug to go away follow these steps.
1) download msvcirt.dll from [http://www.dll-files.com/dllindex/dll-files.shtml?msvcirt](http://www.dll-files.com/dllindex/dll-files.shtml?msvcirt)
2) run winecfg and under libaries override msvcirt and set it to native.

place the dll file that you recently downloaded in ~/.wine/windows/system32

PS: rename the one that already exists as msvcirt_buildIN.dll
(it might be important in the future)

Cheers - CC7

---

