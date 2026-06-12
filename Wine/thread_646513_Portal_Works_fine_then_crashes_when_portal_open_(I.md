---
title: "Portal Works fine then crashes when portal open (IRONIC)"
date: 2007-12-21
forum: Wine
---

### Post by kthakore on 2007-12-21
I start portal fine with this launch command

```
 wine '/home/kthakore/.wine/drive_c/Program Files/UPortal/portal/hl2.exe' -steam -game portal -novid -window -dxlevel 90
```

 and it works perfectly until when the first portal opens and then all the shaders go beserk then when I walk through it I get the following error.

```
fixme:d3d:get_src_and_opr Unhandled texture arg WINED3DTA_SPECULAR
fixme:d3d:get_src_and_opr Unhandled texture arg WINED3DTA_SPECULAR
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:d3d:get_src_and_opr Unhandled texture arg WINED3DTA_SPECULAR
fixme:d3d:get_src_and_opr Unhandled texture arg WINED3DTA_SPECULAR
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x17877740)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x17877740)
fixme:shdocvw:OleObject_Close (0x17877740)->(1)
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
wine: Unhandled privileged instruction at address 0x1d001c (thread 0013), starting debugger...
Unhandled exception: privileged instruction in 32-bit code (0x001d001c).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:001d001c ESP:0034e6f4 EBP:00000000 EFLAGS:00210206(   - 00      - RIP1)
 EAX:001d001c EBX:0df85e80 ECX:08fa02c0 EDX:08faaa80
 ESI:0df85b50 EDI:00000000
Stack dump:
0x0034e6f4:  0def14a8 00000001 0000000a 0034e7c0
0x0034e704:  00400000 ffffffff ffffffff 0dfcebe1
0x0034e714:  0000000d 100084be 00000003 0034e7c0
0x0034e724:  10008747 00110b88 0034e764 1000873e
0x0034e734:  00110b88 00351a40 10004f45 00000001
0x0034e744:  005321cd 00000002 00000000 00000000
Backtrace:
=>1 0x001d001c (0x00000000)
0x001d001c: outb        %al,$0x1
Modules:
Module  Address                 Debug info      Name (136 modules)
PE        350000-  38b000       Deferred        tier0
PE        390000-  3e5000       Deferred        vstdlib
PE        400000-  41a000       Deferred        hl2
PE       b3a0000- b3e9000       Deferred        filesystem_steam
PE       c5b0000- cb93000       Deferred        engine
PE       cba0000- cbb4000       Deferred        steam_api
PE       d230000- d250000       Deferred        inputsystem
PE       d250000- d371000       Deferred        materialsystem
PE       d780000- d7bc000       Deferred        datacache
PE       d7c0000- dbac000       Deferred        studiorender
PE       ddd0000- dec0000       Deferred        vphysics
PE       dec0000- dedf000       Deferred        valve_avi
PE       dee0000- dfa8000       Deferred        vguimatsurface
PE       dfb0000- e00d000       Deferred        vgui2
PE       e010000- e198000       Deferred        shaderapidx9
PE       fd30000- fd44000       Deferred        xinput1_3
PE       fe60000- fe91000       Deferred        stdshader_dbg
PE       fea0000- fee6000       Deferred        stdshader_dx6
PE       fef0000- ff05000       Deferred        unicode
PE       ff50000- ff73000       Deferred        soundemittersystem
PE       ff80000- ff97000       Deferred        scenefilecache
PE      10000000-1002d000       Deferred        launcher
PE      10c40000-11179000       Deferred        client
PE      11540000-11cda000       Deferred        server
PE      16ff0000-171b9000       Deferred        gameui
PE      18000000-18033000       Deferred        binkw32
PE      18410000-18425000       Deferred        vaudio_miles
PE      188f0000-189ab000       Deferred        serverbrowser
PE      21100000-21164000       Deferred        mss32
PE      26400000-26439000       Deferred        mssvoice.asi
PE      26f00000-26f2e000       Deferred        mssmp3.asi
PE      30000000-300a1000       Deferred        steam
ELF     7b800000-7b92b000       Deferred        kernel32<elf>
  \-PE  7b820000-7b92b000       \               kernel32
ELF     7b97e000-7b989000       Deferred        libgcc_s.so.1
ELF     7b9a1000-7b9eb000       Deferred        dsound<elf>
  \-PE  7b9b0000-7b9eb000       \               dsound
ELF     7b9ed000-7ba27000       Deferred        shdocvw<elf>
  \-PE  7ba00000-7ba27000       \               shdocvw
ELF     7bc00000-7bca3000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca3000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d494000-7d4a8000       Deferred        winejoystick<elf>
  \-PE  7d4a0000-7d4a8000       \               winejoystick
ELF     7d4a8000-7d50e000       Deferred        setupapi<elf>
  \-PE  7d4b0000-7d50e000       \               setupapi
ELF     7d50e000-7d5fb000       Deferred        wined3d<elf>
  \-PE  7d520000-7d5fb000       \               wined3d
ELF     7d5fb000-7d629000       Deferred        d3d9<elf>
  \-PE  7d600000-7d629000       \               d3d9
ELF     7d629000-7d6ca000       Deferred        oleaut32<elf>
  \-PE  7d640000-7d6ca000       \               oleaut32
ELF     7d6ca000-7d6de000       Deferred        lz32<elf>
  \-PE  7d6d0000-7d6de000       \               lz32
ELF     7d6de000-7d6f8000       Deferred        version<elf>
  \-PE  7d6e0000-7d6f8000       \               version
ELF     7d6f8000-7d71f000       Deferred        msvfw32<elf>
  \-PE  7d700000-7d71f000       \               msvfw32
ELF     7d71f000-7d759000       Deferred        avifil32<elf>
  \-PE  7d730000-7d759000       \               avifil32
ELF     7d759000-7d76e000       Deferred        midimap<elf>
  \-PE  7d760000-7d76e000       \               midimap
ELF     7d76e000-7d795000       Deferred        msacm32<elf>
  \-PE  7d780000-7d795000       \               msacm32
ELF     7d795000-7d7d1000       Deferred        wineoss<elf>
  \-PE  7d7a0000-7d7d1000       \               wineoss
ELF     7d7d1000-7d897000       Deferred        libasound.so.2
ELF     7d897000-7d8af000       Deferred        msacm32<elf>
  \-PE  7d8a0000-7d8af000       \               msacm32
ELF     7d8af000-7d8e5000       Deferred        winealsa<elf>
  \-PE  7d8c0000-7d8e5000       \               winealsa
ELF     7d8e5000-7d906000       Deferred        mpr<elf>
  \-PE  7d8f0000-7d906000       \               mpr
ELF     7d906000-7d953000       Deferred        wininet<elf>
  \-PE  7d910000-7d953000       \               wininet
ELF     7d953000-7d9e1000       Deferred        winmm<elf>
  \-PE  7d960000-7d9e1000       \               winmm
ELF     7db5e000-7db90000       Deferred        uxtheme<elf>
  \-PE  7db70000-7db90000       \               uxtheme
ELF     7db90000-7dbec000       Deferred        rpcrt4<elf>
  \-PE  7dba0000-7dbec000       \               rpcrt4
ELF     7dbec000-7dc8f000       Deferred        ole32<elf>
  \-PE  7dc00000-7dc8f000       \               ole32
ELF     7dc8f000-7dd4d000       Deferred        comctl32<elf>
  \-PE  7dca0000-7dd4d000       \               comctl32
ELF     7dd4d000-7dda6000       Deferred        shlwapi<elf>
  \-PE  7dd60000-7dda6000       \               shlwapi
ELF     7dda6000-7deab000       Deferred        shell32<elf>
  \-PE  7ddc0000-7deab000       \               shell32
ELF     7deab000-7debe000       Deferred        libresolv.so.2
ELF     7debe000-7dedc000       Deferred        iphlpapi<elf>
  \-PE  7ded0000-7dedc000       \               iphlpapi
ELF     7dedc000-7df09000       Deferred        ws2_32<elf>
  \-PE  7def0000-7df09000       \               ws2_32
ELF     7df09000-7df23000       Deferred        wsock32<elf>
  \-PE  7df10000-7df23000       \               wsock32
ELF     7df23000-7df2c000       Deferred        libxcursor.so.1
ELF     7df2c000-7df4a000       Deferred        imm32<elf>
  \-PE  7df30000-7df4a000       \               imm32
ELF     7df4a000-7df50000       Deferred        libxrandr.so.2
ELF     7df50000-7df58000       Deferred        libxrender.so.1
ELF     7e650000-7e8ac000       Deferred        r200_dri.so
ELF     7e8ac000-7e8b6000       Deferred        libdrm.so.2
ELF     7e8b6000-7e8bb000       Deferred        libxfixes.so.3
ELF     7e8bb000-7e8be000       Deferred        libxdamage.so.1
ELF     7e8be000-7e91f000       Deferred        libgl.so.1
ELF     7e91f000-7e924000       Deferred        libxdmcp.so.6
ELF     7e924000-7e927000       Deferred        libxau.so.6
ELF     7e927000-7ea18000       Deferred        libx11.so.6
ELF     7ea18000-7ea26000       Deferred        libxext.so.6
ELF     7ea26000-7ea2b000       Deferred        libxxf86vm.so.1
ELF     7ea2b000-7ea43000       Deferred        libice.so.6
ELF     7ea43000-7ea4b000       Deferred        libsm.so.6
ELF     7ea4d000-7ea50000       Deferred        libxcomposite.so.1
ELF     7ea63000-7eaf0000       Deferred        winex11<elf>
  \-PE  7ea70000-7eaf0000       \               winex11
ELF     7eb64000-7eb84000       Deferred        libexpat.so.1
ELF     7eb84000-7ebaf000       Deferred        libfontconfig.so.1
ELF     7ebaf000-7ebc4000       Deferred        libz.so.1
ELF     7ebc4000-7ec34000       Deferred        libfreetype.so.6
ELF     7ec4c000-7ec98000       Deferred        advapi32<elf>
  \-PE  7ec60000-7ec98000       \               advapi32
ELF     7ec98000-7ed31000       Deferred        gdi32<elf>
  \-PE  7ecb0000-7ed31000       \               gdi32
ELF     7ed31000-7ee6e000       Deferred        user32<elf>
  \-PE  7ed50000-7ee6e000       \               user32
ELF     7ef8d000-7ef98000       Deferred        libnss_files.so.2
ELF     7ef98000-7efa2000       Deferred        libnss_nis.so.2
ELF     7efa2000-7efba000       Deferred        libnsl.so.1
ELF     7efba000-7efc3000       Deferred        libnss_compat.so.2
ELF     7efc3000-7efe8000       Deferred        libm.so.6
ELF     b7cc6000-b7cca000       Deferred        libdl.so.2
ELF     b7cca000-b7e14000       Deferred        libc.so.6
ELF     b7e15000-b7e2d000       Deferred        libpthread.so.0
ELF     b7e45000-b7f59000       Deferred        libwine.so.1
ELF     b7f5b000-b7f77000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000015 
        00000017    0
        00000016    0
00000012 (D) C:\Program Files\UPortal\portal\hl2.exe
        0000001b    0
        0000001a   15
        00000019    2
        00000018    0
        00000014    0
        00000013    0 <==
Backtrace:
=>1 0x001d001c (0x00000000)

```

---

### Post by Termy58 on 2007-12-22
> **kthakore said:**
> I start portal fine with this launch command

```
 wine '/home/kthakore/.wine/drive_c/Program Files/UPortal/portal/hl2.exe' -steam -game portal -novid -window -dxlevel 90
```

 and it works perfectly until when the first portal opens and then all the shaders go beserk then when I walk through it I get the following error.


Does this help you?

```

wine '/home/kthakore/.wine/drive_c/Program Files/UPortal/portal/hl2.exe' -steam -game portal -novid -window -dxlevel 80 -insecure
```

Insecure fixes a rare crash with it, and sometime it crashes in DX9, so I booted it back to DX8 and if it crashes with -insecure try it without -insecure.

---

### Post by theadmiral on 2009-06-26
did you fix this?
i get the same error, from some googling i think it might be a problem with older video cards not wine or anything with linux

---

