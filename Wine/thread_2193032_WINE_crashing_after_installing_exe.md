---
title: "WINE crashing after installing exe"
date: 2013-12-10
forum: Wine
---

### Post by Kymus on 2013-12-10
I'm running a fresh install of Ubuntu 13.04 (ok, well, backup, format, and a pasting of my home folder). Installed WINE no problem. Not to install some windows programs.. 

Everything goes through fine until right at the end of the installation, then WINE crashes. I've done this with two different programs, I've resetted, I've tried again; still the same problem.

This is the program error details:

```
Unhandled exception: unimplemented function urlmon.dll.CreateUri called in 32-bit code (0x7bc4db42).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7bc4db42 ESP:0033fd20 EBP:0033fd84 EFLAGS:00000216(   - --  I   -A-P- )
 EAX:0033fd2c EBX:7bcc8000 ECX:00131070 EDX:ffffffff
 ESI:7ffd8000 EDI:00000000
Stack dump:
0x0033fd20:  0000c000 00007fff 001359ba 80000100
0x0033fd30:  00000001 00000000 7bc4db42 00000002
0x0033fd40:  7efff498 7efff2d6 00000000 00000000
0x0033fd50:  00000000 00000000 f75dd6ff f7410000
0x0033fd60:  00135a26 f75dde5f 00000000 0005009c
0x0033fd70:  000003e8 0006002e 0013105a 00004d89
Backtrace:
=>0 0x7bc4db42 call_dll_entry_point+0x66() in ntdll (0x0033fd84)
  1 0x0034001e (0x0033fe10)
  2 0x7effd21a in winebrowser (+0xd219) (0x0033fe40)
  3 0x7b8621c8 call_process_entry+0xb() in kernel32 (0x0033fe58)
  4 0x7b86230e call_process_entry+0x151() in kernel32 (0x0033fea8)
  5 0x7bc7f84c call_thread_func_wrapper+0xb() in ntdll (0x0033feb8)
  6 0x7bc7f89b call_thread_func+0x44() in ntdll (0x0033ff98)
  7 0x7bc7f82a in ntdll (+0x6f829) (0x0033ffb8)
  8 0x7bc54b97 in ntdll (+0x44b96) (0x0033ffe8)
  9 0xf75dcc19 wine_call_on_stack+0x1c() in libwine.so.1 (0x00000000)
  10 0xf75dcbf7 wine_switch_to_stack+0x2a() in libwine.so.1 (0xfffc94b8)
  11 0x7bc54ed9 LdrInitializeThunk+0x341() in ntdll (0xfffc9538)
  12 0x7b862be7 __wine_kernel_init+0x71b() in kernel32 (0xfffca3c8)
  13 0x7bc5566e __wine_process_init+0x156() in ntdll (0xfffca418)
  14 0xf75db446 wine_init+0x13d() in libwine.so.1 (0xfffca458)
  15 0x7bf011ca main+0x13d() in <wine-loader> (0xfffca898)
  16 0xf7404935 __libc_start_main+0xf4() in libc.so.6 (0x00000000)
0x7bc4db42 call_dll_entry_point+0x66 in ntdll: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (64 modules)
PE    702b0000-70328000    Deferred        urlmon
PE    70bd0000-70c34000    Deferred        shlwapi
ELF    7b800000-7ba44000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba44000    \               kernel32
ELF    7bc00000-7bce4000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bce4000    \               ntdll
ELF    7bf00000-7bf04000    Dwarf           <wine-loader>
ELF    7dfbd000-7dff4000    Deferred        uxtheme<elf>
  \-PE    7dfc0000-7dff4000    \               uxtheme
ELF    7dff4000-7e113000    Deferred        comctl32<elf>
  \-PE    7e000000-7e113000    \               comctl32
ELF    7e113000-7e11a000    Deferred        libxfixes.so.3
ELF    7e11a000-7e125000    Deferred        libxcursor.so.1
ELF    7e17b000-7e1a3000    Deferred        libexpat.so.1
ELF    7e1a3000-7e1dc000    Deferred        libfontconfig.so.1
ELF    7e1dc000-7e1ec000    Deferred        libxi.so.6
ELF    7e1ec000-7e1f0000    Deferred        libxcomposite.so.1
ELF    7e1f0000-7e1fb000    Deferred        libxrandr.so.2
ELF    7e1fb000-7e205000    Deferred        libxrender.so.1
ELF    7e205000-7e20b000    Deferred        libxxf86vm.so.1
ELF    7e20b000-7e22f000    Deferred        imm32<elf>
  \-PE    7e210000-7e22f000    \               imm32
ELF    7e22f000-7e236000    Deferred        libxdmcp.so.6
ELF    7e236000-7e258000    Deferred        libxcb.so.1
ELF    7e258000-7e25e000    Deferred        libuuid.so.1
ELF    7e25e000-7e278000    Deferred        libice.so.6
ELF    7e278000-7e3af000    Deferred        libx11.so.6
ELF    7e3af000-7e3c1000    Deferred        libxext.so.6
ELF    7e3c1000-7e3ca000    Deferred        libsm.so.6
ELF    7e3ca000-7e47b000    Deferred        winex11<elf>
  \-PE    7e3d0000-7e47b000    \               winex11
ELF    7e47b000-7e494000    Deferred        libz.so.1
ELF    7e494000-7e52f000    Deferred        libfreetype.so.6
ELF    7e548000-7e68d000    Deferred        oleaut32<elf>
  \-PE    7e560000-7e68d000    \               oleaut32
ELF    7e68d000-7e72f000    Deferred        msvcrt<elf>
  \-PE    7e6a0000-7e72f000    \               msvcrt
ELF    7e72f000-7e7b9000    Deferred        rpcrt4<elf>
  \-PE    7e740000-7e7b9000    \               rpcrt4
ELF    7e7b9000-7e7d4000    Deferred        version<elf>
  \-PE    7e7c0000-7e7d4000    \               version
ELF    7e7d4000-7e944000    Deferred        user32<elf>
  \-PE    7e7f0000-7e944000    \               user32
ELF    7e944000-7eaa6000    Deferred        ole32<elf>
  \-PE    7e960000-7eaa6000    \               ole32
ELF    7eaa6000-7eb87000    Deferred        gdi32<elf>
  \-PE    7eab0000-7eb87000    \               gdi32
ELF    7eb87000-7ebf9000    Deferred        advapi32<elf>
  \-PE    7eb90000-7ebf9000    \               advapi32
ELF    7ebf9000-7ec06000    Deferred        libnss_files.so.2
ELF    7ec06000-7ec12000    Deferred        libnss_nis.so.2
ELF    7ec12000-7ec2b000    Deferred        libnsl.so.1
ELF    7ec2b000-7ec34000    Deferred        libnss_compat.so.2
ELF    7efa4000-7efe7000    Deferred        libm.so.6
ELF    7efea000-7f000000    Dwarf           winebrowser<elf>
  \-PE    7eff0000-7f000000    \               winebrowser
ELF    f73e1000-f73e5000    Deferred        libxinerama.so.1
ELF    f73e6000-f73eb000    Deferred        libdl.so.2
ELF    f73eb000-f759f000    Dwarf           libc.so.6
ELF    f75a0000-f75bb000    Deferred        libpthread.so.0
ELF    f75bc000-f75c0000    Deferred        libxau.so.6
ELF    f75d4000-f7718000    Dwarf           libwine.so.1
ELF    f771a000-f773c000    Deferred        ld-linux.so.2
ELF    f773c000-f773d000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000001f    0
    0000001e    0
    00000019    0
    00000017    0
    00000015    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001d    0
    00000018    0
    00000014    0
    00000013    0
0000001a plugplay.exe
    00000020    0
    0000001c    0
    0000001b    0
00000021 explorer.exe
    00000022    0
00000023 Semagic1799for2k.exe
    00000025    0
    00000024    0
0000002b (D) C:\windows\system32\winebrowser.exe
    0000002c    0 <==
System information:
    Wine build: wine-1.4.1
    Platform: i386
    Host system: Linux
    Host version: 3.8.0-34-generic

```

---

### Post by oldos2er on 2013-12-11
Moved to Wine.

---

