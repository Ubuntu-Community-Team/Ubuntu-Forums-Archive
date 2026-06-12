---
title: "Half Life 2 on Dell Inspiron E1505. Does _not_ work."
date: 2008-02-15
forum: Wine
---

### Post by Jcink on 2008-02-15
Ubuntu 7.10

I have been working on this for 4 days now and I'm at the end of my rope. I don't know how to get this working, I could be missing something major here, but in any case I'm just not seeing it. There seems to be some sort of problem for me getting Half life 2 to work. Steam starts up, I launch the game, I see the value guy. We go to the loading screen. Then around 30 seconds later, it blacks out, showing me a black screen, and throws the below info in my terminal output with a backtrace. 

No idea what to do... I've played with the settings a lot and it just doesn't work. Any tips/ideas would be extremely appreciated. :) More info will gladly be given if needed.

1. Wine version - 0.9.54

2. Terminal output - 

```
fixme:avifile:AVIFileExit (): stub!
wine: Unhandled page fault on write access to 0x00000022 at address 0xd498a37 (thread 0039), starting debugger...
Unhandled exception: page fault on write access to 0x00000022 in 32-bit code (0x0d498a37).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0d498a37 ESP:0034e574 EBP:00000004 EFLAGS:00010206(   - 00      - RIP1)
 EAX:00000000 EBX:07350070 ECX:0d4aa9d0 EDX:0d4a67b8
 ESI:00000700 EDI:0d4aa9d0
Stack dump:
0x0034e574:  00000090 0d4aa9d0 00000004 0069fc2c
0x0034e584:  0d499d32 07350070 00000730 23140074
0x0034e594:  0d4aa9d0 0069fc2c 0d49a084 23140074
0x0034e5a4:  00000730 23140074 0d4aa9f0 0d4aa9d0
0x0034e5b4:  0d4986ca 23140074 ffffffff 0034e60c
0x0034e5c4:  00000008 0034ff08 00000000 100070bb
Backtrace:
=>1 0x0d498a37 in datacache (+0x8a37) (0x00000004)
  2 0x00000000 (0x00000000)
0x0d498a37: addw        $0xffff,0x22(%eax)
Modules:
Module  Address                 Debug info      Name (143 modules)
PE        350000-  384000       Deferred        tier0
PE        390000-  3b0000       Deferred        vstdlib
PE        3b0000-  3e6000       Deferred        filesystem_steam
PE        3f0000-  400000       Deferred        steam_api
PE        400000-  41c000       Deferred        hl2
PE       cf50000- cf5e000       Deferred        unicode
PE       d1c0000- d298000       Deferred        datamodel
PE       d3b0000- d3d9000       Deferred        dmserializers
PE       d3e0000- d485000       Deferred        materialsystem
PE       d490000- d4b1000       Export          datacache
PE       d4c0000- d4d5000       Deferred        valve_avi
PE       d5f0000- d6b4000       Deferred        vguimatsurface
PE       d6c0000- d727000       Deferred        vgui2
PE       d730000- d75f000       Deferred        soundemittersystem
PE       da90000- dab8000       Deferred        stdshader_dbg
PE       dac0000- daf3000       Deferred        stdshader_dx6
PE       db00000- db27000       Deferred        stdshader_dx7
PE       e6d0000- e89c000       Deferred        steamclient
PE       e8a0000- e8df000       Deferred        tier0_s
PE       e8f0000- e92d000       Deferred        vstdlib_s
PE       ea50000- ea7e000       Deferred        nattypeprobe
PE       ea80000- ed1f000       Deferred        p2pcore
PE       ed20000- ee7c000       Deferred        p2pvoice
PE       ef90000- f14d000       Deferred        gameui
PE       fe40000- fe50000       Deferred        vaudio_miles
PE       fe50000- feb4000       Deferred        mss32
PE      10000000-1002e000       Deferred        launcher
PE      1de80000-1df94000       Deferred        serverbrowser
PE      20000000-2064b000       Deferred        engine
PE      21100000-211ad000       Deferred        mss32_s
PE      22000000-2263d000       Deferred        server
PE      24000000-24388000       Deferred        client
PE      26000000-26126000       Deferred        vphysics
PE      26400000-26439000       Deferred        mssvoice.asi
PE      26f00000-26f2e000       Deferred        mssmp3.asi
PE      2a000000-2a09f000       Deferred        shaderapidx9
PE      2c000000-2c2d8000       Deferred        studiorender
PE      30000000-3031d000       Deferred        steam
PE      60000000-60021000       Deferred        cserhelper
PE      628c0000-628d9000       Deferred        parsifal
ELF     6fefa000-6ff42000       Deferred        dbghelp<elf>
  \-PE  6ff00000-6ff42000       \               dbghelp
ELF     7b800000-7b925000       Deferred        kernel32<elf>
  \-PE  7b820000-7b925000       \               kernel32
ELF     7bc00000-7bca1000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bced000-7bd37000       Deferred        dsound<elf>
  \-PE  7bcf0000-7bd37000       \               dsound
ELF     7bd37000-7bd4b000       Deferred        winejoystick<elf>
  \-PE  7bd40000-7bd4b000       \               winejoystick
ELF     7bd4b000-7bd70000       Deferred        netapi32<elf>
  \-PE  7bd50000-7bd70000       \               netapi32
ELF     7bd70000-7bd96000       Deferred        secur32<elf>
  \-PE  7bd80000-7bd96000       \               secur32
ELF     7bd96000-7be86000       Deferred        wined3d<elf>
  \-PE  7bdb0000-7be86000       \               wined3d
ELF     7be86000-7beb5000       Deferred        d3d9<elf>
  \-PE  7be90000-7beb5000       \               d3d9
ELF     7beb5000-7bf00000       Deferred        wininet<elf>
  \-PE  7bec0000-7bf00000       \               wininet
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf08000-7bf1d000       Deferred        psapi<elf>
  \-PE  7bf10000-7bf1d000       \               psapi
ELF     7bf2b000-7bf4c000       Deferred        mpr<elf>
  \-PE  7bf30000-7bf4c000       \               mpr
ELF     7bf4c000-7bfec000       Deferred        oleaut32<elf>
  \-PE  7bf60000-7bfec000       \               oleaut32
ELF     7bfec000-7c000000       Deferred        midimap<elf>
  \-PE  7bff0000-7c000000       \               midimap
ELF     7c365000-7c37c000       Deferred        msacm32<elf>
  \-PE  7c370000-7c37c000       \               msacm32
ELF     7c37c000-7c3a3000       Deferred        msvfw32<elf>
  \-PE  7c380000-7c3a3000       \               msvfw32
ELF     7c3a3000-7c42f000       Deferred        winmm<elf>
  \-PE  7c3b0000-7c42f000       \               winmm
ELF     7c42f000-7c455000       Deferred        msacm32<elf>
  \-PE  7c440000-7c455000       \               msacm32
ELF     7c455000-7c48f000       Deferred        avifil32<elf>
  \-PE  7c460000-7c48f000       \               avifil32
ELF     7c5c4000-7c622000       Deferred        rpcrt4<elf>
  \-PE  7c5d0000-7c622000       \               rpcrt4
ELF     7c622000-7c6c1000       Deferred        ole32<elf>
  \-PE  7c630000-7c6c1000       \               ole32
ELF     7c722000-7c754000       Deferred        uxtheme<elf>
  \-PE  7c730000-7c754000       \               uxtheme
ELF     7c754000-7c813000       Deferred        comctl32<elf>
  \-PE  7c760000-7c813000       \               comctl32
ELF     7c813000-7c917000       Deferred        shell32<elf>
  \-PE  7c820000-7c917000       \               shell32
ELF     7c917000-7c96e000       Deferred        shlwapi<elf>
  \-PE  7c920000-7c96e000       \               shlwapi
ELF     7c96e000-7c982000       Deferred        mswsock<elf>
  \-PE  7c970000-7c982000       \               mswsock
ELF     7c982000-7c996000       Deferred        lz32<elf>
  \-PE  7c990000-7c996000       \               lz32
ELF     7c996000-7c9af000       Deferred        version<elf>
  \-PE  7c9a0000-7c9af000       \               version
ELF     7c9af000-7c9c2000       Deferred        libresolv.so.2
ELF     7c9d0000-7c9ee000       Deferred        iphlpapi<elf>
  \-PE  7c9e0000-7c9ee000       \               iphlpapi
ELF     7c9ee000-7ca19000       Deferred        ws2_32<elf>
  \-PE  7ca00000-7ca19000       \               ws2_32
ELF     7ca19000-7ca32000       Deferred        wsock32<elf>
  \-PE  7ca20000-7ca32000       \               wsock32
ELF     7d590000-7d595000       Deferred        libxfixes.so.3
ELF     7d595000-7d59e000       Deferred        libxcursor.so.1
ELF     7d59e000-7d5bb000       Deferred        imm32<elf>
  \-PE  7d5a0000-7d5bb000       \               imm32
ELF     7d5bb000-7d5c3000       Deferred        libxrender.so.1
ELF     7de91000-7de9c000       Deferred        libgcc_s.so.1
ELF     7de9c000-7dea5000       Deferred        librt.so.1
ELF     7df5f000-7e8c2000       Deferred        fglrx_dri.so
ELF     7e8c2000-7e962000       Deferred        libgl.so.1
ELF     7e962000-7e967000       Deferred        libxdmcp.so.6
ELF     7e967000-7e96a000       Deferred        libxau.so.6
ELF     7e96a000-7ea5b000       Deferred        libx11.so.6
ELF     7ea5b000-7ea69000       Deferred        libxext.so.6
ELF     7ea69000-7ea6e000       Deferred        libxxf86vm.so.1
ELF     7ea6e000-7ea86000       Deferred        libice.so.6
ELF     7ea86000-7ea8e000       Deferred        libsm.so.6
ELF     7ea8f000-7ea95000       Deferred        libxrandr.so.2
ELF     7ea9c000-7eb2b000       Deferred        winex11<elf>
  \-PE  7eab0000-7eb2b000       \               winex11
ELF     7eb8b000-7ebab000       Deferred        libexpat.so.1
ELF     7ebab000-7ebd6000       Deferred        libfontconfig.so.1
ELF     7ebd6000-7ebeb000       Deferred        libz.so.1
ELF     7ebeb000-7ec5b000       Deferred        libfreetype.so.6
ELF     7ec69000-7ecb3000       Deferred        advapi32<elf>
  \-PE  7ec70000-7ecb3000       \               advapi32
ELF     7ecb3000-7ed4a000       Deferred        gdi32<elf>
  \-PE  7ecc0000-7ed4a000       \               gdi32
ELF     7ed4a000-7ee81000       Deferred        user32<elf>
  \-PE  7ed60000-7ee81000       \               user32
ELF     7efa0000-7efab000       Deferred        libnss_files.so.2
ELF     7efab000-7efb5000       Deferred        libnss_nis.so.2
ELF     7efb5000-7efcd000       Deferred        libnsl.so.1
ELF     7efcd000-7eff2000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7d46000-b7d4a000       Deferred        libdl.so.2
ELF     b7d4a000-b7e94000       Deferred        libc.so.6
ELF     b7e95000-b7ead000       Deferred        libpthread.so.0
ELF     b7ebb000-b7fcf000       Deferred        libwine.so.1
ELF     b7fd1000-b7fed000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008
        0000002c    1
        0000000e    0
        0000000f    1
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
        0000003c    1
        00000037    0
        00000036    0
        00000035    0
        00000034    0
        00000033    0
        00000031    0
        00000030    0
        0000002f    0
        0000002e    0
        0000002b    0
        0000002a    0
        00000029    1
        00000028    0
        00000027    0
        00000025    0
        00000024    1
        00000022    0
        00000020    0
        0000001f    0
        0000001e    0
        0000001d    0
        0000001c    0
        0000001b    0
        0000001a    1
        00000019    0
        00000018    0
        00000017    0
        00000016    0
        00000015    0
        00000014    0
        00000013    0
        00000009    0
0000000a
        0000000b    0
00000010
        00000012    0
        00000011    0
00000038 (D) C:\Program Files\Steam\steamapps\jcinker\half-life 2\hl2.exe
        00000032    0
        0000000c    0
        0000000d    0
        0000003d    0
        0000003b    0
        0000003a    2
        00000039    0 <==
Backtrace:
=>1 0x0d498a37 in datacache (+0x8a37) (0x00000004)
  2 0x00000000 (0x00000000)
```

3. Wine configuration

OS version: WIndows XP

Library overrides: none

Sound settings: disabled

Graphics settings: 

Allow directx to stop the mouse... -> unchecked
Allow window manager to control windows -> checked
emulate a virtual desktop -> checked, 1024 by 800 but it does not matter enabled or disabled
Direct3D -> Vertex shader support: hardware
Allow pixel shader -> unchecked (checked it doesnt work either0
Registry edits: (none)

 4. Hardware specs/drivers 

Hardware:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
```

Using ATI Accelerated Graphics driver.

5. Other Wine applications: Whatpulse, GTA Vice City

---

### Post by gavintlgold on 2008-02-16
Did you follow the installation instructions here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=2890](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2890) ? If not, maybe they'll help...

---

