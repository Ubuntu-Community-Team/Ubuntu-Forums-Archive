---
title: "GTA V d3d_get_adapter_identifier+0x76 Fix needed"
date: 2015-12-03
forum: Wine
---

### Post by billybobpickle on 2015-12-03
Hello, I have almost gotten Grand Theft Auto V in wine. I have a gtx 610, but the debugger is giving out a d3d_get_adapter_identifier+0x76 in wined3d error. Running wine version 1.7.50 on lubuntu 15.04.
```
Unhandled exception: page fault on read access to 0x00000008 in 64-bit code (0x00007f2c143bb086).Register dump:
 rip:00007f2c143bb086 rsp:000000005075d510 rbp:0000000000000000 eflags:00010246 (  R- --  I  Z- -P- )
 rax:00000000000e8000 rbx:000000005075d660 rcx:0000000000000000 rdx:0000000000000000
 rsi:000000005075d850 rdi:000000005075d6d0  r8:0000000000000000  r9:000000005075d660 r10:000000005075eb5c
 r11:00000001427e40c0 r12:0000000000000000 r13:0000000000000000 r14:0000000000000000 r15:0000000000000002
Stack dump:
0x000000005075d510:  000000005075d5c0 00007f2c0f622cf6
0x000000005075d520:  00000000006e0101 0160010d000002ac
0x000000005075d530:  038203ec038203ec 0000000000000010
0x000000005075d540:  0000000000000001 000000005075da10
0x000000005075d550:  0000000000000000 0000000000000000
0x000000005075d560:  0000000000000000 0000000000000000
0x000000005075d570:  0000000000000000 0000000000000000
0x000000005075d580:  0000000000000000 0000000000000000
0x000000005075d590:  0000000000000000 0000000000000000
0x000000005075d5a0:  0000000000000000 0000000000000000
0x000000005075d5b0:  0000000000000000 00ff0000000000ff
0x000000005075d5c0:  0000000000000000 0000000000000000
Backtrace:
=>0 0x00007f2c143bb086 wined3d_get_adapter_identifier+0x76() in wined3d (0x0000000000000000)
  1 0x00007f2c0daea72d in dxgi (+0xa72c) (0x000000000006d7b0)
  2 0x00007f2c0daea97f in dxgi (+0xa97e) (0x000000000006d7b0)
  3 0x00000001411bdcd1 in gta5 (+0x11bdcd0) (0x000000005075db60)
0x00007f2c143bb086 wined3d_get_adapter_identifier+0x76 in wined3d: cmpl    0x0000000000000008(%rbp),%r12d
Modules:
Module    Address                    Debug info    Name (122 modules)
PE              350000-          3dd000    Deferred        3dmgame
PE              530000-          5bd000    Deferred        bink2w64
PE              5c0000-          5dc000    Deferred        gfsdk_txaa_alpharesolve.win64
PE            3b400000-        3b437000    Deferred        steam_api64
ELF            7a800000-        7abd7000    Deferred        opengl32<elf>
  \-PE            7a850000-        7abd7000    \               opengl32
ELF            7b800000-        7bc7e000    Deferred        kernel32<elf>
  \-PE            7b820000-        7bc7e000    \               kernel32
ELF            7be00000-        7c103000    Deferred        <wine-loader>
PE           140000000-       143f04c00    Export          gta5
PE           180000000-       18037f000    Deferred        gfsdk_shadowlib.win64
ELF        7f2c0d020000-    7f2c0d235000    Deferred        d3d10core<elf>
  \-PE        7f2c0d030000-    7f2c0d235000    \               d3d10core
ELF        7f2c0d238000-    7f2c0d44d000    Deferred        d3d10_1<elf>
  \-PE        7f2c0d240000-    7f2c0d44d000    \               d3d10_1
ELF        7f2c0d450000-    7f2c0d66c000    Deferred        cryptnet<elf>
  \-PE        7f2c0d460000-    7f2c0d66c000    \               cryptnet
ELF        7f2c0d670000-    7f2c0d8b2000    Deferred        rsaenh<elf>
  \-PE        7f2c0d680000-    7f2c0d8b2000    \               rsaenh
ELF        7f2c0d8b8000-    7f2c0dad3000    Deferred        imagehlp<elf>
  \-PE        7f2c0d8c0000-    7f2c0dad3000    \               imagehlp
ELF        7f2c0dad8000-    7f2c0dd03000    Dwarf           dxgi<elf>
  \-PE        7f2c0dae0000-    7f2c0dd03000    \               dxgi
ELF        7f2c0dd08000-    7f2c0df59000    Deferred        d3d11<elf>
  \-PE        7f2c0dd10000-    7f2c0df59000    \               d3d11
ELF        7f2c0df60000-    7f2c0e166000    Deferred        libxfixes.so.3
ELF        7f2c0e168000-    7f2c0e372000    Deferred        libxcursor.so.1
ELF        7f2c0e378000-    7f2c0e588000    Deferred        libxi.so.6
ELF        7f2c0e588000-    7f2c0e78b000    Deferred        libxcomposite.so.1
ELF        7f2c0e790000-    7f2c0e99a000    Deferred        libxrandr.so.2
ELF        7f2c0e9a0000-    7f2c0ebaa000    Deferred        libxrender.so.1
ELF        7f2c0ebb0000-    7f2c0edb6000    Deferred        libxxf86vm.so.1
ELF        7f2c0edb8000-    7f2c0efbb000    Deferred        libxinerama.so.1
ELF        7f2c0efc0000-    7f2c0f1c6000    Deferred        libxdmcp.so.6
ELF        7f2c0f1c8000-    7f2c0f3cc000    Deferred        libxau.so.6
ELF        7f2c0f3d0000-    7f2c0f5ef000    Deferred        libxcb.so.1
ELF        7f2c0f5f0000-    7f2c0f929000    Deferred        libx11.so.6
ELF        7f2c0f930000-    7f2c0fb42000    Deferred        libxext.so.6
ELF        7f2c0fb48000-    7f2c0fde4000    Deferred        winex11<elf>
  \-PE        7f2c0fb60000-    7f2c0fde4000    \               winex11
ELF        7f2c0fde8000-    7f2c0fffc000    Deferred        xinput1_3<elf>
  \-PE        7f2c0fdf0000-    7f2c0fffc000    \               xinput1_3
ELF        7f2c14128000-    7f2c14343000    Deferred        dinput8<elf>
  \-PE        7f2c14130000-    7f2c14343000    \               dinput8
ELF        7f2c14348000-    7f2c146a3000    Dwarf           wined3d<elf>
  \-PE        7f2c14360000-    7f2c146a3000    \               wined3d
ELF        7f2c146a8000-    7f2c148f5000    Deferred        d3d9<elf>
  \-PE        7f2c146b0000-    7f2c148f5000    \               d3d9
ELF        7f2c148f8000-    7f2c14b11000    Deferred        wtsapi32<elf>
  \-PE        7f2c14900000-    7f2c14b11000    \               wtsapi32
ELF        7f2c14b18000-    7f2c14d54000    Deferred        wintrust<elf>
  \-PE        7f2c14b20000-    7f2c14d54000    \               wintrust
ELF        7f2c14d58000-    7f2c15039000    Deferred        crypt32<elf>
  \-PE        7f2c14d70000-    7f2c15039000    \               crypt32
ELF        7f2c15040000-    7f2c153c6000    Deferred        oleaut32<elf>
  \-PE        7f2c15060000-    7f2c153c6000    \               oleaut32
ELF        7f2c153c8000-    7f2c155f1000    Deferred        propsys<elf>
  \-PE        7f2c153d0000-    7f2c155f1000    \               propsys
ELF        7f2c155f8000-    7f2c1580c000    Deferred        mfreadwrite<elf>
  \-PE        7f2c15600000-    7f2c1580c000    \               mfreadwrite
ELF        7f2c15810000-    7f2c15a2e000    Deferred        msdmo<elf>
  \-PE        7f2c15820000-    7f2c15a2e000    \               msdmo
ELF        7f2c15a30000-    7f2c15c4c000    Deferred        mfplat<elf>
  \-PE        7f2c15a40000-    7f2c15c4c000    \               mfplat
ELF        7f2c15c50000-    7f2c15e65000    Deferred        mf<elf>
  \-PE        7f2c15c60000-    7f2c15e65000    \               mf
ELF        7f2c15e68000-    7f2c1607b000    Deferred        psapi<elf>
  \-PE        7f2c15e70000-    7f2c1607b000    \               psapi
ELF        7f2c16080000-    7f2c162ac000    Deferred        msacm32<elf>
  \-PE        7f2c16090000-    7f2c162ac000    \               msacm32
ELF        7f2c162b0000-    7f2c16570000    Deferred        winmm<elf>
  \-PE        7f2c162c0000-    7f2c16570000    \               winmm
ELF        7f2c16570000-    7f2c167c2000    Deferred        dsound<elf>
  \-PE        7f2c16580000-    7f2c167c2000    \               dsound
ELF        7f2c167c8000-    7f2c169ef000    Deferred        imm32<elf>
  \-PE        7f2c167d0000-    7f2c169ef000    \               imm32
ELF        7f2c169f0000-    7f2c16c2f000    Deferred        ws2_32<elf>
  \-PE        7f2c16a00000-    7f2c16c2f000    \               ws2_32
ELF        7f2c16c30000-    7f2c16f11000    Deferred        msvcr100<elf>
  \-PE        7f2c16c50000-    7f2c16f11000    \               msvcr100
ELF        7f2c16fb8000-    7f2c171e1000    Deferred        libexpat.so.1
ELF        7f2c171e8000-    7f2c17426000    Deferred        libfontconfig.so.1
ELF        7f2c17428000-    7f2c1764e000    Deferred        libpng12.so.0
ELF        7f2c17650000-    7f2c1786b000    Deferred        libz.so.1
ELF        7f2c17870000-    7f2c17b18000    Deferred        libfreetype.so.6
ELF        7f2c17b18000-    7f2c17dac000    Deferred        rpcrt4<elf>
  \-PE        7f2c17b30000-    7f2c17dac000    \               rpcrt4
ELF        7f2c17db0000-    7f2c1812f000    Deferred        ole32<elf>
  \-PE        7f2c17de0000-    7f2c1812f000    \               ole32
ELF        7f2c18130000-    7f2c18358000    Deferred        d3dxof<elf>
  \-PE        7f2c18140000-    7f2c18358000    \               d3dxof
ELF        7f2c18358000-    7f2c185d6000    Deferred        d3dcompiler_43<elf>
  \-PE        7f2c18370000-    7f2c185d6000    \               d3dcompiler_43
ELF        7f2c185d8000-    7f2c18886000    Deferred        d3dx9_36<elf>
  \-PE        7f2c185f0000-    7f2c18886000    \               d3dx9_36
ELF        7f2c18888000-    7f2c18aa4000    Deferred        d3dx9_43<elf>
  \-PE        7f2c18890000-    7f2c18aa4000    \               d3dx9_43
ELF        7f2c18aa8000-    7f2c18d36000    Deferred        shlwapi<elf>
  \-PE        7f2c18ac0000-    7f2c18d36000    \               shlwapi
ELF        7f2c18d38000-    7f2c191b3000    Deferred        shell32<elf>
  \-PE        7f2c18d50000-    7f2c191b3000    \               shell32
ELF        7f2c191b8000-    7f2c193d2000    Deferred        version<elf>
  \-PE        7f2c191c0000-    7f2c193d2000    \               version
ELF        7f2c193d8000-    7f2c19666000    Deferred        advapi32<elf>
  \-PE        7f2c193f0000-    7f2c19666000    \               advapi32
ELF        7f2c19668000-    7f2c199ca000    Deferred        gdi32<elf>
  \-PE        7f2c19680000-    7f2c199ca000    \               gdi32
ELF        7f2c199d0000-    7f2c19d70000    Deferred        user32<elf>
  \-PE        7f2c199f0000-    7f2c19d70000    \               user32
ELF        7f2c19d70000-    7f2c19f7d000    Deferred        libnss_files.so.2
ELF        7f2c19f80000-    7f2c1a18c000    Deferred        libnss_nis.so.2
ELF        7f2c1a190000-    7f2c1a3aa000    Deferred        libnsl.so.1
ELF        7f2c1a3b0000-    7f2c1a5b9000    Deferred        libnss_compat.so.2
ELF        7f2c1a890000-    7f2c1aaa6000    Deferred        libgcc_s.so.1
ELF        7f2c1aaa8000-    7f2c1adb0000    Deferred        libm.so.6
ELF        7f2c1adb0000-    7f2c1b0ba000    Deferred        ntdll<elf>
  \-PE        7f2c1add0000-    7f2c1b0ba000    \               ntdll
ELF        7f2c1b0c0000-    7f2c1b48a000    Deferred        libc.so.6
ELF        7f2c1b698000-    7f2c1b8b6000    Deferred        libpthread.so.0
ELF        7f2c1b8e0000-    7f2c1bc85000    Dwarf           libwine.so.1
ELF        7f2c1bc88000-    7f2c1beae000    Deferred        ld-linux-x86-64.so.2
ELF        7fff871f2000-    7fff871f4000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000002f    0
    0000002e    0
    00000025    0
    0000001d    0
    00000014    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001c    0
    00000019    0
    00000018    0
    00000013    0
0000001a plugplay.exe
    00000020    0
    0000001f    0
    0000001b    0
00000021 PnkBstrA.exe
    00000028    0
    00000027    0
    00000022    0
00000023 explorer.exe
    0000002d    0
    0000002c    0
    0000002b    0
    00000024    0
00000029 PnkBstrB.exe
    00000031    0
    00000030    0
    0000002a    0
00000034 (D) Z:\home\anthony\.local\share\wineprefixes\steam\drive_c\Program Files (x86)\Steam\steamapps\common\Grand Theft Auto V\GTA5.exe
    00000041    1 <==
    00000040   -2
    0000003f   15
    0000003e   -1
    0000003d   15
    0000003c    2
    0000003b    2
    0000003a   15
    00000039    0
    00000038    0
    00000037    0
    00000035    0
System information:
    Wine build: wine-1.7.50
    Platform: x86_64
    Host system: Linux
    Host version: 3.19.0-37-generic
```

I feel like I am almost there and would like some assistance on how to fix this. Thanks in advanced!

---

### Post by T.J. on 2015-12-06
[https://appdb.winehq.org/objectManager.php?sClass=application&iId=16807](https://appdb.winehq.org/objectManager.php?sClass=application&iId=16807).  According to WineDB GTA 5 does not run properly.  If you get it working you have my utmost respect for your determination.  

The reason I am posting is to suggest that you should try running newer games in a KVM with passthrough, rather than using Wine.  Newer games seldom work with Wine, and at any time a patch may render a working game unplayable.  I would only use Wine for games that have been out for at least 2 years and are reasonably bug free.

---

### Post by r2rX on 2015-12-06
Until Wine fully supports DirectX11, it definitely won't work. There's progress on that front, so it'll happen sooner than later. :)

---

