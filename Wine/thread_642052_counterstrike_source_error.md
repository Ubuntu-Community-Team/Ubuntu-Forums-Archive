---
title: "counterstrike source error"
date: 2007-12-16
forum: Wine
---

### Post by 123qwe on 2007-12-16
hey i hav a radeon 9550 graphics card, Direct Rendering Enabled and fglrx shows Ati and everything good.

but when i load up cs:source it crashes just when its about to open the menu, i set theregistry with this 

 [HKEY_CURRENT_USER\Software\Wine\Direct3D]"VideoMemorySize" "128"

but it does nothing :/

here is my output i get from running it from terminal., i bolded the thigns that i **think ** may be the cause of the error. thanks for all your helps =] im running xubuntu amd64 btw. thhhanks :D

```
tsuyoshi@tsuyoshi-desktop:~$ **cd ~/.wine/drive_c/Program\ Files/Steam && WINEDEBUG=-all wine steam -applaunch 240 -dxlevel 70**
dir: C:\Program Files\Steam\bin\ *.mix
dir: C:\Program Files\Steam\bin\ *.asi
dir: C:\Program Files\Steam\bin\ *.flt
[B]warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30[/B]
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
**Failed to verifiy SteamService.dll**
wine: Unhandled page fault on read access to 0x0d35a1a0 at address 0xe423e2c (thread 002b), starting debugger...
Unhandled exception: page fault on read access to 0x0d35a1a0 in 32-bit code (0x0e423e2c).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:0e423e2c ESP:0034fc14 EBP:0034fc4c EFLAGS:00010202(   - 00      - -RI1)
 EAX:0d35a1a0 EBX:00000001 ECX:05350240 EDX:ffffffff
 ESI:05350240 EDI:0e436050
Stack dump:
0x0034fc14:  00000001 00000000 00000001 0e43604c
0x0034fc24:  0e4282e7 00000000 00000000 00000001
0x0034fc34:  0034fc28 0034f778 0034fc94 0e4283d4
0x0034fc44:  0e433518 00000000 0034fc68 0e42836b
0x0034fc54:  00000000 00000000 00000001 0e4269b8
0x0034fc64:  00000000 0034fca4 0e426ac4 0e420000
Backtrace:
=>1 0x0e423e2c in scenefilecache (+0x3e2c) (0x0034fc4c)
  2 0x0e42836b in scenefilecache (+0x836b) (0x0034fc68)
  3 0x0e426ac4 in scenefilecache (+0x6ac4) (0x0034fca4)
  4 0x7bc43f55 call_dll_entry_point+0x15() in ntdll (0x0034fcc4)
  5 0x7bc4592d in ntdll (+0x3592d) (0x0034fd54)
  6 0x7bc45d88 in ntdll (+0x35d88) (0x0034fd84)
  7 0x7b8733ff ExitProcess+0x1f() in kernel32 (0x0034fda4)
  8 0x00401abe in hl2 (+0x1abe) (0x0034fddc)
  9 0x00401c41 in hl2 (+0x1c41) (0x0034ff08)
  10 0x7b87618e in kernel32 (+0x5618e) (0x0034ffe8)
  11 0xf7e78937 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x0e423e2c: call        *0x0(%eax)
Modules:
Module  Address                 Debug info      Name (123 modules)
PE        350000-  386000       Deferred        tier0
PE        390000-  3ae000       Deferred        vstdlib
PE        400000-  41c000       Export          hl2
PE       cf50000- cfa4000       Deferred        filesystem_steam
PE       d690000- d6a4000       Deferred        steam_api
PE       d940000- d94f000       Deferred        unicode
PE       e3e0000- e416000       Deferred        soundemittersystem
PE       e420000- e43b000       Export          scenefilecache
PE       e440000- e601000       Deferred        steamclient
PE       e610000- e688000       Deferred        vstdlib_s
PE       e690000- e6d0000       Deferred        tier0_s
PE       e7f0000- e81e000       Deferred        nattypeprobe
PE       e820000- eabf000       Deferred        p2pcore
PE       eac0000- ec1c000       Deferred        p2pvoice
PE       ee40000- f023000       Deferred        gameui
PE       ff50000- ff60000       Deferred        vaudio_miles
PE       ff60000- ffc4000       Deferred        mss32
PE      10000000-10030000       Deferred        launcher
PE      20000000-205ee000       Deferred        engine
PE      21100000-211ad000       Deferred        mss32_s
PE      22000000-22642000       Deferred        server
PE      24000000-24476000       Deferred        client
PE      26400000-26439000       Deferred        mssvoice.asi
PE      26f00000-26f2e000       Deferred        mssmp3.asi
PE      30000000-30320000       Deferred        steam
PE      60000000-60021000       Deferred        cserhelper
ELF     717d2000-7180c000       Deferred        shdocvw<elf>
  \-PE  717e0000-7180c000       \               shdocvw
ELF     72ab6000-72acb000       Deferred        psapi<elf>
  \-PE  72ac0000-72acb000       \               psapi
ELF     73210000-7325a000       Deferred        dbghelp<elf>
  \-PE  73220000-7325a000       \               dbghelp
ELF     7325a000-732a4000       Deferred        dsound<elf>
  \-PE  73260000-732a4000       \               dsound
ELF     732a4000-732ca000       Deferred        netapi32<elf>
  \-PE  732b0000-732ca000       \               netapi32
ELF     736db000-736ef000       Deferred        winejoystick<elf>
  \-PE  736e0000-736ef000       \               winejoystick
ELF     7b800000-7b92b000       Export          kernel32<elf>
  \-PE  7b820000-7b92b000       \               kernel32
ELF     7b93a000-7b961000       Deferred        secur32<elf>
  \-PE  7b940000-7b961000       \               secur32
ELF     7bb5f000-7bc00000       Deferred        oleaut32<elf>
  \-PE  7bb70000-7bc00000       \               oleaut32
ELF     7bc00000-7bca3000       Export          ntdll<elf>
  \-PE  7bc10000-7bca3000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf0a000-7bf2b000       Deferred        mpr<elf>
  \-PE  7bf10000-7bf2b000       \               mpr
ELF     7bf2b000-7bf78000       Deferred        wininet<elf>
  \-PE  7bf40000-7bf78000       \               wininet
ELF     7bfd9000-7c000000       Deferred        msacm32<elf>
  \-PE  7bfe0000-7c000000       \               msacm32
ELF     7c511000-7c526000       Deferred        midimap<elf>
  \-PE  7c520000-7c526000       \               midimap
ELF     7c526000-7c53e000       Deferred        msacm32<elf>
  \-PE  7c530000-7c53e000       \               msacm32
ELF     7c53e000-7c57a000       Deferred        wineoss<elf>
  \-PE  7c550000-7c57a000       \               wineoss
ELF     7c57a000-7c608000       Deferred        winmm<elf>
  \-PE  7c590000-7c608000       \               winmm
ELF     7c6e1000-7c713000       Deferred        uxtheme<elf>
  \-PE  7c6f0000-7c713000       \               uxtheme
ELF     7c713000-7c727000       Deferred        mswsock<elf>
  \-PE  7c720000-7c727000       \               mswsock
ELF     7c727000-7c73b000       Deferred        lz32<elf>
  \-PE  7c730000-7c73b000       \               lz32
ELF     7c73b000-7c755000       Deferred        version<elf>
  \-PE  7c740000-7c755000       \               version
ELF     7c755000-7c813000       Deferred        comctl32<elf>
  \-PE  7c760000-7c813000       \               comctl32
ELF     7c813000-7c86c000       Deferred        shlwapi<elf>
  \-PE  7c820000-7c86c000       \               shlwapi
ELF     7c86c000-7c971000       Deferred        shell32<elf>
  \-PE  7c880000-7c971000       \               shell32
ELF     7c971000-7c9cd000       Deferred        rpcrt4<elf>
  \-PE  7c980000-7c9cd000       \               rpcrt4
ELF     7c9cd000-7ca70000       Deferred        ole32<elf>
  \-PE  7c9e0000-7ca70000       \               ole32
ELF     7ca70000-7ca83000       Deferred        libresolv.so.2
ELF     7ca91000-7caaf000       Deferred        iphlpapi<elf>
  \-PE  7caa0000-7caaf000       \               iphlpapi
ELF     7caaf000-7cadc000       Deferred        ws2_32<elf>
  \-PE  7cac0000-7cadc000       \               ws2_32
ELF     7cadc000-7caf6000       Deferred        wsock32<elf>
  \-PE  7cae0000-7caf6000       \               wsock32
ELF     7caf6000-7cafb000       Deferred        libxfixes.so.3
ELF     7cafb000-7cb04000       Deferred        libxcursor.so.1
ELF     7cb04000-7cb22000       Deferred        imm32<elf>
  \-PE  7cb10000-7cb22000       \               imm32
ELF     7cb22000-7cb28000       Deferred        libxrandr.so.2
ELF     7cb28000-7cb33000       Deferred        libgcc_s.so.1
ELF     7d902000-7d90b000       Deferred        librt.so.1
ELF     7d90b000-7e8c8000       Deferred        fglrx_dri.so
ELF     7e8c8000-7e952000       Deferred        libgl.so.1
ELF     7e952000-7e957000       Deferred        libxdmcp.so.6
ELF     7e957000-7e95a000       Deferred        libxau.so.6
ELF     7e95a000-7ea4b000       Deferred        libx11.so.6
ELF     7ea4b000-7ea59000       Deferred        libxext.so.6
ELF     7ea5a000-7ea62000       Deferred        libxrender.so.1
ELF     7ea62000-7ea65000       Deferred        libxinerama.so.1
ELF     7ea67000-7eaf8000       Deferred        winex11<elf>
  \-PE  7ea80000-7eaf8000       \               winex11
ELF     7eb7f000-7eb9f000       Deferred        libexpat.so.1
ELF     7eb9f000-7ebca000       Deferred        libfontconfig.so.1
ELF     7ebd8000-7ebed000       Deferred        libz.so.1
ELF     7ebed000-7ec5d000       Deferred        libfreetype.so.6
ELF     7ec5d000-7eca9000       Deferred        advapi32<elf>
  \-PE  7ec70000-7eca9000       \               advapi32
ELF     7eca9000-7ed42000       Deferred        gdi32<elf>
  \-PE  7ecc0000-7ed42000       \               gdi32
ELF     7ed42000-7ee7f000       Deferred        user32<elf>
  \-PE  7ed60000-7ee7f000       \               user32
ELF     7ee7f000-7ee97000       Deferred        libnsl.so.1
ELF     7ee97000-7eea0000       Deferred        libnss_compat.so.2
ELF     7efcd000-7eff2000       Deferred        libm.so.6
ELF     7eff5000-7f000000       Deferred        libnss_files.so.2
ELF     f7cf1000-f7cfb000       Deferred        libnss_nis.so.2
ELF     f7cfc000-f7d00000       Deferred        libdl.so.2
ELF     f7d00000-f7e4a000       Deferred        libc.so.6
ELF     f7e4b000-f7e63000       Deferred        libpthread.so.0
ELF     f7e71000-f7f85000       Export          libwine.so.1
ELF     f7f87000-f7fa5000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000028 (D) C:\Program Files\Steam\steamapps\psychoturkeys\counter-strike source\hl2.exe
        0000004b   15
        0000004a   15
        00000048    2
        00000046    0
        00000031    2
        0000002b    0 <==
00000017 
        00000019    0
        00000018    0
0000000a 
        0000000b    0
00000008 
        00000026    0
        00000047    0
        00000045    0
        00000044    0
        00000043    1
        00000042    0
        00000041    1
        00000040    0
        0000003f    1
        0000003e    0
        0000003d    1
        0000003c    0
        0000003b    1
        0000003a    0
        00000039    1
        00000038    0
        00000037    1
        00000036    0
        00000035    1
        00000030    0
        0000002f    0
        0000002e    1
        0000002d    0
        0000002c    0
        0000002a    0
        00000029    1
        00000027    0
        00000025    0
        00000024   15
        00000023   15
        0000001f   15
        0000001c    0
        0000001b    0
        00000016    0
        00000015    0
        00000014    1
        00000013    0
        00000012    0
        00000011    0
        00000010    0
        0000000f    0
        0000000e    0
        0000000d    0
        0000000c    0
        00000009    0
Backtrace:
=>1 0x0e423e2c in scenefilecache (+0x3e2c) (0x0034fc4c)
  2 0x0e42836b in scenefilecache (+0x836b) (0x0034fc68)
  3 0x0e426ac4 in scenefilecache (+0x6ac4) (0x0034fca4)
  4 0x7bc43f55 call_dll_entry_point+0x15() in ntdll (0x0034fcc4)
  5 0x7bc4592d in ntdll (+0x3592d) (0x0034fd54)
  6 0x7bc45d88 in ntdll (+0x35d88) (0x0034fd84)
  7 0x7b8733ff ExitProcess+0x1f() in kernel32 (0x0034fda4)
  8 0x00401abe in hl2 (+0x1abe) (0x0034fddc)
  9 0x00401c41 in hl2 (+0x1c41) (0x0034ff08)
  10 0x7b87618e in kernel32 (+0x5618e) (0x0034ffe8)
  11 0xf7e78937 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)



```

---

### Post by Beren Camlost on 2007-12-16
> **123qwe said:**
> ```
tsuyoshi@tsuyoshi-desktop:~$ **cd ~/.wine/drive_c/Program\ Files/Steam && WINEDEBUG=-all wine steam -applaunch 240 -dxlevel 70**
```You are trying to run cs:s with DirectX 7.0 (-dxlevel 70). I don't think cs:s will run under that, so try with newer versions of DirectX (setting the value to such as 80, 81 or 90).

---

### Post by 123qwe on 2007-12-17
when i set it to any of those directX versions i still get the same error =[

anyone else knows a possible fix?

---

### Post by Beren Camlost on 2007-12-17
What is causing the unhandled exception in this case is this:

```

**[B]Failed to verifiy SteamService.dll**[/B]
```

My first assumption was that this was caused by trying to load CS:S with a DirectX version I don't think CS:S supports, but obviously I was wrong. I think you should do a search to see if SteamService.dll is actually present on your system.

Other than that I'm cluesless. Everywhere I've searched I found noone with a similar error.


---

### Post by Brynster on 2007-12-18
```
Failed to verifiy SteamService.dll
```

is almost certainly the issue, I would firstly find the .dll in the steam folder in wine and delete, launch steam and it should update the .dll with a new copy, if that doesn't work then you could end up having to reinstall Steam.

---

### Post by 123qwe on 2007-12-18
ok i only got that SteamService.dll problem when i tried running wine as vista, it said it need the dll >_<

but its ok i installed 1.6 :D

win! lol

---

