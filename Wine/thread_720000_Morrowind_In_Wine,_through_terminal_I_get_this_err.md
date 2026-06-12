---
title: "Morrowind In Wine, through terminal I get this error:"
date: 2008-03-09
forum: Wine
---

### Post by Astura on 2008-03-09
Hi when I try to run Morrowind.exe through wine the game loads up but the graphics flash and go horribly garbled, then the program times out.

The terminal reads this error:



[noparse]
astral@Velio:~/Personal/Game/Morrowind$ wine Morrowind.exe
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/seq/seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:win:EnumDisplayDevicesW ((null),0,0x33f170,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x19b7c0) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x19b7c0) : stub
wine: Unhandled page fault on read access to 0x00000000 at address 0x403664 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00403664).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00403664 ESP:0033fcc8 EBP:0015fb60 EFLAGS:00010297(   - 00     RISAP1C)
 EAX:00000000 EBX:00ff9510 ECX:00ff72e8 EDX:0015f7a8
 ESI:00ffa350 EDI:0033fd44
Stack dump:
0x0033fcc8:  0041758a 00000000 00020024 00400000
0x0033fcd8:  ffffffea 007b3310 00ff8d98 447a0000
0x0033fce8:  00720065 00000000 00740053 007b3110
0x0033fcf8:  00610064 00160838 00000000 00000000
0x0033fd08:  00000280 000001e0 00200001 00690054
0x0033fd18:  0065006d 00000000 000b0000 00010000
Backtrace:
=>1 0x00403664 in morrowind (+0x3664) (0x0015fb60)
  2 0x001940a0 (0x007325fc)
  3 0x004e2900 in morrowind (+0xe2900) (0x00416b30)
  4 0x00000018 (0xe8f18b56)
  5 0x00000000 (0x00000000)
0x00403664: movl        0x0(%eax),%ecx
Modules:
Module  Address                 Debug info      Name (76 modules)
PE        400000-  7cc000       Export          morrowind
PE      30000000-3006e000       Deferred        binkw32
PE      780c0000-78121000       Deferred        msvcp60
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca3000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca3000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d86a000-7e37f000       Deferred        libglcore.so.1
ELF     7e37f000-7e423000       Deferred        libgl.so.1
ELF     7e433000-7e450000       Deferred        imm32<elf>
  \-PE  7e440000-7e450000       \               imm32
ELF     7e450000-7e482000       Deferred        uxtheme<elf>
  \-PE  7e460000-7e482000       \               uxtheme
ELF     7e497000-7e4ac000       Deferred        midimap<elf>
  \-PE  7e4a0000-7e4ac000       \               midimap
ELF     7e4ac000-7e4d2000       Deferred        msacm32<elf>
  \-PE  7e4b0000-7e4d2000       \               msacm32
ELF     7e4d2000-7e4ea000       Deferred        msacm32<elf>
  \-PE  7e4e0000-7e4ea000       \               msacm32
ELF     7e4ea000-7e5af000       Deferred        libasound.so.2
ELF     7e5bf000-7e5f4000       Deferred        winealsa<elf>
  \-PE  7e5d0000-7e5f4000       \               winealsa
ELF     7e5f4000-7e5fa000       Deferred        libxrandr.so.2
ELF     7e5fa000-7e602000       Deferred        libxrender.so.1
ELF     7e602000-7e605000       Deferred        libxinerama.so.1
ELF     7e605000-7e60a000       Deferred        libxdmcp.so.6
ELF     7e60a000-7e60d000       Deferred        libxau.so.6
ELF     7e60d000-7e6fe000       Deferred        libx11.so.6
ELF     7e6fe000-7e70c000       Deferred        libxext.so.6
ELF     7e718000-7e71a000       Deferred        libnvidia-tls.so.1
ELF     7e71c000-7e7a9000       Deferred        winex11<elf>
  \-PE  7e730000-7e7a9000       \               winex11
ELF     7e7ff000-7e81f000       Deferred        libexpat.so.1
ELF     7e81f000-7e84a000       Deferred        libfontconfig.so.1
ELF     7e85a000-7e86e000       Deferred        libz.so.1
ELF     7e86e000-7e8d8000       Deferred        libfreetype.so.6
ELF     7e8d8000-7e999000       Deferred        comctl32<elf>
  \-PE  7e8e0000-7e999000       \               comctl32
ELF     7e999000-7e9ff000       Deferred        msvcrt<elf>
  \-PE  7e9b0000-7e9ff000       \               msvcrt
ELF     7e9ff000-7eaf7000       Deferred        wined3d<elf>
  \-PE  7ea10000-7eaf7000       \               wined3d
ELF     7eaf7000-7eb22000       Deferred        d3d8<elf>
  \-PE  7eb00000-7eb22000       \               d3d8
ELF     7eb22000-7eb6c000       Deferred        dsound<elf>
  \-PE  7eb30000-7eb6c000       \               dsound
ELF     7eb6c000-7eba3000       Deferred        dinput<elf>
  \-PE  7eb70000-7eba3000       \               dinput
ELF     7eba3000-7ebbb000       Deferred        dinput8<elf>
  \-PE  7ebb0000-7ebbb000       \               dinput8
ELF     7ebbb000-7ec48000       Deferred        winmm<elf>
  \-PE  7ebd0000-7ec48000       \               winmm
ELF     7ec48000-7ec5b000       Deferred        libresolv.so.2
ELF     7ec5b000-7ec79000       Deferred        iphlpapi<elf>
  \-PE  7ec60000-7ec79000       \               iphlpapi
ELF     7ec79000-7ecd8000       Deferred        rpcrt4<elf>
  \-PE  7ec80000-7ecd8000       \               rpcrt4
ELF     7ecd8000-7ed7b000       Deferred        ole32<elf>
  \-PE  7ecf0000-7ed7b000       \               ole32
ELF     7ed7b000-7edc6000       Deferred        advapi32<elf>
  \-PE  7ed90000-7edc6000       \               advapi32
ELF     7edc6000-7ee5f000       Deferred        gdi32<elf>
  \-PE  7ede0000-7ee5f000       \               gdi32
ELF     7ee5f000-7ef9d000       Deferred        user32<elf>
  \-PE  7ee80000-7ef9d000       \               user32
ELF     7ef9d000-7efa8000       Deferred        libnss_files.so.2
ELF     7efa8000-7efb2000       Deferred        libnss_nis.so.2
ELF     7efb2000-7efc9000       Deferred        libnsl.so.1
ELF     7efc9000-7eff0000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     f7d06000-f7d0a000       Deferred        libdl.so.2
ELF     f7d0a000-f7e4b000       Deferred        libc.so.6
ELF     f7e4c000-f7e63000       Deferred        libpthread.so.0
ELF     f7e73000-f7f87000       Deferred        libwine.so.1
ELF     f7f89000-f7fa7000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) H:\Personal\Game\Morrowind\Morrowind.exe
        00000012    0
        00000009    0 <==
0000000a 
        0000000b    0
0000000c 
        0000000f    0
        0000000e    0
        0000000d    0
00000010 
        00000011    0
Backtrace:
=>1 0x00403664 in morrowind (+0x3664) (0x0015fb60)
  2 0x001940a0 (0x007325fc)
  3 0x004e2900 in morrowind (+0xe2900) (0x00416b30)
  4 0x00000018 (0xe8f18b56)
  5 0x00000000 (0x00000000)
Segmentation fault (core dumped)
astral@Velio:~/Personal/Game/Morrowind$ 
[/noparse]



Any advice?

---

