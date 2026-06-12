---
title: "Steam (in Wine): games don't run when lauched"
date: 2007-03-03
forum: Wine
---

### Post by Rippy on 2007-03-03
First off, sorry if this is out of place for an Ubuntu forum, Wine doesn't have forums in seems, and I don't have an IRC client atm so I thought I would try here.

Basically the problem is this: I've installed steam and some of my games successfully. However, when launching them, it displays the "launching [game]" window properly, but then nothing happens.

Here's the output when I tried to start CSS:
```
paul@paul-ubuntu:~$ cd ~/.wine/drive_c/Program\ Files/Steam && WINEDEBUG=-all wine steam -applaunch 240
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
Could not load Mozilla. HTML rendering will be disabled.
libGL warning: 3D driver claims to not support visual 0x4b
wine: Unhandled page fault on read access to 0x800000ec at address 0x7bc3681b (thread 0037), starting debugger...
Unhandled exception: page fault on read access to 0x800000ec in 32-bit code (0x7bc3681b).
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 772fee50 while expecting 1ef97e02)
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc3681b ESP:0034e334 EBP:0034e35c EFLAGS:00010286(   - 00      -RISP1)
 EAX:80000000 EBX:7bc7a370 ECX:65faf1f0 EDX:65f22392
 ESI:00000000 EDI:0df30154
Stack dump:
0x0034e334:  00000000 7eb8d6f4 0034e34c 7eb72423
0x0034e344:  00000000 0df30018 0034e404 65f24247
0x0034e354:  7bc7a370 00000000 0034e3bc 7bc3800c
0x0034e364:  0034e324 00000000 00110000 7bc29ba1
0x0034e374:  001a5448 00000030 0034e40c 7bc2951f
0x0034e384:  00110000 7bc7a370 0034e3cc 7bc37807
Backtrace:
=>1 0x7bc3681b in ntdll (+0x2681b) (0x0034e35c)
  2 0x7bc3800c RtlAllocateHeap+0x1c() in ntdll (0x0034e3bc)
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file ole32.dbg ("\xd1n\xe0~")
  3 0x65f01b9b in ole32 (+0x1b9b) (0x0034e454)
  4 0x65f2389d in ole32 (+0x2389d) (0x0034e474)
  5 0x65f2376c in ole32 (+0x2376c) (0x0034e490)
  6 0x65f235cd in ole32 (+0x235cd) (0x0034e4a4)
  7 0x65f2354d in ole32 (+0x2354d) (0x0034e4d4)
  8 0x65f018b4 in ole32 (+0x18b4) (0x0034e53c)
  9 0x65f63f00 in ole32 (+0x63f00) (0x0034e56c)
  10 0x2a02e3d0 in shaderapidx9 (+0x2e3d0) (0x02a86410)
  11 0x00000000 (0x00000001)
  12 0x00000000 (0x00000000)
0x7bc3681b: cmpl        $0x50414548,0xec(%eax)
Modules:
Module  Address                 Debug info      Name (120 modules)
PE      350000-386000   Deferred        tier0
PE      390000-3ae000   Deferred        vstdlib
PE      3b0000-3fd000   Deferred        filesystem_steam
PE      400000-41c000   Deferred        hl2
PE      d0a0000-d19e000 Deferred        datamodel
PE      d2b0000-d2ed000 Deferred        dmserializers
PE      d2f0000-d315000 Deferred        datacache
PE      d320000-d334000 Deferred        inputsystem
PE      d450000-d504000 Deferred        materialsystem
PE      d510000-d526000 Deferred        valve_avi
PE      d530000-d5fe000 Deferred        vguimatsurface
PE      d600000-d675000 Deferred        vgui2
PE      d680000-dc69000 Deferred        engine
PE      dc70000-dc83000 Deferred        steam_api
PE      deb0000-ded9000 Deferred        stdshader_dbg
PE      dee0000-df15000 Deferred        stdshader_dx6
PE      10000000-10030000       Deferred        launcher
PE      20000000-2031d000       Deferred        steam
PE      26000000-26138000       Deferred        vphysics
PE      2a000000-2a0a8000       Export          shaderapidx9
PE      2c000000-2c3e3000       Deferred        studiorender
PE      628c0000-628d9000       Deferred        parsifal
PE      65f00000-65fc2000       Export          ole32
ELF     7b800000-7b928000       Deferred        kernel32<elf>
  \-PE  7b820000-7b928000       \               kernel32
ELF     7bc00000-7bc95000       Export          ntdll<elf>
  \-PE  7bc10000-7bc95000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d32c000-7d340000       Deferred        winejoystick<elf>
  \-PE  7d330000-7d340000       \               winejoystick
ELF     7d562000-7d568000       Deferred        libnss_dns.so.2
ELF     7d576000-7d5f6000       Deferred        libglu.so.1
ELF     7d5f6000-7d6af000       Deferred        wined3d<elf>
  \-PE  7d610000-7d6af000       \               wined3d
ELF     7d6af000-7d6da000       Deferred        d3d9<elf>
  \-PE  7d6c0000-7d6da000       \               d3d9
ELF     7d6da000-7d6f9000       Deferred        mpr<elf>
  \-PE  7d6e0000-7d6f9000       \               mpr
ELF     7d6f9000-7d740000       Deferred        wininet<elf>
  \-PE  7d700000-7d740000       \               wininet
ELF     7d740000-7d7db000       Deferred        oleaut32<elf>
  \-PE  7d750000-7d7db000       \               oleaut32
ELF     7d7db000-7d802000       Deferred        msvfw32<elf>
  \-PE  7d7e0000-7d802000       \               msvfw32
ELF     7d802000-7d83c000       Deferred        avifil32<elf>
  \-PE  7d810000-7d83c000       \               avifil32
ELF     7d83c000-7d851000       Deferred        midimap<elf>
  \-PE  7d840000-7d851000       \               midimap
ELF     7d877000-7d88f000       Deferred        msacm32<elf>
  \-PE  7d880000-7d88f000       \               msacm32
ELF     7d88f000-7d8cb000       Deferred        wineoss<elf>
  \-PE  7d8a0000-7d8cb000       \               wineoss
ELF     7d8cb000-7d95a000       Deferred        winmm<elf>
  \-PE  7d8e0000-7d95a000       \               winmm
ELF     7d95a000-7d9af000       Deferred        rpcrt4<elf>
  \-PE  7d970000-7d9af000       \               rpcrt4
ELF     7db21000-7db53000       Deferred        uxtheme<elf>
  \-PE  7db30000-7db53000       \               uxtheme
ELF     7db53000-7db67000       Deferred        mswsock<elf>
  \-PE  7db60000-7db67000       \               mswsock
ELF     7db67000-7db7b000       Deferred        lz32<elf>
  \-PE  7db70000-7db7b000       \               lz32
ELF     7db7b000-7db94000       Deferred        version<elf>
  \-PE  7db80000-7db94000       \               version
ELF     7db94000-7dc53000       Deferred        comctl32<elf>
  \-PE  7dba0000-7dc53000       \               comctl32
ELF     7dc53000-7dcac000       Deferred        shlwapi<elf>
  \-PE  7dc60000-7dcac000       \               shlwapi
ELF     7dcac000-7dda1000       Deferred        shell32<elf>
  \-PE  7dcc0000-7dda1000       \               shell32
ELF     7dda1000-7ddb4000       Deferred        libresolv.so.2
ELF     7ddb4000-7ddb7000       Deferred        libnss_mdns4.so.2
ELF     7ddb7000-7ddba000       Deferred        libnss_mdns4_minimal.so.2
ELF     7ddc2000-7dde0000       Deferred        iphlpapi<elf>
  \-PE  7ddd0000-7dde0000       \               iphlpapi
ELF     7dde0000-7de0d000       Deferred        ws2_32<elf>
  \-PE  7ddf0000-7de0d000       \               ws2_32
ELF     7de0d000-7de27000       Deferred        wsock32<elf>
  \-PE  7de10000-7de27000       \               wsock32
ELF     7de29000-7de2e000       Deferred        libxfixes.so.3
ELF     7de2e000-7de37000       Deferred        libxcursor.so.1
ELF     7de37000-7de3f000       Deferred        libxrender.so.1
ELF     7de3f000-7de5b000       Deferred        imm32<elf>
  \-PE  7de50000-7de5b000       \               imm32
ELF     7de5b000-7de5e000       Deferred        libxinerama.so.1
ELF     7e551000-7e7c6000       Deferred        r200_dri.so
ELF     7e7c6000-7e7cf000       Deferred        libdrm.so.2
ELF     7e7cf000-7e82f000       Deferred        libgl.so.1
ELF     7e82f000-7e834000       Deferred        libxdmcp.so.6
ELF     7e834000-7e84c000       Deferred        libxcb.so.1
ELF     7e84c000-7e84e000       Deferred        libxcb-xlib.so.0
ELF     7e84e000-7e851000       Deferred        libxau.so.6
ELF     7e851000-7e93c000       Deferred        libx11.so.6
ELF     7e93c000-7e94a000       Deferred        libxext.so.6
ELF     7e94a000-7e94f000       Deferred        libxxf86vm.so.1
ELF     7e94f000-7e967000       Deferred        libice.so.6
ELF     7e967000-7e970000       Deferred        libsm.so.6
ELF     7e970000-7e9fd000       Deferred        winex11<elf>
  \-PE  7e980000-7e9fd000       \               winex11
ELF     7ea83000-7eaa2000       Deferred        libexpat.so.1
ELF     7eaa2000-7eacd000       Deferred        libfontconfig.so.1
ELF     7eacd000-7eae1000       Deferred        libz.so.1
ELF     7eae1000-7eb4b000       Deferred        libfreetype.so.6
ELF     7eb4b000-7eb92000       Deferred        advapi32<elf>
  \-PE  7eb60000-7eb92000       \               advapi32
ELF     7eb92000-7eb9e000       Deferred        libgcc_s.so.1
ELF     7ec88000-7ed44000       Deferred        gdi32<elf>
  \-PE  7eca0000-7ed44000       \               gdi32
ELF     7ed44000-7ee80000       Deferred        user32<elf>
  \-PE  7ed60000-7ee80000       \               user32
ELF     7ee80000-7ee8b000       Deferred        libnss_files.so.2
ELF     7ee8b000-7eea2000       Deferred        libnsl.so.1
ELF     7eea2000-7eeab000       Deferred        libnss_compat.so.2
ELF     7efcb000-7eff2000       Deferred        libm.so.6
ELF     7eff4000-7effe000       Deferred        libnss_nis.so.2
ELF     b7ce2000-b7ce6000       Deferred        libdl.so.2
ELF     b7ce6000-b7e27000       Deferred        libc.so.6
ELF     b7e27000-b7e3e000       Deferred        libpthread.so.0
ELF     b7e4c000-b7f5d000       Deferred        libwine.so.1
ELF     b7f5f000-b7f7a000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000034 (D) C:\Program Files\Steam\steamapps\ripazoid\counter-strike source\hl2.exe
        0000004a    0
        00000048    0
        0000001b    2
        00000037    0 <==
0000000a 
        0000000c    0
        0000000b    0
00000008 
        00000049    1
        00000033    0
        0000001e    0
        00000018    0
        00000047    0
        00000046    1
        00000045    0
        00000044    1
        00000043    0
        00000042    1
        00000041    0
        00000040    1
        0000003f    0
        0000003e    1
        0000003d    0
        0000003c    1
        0000003b    0
        0000003a    1
        00000039    0
        00000038    1
        00000035    0
        00000020    0
        0000001f    0
        0000001d    0
        0000001c    1
        0000001a    0
        00000019    0
        00000017    0
        00000016    0
        00000015    1
        00000014    0
        00000013    0
        00000012    0
        00000011    0
        00000010    0
        0000000f    0
        0000000e    0
        0000000d    0
        00000009    0
```
Any ideas?

Info:
- Feisty Herd 5
- ATI Radeon 9200 PRO, using "ati" driver with AIGLX acceleration
- Latest repo of Wine (0.9.31)
- Winetools was used to install many components

Thanks!

-Rippy

---

### Post by YokoZar on 2007-03-04
> **Rippy said:**
> Info:
- Feisty Herd 5
- ATI Radeon 9200 PRO, using "ati" driver with AIGLX acceleration
- Latest repo of Wine (0.9.31)
- Winetools was used to install many components

Thanks!

-RippyTry Wine 0.9.32.  Came out this morning.  0.9.31 had a big regression that would cause steam games to crash.

But, you're using Feisty.  I didn't make a Feisty package yet, but \sh usually forwardports the edgy package for me within a few days.

---

### Post by Rippy on 2007-03-04
Well I think I'll just wait a couple days for the repository version to get updated, rather than mess around trying to install it myself. Hopefully I'll have more success with 0.9.32 :)

I knew 0.9.32 had just come out, but at that point the only option was to compile the source, since they didn't even have distribution packages out yet. Just wanted to save myself the trouble of getting that to work.

---

### Post by Rippy on 2007-03-06
Well, I just updated to 0.9.32, and there's no improvement.

Any other ideas?

---

### Post by saz on 2008-02-22
help same problem here...

---

