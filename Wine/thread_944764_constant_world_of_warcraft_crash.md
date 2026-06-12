---
title: "constant world of warcraft crash"
date: 2008-10-11
forum: Wine
---

### Post by c/Kr3t on 2008-10-11
everytime i try to start the game it crashes, it pulls up that crash report thing and then closes.  i tried everything in the troubleshoot.   can anyone help?

---

### Post by linux_lover69 on 2008-10-11
Have you tried reinstalling the game

---

### Post by c/Kr3t on 2008-10-11
> **linux_lover69 said:**
> Have you tried reinstalling the game

yes i have done it twice now,  once was with the cd's in and out. second time was with the files saved to my hard drive


it gives me this every time it crashes


===========================================================================
World of WarCraft (build 6080)

Exe:      C:\Program Files\World of Warcraft\WoW.exe
Time:     Oct 11, 2008  3:51:30.241 PM
User:     danny
Computer: danny-desktop
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\WoW.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:00000000

The instruction at "0x00000000" referenced memory at "0x00000000".
The memory could not be "read".


WoWBuild: 6080
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=0033F0C0  EBX=7D5EDA28  ECX=00000000  EDX=00000000  ESI=00000000
EDI=7D5CC815  EBP=0033F0E0  ESP=0033EC54  EIP=00000000  FLG=00010246
CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

00000000 0033F0E0 0000:00000000 C:\Program Files\World of Warcraft\WoW.exe
7D5BBD02 0033F110 0001:000CAD02 C:\windows\system32\wined3d.dll
7D6054C7 0033F140 0001:000044C7 C:\windows\system32\d3d9.dll
005CF295 0033F764 0001:001CE295 C:\Program Files\World of Warcraft\WoW.exe
005BFCE0 0033F774 0001:001BECE0 C:\Program Files\World of Warcraft\WoW.exe
00682A62 0033FBAC 0001:00281A62 C:\Program Files\World of Warcraft\WoW.exe
0067B7E0 0033FC14 0001:0027A7E0 C:\Program Files\World of Warcraft\WoW.exe
004028DF 0033FE68 0001:000018DF C:\Program Files\World of Warcraft\WoW.exe
00402477 0033FE78 0001:00001477 C:\Program Files\World of Warcraft\WoW.exe
0040447E 0033FF08 0001:0000347E C:\Program Files\World of Warcraft\WoW.exe
7B877B77 0033FFE8 0001:00056B77 C:\windows\system32\KERNEL32.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

7D5BBD02 wined3d.dll  WineDirect3DCreate+34 (0x00000020,0x00000009,0x0012DF30,0x7B86817D)
7D6054C7 d3d9.dll     Direct3DCreate9+119 (0x00000020,0x0033F659,0x00CCD286,0x005C1E89)
005CF295 WoW.exe      <unknown symbol>+0 (0x00CCD288,0x00CCD28C,0x0033FBAC,0x00682A62)
005BFCE0 WoW.exe      <unknown symbol>+0 (0x00CCD288,0x00CCD28C,0x00401000,0x00000000)
00682A62 WoW.exe      <unknown symbol>+0 (0x00401000,0x00000000,0x7B8B4F68,0x7BC33DDF)
0067B7E0 WoW.exe      <unknown symbol>+0 (0x00000001,0x6C726F57,0x666F2064,0x72615720)
004028DF WoW.exe      <unknown symbol>+0 (0x00000001,0x00000001,0x0033FF08,0x0040447E)
00402477 WoW.exe      <unknown symbol>+0 (0x0040A380,0x00400000,0x00000000,0x001118FC)
0040447E WoW.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)
7B877B77 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00340000 - 0x003D0000  C:\Program Files\World of Warcraft\fmod.dll
0x00400000 - 0x00D89000  C:\Program Files\World of Warcraft\WoW.exe
0x10000000 - 0x10069000  C:\Program Files\World of Warcraft\DivxDecoder.dll
0x7B820000 - 0x7B93C000  C:\windows\system32\KERNEL32.dll
0x7BC10000 - 0x7BCA6000  C:\windows\system32\ntdll.dll
0x7D480000 - 0x7D493000  C:\windows\system32\psapi.dll
0x7D4A0000 - 0x7D4DF000  C:\windows\system32\dbghelp.dll
0x7D4F0000 - 0x7D5F0000  C:\windows\system32\wined3d.dll
0x7D600000 - 0x7D620000  C:\windows\system32\d3d9.dll
0x7D860000 - 0x7D871000  C:\windows\system32\midimap.dll
0x7D880000 - 0x7D888000  C:\windows\system32\msacm32.drv
0x7D890000 - 0x7D8C3000  C:\windows\system32\wineoss.drv
0x7D920000 - 0x7D942000  C:\windows\system32\uxtheme.dll
0x7D980000 - 0x7DA06000  C:\windows\system32\winex11.drv
0x7DB10000 - 0x7DB29000  C:\windows\system32\mpr.dll
0x7DB30000 - 0x7DB78000  C:\windows\system32\wininet.dll
0x7DB80000 - 0x7DBDD000  C:\windows\system32\rpcrt4.dll
0x7DC00000 - 0x7DCE6000  C:\windows\system32\ole32.dll
0x7DD00000 - 0x7DD50000  C:\windows\system32\msvcrt.dll
0x7DD60000 - 0x7DD77000  C:\windows\system32\msacm32.dll
0x7DD80000 - 0x7DD8B000  C:\windows\system32\lz32.dll
0x7DD90000 - 0x7DDA4000  C:\windows\system32\version.dll
0x7DDB0000 - 0x7DE36000  C:\windows\system32\winmm.dll
0x7DE40000 - 0x7DE56000  C:\windows\system32\imm32.dll
0x7E910000 - 0x7E992000  C:\windows\system32\opengl32.dll
0x7E9B0000 - 0x7E9C4000  C:\windows\system32\iphlpapi.dll
0x7E9D0000 - 0x7E9F0000  C:\windows\system32\ws2_32.dll
0x7EA00000 - 0x7EA0A000  C:\windows\system32\wsock32.dll
0x7EA20000 - 0x7EA64000  C:\windows\system32\shlwapi.dll
0x7EA70000 - 0x7EB7E000  C:\windows\system32\shell32.dll
0x7EB90000 - 0x7EC1C000  C:\windows\system32\gdi32.dll
0x7EC40000 - 0x7ED65000  C:\windows\system32\user32.dll
0x7ED70000 - 0x7EE26000  C:\windows\system32\comctl32.dll
0x7EE30000 - 0x7EE7A000  C:\windows\system32\advapi32.dll


----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = 00000000)

00000000: <can't read from this address>


Stack: 1024 bytes starting at (ESP = 0033EC54)

* = addr               **                                         *           
0033EC50: 00 00 00 00  A1 81 54 7D  01 00 00 00  C0 F0 33 00  ......T}......3.
0033EC60: 58 80 00 00  04 00 00 00  04 00 00 00  00 00 00 00  X...............
0033EC70: E1 80 00 00  67 83 00 00  00 00 00 00  00 00 00 00  ....g...........
0033EC80: 00 00 00 00  00 00 00 00  44 A4 C8 7B  60 70 61 7D  ........D..{`pa}
0033EC90: B0 EC 33 00  85 4C C4 7B  00 00 60 7D  01 00 00 00  ..3..L.{..`}....
0033ECA0: 20 03 00 00  64 C2 5C 7D  50 E8 5E 7D  44 A4 C8 7B   ...d.\}P.^}D..{
0033ECB0: C4 F0 33 00  C0 F0 33 00  90 F0 33 00  68 F0 33 00  ..3...3...3.h.3.
0033ECC0: 01 00 00 00  00 00 00 00  28 F0 33 00  20 03 00 00  ........(.3. ...
0033ECD0: E8 0D 13 00  01 00 00 00  00 00 00 00  00 00 00 00  ................
0033ECE0: 48 03 00 00  5C 00 5C 00  2E 00 5C 00  44 00 49 00  H...\.\...\.D.I.
0033ECF0: 53 00 50 00  4C 00 41 00  59 00 31 00  00 00 33 00  S.P.L.A.Y.1...3.
0033ED00: 44 A4 C8 7B  60 70 61 7D  68 DE 12 00  F0 ED 33 00  D..{`pa}h.....3.
0033ED10: FE 71 D9 73  09 63 D6 9C  00 00 00 00  88 F3 33 00  .q.s.c........3.
0033ED20: 78 ED 33 00  58 00 31 00  31 00 20 00  57 00 69 00  x.3.X.1.1. .W.i.
0033ED30: 6E 00 64 00  6F 00 77 00  69 00 6E 00  67 00 20 00  n.d.o.w.i.n.g. .
0033ED40: 53 00 79 00  73 00 74 00  65 00 6D 00  00 00 FD 7F  S.y.s.t.e.m.....
0033ED50: E8 DC 12 00  2F 39 C4 7B  2C F0 33 00  00 00 00 00  ..../9.{,.3.....
0033ED60: 06 00 00 00  00 00 00 00  28 DE 12 00  48 1C 13 00  ........(...H...
0033ED70: 00 00 11 00  12 23 E2 B7  43 00 3A 00  00 00 00 00  .....#..C.:.....
0033ED80: 00 00 00 00  64 00 6F 00  77 00 73 00  5C 00 73 00  ....d.o.w.s.\.s.
0033ED90: 3D 73 C4 7B  44 A4 C8 7B  00 00 00 00  58 DF 12 00  =s.{D..{....X...
0033EDA0: 38 01 00 00  14 00 11 00  F0 DC 12 00  18 DE 12 00  8...............
0033EDB0: 00 00 11 00  44 A4 C8 7B  E0 DC 12 00  38 01 00 00  ....D..{....8...
0033EDC0: 10 EE 33 00  06 30 C4 7B  55 00 00 00  00 00 00 00  ..3..0.{U.......
0033EDD0: 00 00 00 00  E5 17 C4 7B  5A 40 00 01  00 00 00 06  .......{Z@......
0033EDE0: 3D 73 C4 7B  AE 20 C4 7B  00 00 00 00  68 DE 12 00  =s.{. .{....h...
0033EDF0: 14 00 11 00  31 44 C3 7B  00 00 00 00  00 00 00 00  ....1D.{........
0033EE00: 14 00 11 00  DF 3D C3 7B  14 00 11 00  44 A4 C8 7B  .....=.{....D..{
0033EE10: 50 EE 33 00  97 32 C4 7B  48 00 11 00  00 00 00 00  P.3..2.{H.......
0033EE20: 00 00 00 00  15 00 00 00  00 00 4C 00  00 00 0A FF  ..........L.....
0033EE30: 3D 73 C4 7B  DF 3D C3 7B  00 00 00 00  00 00 11 00  =s.{.=.{........
0033EE40: 02 00 00 00  68 4F 8B 7B  00 00 00 00  F0 F0 33 00  ....hO.{......3.
0033EE50: 70 EE 33 00  2F 12 85 7B  00 00 11 00  00 00 00 00  p.3./..{........
0033EE60: E8 DC 12 00  68 4F 8B 7B  00 00 00 00  F0 F0 33 00  ....hO.{......3.
0033EE70: D0 F0 33 00  93 7D 86 7B  00 00 11 00  00 00 00 00  ..3..}.{........
0033EE80: E8 DC 12 00  C0 F0 33 00  D6 E7 C7 7B  D6 E7 C7 7B  ......3....{...{
0033EE90: 86 4E CA 7B  F4 CF DE B7  D5 E7 C7 7B  C0 F0 33 00  .N.{.......{..3.
0033EEA0: C0 F4 33 00  E8 DC 12 00  83 9F D0 B7  87 4E CA 7B  ..3..........N.{
0033EEB0: 30 28 C8 7B  29 00 00 00  5C 28 C8 7B  5C 28 C8 7B  0(.{)...\(.{\(.{
0033EEC0: B2 4E CA 7B  F4 CF DE B7  5B 28 C8 7B  01 00 00 00  .N.{....[(.{....
0033EED0: F0 F4 33 00  CF 07 CE B7  14 F5 33 00  5B 28 C8 7B  ..3.......3.[(.{
0033EEE0: 01 00 00 00  00 00 00 00  18 00 FE 01  34 F4 33 00  ............4.3.
0033EEF0: 04 F0 33 00  D4 FF FF FF  D4 FF FF FF  D4 FF FF FF  ..3.............
0033EF00: 91 DD D0 B7  0C 3D 13 00  FF 1F CE B7  78 F5 33 00  .....=......x.3.
0033EF10: 5C 00 77 00  69 00 6E 00  64 00 6F 00  64 F4 33 00  \.w.i.n.d.o.d.3.
0033EF20: 28 E5 DE B7  F5 F2 DC B7  00 00 00 00  00 00 DE B7  (...............
0033EF30: 00 00 00 00  0B 00 00 00  1F 00 00 00  A8 F5 33 00  ..............3.
0033EF40: CD E7 C7 7B  00 00 00 00  34 F4 33 00  02 00 00 00  ...{....4.3.....
0033EF50: 19 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033EF60: 00 00 00 00  FF FF FF FF  2C 00 00 00  5C 28 C8 7B  ........,...\(.{
0033EF70: 59 28 C8 7B  00 00 00 00  64 F4 33 00  00 00 00 00  Y(.{....d.3.....
0033EF80: 19 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033EF90: 0A 00 00 00  62 F4 33 00  00 00 00 00  00 00 00 00  ....b.3.........
0033EFA0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033EFB0: 00 00 00 00  91 CD CC B7  00 00 00 00  00 00 00 00  ................
0033EFC0: 20 00 00 00  44 A4 C8 7B  00 00 60 7D  9C F0 33 00   ...D..{..`}..3.
0033EFD0: 17 64 C4 7B  F4 EF 33 00  00 00 00 00  F4 F0 33 00  .d.{..3.......3.
0033EFE0: 40 00 00 00  65 13 D7 B7  F8 FE 33 00  10 77 C4 7B  @...e.....3..w.{
0033EFF0: 00 80 FD 7F  44 A4 C8 7B  00 00 60 7D  00 00 00 00  ....D..{..`}....
0033F000: 9C F0 33 00  FE A9 DF 73  09 2F C8 9C  00 00 00 00  ..3....s./......
0033F010: 80 B2 87 00  00 00 00 00  00 00 00 00  94 0D E2 B7  ................
0033F020: 0C 00 00 00  44 A4 C8 7B  28 00 01 00  2D 00 00 00  ....D..{(...-...
0033F030: 00 20 08 10  08 08 08 00  00 00 40 10  10 10 10 18  . ........@.....
0033F040: 08 04 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033F050: 40 00 00 00  44 A4 C8 7B  10 00 00 00  30 DF 12 00  @...D..{....0...


------------------------------------------------------------------------------

======================================================================
Hardware/Driver Information:
Processor:              0x0
Page Size:              4096
Min App Address:        0x10000
Max App Address:        0x7ffeffff
Processor Mask:         0xf
Number of Processors:   4
Processor Type:         586
Allocation Granularity: 65536
Processor Level:        16
Processor Revision:     515

Percent memory used:    13
Total physical memory:  2147483647
Free Memory:            2147483647
Page file:              -1
Total virtual memory:   2147352575

---

