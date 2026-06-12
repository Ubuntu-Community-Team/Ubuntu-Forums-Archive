---
title: "WINE won't start (Program Error)"
date: 2012-11-22
forum: Wine
---

### Post by khatzmaniadevil on 2012-11-22
I was playing with wine when it suddenly stuck up. I tried to stop all wine processes in the System Monitor tool. When I tried to start wine, it says "The program (unidenified) has encountered a serious problem and needs to close...".

I tried reinstalling it but it gives me the same error.

Here's the program error details:

Unhandled exception: unimplemented function shell32.dll.SHGetFolderPathW called in 32-bit code (0x7b839d82).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b839d82 ESP:0033ed14 EBP:0033ed78 EFLAGS:00200283(   - --  I S - - -C)
 EAX:7b826255 EBX:7b894ff4 ECX:00000008 EDX:0033ed3c
 ESI:80000100 EDI:7ed7d958
Stack dump:
0x0033ed14:  0033eda8 00000008 7ed7cff4 80000100
0x0033ed24:  00000001 00000000 7b839d82 00000002
0x0033ed34:  7ed7d958 7ed7d99a 0033ed4c 7ed7d964
0x0033ed44:  00150014 7ed7d9e0 7b854360 00000001
0x0033ed54:  00000020 0033edb8 7ed74971 7eca0000
0x0033ed64:  7ed7d9e0 000c000b 7b839d3a 7b894ff4
Backtrace:
=>0 0x7b839d82 in kernel32 (+0x29d82) (0x0033ed78
  1 0x7b8543bb DelayLoadFailureHook+0x5a() in kernel32 (0x0033edc8
  2 0x7ed749f1 in wineboot (+0x149f0) (0x0033ee28
  3 0x7ed70000 in wineboot (+0xffff) (0x0033fe28
  4 0x7ed72be2 main+0xe31() in wineboot (0x0033fe28
  5 0x7ed74acc in wineboot (+0x14acb) (0x0033fe70)
  6 0x7b859ddc call_process_entry+0xb() in kernel32 (0x0033fe88
  7 0x7b85b04f in kernel32 (+0x4b04e) (0x0033fec8
  8 0x7bc71d90 call_thread_func_wrapper+0xb() in ntdll (0x0033fed8
  9 0x7bc7486d call_thread_func+0x7c() in ntdll (0x0033ffa8
  10 0x7bc71d6e RtlRaiseException+0x21() in ntdll (0x0033ffc8
  11 0x7bc49f4e call_dll_entry_point+0x61d() in ntdll (0x0033ffe8
0x7b839d82: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (48 modules)
ELF    7b800000-7ba29000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba29000    \               kernel32
ELF    7bc00000-7bcc3000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcc3000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7e355000-7e35b000    Deferred        libxfixes.so.3
ELF    7e35b000-7e366000    Deferred        libxcursor.so.1
ELF    7e366000-7e376000    Deferred        libxi.so.6
ELF    7e376000-7e37a000    Deferred        libxcomposite.so.1
ELF    7e37a000-7e383000    Deferred        libxrandr.so.2
ELF    7e383000-7e38d000    Deferred        libxrender.so.1
ELF    7e38d000-7e393000    Deferred        libxxf86vm.so.1
ELF    7e393000-7e397000    Deferred        libxinerama.so.1
ELF    7e397000-7e3b9000    Deferred        imm32<elf>
  \-PE    7e3a0000-7e3b9000    \               imm32
ELF    7e3b9000-7e3c0000    Deferred        libxdmcp.so.6
ELF    7e3c0000-7e3c4000    Deferred        libxau.so.6
ELF    7e3c4000-7e3e5000    Deferred        libxcb.so.1
ELF    7e3e5000-7e3eb000    Deferred        libuuid.so.1
ELF    7e3eb000-7e405000    Deferred        libice.so.6
ELF    7e405000-7e539000    Deferred        libx11.so.6
ELF    7e539000-7e54b000    Deferred        libxext.so.6
ELF    7e54b000-7e554000    Deferred        libsm.so.6
ELF    7e56e000-7e602000    Deferred        winex11<elf>
  \-PE    7e580000-7e602000    \               winex11
ELF    7e648000-7e672000    Deferred        libexpat.so.1
ELF    7e672000-7e6a6000    Deferred        libfontconfig.so.1
ELF    7e6a6000-7e6bc000    Deferred        libz.so.1
ELF    7e6bc000-7e756000    Deferred        libfreetype.so.6
ELF    7e869000-7e882000    Deferred        version<elf>
  \-PE    7e870000-7e882000    \               version
ELF    7e882000-7e93f000    Deferred        gdi32<elf>
  \-PE    7e890000-7e93f000    \               gdi32
ELF    7e93f000-7ea7f000    Deferred        user32<elf>
  \-PE    7e950000-7ea7f000    \               user32
ELF    7ec92000-7ecfc000    Deferred        shlwapi<elf>
  \-PE    7eca0000-7ecfc000    \               shlwapi
ELF    7ecfc000-7ed5e000    Deferred        advapi32<elf>
  \-PE    7ed10000-7ed5e000    \               advapi32
ELF    7ed5e000-7ed85000    Dwarf           wineboot<elf>
  \-PE    7ed60000-7ed85000    \               wineboot
ELF    7efba000-7efe6000    Deferred        libm.so.6
ELF    b74a1000-b74a6000    Deferred        libdl.so.2
ELF    b74a6000-b7650000    Deferred        libc.so.6
ELF    b7651000-b766c000    Deferred        libpthread.so.0
ELF    b7686000-b77c8000    Dwarf           libwine.so.1
ELF    b77ca000-b77ec000    Deferred        ld-linux.so.2
ELF    b77ec000-b77ed000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000a (D) C:\windows\system32\wineboot.exe
    0000000b    0 <==
System information:
    Wine build: wine-1.4.1
    Platform: i386
    Host system: Linux
    Host version: 3.2.0-33-generic-pae

Any help is much appreciated. Thanks!

---

