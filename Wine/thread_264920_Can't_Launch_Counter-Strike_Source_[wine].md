---
title: "Can't Launch Counter-Strike Source [wine]"
date: 2006-09-25
forum: Wine
---

### Post by delta99 on 2006-09-25
hello, me again :p ](*,) 

well thanks to members here, helped me alot with steam/wine.

yet again, im getting there... but some other problem lays ahead.

Basically steam is fine. I finished downloading Counter-Strike Source via steam but when I go to launch it, nothing happens.


I get this message when I click "launch game":
[IMG]http://xs107.xs.to/xs107/06391/vid-error.jpg[/IMG]

I then click "Continue anyway"... I do get the "preparing the launch" box as you see before css opens... but that just dissapears and css does not launch.

Any ideas please ? 
would be most grateful, thank you :)

My terminal data:

```
delta@delta-desktop:~$ cd "/home/delta/.wine/c/Program Files/Steam"
delta@delta-desktop:~/.wine/c/Program Files/Steam$ WINEDEBUG="fixme-all" wine Steam
wine: Unhandled page fault on read access to 0x80000bf4 at address 0x7d7b69b2 (thread 003d), starting debugger...
WineDbg starting on pid 0x3c
Unhandled exception: page fault on read access to 0x80000bf4 in 32-bit code (0x7d7b69b2).
In 32 bit mode.
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file rpcrt4.dbg ("rpcrt4.dbg")
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7d7b69b2 ESP:7fb9d22c EBP:7fb9d26c EFLAGS:00010282(   - 00      - RIS1)
 EAX:0000003c EBX:00000000 ECX:80000be0 EDX:00000014
 ESI:80000be0 EDI:00000000
Stack dump:
0x7fb9d22c:  000000b8 7d7b67e6 00000000 7d7b1dc3
0x7fb9d23c:  7d7b1ba1 00000000 7ffd41b0 7fd6c080
0x7fb9d24c:  7f7e7d7c 00000000 7fb9d23c 7fb9cde8
0x7fb9d25c:  7fb9ff10 7d7ba6dc 7d7f6488 ffffffff
0x7fb9d26c:  7fb9d28c 7ffa00b5 7d7b0000 00000001
0x7fb9d27c:  00000000 00000000 00000000 7ffd41b0
0200: sel=1007 base=7fe50000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7d7b69b2 NdrServerMarshall+0x430 in rpcrt4 (0x7d7b69b2)
  2 0x7ffa00b5 call_dll_entry_point+0x15 in ntdll (0x7ffa00b5)
  3 0x7ffa0e6a in ntdll (+0x20e6a) (0x7ffa0e6a)
  4 0x7ffa176c in ntdll (+0x2176c) (0x7ffa176c)
  5 0x7ffa1742 in ntdll (+0x21742) (0x7ffa1742)
  6 0x7ffa3eb7 LdrLoadDll+0x77 in ntdll (0x7ffa3eb7)
  7 0x7fc515f9 in kernel32 (+0x415f9) (0x7fc515f9)
  8 0x7fc5175a LoadLibraryExW+0x4a in kernel32 (0x7fc5175a)
  9 0x7fc5187f LoadLibraryExA+0x2f in kernel32 (0x7fc5187f)
  10 0x7fc518ad LoadLibraryA+0x1d in kernel32 (0x7fc518ad)
fixme:dbghelp:sffip_cb NIY on 'U:\rel\hl2\src\filesystem\filesystem_stdio\Release_Steam\filesystem_steam.pdb'
  11 0x7e122250 CreateInterface+0x160 in filesystem_steam (0x7e122250)
  12 0x7e13dae0 in filesystem_steam (+0x3dae0) (0x7e13dae0)
  13 0x7e1018b0 in filesystem_steam (+0x18b0) (0x7e1018b0)
0x7d7b69b2 NdrServerMarshall+0x430 in rpcrt4: cmpl      0x14(%esi),%eax
Modules:
Module  Address                 Debug info      Name (74 modules)
PE      0x00400000-0041c000     Deferred        hl2
PE      0x10000000-10030000     Deferred        launcher
PE      0x20000000-2030b000     Deferred        steam
PE      0x628c0000-628d9000     Deferred        parsifal
PE      0x65f00000-65fc2000     Deferred        ole32
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
PE      0x7d7b0000-7d803000     Export          rpcrt4
PE      0x7d810000-7d90e000     Deferred        datamodel
ELF     0x7dd50000-7dd80000     Deferred        uxtheme<elf>
  \-PE  0x7dd60000-7dd80000     \               uxtheme
ELF     0x7de91000-7dea5000     Deferred        mswsock<elf>
  \-PE  0x7dea0000-7dea5000     \               mswsock
ELF     0x7dea5000-7deb9000     Deferred        lz32<elf>
  \-PE  0x7deb0000-7deb9000     \               lz32
ELF     0x7deb9000-7ded1000     Deferred        version<elf>
  \-PE  0x7dec0000-7ded1000     \               version
ELF     0x7ded1000-7df80000     Deferred        comctl32<elf>
  \-PE  0x7dee0000-7df80000     \               comctl32
PE      0x7df80000-7dfc4000     Deferred        msvcrt
PE      0x7dfd0000-7e035000     Deferred        shlwapi
ELF     0x7e041000-7e100000     Deferred        shell32<elf>
  \-PE  0x7e060000-7e100000     \               shell32
PE      0x7e100000-7e14d000     Export          filesystem_steam
PE      0x7e280000-7e2b6000     Deferred        tier0
PE      0x7e2c0000-7e2de000     Deferred        vstdlib
ELF     0x7e2e0000-7e2fe000     Deferred        iphlpapi<elf>
  \-PE  0x7e2f0000-7e2fe000     \               iphlpapi
ELF     0x7e2fe000-7e327000     Deferred        ws2_32<elf>
  \-PE  0x7e310000-7e327000     \               ws2_32
ELF     0x7e327000-7e340000     Deferred        wsock32<elf>
  \-PE  0x7e330000-7e340000     \               wsock32
ELF     0x7e4a4000-7e4ad000     Deferred        libxcursor.so.1
ELF     0x7e4ad000-7e4b5000     Deferred        libxrender.so.1
ELF     0x7e4bf000-7e4da000     Deferred        imm32<elf>
  \-PE  0x7e4d0000-7e4da000     \               imm32
ELF     0x7e4da000-7ec9c000     Deferred        libglcore.so.1
ELF     0x7ec9c000-7ed21000     Deferred        libgl.so.1
ELF     0x7ed21000-7ee07000     Deferred        libx11.so.6
ELF     0x7ee07000-7ee1f000     Deferred        libice.so.6
ELF     0x7ee1f000-7ee9c000     Deferred        winex11<elf>
  \-PE  0x7ee30000-7ee9c000     \               winex11
ELF     0x7ee9c000-7eebb000     Deferred        libexpat.so.1
ELF     0x7eebb000-7eee9000     Deferred        libfontconfig.so.1
ELF     0x7eee9000-7eefd000     Deferred        libz.so.1
ELF     0x7eefd000-7ef66000     Deferred        libfreetype.so.6
ELF     0x7ef66000-7efa2000     Deferred        advapi32<elf>
  \-PE  0x7ef70000-7efa2000     \               advapi32
ELF     0x7f077000-7f977000     Deferred        gdi32<elf>
  \-PE  0x7f0c0000-7f977000     \               gdi32
ELF     0x7f977000-7fa90000     Deferred        user32<elf>
  \-PE  0x7f990000-7fa90000     \               user32
ELF     0x7fba3000-7fbb0000     Deferred        libxext.so.6
ELF     0x7fbb4000-7fbb9000     Deferred        libxxf86vm.so.1
ELF     0x7fbb9000-7fbc1000     Deferred        libsm.so.6
ELF     0x7fbf4000-7fcf0000     Export          kernel32<elf>
  \-PE  0x7fc10000-7fcf0000     \               kernel32
ELF     0x7fcf6000-7fd00000     Deferred        libgcc_s.so.1
ELF     0x7fe10000-7fe15000     Deferred        libxxf86dga.so.1
ELF     0x7fe15000-7fe1f000     Deferred        libnss_files.so.2
ELF     0x7fe1f000-7fe28000     Deferred        libnss_nis.so.2
ELF     0x7fe28000-7fe3d000     Deferred        libnsl.so.1
ELF     0x7fe3d000-7fe46000     Deferred        libnss_compat.so.2
ELF     0x7fe4a000-7fe4e000     Deferred        libxfixes.so.3
ELF     0x7fe53000-7fe75000     Deferred        libm.so.6
ELF     0x7fe75000-7ff6c000     Deferred        libwine_unicode.so.1
ELF     0x7ff6c000-7ffe0000     Export          ntdll<elf>
  \-PE  0x7ff80000-7ffe0000     \               ntdll
ELF     0xb7dd0000-b7dd3000     Deferred        libxau.so.6
ELF     0xb7de0000-b7de3000     Deferred        libdl.so.2
ELF     0xb7de3000-b7f12000     Deferred        libc.so.6
ELF     0xb7f13000-b7f25000     Deferred        libpthread.so.0
ELF     0xb7f25000-b7f3f000     Deferred        libwine.so.1
ELF     0xb7f3f000-b7f41000     Deferred        libnvidia-tls.so.1
ELF     0xb7f4c000-b7f62000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000003c (D) C:\Program Files\Steam\steamapps\opsnake\counter-strike source\hl2.exe
        0000003e    2
        0000003d    0 <==
00000008
        0000003b    0
        0000003a    0
        00000038    0
        00000037    0
        00000036    1
        00000035    0
        00000034    1
        00000033    0
        00000032    1
        00000031    0
        00000030    1
        0000002f    0
        0000002e    1
        0000002d    0
        0000002c    1
        0000002b    0
        0000002a    1
        00000029    0
        00000028    1
        00000025    0
        00000024    0
        00000023    0
        00000022    0
        00000021    0
        0000001d    0
        0000001c    0
        0000001a    0
        00000019    1
        00000017    0
        00000014    0
        00000013    0
        00000012    1
        00000011    0
        00000010    0
        0000000f    0
        0000000e    0
        0000000d    0
        0000000b    0
        0000000a    0
        00000009    0
WineDbg terminated on pid 0x3c
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file ole32.dbg ("ole32.dbg")err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file oleaut32.dbg ("oleaut32.dbg")
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file dll\crypt32.dbg ("dll\\crypt32.dbg")
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file dll\msoss.dbg ("dll\\msoss.dbg")
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file rpcrt4.dbg ("rpcrt4.dbg")
wine: Call from 0x7fc43ed0 to unimplemented function dbghelp.dll.SymGetModuleBase64, aborting
Shutting down. . .
300client callback thread error
Killed
delta@delta-desktop:~/.wine/c/Program Files/Steam$


```


I read another similar problem thread and someone suggested to check the video drivers are installed correctly. Do you think that's my problem?

And how does one check video drivers are installed correctly?

---

### Post by pete224 on 2008-02-26
All you have to do is in wine config choose a compatible windows version. You might have to reinstall the game tho :(

---

### Post by Tim0miT on 2008-02-27
make sure you have the most up to date wine version. Also, try setting steam.exe to Win2000 and HL2.exe to XP

Thats what i did and it works fine:guitar:

---

