---
title: "WoW not loading, and yes I did search the forums and read the sticky."
date: 2012-12-30
forum: Wine
---

### Post by Crossbow on 2012-12-30
All right, I posted this on the &#8220;how to&#8221; thread and got no reply. I posted it on the Battlenet forums but no help there either. 

YES, I DID search the forums. I have been searching them for 2 days. I can find many people having similar problems but none are solved, and the people trying to help just keep pointing back at the installation guide. That is not helpful because the game IS installed correctly. Until now it has been working. 

It was working until Friday 12/21. That day my graphics driver, Nvidia, decided I could no longer use the correct resolution. I replaced Nvidia-Current with Nvidia-173 and that fixed the resolution problem but now I have a new one: 

When I launch WoW I get the first page, where it tells you whether the game is up to date and you can select full screen or windowed. When I click "Play" it just shuts the window. No error message, just shuts the WoW window and does nothing else.

Ubuntu 12.04
Dell Inspiron 530
Nvidia-173
Wine verison 1.5.12 (tried with setting for Windows XP and 7)

Here is the error report: 

> ================================================== ============================
World of WarCraft: Retail Build (build 16357)

Exe: C:\Program Files\World of Warcraft\Wow.exe
Time: Dec 29, 2012 3:17:44.315 PM
User: anna
Computer: anna-desktop
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal exception!

Program: C:\Program Files\World of Warcraft\Wow.exe
ProcessID: 74
Exception: 0xC0000005 (ACCESS_VIOLATION) at 0073:69AB96C5

The instruction at "0x69AB96C5" referenced memory at "0xFFFFFFFF".
The memory could not be "read".

WoWBuild: 16357
Version: 5.1.0
Type: WoW
Platform: X86
Session Time(hh:mm:ss): 00:00:00
Time in World(hh:mm:ss): 00:00:00
Number of Char Logins: 0

Settings: 
SET locale "enUS"
SET Sound_EnableHardware "0"
SET installLocale "enUS"

----------------------------------------
Installation settings:
----------------------------------------
UID: wow_enus
Expansion Level: 4
PTR: 0
Beta: 0
PatchURL: 'http://enUS.patch.battle.net:1119/patch'
ProductCode: 'WoW'

----------------------------------------
GxInfo
----------------------------------------
No GX Device Created
Desktop Display List:
Device Name: \\.\DISPLAY1
Device String: X11 Windowing System
State Flags: 0x00000015
Device ID: PCI\VEN_0000&DEV_0000

Installed DX9 Version:
File Version: 5.3.1.904
------------------------------------------------------------------------------

----------------------------------------
x86 Registers
----------------------------------------

EAX=FFFFFFFF EBX=00000000 ECX=7D3F2058 EDX=00000001 ESI=7D4632D0
EDI=00000008 EBP=00000001 ESP=0187EDAC EIP=69AB96C5 FLG=00210286
CS =0073 DS =007B ES =007B SS =007B FS =0033 GS =003B

----------------------------------------
Stack Trace (Manual)
----------------------------------------

Address Frame Logical addr Module

Showing 9/9 threads...

--- Thread ID: 87 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 86 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 85 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 84 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 83 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 82 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 81 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 80 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 75 [Current Thread] ---
69AB96C5 00000001 0000:00000000 <unknown>

----------------------------------------
Stack Trace (Using DBGHELP.DLL)
----------------------------------------

Showing 9/9 threads...

--- Thread ID: 87 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 86 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 85 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 84 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 83 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 82 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 81 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 80 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 75 [Current Thread] ---



----------------------------------------
Loaded Modules
----------------------------------------

DBG-MODULE<00400000 00F51000 "Wow.exe" "Wow.pdb" 0 {5aa2aa29-afb6-4524-b8907c5fdc6893da} 1 1354589228>
DBG-MODULE<68350000 00144000 "user32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<684A0000 000C6000 "gdi32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68570000 00060000 "advapi32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<685E0000 0000A000 "version.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<685F0000 00070000 "wininet.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68680000 0001D000 "mpr.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<686B0000 00089000 "msvcrt.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68750000 00210000 "shell32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68970000 000F4000 "comctl32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68A70000 00072000 "rpcrt4.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68AF0000 0001C000 "msacm32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68B20000 00123000 "wined3d.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68C50000 00017000 "imm32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68C70000 0002B000 "ws2_32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68CA0000 00017000 "dinput8.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68CC0000 00063000 "setupapi.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68D30000 00032000 "winspool.drv" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68D70000 00007000 "hid.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68E20000 00080000 "winex11.drv" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68FA0000 00030000 "uxtheme.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<69000000 000DF000 "opengl32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<69190000 0005B000 "dbghelp.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<691F0000 0000F000 "psapi.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<6D2E0000 00114000 "ole32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<71400000 000AD000 "winmm.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<73C40000 00035000 "d3d9.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<77F60000 00076000 "shlwapi.dll" "shlwapi.pdb" 0 {658b2b7c-8638-42a0-be311e436027f6e3} 2 1158222689>
DBG-MODULE<7B810000 0022B000 "KERNEL32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7BC10000 000C2000 "ntdll.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>

----------------------------------------
Memory Dump
----------------------------------------

Code: 32 bytes starting at (EIP = 69AB96C5 - 10)

69AB96B5: 1C 8B 5C 24 20 89 74 24 08 89 4C 24 04 89 1C 24 ..\$ .t$..L$...$
* = addr ** * 
69AB96C5: FF D0 8B 54 24 1C 8D 46 10 89 44 24 04 8B 42 04 ...T$..F..D$..B.


Stack: 1024 bytes starting at (ESP = 0187EDAC - 20)

0187ED80: B4 22 3F 7D 90 18 3F 7D D8 0A 47 7D C8 0A 47 7D ."?}..?}..G}..G}
0187ED90: 08 00 00 00 01 00 00 00 00 00 00 00 D0 32 46 7D .............2F}
0187EDA0: 08 00 00 00 01 00 00 00 AC 96 AB 69 00 00 00 00 ...........i....
* = addr ** * 
0187EDA0: 08 00 00 00 01 00 00 00 AC 96 AB 69 00 00 00 00 ...........i....
0187EDB0: 58 20 3F 7D D0 32 46 7D 01 00 00 00 08 C0 62 B7 X ?}.2F}......b.
0187EDC0: 00 00 00 00 01 00 00 00 58 20 3F 7D 00 00 00 00 ........X ?}....
0187EDD0: 01 00 00 00 01 00 00 00 00 00 00 00 D0 32 46 7D .............2F}
0187EDE0: 98 00 00 00 1C 69 43 7D B6 9B AB 69 00 00 00 00 .....iC}...i....
0187EDF0: 58 20 3F 7D D0 32 46 7D 01 00 00 00 10 B7 01 00 X ?}.2F}........
0187EE00: 01 00 00 00 01 00 00 00 00 00 00 00 18 35 46 7D .............5F}
0187EE10: 01 00 00 00 01 00 00 00 00 00 00 00 80 18 3F 7D ..............?}
0187EE20: 54 00 00 04 00 00 00 00 1D A7 14 69 00 00 00 00 T..........i....
0187EE30: 58 20 3F 7D 00 00 00 00 01 00 00 00 10 B7 3C 7D X ?}..........<}
0187EE40: 54 00 00 04 87 00 00 00 E2 EA 14 69 54 00 00 04 T..........iT...
0187EE50: 54 00 00 04 87 00 00 00 08 7B 12 69 90 1D 45 7D T........{.i..E}
0187EE60: 54 00 00 04 00 00 00 00 00 00 00 00 00 00 00 00 T...............
0187EE70: 98 22 46 7D 00 20 69 B7 C7 8A 12 69 10 B7 3C 7D ."F}. i....i..<}
0187EE80: 54 00 00 04 00 00 00 00 E4 57 76 69 18 3D 43 7D T........Wvi.=C}
0187EE90: 00 00 00 00 00 00 00 00 01 00 00 00 98 71 54 7D .............qT}
0187EEA0: 00 00 00 00 00 00 00 00 CC 75 79 69 00 20 69 B7 .........uyi. i.
0187EEB0: 98 22 46 7D 08 00 00 00 00 20 69 01 00 00 00 00 ."F}..... i.....
0187EEC0: 01 00 00 00 01 00 00 00 01 00 00 00 00 00 00 00 ................
0187EED0: 00 00 00 00 00 20 69 01 01 00 00 00 00 20 69 B7 ..... i...... i.
0187EEE0: 00 00 00 00 E0 EF 87 01 DA 5D 76 69 00 20 69 B7 .........]vi. i.
0187EEF0: 80 A0 46 7D 01 00 00 00 01 00 00 00 00 00 00 00 ..F}............
0187EF00: 00 00 80 BF 00 00 80 BF 98 C6 6A B7 8C C6 6A B7 ..........j...j.
0187EF10: 01 00 00 01 01 00 00 00 02 00 00 00 F4 78 14 00 .............x..
0187EF20: 00 00 00 00 7F B6 BE 01 F4 EF C3 68 F4 78 14 00 ...........h.x..
0187EF30: E0 EF 87 01 04 F0 87 01 97 D5 BE 68 01 00 00 00 ...........h....
0187EF40: E0 EF 87 01 00 00 00 00 00 00 00 00 BC DB FB 69 ...............i
0187EF50: D0 80 C0 68 9D 78 B6 68 F4 EF C3 68 01 00 00 00 ...h.x.h...h....
0187EF60: F4 78 14 00 04 F0 87 01 43 CE B6 68 F4 78 14 00 .x......C..h.x..
0187EF70: C0 DB 20 6A 05 00 00 00 DE 10 00 00 23 04 00 00 .. j........#...
0187EF80: 00 00 02 00 C4 EF 87 01 94 A1 14 00 F4 78 14 00 .............x..
0187EF90: 20 06 C2 68 F0 88 00 00 0C FC C1 68 00 00 00 00 ..h.......h....
0187EFA0: F4 6F 0D 69 C4 EF 87 01 74 FE 06 69 E0 BE 0D 69 .o.i....t..i...i
0187EFB0: E0 78 14 00 32 81 C0 68 D0 85 C3 68 C0 DB 20 6A .x..2..h...h.. j
0187EFC0: 23 04 00 00 DE 10 00 00 05 00 00 00 3C 03 00 00 #...........<...
0187EFD0: 78 B1 14 00 00 04 00 00 FF FF FE 03 08 00 00 00 x...............
0187EFE0: 01 00 00 00 02 00 00 00 02 00 00 00 3C 03 00 00 ............<...
0187EFF0: 01 00 00 00 FD A0 B6 68 F4 EF C3 68 01 00 00 00 .......h...h....
0187F000: 60 F4 87 01 A4 F4 87 01 B7 E1 B6 68 F4 78 14 00 `..........h.x..
0187F010: DE 10 00 00 38 F4 87 01 38 F4 87 01 0A 00 00 00 ....8...8.......
0187F020: 0A 00 00 00 0A 00 00 00 0A 00 00 00 00 00 00 00 ................
0187F030: 00 00 00 00 00 00 00 00 00 00 00 00 8B C5 3B 7D ..............;}
0187F040: 00 00 00 00 88 52 14 00 88 F0 87 01 FF FF FF FF .....R..........
0187F050: E9 A5 1B 68 05 00 00 00 E0 EF 87 01 00 F2 87 01 ...h............
0187F060: 00 00 00 00 00 00 00 00 05 00 00 00 E0 35 46 7D .............5F}
0187F070: F4 9F 2E 68 02 00 00 00 E0 9A 2E 68 E0 78 14 00 ...h.......h.x..
0187F080: F4 78 14 00 D0 78 14 00 38 F4 87 01 40 A4 2E 68 .x...x..8...@..h
0187F090: F4 9F 2E 68 AF 51 2A 68 00 00 00 00 01 00 00 00 ...h.Q*h........
0187F0A0: AB 0F 19 68 F0 F0 87 01 53 FA 2E 68 CC F0 87 01 ...h....S..h....
0187F0B0: F4 1F 2F 68 69 53 41 7D 3C FA 2E 68 48 B2 3B 7D ../hiSA}<..hH.;}
0187F0C0: 58 F2 2E 68 00 00 00 00 20 EF 2E 68 FF 35 46 7D X..h.... ..h.5F}
0187F0D0: 49 FA 2E 68 E0 35 46 7D AF 51 2A 68 4C F1 87 01 I..h.5F}.Q*hL...
0187F0E0: E9 A5 1B 68 96 54 14 00 D1 98 45 00 00 00 00 00 ...h.T....E.....
0187F0F0: 00 00 00 00 A2 56 41 7D 02 00 00 00 58 00 00 00 .....VA}....X...
0187F100: F4 FF 12 68 62 00 00 00 68 53 41 7D 4C F1 87 01 ...hb...hSA}L...
0187F110: F8 5F 00 68 20 F3 87 01 68 53 41 7D 40 A4 2E 68 ._.h ...hSA}@..h
0187F120: F9 09 24 68 00 00 00 00 00 00 00 00 AC F1 87 01 ..$h............
0187F130: CE 1F 22 68 C0 55 14 00 B0 63 14 00 00 00 00 00 .."h.U...c......
0187F140: F4 FF 12 68 18 F2 87 01 00 00 00 00 AC F1 87 01 ...h............
0187F150: AD 66 00 68 00 00 00 00 00 00 00 00 20 F3 87 01 .f.h........ ...
0187F160: 00 01 00 00 00 00 00 00 F0 34 12 68 20 F3 87 01 .........4.h ...
0187F170: 18 F2 87 01 04 00 00 00 98 56 41 7D BC 56 41 7D .........VA}.VA}
0187F180: 0A 00 00 00 00 00 00 00 E0 FB C4 7B 1C F2 87 01 ...........{....
0187F190: 00 5C B5 EF 00 F2 87 01 E2 9F 00 68 F4 FF 12 68 .\.........h...h
0187F1A0: 10 00 00 00 E4 F1 87 01 7A A9 00 68 00 00 00 00 ........z..h....


------------------------------------------------------------------------------
Percent memory used: 61
Total physical memory: 1048584192
Free physical memory: 408907776
Page file: 4124798976
Total virtual memory: 3221159935
Free virtual memory: 3221094399
------------------------------------------------------------------------------

List of running Wow.exe processes

Could not list processes

List of running Agent.exe processes

Could not list processes

I tried launching it through the terminal and got this result: 

> anna@anna-desktop:~$ env WINEPREFIX="/home/anna/.wine" wine "C:\Program Files\World of Warcraft\Wow.exe" -opengl

^[[Dfixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:process:GetLogicalProcessorInformation (0x187f754,0x187fd54): stub

fixme:process:GetLogicalProcessorInformation (0x32c008,0x32c608): stub
fixme:process:GetLogicalProcessorInformation (0x32bfd8,0x32c5d8): stub
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:process:GetLogicalProcessorInformation (0x197e338,0x197e938): stub
fixme:process:GetLogicalProcessorInformation (0x197e308,0x197e908): stub
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:process:GetLogicalProcessorInformation (0x197e338,0x197e938): stub
fixme:process:GetLogicalProcessorInformation (0x197e308,0x197e908): stub
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:process:GetLogicalProcessorInformation (0x197e338,0x197e938): stub
fixme:process:GetLogicalProcessorInformation (0x197e308,0x197e908): stub
fixme:process:GetLogicalProcessorInformation (0x187f57c,0x187fb7c): stub
fixme:process:GetLogicalProcessorInformation (0x187f54c,0x187fb4c): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x187ed28,0x00000000), stub!
fixme:d3d:init_driver_info Unhandled OS version 6.2, reporting Win 7.
fixme:win:EnumDisplayDevicesW ((null),0,0x187ebc8,0x00000000), stub!
fixme:d3d:init_driver_info Unhandled OS version 6.2, reporting Win 7.
fixme:win:EnumDisplayDevicesW ((null),0,0x187bfb0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x187bfb0,0x00000000), stub!
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
wine: Unhandled page fault on read access to 0xefdd7818 at address 0x69a908d2 (thread 0009), starting debugger...


... and the previous error report plus this new one: 

> Unhandled exception: page fault on read access to 0xefdd7818 in 32-bit code (0x69a908d2).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:69a908d2 ESP:0187ed5c EBP:7ce81f2b EFLAGS:00010216(  R- --  I   -A-P- )
 EAX:efdd7800 EBX:7cee97b8 ECX:00000001 EDX:7ce673d0
 ESI:7cee97a8 EDI:00000008
Stack dump:
0x0187ed5c:  00000000 7ce6743c 7cee1300 00000000
0x0187ed6c:  00000001 00000001 01011248 0000006f
0x0187ed7c:  efdd7800 7ce6743c 7ce66b90 7cee97b8
0x0187ed8c:  7cee97a8 00000008 00000001 69a90caa
0x0187ed9c:  7ce673d0 7ce81f2b 00000000 69ae26dd
0x0187edac:  7ce673d0 7cee97b8 00000008 00000001
Backtrace:
=>0 0x69a908d2 in libglcore.so.1 (+0x5968d2) (0x7ce81f2b)
0x69a908d2: movl	0x18(%eax),%edx
Modules:
Module	Address			Debug info	Name (114 modules)
PE	  400000- 1351000	Deferred        wow
ELF	68000000-68022000	Deferred        ld-linux.so.2
ELF	68022000-68166000	Dwarf           libwine.so.1
ELF	68166000-68181000	Deferred        libpthread.so.0
ELF	68181000-6832b000	Deferred        libc.so.6
ELF	6832b000-68330000	Deferred        libdl.so.2
ELF	68330000-6834a000	Deferred        libnsl.so.1
ELF	6834a000-68356000	Deferred        libnss_nis.so.2
ELF	68356000-68428000	Deferred        gdi32<elf>
  \-PE	68360000-68428000	\               gdi32
ELF	68428000-68442000	Deferred        version<elf>
  \-PE	68430000-68442000	\               version
ELF	68442000-68458000	Deferred        libz.so.1
ELF	68458000-6845a000	Deferred        libnvidia-tls.so.1
ELF	6845b000-685ad000	Deferred        user32<elf>
  \-PE	68470000-685ad000	\               user32
ELF	685ad000-68617000	Deferred        advapi32<elf>
  \-PE	685c0000-68617000	\               advapi32
ELF	68617000-686b3000	Deferred        msvcrt<elf>
  \-PE	68630000-686b3000	\               msvcrt
ELF	686b3000-688da000	Deferred        shell32<elf>
  \-PE	686c0000-688da000	\               shell32
ELF	688da000-689de000	Deferred        comctl32<elf>
  \-PE	688e0000-689de000	\               comctl32
ELF	689de000-68b05000	Deferred        ole32<elf>
  \-PE	689f0000-68b05000	\               ole32
ELF	68b05000-68b83000	Deferred        rpcrt4<elf>
  \-PE	68b10000-68b83000	\               rpcrt4
ELF	68b83000-68bad000	Deferred        msacm32<elf>
  \-PE	68b90000-68bad000	\               msacm32
ELF	68bad000-68ce4000	Deferred        wined3d<elf>
  \-PE	68bc0000-68ce4000	\               wined3d
ELF	68ce4000-68d08000	Deferred        imm32<elf>
  \-PE	68cf0000-68d08000	\               imm32
ELF	68d08000-68d74000	Deferred        setupapi<elf>
  \-PE	68d10000-68d74000	\               setupapi
ELF	68d74000-68db3000	Deferred        winspool<elf>
  \-PE	68d80000-68db3000	\               winspool
ELF	68db3000-68dc8000	Deferred        hid<elf>
  \-PE	68dc0000-68dc8000	\               hid
ELF	68dc8000-68dea000	Deferred        libncurses.so.5
ELF	68dea000-68e09000	Deferred        libtinfo.so.5
ELF	68e09000-68ea3000	Deferred        libfreetype.so.6
ELF	68ea3000-68eac000	Deferred        libsm.so.6
ELF	68eac000-68ebe000	Deferred        libxext.so.6
ELF	68ebe000-68ed8000	Deferred        libice.so.6
ELF	68ed8000-68ede000	Deferred        libuuid.so.1
ELF	68ede000-68eff000	Deferred        libxcb.so.1
ELF	68eff000-68f03000	Deferred        libxau.so.6
ELF	68f03000-68f0a000	Deferred        libxdmcp.so.6
ELF	68f0a000-68f10000	Deferred        libxxf86vm.so.1
ELF	68f10000-68f1a000	Deferred        libxrender.so.1
ELF	68f1a000-68f1e000	Deferred        libxcomposite.so.1
ELF	68f1e000-68f48000	Deferred        libexpat.so.1
ELF	68f48000-68f4e000	Deferred        libxfixes.so.3
ELF	68f4e000-68f84000	Deferred        uxtheme<elf>
ELF	68f84000-68fd7000	Deferred        libcups.so.2
ELF	68fd7000-69015000	Deferred        libgssapi_krb5.so.2
ELF	69015000-690d9000	Deferred        libgnutls.so.26
ELF	690d9000-690e7000	Deferred        libavahi-common.so.3
ELF	690e7000-690f9000	Deferred        libavahi-client.so.3
ELF	690f9000-691c8000	Deferred        libkrb5.so.3
ELF	691c8000-691f0000	Deferred        libk5crypto.so.3
ELF	691f0000-691f5000	Deferred        libcom_err.so.2
ELF	691f5000-691fe000	Deferred        libkrb5support.so.0
ELF	691fe000-69210000	Deferred        libtasn1.so.3
ELF	69210000-69295000	Deferred        libgcrypt.so.11
ELF	69295000-692a7000	Deferred        libp11-kit.so.0
ELF	692a7000-692ab000	Deferred        libkeyutils.so.1
ELF	692ab000-692c3000	Deferred        libresolv.so.2
ELF	692c3000-692c8000	Deferred        libgpg-error.so.0
ELF	692c8000-692d1000	Deferred        librt.so.1
ELF	692d1000-692d5000	Deferred        libnss_mdns4_minimal.so.2
ELF	692d6000-69302000	Deferred        libm.so.6
ELF	69302000-6934b000	Deferred        libdbus-1.so.3
ELF	6934b000-69352000	Deferred        libnss_dns.so.2
ELF	69352000-69456000	Deferred        opengl32<elf>
  \-PE	69370000-69456000	\               opengl32
ELF	69456000-694fa000	Deferred        libgl.so.1
ELF	694fa000-6a23a000	Export          libglcore.so.1
ELF	6a23c000-6a2a0000	Deferred        dbghelp<elf>
  \-PE	6a240000-6a2a0000	\               dbghelp
ELF	6a2a0000-6a2b4000	Deferred        psapi<elf>
  \-PE	6a2b0000-6a2b4000	\               psapi
ELF	6a2b4000-6a2d2000	Deferred        libgcc_s.so.1
ELF	6aa06000-6aa2d000	Deferred        mpr<elf>
  \-PE	6aa10000-6aa2d000	\               mpr
ELF	6c056000-6c092000	Deferred        d3d9<elf>
  \-PE	6c060000-6c092000	\               d3d9
ELF	6d3e8000-6d3f5000	Deferred        libnss_files.so.2
ELF	6e19f000-6e1aa000	Deferred        libxcursor.so.1
ELF	6e6df000-6e6ef000	Deferred        libxi.so.6
ELF	6e79f000-6e7b2000	Deferred        gnome-keyring-pkcs11.so
ELF	700e8000-700ec000	Deferred        libxinerama.so.1
ELF	747ed000-7487c000	Deferred        winex11<elf>
  \-PE	74800000-7487c000	\               winex11
ELF	7612b000-76147000	Deferred        dinput8<elf>
  \-PE	76130000-76147000	\               dinput8
ELF	767a0000-767a9000	Deferred        libnss_compat.so.2
ELF	7723e000-772f0000	Deferred        winmm<elf>
  \-PE	77250000-772f0000	\               winmm
ELF	775fc000-77730000	Deferred        libx11.so.6
PE	77f60000-77fd6000	Deferred        shlwapi
ELF	7835e000-783d4000	Deferred        wininet<elf>
  \-PE	78370000-783d4000	\               wininet
ELF	793c5000-793ce000	Deferred        libxrandr.so.2
ELF	7aee4000-7af18000	Deferred        ws2_32<elf>
  \-PE	7aef0000-7af18000	\               ws2_32
ELF	7b40a000-7b43e000	Deferred        libfontconfig.so.1
ELF	7b800000-7ba3b000	Deferred        kernel32<elf>
  \-PE	7b810000-7ba3b000	\               kernel32
ELF	7bc00000-7bcd2000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcd2000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\World of Warcraft\Wow.exe
	00000009    0 <==
0000000e services.exe
	00000020    0
	0000001f    0
	00000019    0
	00000018    0
	00000017    0
	00000015    0
	00000010    0
	0000000f    0
00000012 winedevice.exe
	0000001b    0
	0000001a    0
	00000014    0
	00000013    0
0000001c plugplay.exe
	00000021    0
	0000001e    0
	0000001d    0
00000022 explorer.exe
	00000023    0
0000002d WowError.exe
	0000002e    0
System information:
    Wine build: wine-1.5.12
    Platform: i386
    Host system: Linux
    Host version: 3.2.0-35-generic

---

### Post by Crossbow on 2012-12-30
I'm pretty sure this is a driver problem, but I noticed that although the package manager said I installed Wine 1.4, the config says it is 1.5.12. I uninstalled and reinstalled but I've still got the same situation. However, I haven't changed Wine for months so I still think it's Nvidia, since that is the thing I changed.

---

### Post by dino99 on 2012-12-31
maybe look at this recent bug report:

[https://bugs.launchpad.net/ubuntu/+source/wine/+bug/1094870](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/1094870)

---

### Post by Crossbow on 2012-12-31
Could be part of the problem... I don't really know how to read that bug report or what I need to do.

---

### Post by linuxlizard on 2013-01-01
You might try installing through this software. I use this for almost everything wine because it takes care of all the details for you. 

[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

---

### Post by Crossbow on 2013-01-01
I did actually try reinstalling with playonlinux but still had the problem. I will have to try it again because I don't remember if it gave me any errors duringinstall.

---

### Post by Crossbow on 2013-01-06
Tried reinstalling today. Got an error message: 

ERROR: The shortcut "c:\users\public\start menu\programs\world of warcraft/blizard\technical support link" could not be found. The file "techsupport.url" could not be found.

---

### Post by Crossbow on 2013-01-06
Uninstalled and reinstalled wine. Uninstalled and reinstalled warcraft. It appeared to have worked but...

==============================================================================
World of WarCraft: Retail Build (build 16357)

Exe:      C:\Program Files\World of Warcraft\Wow.exe
Time:     Jan  6, 2013 10:34:01.995 PM
User:     anna
Computer: anna-desktop
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal exception!

Program:	C:\Program Files\World of Warcraft\Wow.exe
ProcessID:	76
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:69B066C5

The instruction at "0x69B066C5" referenced memory at "0xFFFFFFFF".
The memory could not be "read".


WoWBuild: 16357
Version: 5.1.0
Type:  WoW
Platform: X86
Session Time(hh:mm:ss):  00:00:00
Time in World(hh:mm:ss): 00:00:00
Number of Char Logins:  0

Settings: 
SET readTOS "-1"
SET readEULA "-1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET checkAddonVersion "1"
SET locale "enUS"
SET installLocale "enUS"

----------------------------------------
Installation settings:
----------------------------------------
UID:  wow_enus
Expansion Level: 4
PTR: 0
Beta: 0
PatchURL: 'http://enUS.patch.battle.net:1119/patch'
ProductCode: 'WoW'

----------------------------------------
               GxInfo
----------------------------------------
No GX Device Created
Desktop Display List:
Device Name: \\.\DISPLAY1
Device String: X11 Windowing System
State Flags: 0x00000015
Device ID: PCI\VEN_0000&DEV_0000

Installed DX9 Version:
File Version: 5.3.1.904
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=FFFFFFFF  EBX=00000000  ECX=7DDB5048  EDX=00000001  ESI=7DF0B570
EDI=00000008  EBP=00000001  ESP=0187EDAC  EIP=69B066C5  FLG=00010286
CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

Showing 9/9 threads...

--- Thread ID: 89 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 88 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 84 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 81 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 95 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 77 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 23 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 24 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 73 [Current Thread] ---
69B066C5 00000001 0000:00000000 <unknown>

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

Showing 9/9 threads...

--- Thread ID: 89 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 88 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 84 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 81 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 95 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 77 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 23 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 24 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 73 [Current Thread] ---



----------------------------------------
    Loaded Modules
----------------------------------------

DBG-MODULE<00400000 00F51000 "Wow.exe" "Wow.pdb" 0 {5aa2aa29-afb6-4524-b8907c5fdc6893da} 1 1354589228>
DBG-MODULE<68390000 00145000 "user32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<684E0000 000C7000 "gdi32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<685B0000 00061000 "advapi32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68620000 0000B000 "version.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68630000 00071000 "wininet.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<686C0000 0001E000 "mpr.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<686F0000 0008A000 "msvcrt.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68790000 00211000 "shell32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<689B0000 000F5000 "comctl32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68AB0000 000A7000 "winmm.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68B70000 0010E000 "ole32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68C90000 0006C000 "rpcrt4.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68D00000 00026000 "msacm32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68D30000 00032000 "d3d9.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68D70000 00129000 "wined3d.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68EA0000 0001D000 "imm32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68EC0000 00031000 "ws2_32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68F00000 0000D000 "dinput8.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68F20000 00059000 "setupapi.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68F80000 00038000 "winspool.drv" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68FC0000 0000D000 "hid.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<69070000 00086000 "winex11.drv" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<69330000 0002A000 "uxtheme.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<69390000 000EA000 "opengl32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<6A270000 00056000 "dbghelp.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<6A2D0000 0000A000 "psapi.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<77F60000 00076000 "shlwapi.dll" "shlwapi.pdb" 0 {658b2b7c-8638-42a0-be311e436027f6e3} 2 1158222689>
DBG-MODULE<7B810000 0022B000 "KERNEL32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7BC10000 000C2000 "ntdll.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>

----------------------------------------
    Memory Dump
----------------------------------------

Code: 32 bytes starting at (EIP = 69B066C5 - 10)

69B066B5: 1C 8B 5C 24  20 89 74 24  08 89 4C 24  04 89 1C 24  ..\$ .t$..L$...$
* = addr  **                                                  *               
69B066C5: FF D0 8B 54  24 1C 8D 46  10 89 44 24  04 8B 42 04  ...T$..F..D$..B.


Stack: 1024 bytes starting at (ESP = 0187EDAC - 20)

0187ED80: A4 52 DB 7D  80 48 DB 7D  38 8B DF 7D  28 8B DF 7D  .R.}.H.}8..}(..}
0187ED90: 08 00 00 00  01 00 00 00  00 00 00 00  70 B5 F0 7D  ............p..}
0187EDA0: 08 00 00 00  01 00 00 00  AC 66 B0 69  00 00 00 00  .........f.i....
* = addr                                         **                       *   
0187EDA0: 08 00 00 00  01 00 00 00  AC 66 B0 69  00 00 00 00  .........f.i....
0187EDB0: 48 50 DB 7D  70 B5 F0 7D  01 00 00 00  08 80 27 B7  HP.}p..}......'.
0187EDC0: 00 00 00 00  01 00 00 00  48 50 DB 7D  00 00 00 00  ........HP.}....
0187EDD0: 01 00 00 00  01 00 00 00  00 00 00 00  70 B5 F0 7D  ............p..}
0187EDE0: 99 00 00 00  34 99 DF 7D  B6 6B B0 69  00 00 00 00  ....4..}.k.i....
0187EDF0: 48 50 DB 7D  70 B5 F0 7D  01 00 00 00  D8 D4 01 00  HP.}p..}........
0187EE00: 01 00 00 00  01 00 00 00  00 00 00 00  C0 E1 E4 7D  ...............}
0187EE10: 01 00 00 00  01 00 00 00  00 00 00 00  70 48 DB 7D  ............pH.}
0187EE20: 54 00 40 04  00 00 00 00  1D 57 4E 69  00 00 00 00  T.@......WNi....
0187EE30: 48 50 DB 7D  00 00 00 00  01 00 00 00  D8 D4 D8 7D  HP.}...........}
0187EE40: 54 00 40 04  87 00 00 00  E2 9A 4E 69  54 00 40 04  T.@.......NiT.@.
0187EE50: 54 00 40 04  87 00 00 00  08 2B 4C 69  C8 B0 F1 7D  T.@......+Li...}
0187EE60: 54 00 40 04  00 00 00 00  00 00 00 00  00 00 00 00  T.@.............
0187EE70: 38 34 E4 7D  00 C0 29 B7  C7 3A 4C 69  D8 D4 D8 7D  84.}..)..:Li...}
0187EE80: 54 00 40 04  00 00 00 00  E4 27 7B 69  58 79 F1 7D  T.@......'{iXy.}
0187EE90: 00 00 00 00  00 00 00 00  01 00 00 00  B0 DF F0 7D  ...............}
0187EEA0: 00 00 00 00  00 00 00 00  CC 45 7E 69  00 C0 29 B7  .........E~i..).
0187EEB0: 38 34 E4 7D  08 00 00 00  00 C0 29 01  00 00 00 00  84.}......).....
0187EEC0: 01 00 00 00  01 00 00 00  01 00 00 00  00 00 00 00  ................
0187EED0: 00 00 00 00  00 C0 29 01  01 00 00 00  00 C0 29 B7  ......).......).
0187EEE0: 00 00 00 00  E0 EF 87 01  DA 2D 7B 69  00 C0 29 B7  .........-{i..).
0187EEF0: 80 27 E3 7D  01 00 00 00  01 00 00 00  00 00 00 00  .'.}............
0187EF00: 00 00 80 BF  00 00 80 BF  98 66 2B B7  8C 66 2B B7  .........f+..f+.
0187EF10: 01 00 00 01  01 00 00 00  02 00 00 00  EC 76 14 00  .............v..
0187EF20: 00 00 00 00  7F 16 E4 01  F4 4F E9 68  EC 76 14 00  .........O.h.v..
0187EF30: E0 EF 87 01  04 F0 87 01  97 35 E4 68  01 00 00 00  .........5.h....
0187EF40: E0 EF 87 01  00 00 00 00  00 00 00 00  BC AB 00 6A  ...............j
0187EF50: D0 E0 E5 68  9D D8 DB 68  F4 4F E9 68  01 00 00 00  ...h...h.O.h....
0187EF60: EC 76 14 00  04 F0 87 01  43 2E DC 68  EC 76 14 00  .v......C..h.v..
0187EF70: C0 AB 25 6A  05 00 00 00  DE 10 00 00  23 04 00 00  ..%j........#...
0187EF80: 00 00 02 00  C4 EF 87 01  8C 9F 14 00  EC 76 14 00  .............v..
0187EF90: 20 66 E7 68  F0 88 00 00  0C 5C E7 68  00 00 00 00   f.h.....\.h....
0187EFA0: F4 1F 47 69  C4 EF 87 01  74 AE 40 69  E0 6E 47 69  ..Gi....t.@i.nGi
0187EFB0: D8 76 14 00  32 E1 E5 68  D0 E5 E8 68  C0 AB 25 6A  .v..2..h...h..%j
0187EFC0: 23 04 00 00  DE 10 00 00  05 00 00 00  3C 03 00 00  #...........<...
0187EFD0: 00 B3 14 00  00 04 00 00  FF FF FE 03  08 00 00 00  ................
0187EFE0: 01 00 00 00  02 00 00 00  02 00 00 00  3C 03 00 00  ............<...
0187EFF0: 01 00 00 00  FD 00 DC 68  F4 4F E9 68  01 00 00 00  .......h.O.h....
0187F000: 60 F4 87 01  A4 F4 87 01  B7 41 DC 68  EC 76 14 00  `........A.h.v..
0187F010: DE 10 00 00  38 F4 87 01  38 F4 87 01  0A 00 00 00  ....8...8.......
0187F020: 0A 00 00 00  0A 00 00 00  0A 00 00 00  00 00 00 00  ................
0187F030: 00 00 00 00  00 00 00 00  00 00 00 00  8B F5 D7 7D  ...............}
0187F040: 00 00 00 00  B0 51 14 00  88 F0 87 01  FF FF FF FF  .....Q..........
0187F050: E9 75 1F 68  05 00 00 00  E0 EF 87 01  00 F2 87 01  .u.h............
0187F060: 00 00 00 00  00 00 00 00  05 00 00 00  50 D2 E2 7D  ............P..}
0187F070: F4 6F 32 68  02 00 00 00  E0 6A 32 68  D8 76 14 00  .o2h.....j2h.v..
0187F080: EC 76 14 00  C8 76 14 00  38 F4 87 01  40 74 32 68  .v...v..8...@t2h
0187F090: F4 6F 32 68  AF 21 2E 68  00 00 00 00  01 00 00 00  .o2h.!.h........
0187F0A0: AB DF 1C 68  F0 F0 87 01  53 CA 32 68  CC F0 87 01  ...h....S.2h....
0187F0B0: F4 EF 32 68  C9 9E E4 7D  3C CA 32 68  48 E2 D7 7D  ..2h...}<.2hH..}
0187F0C0: 58 C2 32 68  00 00 00 00  20 BF 32 68  6F D2 E2 7D  X.2h.... .2ho..}
0187F0D0: 49 CA 32 68  50 D2 E2 7D  AF 21 2E 68  4C F1 87 01  I.2hP..}.!.hL...
0187F0E0: E9 75 1F 68  B1 80 1F 68  D1 98 45 00  00 00 00 00  .u.h...h..E.....
0187F0F0: 00 00 00 00  9A 29 E3 7D  02 00 00 00  43 F3 87 01  .....).}....C...
0187F100: F4 1F 15 68  62 00 00 00  C8 9E E4 7D  4C F1 87 01  ...hb......}L...
0187F110: F8 7F 02 68  20 F3 87 01  C8 9E E4 7D  40 74 32 68  ...h ......}@t2h
0187F120: F9 D9 27 68  00 00 00 00  00 00 00 00  AC F1 87 01  ..'h............
0187F130: CE EF 25 68  09 00 00 00  01 00 00 00  00 00 00 00  ..%h............
0187F140: F4 1F 15 68  18 F2 87 01  00 00 00 00  AC F1 87 01  ...h............
0187F150: AD 86 02 68  00 00 00 00  00 00 00 00  20 F3 87 01  ...h........ ...
0187F160: 00 01 00 00  00 00 00 00  F0 54 14 68  20 F3 87 01  .........T.h ...
0187F170: 18 F2 87 01  04 00 00 00  90 29 E3 7D  B4 29 E3 7D  .........).}.).}
0187F180: 0A 00 00 00  00 00 00 00  E0 FB C4 7B  1C F2 87 01  ...........{....
0187F190: 00 29 80 6A  00 F2 87 01  E2 BF 02 68  F4 1F 15 68  .).j.......h...h
0187F1A0: 10 00 00 00  E4 F1 87 01  7A C9 02 68  00 00 00 00  ........z..h....


------------------------------------------------------------------------------
Percent memory used:    55
Total physical memory:  1048584192
Free physical memory:   465051648
Page file:              4124798976
Total virtual memory:   3221159935
Free virtual memory:    3221094399
------------------------------------------------------------------------------

List of running Wow.exe processes

Could not list processes

List of running Agent.exe processes

Could not list processes

======================================================================
Hardware/Driver Information:
Processor:              0x0
Page Size:              4096
Min App Address:        0x10000
Max App Address:        0xbfffffff
Processor Mask:         0x3
Number of Processors:   2
Processor Type:         586
Allocation Granularity: 65536
Processor Level:        6
Processor Revision:     3853
Os Version:             6.2
Os Service Pack:        0.0

---

### Post by Crossbow on 2013-01-12
No advice, huh?

I wish I could cancel my WoW account but it's already paid through February. And I haven't been able to play in a month.

---

### Post by Crossbow on 2013-01-12
Ran the repair too - Again. Here is my latest error message:

==============================================================================
World of WarCraft: Retail Build (build 16357)

Exe:      C:\Program Files\World of Warcraft\Wow.exe
Time:     Jan 12, 2013  4:47:08.189 PM
User:     anna
Computer: anna-desktop
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal exception!

Program:	C:\Program Files\World of Warcraft\Wow.exe
ProcessID:	89
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:693F8BC4

The instruction at "0x693F8BC4" referenced memory at "0x00000CA7".
The memory could not be "written".


WoWBuild: 16357
Version: 5.1.0
Type:  WoW
Platform: X86
Session Time(hh:mm:ss):  00:00:00
Time in World(hh:mm:ss): 00:00:00
Number of Char Logins:  0

Settings: 
SET readTOS "-1"
SET readEULA "-1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET checkAddonVersion "1"
SET locale "enUS"
SET installLocale "enUS"

----------------------------------------
Installation settings:
----------------------------------------
UID:  wow_enus
Expansion Level: 4
PTR: 0
Beta: 0
PatchURL: 'http://enUS.patch.battle.net:1119/patch'
ProductCode: 'WoW'

----------------------------------------
               GxInfo
----------------------------------------
No GX Device Created
Desktop Display List:
Device Name: \\.\DISPLAY1
Device String: X11 Windowing System
State Flags: 0x00000015
Device ID: PCI\VEN_0000&DEV_0000

Installed DX9 Version:
File Version: 5.3.1.904
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=00000000  EBX=7DD562E8  ECX=00000000  EDX=00000000  ESI=0187E98C
EDI=B7702008  EBP=FFFFFFFF  ESP=0187E82C  EIP=693F8BC4  FLG=00010246
CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

Showing 9/9 threads...

--- Thread ID: 88 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 101 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 100 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 97 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 96 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 95 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 94 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 93 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 90 [Current Thread] ---
693F8BC4 FFFFFFFF 0000:00000000 <unknown>

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

Showing 9/9 threads...

--- Thread ID: 88 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 101 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 100 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 97 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 96 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 95 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 94 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 93 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 90 [Current Thread] ---



----------------------------------------
    Loaded Modules
----------------------------------------

DBG-MODULE<00400000 00F51000 "Wow.exe" "Wow.pdb" 0 {5aa2aa29-afb6-4524-b8907c5fdc6893da} 1 1354589228>
DBG-MODULE<68380000 0013E000 "user32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<684D0000 000C0000 "gdi32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<685A0000 0005A000 "advapi32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68600000 00014000 "version.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68630000 00021000 "mpr.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68660000 0008D000 "msvcrt.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68700000 00214000 "shell32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68920000 000F8000 "comctl32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68A20000 000AA000 "winmm.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68AE0000 00111000 "ole32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68C00000 0006F000 "rpcrt4.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68C70000 00029000 "msacm32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68CA0000 00035000 "d3d9.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68CE0000 0012C000 "wined3d.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68E10000 00020000 "imm32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68E40000 00024000 "ws2_32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68E70000 00010000 "dinput8.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68E90000 0005C000 "setupapi.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68EF0000 00011000 "hid.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68FB0000 0007A000 "winex11.drv" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<69270000 0002B000 "uxtheme.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<692E0000 000E2000 "opengl32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<6A1B0000 0005E000 "dbghelp.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<6A210000 00012000 "psapi.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<76860000 00039000 "winspool.drv" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<77F60000 00076000 "shlwapi.dll" "shlwapi.pdb" 0 {658b2b7c-8638-42a0-be311e436027f6e3} 2 1158222689>
DBG-MODULE<7AE70000 0006C000 "wininet.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7B810000 0022B000 "KERNEL32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7BC10000 000C2000 "ntdll.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>

----------------------------------------
    Memory Dump
----------------------------------------

Code: 32 bytes starting at (EIP = 693F8BC4 - 10)

693F8BB4: E8 27 2F 03  00 83 C4 1C  5B 5E 5F 5D  C3 8B 43 24  .'/.....[^_]..C$
* = addr  **                                                  *               
693F8BC4: 89 85 A8 0C  00 00 EB D8  8B 43 1C A3  A0 4A 46 69  .........C...JFi


Stack: 1024 bytes starting at (ESP = 0187E82C - 20)

0187E800: 03 00 EF BE  CC 10 EF BF  00 00 00 00  38 2F CB 7D  ............8/.}
0187E810: 84 E8 87 01  00 00 00 00  01 00 00 00  00 00 00 00  ................
0187E820: 84 E8 87 01  FF FF FF FF  79 8B 3F 69  45 00 D0 C1  ........y.?iE...
* = addr                                         **                       *   
0187E820: 84 E8 87 01  FF FF FF FF  79 8B 3F 69  45 00 D0 C1  ........y.?iE...
0187E830: 03 00 EF BE  CC 10 EF BF  B8 2E CB 7D  10 00 00 00  ...........}....
0187E840: 08 20 70 B7  F4 5F 17 69  00 00 00 00  8C E9 87 01  . p.._.i........
0187E850: 00 00 00 00  54 E9 87 01  A8 31 40 69  08 20 70 B7  ....T....1@i. p.
0187E860: CC 10 EF BF  08 03 00 00  69 65 2B 68  D8 24 CB 7D  ........ie+h.$.}
0187E870: 39 FC 16 68  D8 24 CB 7D  31 CB 07 69  5C EC 87 01  9..h.$.}1..i\...
0187E880: F8 79 D4 7D  F4 5F 17 69  00 00 00 00  48 8B CB 7D  .y.}._.i....H..}
0187E890: F3 98 06 69  20 8A CB 7D  D8 24 CB 7D  F4 EC 87 01  ...i ..}.$.}....
0187E8A0: 48 8B CB 00  00 00 00 00  00 00 00 00  01 00 CB 7D  H..............}
0187E8B0: 46 4D 43 69  D8 24 CB 7D  D8 24 CB 7D  5C EC 87 01  FMCi.$.}.$.}\...
0187E8C0: 54 E9 87 01  00 A0 7B B7  FD 47 40 00  C8 47 74 B7  T.....{..G@..Gt.
0187E8D0: 27 00 00 00  00 00 00 00  08 03 00 00  27 00 00 00  '...........'...
0187E8E0: 00 00 00 00  54 E9 87 01  88 B5 40 69  08 20 70 B7  ....T.....@i. p.
0187E8F0: 00 00 00 00  00 00 00 00  54 E9 87 01  20 AC 7B B7  ........T... .{.
0187E900: 00 00 00 00  00 00 00 00  C9 A5 6B 69  1D 00 00 00  ..........ki....
0187E910: 20 AC 7B B7  00 01 00 00  68 43 E3 7D  00 00 00 00   .{.....hC.}....
0187E920: 10 00 00 00  00 00 00 00  5C EC 87 01  10 00 E0 0E  ........\.......
0187E930: 54 E9 87 01  40 C5 D3 7D  3A 07 43 69  08 20 70 B7  T...@..}:.Ci. p.
0187E940: 5C EC 87 01  08 03 00 00  00 00 00 00  00 00 00 00  \...............
0187E950: 18 00 00 00  01 00 00 00  27 00 00 00  13 01 00 00  ........'.......
0187E960: 01 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0187E970: 00 00 00 00  00 00 00 00  25 00 00 00  00 00 00 00  ........%.......
0187E980: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 45 41  ..............EA
0187E990: 00 00 00 00  00 00 5F 00  00 00 00 00  00 00 00 00  ......_.........
0187E9A0: 00 00 00 00  01 00 00 00  00 00 00 00  00 00 01 00  ................
0187E9B0: 00 00 00 00  CC 10 EF BF  00 00 00 00  CC 10 EF BF  ................
0187E9C0: 2E 00 D0 C1  02 02 EF BE  63 0A 4C 47  00 00 00 00  ........c.LG....
0187E9D0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0187E9E0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0187E9F0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 45 41  ..............EA
0187EA00: 00 00 00 00  02 02 EF BE  40 00 00 00  10 00 00 00  ........@.......
0187EA10: 10 00 00 00  01 00 00 00  00 00 00 00  00 00 00 00  ................
0187EA20: 00 00 00 00  02 00 00 00  00 00 00 00  10 00 00 00  ................
0187EA30: 10 00 00 00  01 00 00 00  00 00 00 00  02 00 00 00  ................
0187EA40: 00 00 00 00  00 00 00 00  00 00 00 00  04 00 00 00  ................
0187EA50: 08 00 00 00  08 00 00 00  00 00 00 00  00 00 00 00  ................
0187EA60: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0187EA70: 00 00 00 00  00 00 00 00  00 00 00 00  0E 00 00 00  ................
0187EA80: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0187EA90: 00 00 00 00  03 00 00 00  00 00 00 00  00 00 00 00  ................
0187EAA0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0187EAB0: 00 00 00 00  00 00 00 00  12 00 00 00  FF FF FF FF  ................
0187EAC0: 00 00 00 00  00 00 00 00  00 00 00 00  08 00 00 00  ................
0187EAD0: 08 00 00 00  00 00 00 00  00 00 00 00  78 00 00 00  ............x...
0187EAE0: 00 00 61 00  00 01 00 00  00 00 00 00  00 00 00 00  ..a.............
0187EAF0: 01 00 00 00  FF FF FF FF  FF FF FF FF  FF FF FF FF  ................
0187EB00: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0187EB10: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0187EB20: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0187EB30: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0187EB40: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0187EB50: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0187EB60: 00 00 00 00  FF FF FF FF  FF FF FF FF  00 00 00 00  ................
0187EB70: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0187EB80: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0187EB90: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0187EBA0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0187EBB0: 00 00 00 00  00 00 00 00  08 00 00 00  08 00 00 00  ................
0187EBC0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0187EBD0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0187EBE0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0187EBF0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0187EC00: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0187EC10: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0187EC20: 00 00 00 00  FF FF FF FF  00 00 00 00  00 00 00 00  ................


------------------------------------------------------------------------------
Percent memory used:    54
Total physical memory:  1048584192
Free physical memory:   475189248
Page file:              4124798976
Total virtual memory:   3221159935
Free virtual memory:    3221094399
------------------------------------------------------------------------------

List of running Wow.exe processes

Could not list processes

List of running Agent.exe processes

Could not list processes

======================================================================
Hardware/Driver Information:
Processor:              0x0
Page Size:              4096
Min App Address:        0x10000
Max App Address:        0xbfffffff
Processor Mask:         0x3
Number of Processors:   2
Processor Type:         586
Allocation Granularity: 65536
Processor Level:        6
Processor Revision:     3853
Os Version:             6.2
Os Service Pack:        0.0

---

### Post by Crossbow on 2013-01-12
Dandy - Wine has now decided that it is version 1.4 again, and now when I try to launch the game it throws me back to the Ubuntu login screen. 

What I had done was try to install Q4Wine which synaptic said it could not do, but marked it as installed. So I tried to uninstall it and got the same error.

---

