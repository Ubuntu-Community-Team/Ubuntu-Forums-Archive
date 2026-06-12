---
title: "Thief Gold + ddfix crash"
date: 2013-01-28
forum: Wine
---

### Post by Maloy14 on 2013-01-28
I tried to install Thief Gold via wine. I was able to install successfully but the game crashes after a while. I then found ddfix and installed it -both the prepatched .exe file (v 1.37) and the ddfix_1.5.11.zip (the one with the .dll file). I was able to solve the multithread problem. But when I look at the map or at the options menu, then click 'done' to get back in the game, it crashes.

Here are the details of the crash:

Unhandled exception: page fault on read access to 0x00000014 in 32-bit code (0x7a6a8a4e).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7a6a8a4e ESP:0032f5b4 EBP:00000000 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000001 EBX:00000000 ECX:00000000 EDX:00000000
 ESI:00000009 EDI:7cfe8938
Stack dump:
0x0032f5b4:  7a830ced 00000000 00000008 7b2e0dd3
0x0032f5c4:  00000000 00000008 00000008 7b74a620
0x0032f5d4:  7a830722 00000002 00000000 00000000
0x0032f5e4:  7b7a3200 00000009 00000000 7b7a980c
0x0032f5f4:  00000000 f746c6c0 7d2ae838 7d20b260
0x0032f604:  00000008 7cf87d48 00000001 7a6978e4
Backtrace:
=>0 0x7a6a8a4e in fglrx_dri.so (+0x95ca4e) (0x00000000)
0x7a6a8a4e: movl    0x14(%edx),%eax
Modules:
Module    Address            Debug info    Name (86 modules)
PE      400000-  74d000    Deferred        thief
PE    10000000-1005d000    Deferred        miss02.osm
ELF    79d4c000-7b800000    Dwarf           fglrx_dri.so
ELF    7b800000-7ba17000    Deferred        kernel32<elf>
  \-PE    7b810000-7ba17000    \               kernel32
ELF    7bc00000-7bcc2000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcc2000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7d65d000-7d672000    Deferred        libspeexdsp.so.1
PE    7d68f000-7d692000    Deferred        libasound_module_rate_speexrate.
ELF    7d6a2000-7d76a000    Deferred        libasound.so.2
ELF    7d76a000-7d796000    Deferred        winealsa<elf>
  \-PE    7d770000-7d796000    \               winealsa
ELF    7d796000-7d889000    Deferred        oleaut32<elf>
  \-PE    7d7b0000-7d889000    \               oleaut32
ELF    7d889000-7d8ac000    Deferred        mmdevapi<elf>
  \-PE    7d890000-7d8ac000    \               mmdevapi
ELF    7d8ac000-7d8e0000    Deferred        uxtheme<elf>
  \-PE    7d8b0000-7d8e0000    \               uxtheme
ELF    7d8e0000-7d9d5000    Deferred        comctl32<elf>
  \-PE    7d8f0000-7d9d5000    \               comctl32
ELF    7d9d5000-7da19000    Deferred        dinput<elf>
  \-PE    7d9e0000-7da19000    \               dinput
ELF    7db14000-7db43000    Deferred        libatiadlxx.so
ELF    7e260000-7e269000    Deferred        librt.so.1
ELF    7e269000-7e288000    Deferred        libgcc_s.so.1
ELF    7e288000-7e33e000    Deferred        libgl.so.1
ELF    7e371000-7e4aa000    Deferred        wined3d<elf>
  \-PE    7e380000-7e4aa000    \               wined3d
ELF    7e4aa000-7e511000    Deferred        ddraw<elf>
  \-PE    7e4b0000-7e511000    \               ddraw
ELF    7e511000-7e554000    Deferred        dsound<elf>
  \-PE    7e520000-7e554000    \               dsound
ELF    7e554000-7e55e000    Deferred        libxcursor.so.1
ELF    7e5e7000-7e60e000    Deferred        libexpat.so.1
ELF    7e60e000-7e63e000    Deferred        libfontconfig.so.1
ELF    7e63e000-7e64c000    Deferred        libxi.so.6
ELF    7e64c000-7e652000    Deferred        libxfixes.so.3
ELF    7e652000-7e656000    Deferred        libxcomposite.so.1
ELF    7e656000-7e65e000    Deferred        libxrandr.so.2
ELF    7e65e000-7e668000    Deferred        libxrender.so.1
ELF    7e668000-7e66e000    Deferred        libxxf86vm.so.1
ELF    7e66e000-7e672000    Deferred        libxinerama.so.1
ELF    7e672000-7e694000    Deferred        imm32<elf>
  \-PE    7e680000-7e694000    \               imm32
ELF    7e694000-7e69a000    Deferred        libxdmcp.so.6
ELF    7e69a000-7e69e000    Deferred        libxau.so.6
ELF    7e69e000-7e6b8000    Deferred        libxcb.so.1
ELF    7e6b8000-7e7d5000    Deferred        libx11.so.6
ELF    7e7d5000-7e7e5000    Deferred        libxext.so.6
ELF    7e7e5000-7e7fe000    Deferred        libice.so.6
ELF    7e7fe000-7e892000    Deferred        winex11<elf>
  \-PE    7e810000-7e892000    \               winex11
ELF    7e892000-7e8a7000    Deferred        libz.so.1
ELF    7e8a7000-7e91d000    Deferred        libfreetype.so.6
ELF    7e91d000-7e954000    Deferred        libncurses.so.5
ELF    7e95b000-7e963000    Deferred        libatiuki.so.1
ELF    7e971000-7e999000    Deferred        msacm32<elf>
  \-PE    7e980000-7e999000    \               msacm32
ELF    7e999000-7ea10000    Deferred        rpcrt4<elf>
  \-PE    7e9a0000-7ea10000    \               rpcrt4
ELF    7ea10000-7eb18000    Deferred        ole32<elf>
  \-PE    7ea30000-7eb18000    \               ole32
ELF    7eb18000-7ebc5000    Deferred        winmm<elf>
  \-PE    7eb20000-7ebc5000    \               winmm
ELF    7ebc5000-7ebde000    Deferred        version<elf>
  \-PE    7ebd0000-7ebde000    \               version
ELF    7ebde000-7ec3f000    Deferred        advapi32<elf>
  \-PE    7ebf0000-7ec3f000    \               advapi32
ELF    7ec3f000-7ecfd000    Deferred        gdi32<elf>
  \-PE    7ec50000-7ecfd000    \               gdi32
ELF    7ecfd000-7ee3d000    Deferred        user32<elf>
  \-PE    7ed10000-7ee3d000    \               user32
ELF    7ef9a000-7efa6000    Deferred        libnss_files.so.2
ELF    7efa6000-7efbd000    Deferred        libnsl.so.1
ELF    7efbd000-7efe3000    Deferred        libm.so.6
ELF    7efe4000-7efe9000    Deferred        libuuid.so.1
ELF    7efe9000-7eff2000    Deferred        libsm.so.6
ELF    f7462000-f746c000    Deferred        libnss_nis.so.2
ELF    f746d000-f7471000    Deferred        libdl.so.2
ELF    f7471000-f75d1000    Deferred        libc.so.6
ELF    f75d2000-f75eb000    Deferred        libpthread.so.0
ELF    f7600000-f7608000    Deferred        libnss_compat.so.2
ELF    f7608000-f7749000    Dwarf           libwine.so.1
ELF    f774b000-f7769000    Deferred        ld-linux.so.2
ELF    f7769000-f776a000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\ThiefG\thief.exe
    00000028   15
    00000027    0
    00000026    0
    00000025    0
    00000009    0 <==
0000000e services.exe
    00000020    0
    0000001f    0
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
00000029 taskmgr.exe
    0000002d    0
    0000002c    0
    0000002b    0
    0000002a    0
System information:
    Wine build: wine-1.4
    Platform: i386
    Host system: Linux
    Host version: 2.6.32-34-generic

My computer specs:
ATI Mobility Radeon HD5145 512mb, ram is 2gb. 

Will appreciate any help. Thanks.

---

