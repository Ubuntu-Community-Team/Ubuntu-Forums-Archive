---
title: "Starcraft 2 crash when pushing &quot;Play&quot; from the launcher."
date: 2012-08-19
forum: Wine
---

### Post by Crynix on 2012-08-19
Hello there, I'm trying to play Starcraft 2 through Wine/PlayOnLinux and whenever I push "Play" in the launcher's window, I get the following error message.

```
==============================================================================
Blizzard Launcher.exe:  (build 1815)

Exe:      C:\users\Public\Application Data\Battle.net\Client\Blizzard Launcher.1815\Blizzard Launcher.exe
Time:     Aug 19, 2012  7:50:13.326 PM
User:     crynix
Computer: crynix-desktop
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #1 (0x13370001) Fatal Exception
Program:	C:\users\Public\Application Data\Battle.net\Client\Blizzard Launcher.1815\Blizzard Launcher.exe

The instruction at "0xF757E67F" referenced memory at "0x7C522000".
The memory could not be read.


Project: 19140301
Build: 1815
Project Name: Blizzard Launcher.exe

------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

      EAX = 7c519660      EBX = f75af0e0      ECX = 00017f78      EDX = 7be00020
      ESI = 7ce17b38      EDI = 00008980      EBP = 0033ae78      ESP = 0033adb4
      EIP = f757e67f      FLG = 00010206       CS = 0023       DS = 002b
       ES = 002b       FS = 0063       GS = 006b       SS = 002b


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

Showing 14/14 threads...

--- Thread ID: 23 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 39 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 67 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 58 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 59 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 35 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 62 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 70 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 66 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 9 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 40 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 43 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 65 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 38 [Current Thread] ---
F757E67F 0033AE78 0000:00000000 <unknown>
7DF1F852 0033B328 0001:0004E852 C:\windows\system32\wined3d.dll
7DF204B1 0033B348 0001:0004F4B1 C:\windows\system32\wined3d.dll
7DFABA1A 0033B388 0001:000DAA1A C:\windows\system32\wined3d.dll
7E006C72 0033B3A8 0001:00015C72 C:\windows\system32\d3d9.dll
7DFFD02E 0033B3D8 0001:0000C02E C:\windows\system32\d3d9.dll
005D234A 0033D370 0001:001D134A C:\users\Public\Application Data\Battle.net\Client\Blizzard Launcher.1815\Blizzard Launcher.exe

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

Showing 14/14 threads...

--- Thread ID: 23 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 39 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 67 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 58 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 59 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 35 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 62 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 70 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 66 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 9 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 40 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 43 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 65 ---
**** Unable to retrieve thread context, error: 5

--- Thread ID: 38 [Current Thread] ---


----------------------------------------
    Loaded Modules
----------------------------------------

DBG-MODULE<00340000 00045000 "phonon4.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 1298385592>
DBG-MODULE<003D0000 0000a000 "qgif4.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 1301564188>
DBG-MODULE<003F0000 0000b000 "qico4.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 1301564221>
DBG-MODULE<00400000 010cc000 "Blizzard Launcher.exe" "Launcher.pdb" 0 {99b2f927-7912-4f8a-99275218c7531c5d} 1 1343928538>
DBG-MODULE<01A20000 00033000 "qjpeg4.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 1301564182>
DBG-MODULE<01A60000 0003a000 "qmng4.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 1301564196>
DBG-MODULE<01AA0000 00048000 "qtiff4.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 1301564216>
DBG-MODULE<10000000 00a5d000 "QtWebKit4.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 1298394800>
DBG-MODULE<61000000 00056000 "QtXml4.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 1298383793>
DBG-MODULE<64000000 000f2000 "QtNetwork4.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 1298383887>
DBG-MODULE<65000000 007d2000 "QtGui4.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 1298384766>
DBG-MODULE<67000000 00234000 "QtCore4.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 1298383781>
DBG-MODULE<7B810000 000ed000 "KERNEL32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7BC10000 000b1000 "ntdll.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7BFB0000 00050000 "dbghelp.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7C480000 000a2000 "opengl32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7D210000 0000b000 "psapi.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7D910000 00022000 "winealsa.drv" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7D940000 00014000 "mmdevapi.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7D9A0000 00037000 "dsound.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7DA20000 0000d000 "wintab32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7DA60000 0002e000 "uxtheme.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7DD40000 00081000 "winex11.drv" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7DE60000 0005f000 "ddraw.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7DED0000 00118000 "wined3d.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7DFF0000 0002d000 "d3d9.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E040000 00016000 "iphlpapi.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E060000 0001b000 "mpr.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E0A0000 00060000 "wininet.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E110000 0001e000 "msvcr90.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E140000 0007d000 "msvcrt.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E1F0000 000e3000 "msvcp90.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E2E0000 00022000 "ws2_32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E310000 00013000 "imm32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E340000 000f1000 "oleaut32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E440000 0002d000 "winspool.drv" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E470000 000dc000 "comdlg32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E550000 00023000 "msacm32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E580000 000a0000 "winmm.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E630000 000e3000 "comctl32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E720000 0005e000 "shlwapi.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E790000 001ff000 "shell32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E9A0000 00065000 "rpcrt4.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7EA10000 0000d000 "version.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7EA30000 000ab000 "gdi32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7EAF0000 00129000 "user32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7EC30000 0004b000 "advapi32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7EC90000 000f1000 "ole32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>

----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = F757E67F)

F757E67F: 66 0F 6F 5C  38 20 66 0F  6F E3 66 0F  3A 0F DA 04  f.o\8 f.o.f.:...


Stack: 1024 bytes starting at (ESP = 0033ADB4)

0033ADB4: 50 09 02 00  F4 4F EB 7C  71 D5 E8 7C  18 00 E0 7B  P....O.|q..|...{
0033ADC4: 5C 96 51 7C  40 09 02 00  80 41 FE 7D  80 41 FE 7D  \.Q|@....A.}.A.}
0033ADD4: A0 4B 8A 03  B4 4B 8A 03  91 E6 F1 7D  01 00 00 00  .K...K.....}....
0033ADE4: 54 AE 33 00  94 20 00 00  5C 96 51 7C  00 00 00 00  T.3.. ..\.Q|....
0033ADF4: 00 00 01 00  38 AE 33 00  3F 5A C3 7B  40 E5 51 7C  ....8.3.?Z.{@.Q|
0033AE04: 01 00 00 00  04 00 00 07  04 00 00 07  00 00 00 00  ................
0033AE14: 5C 96 51 7C  38 AE 33 00  C4 C3 4E 7C  40 E5 51 7C  \.Q|8.3...N|@.Q|
0033AE24: 06 00 00 00  BB 94 C4 7B  5C 96 51 7C  3C 4C 8A 03  .......{\.Q|<L..
0033AE34: 54 AE 33 00  48 99 E0 7C  08 E2 E0 7C  44 03 00 00  T.3.H..|...|D...
0033AE44: 38 1E 76 03  14 00 00 00  A0 E3 4E 7C  2C 3B AC 7E  8.v.......N|,;.~
0033AE54: 01 00 00 00  78 AE 33 00  01 00 00 00  44 03 00 00  ....x.3.....D...
0033AE64: 01 00 00 00  2D BC F1 7D  80 41 FE 7D  01 00 00 00  ....-..}.A.}....
0033AE74: A0 4B 8A 03  28 B3 33 00  52 F8 F1 7D  44 03 00 00  .K..(.3.R..}D...
0033AE84: 00 00 01 00  BC B2 33 00  BC B2 33 00  0A 00 00 00  ......3...3.....
0033AE94: 0A 00 00 00  0A 00 00 00  0A 00 00 00  00 00 00 00  ................
0033AEA4: 00 00 00 00  00 00 00 00  00 00 00 00  02 00 00 00  ................
0033AEB4: 18 1C 1D 02  4C 44 CA 7B  00 30 0F 02  08 1C 1D 02  ....LD.{.0......
0033AEC4: 80 9B DB 7D  90 4B 8A 03  20 00 00 00  85 28 F3 D6  ...}.K.. ....(..
0033AED4: 67 7E CD 01  E5 BD F1 90  68 7E CD 01  85 28 F3 D6  g~......h~...(..
0033AEE4: 67 7E CD 01  85 28 F3 D6  67 7E CD 01  00 20 00 00  g~...(..g~... ..
0033AEF4: 00 00 00 00  CE 12 00 00  00 00 00 00  20 00 00 00  ............ ...
0033AF04: A8 50 33 01  18 00 00 00  BC B2 33 00  20 AF 33 00  .P3.......3. .3.
0033AF14: 40 00 00 00  67 7E CD 01  E6 03 46 00  E5 BD F1 90  @...g~....F.....
0033AF24: 68 7E CD 01  64 00 00 00  5C AA 4D 00  20 00 00 00  h~..d...\.M. ...
0033AF34: E5 BD F1 90  AC B0 33 00  00 00 00 00  E4 AF 33 00  ......3.......3.
0033AF44: 2E 9A 5F F7  67 7E CD 01  0F 00 00 00  60 FE 14 00  .._.g~......`...
0033AF54: 00 00 00 00  B8 C3 33 00  20 00 00 00  85 28 F3 D6  ......3. ....(..
0033AF64: 67 7E CD 01  E5 BD F1 90  68 7E CD 01  85 28 F3 D6  g~......h~...(..
0033AF74: 67 7E CD 01  CC AF 33 00  C4 B0 33 00  40 00 00 00  g~....3...3.@...
0033AF84: CC AF 33 00  E4 B9 5F F7  40 00 00 00  C0 07 C7 7B  ..3..._.@......{
0033AF94: 04 00 00 00  C4 B0 33 00  40 00 00 00  5C 00 50 00  ......3.@...\.P.
0033AFA4: 75 00 62 00  6C 00 69 00  63 00 5C 00  00 80 FD 7F  u.b.l.i.c.\.....
0033AFB4: 70 00 6C 00  AC B0 33 00  C4 B0 33 00  4C 44 CA 7B  p.l...3...3.LD.{
0033AFC4: C4 B0 33 00  00 00 00 00  E4 AF 33 00  BE 0C C7 7B  ..3.......3....{
0033AFD4: 02 00 00 00  E4 AF 33 00  00 00 00 00  6E 00 65 00  ......3.....n.e.
0033AFE4: 00 00 00 00  00 00 00 00  69 00 65 00  6E 00 74 00  ........i.e.n.t.
0033AFF4: 5C 00 42 00  6C 00 69 00  7A 00 7A 00  61 00 72 00  \.B.l.i.z.z.a.r.
0033B004: 64 00 20 00  4C 00 61 00  75 00 6E 00  63 00 68 00  d. .L.a.u.n.c.h.
0033B014: 65 00 72 00  2E 00 31 00  21 86 C4 7B  E0 3F 2D 02  e.r...1.!..{.?-.
0033B024: 02 00 00 00  40 3E 2D 02  4C 44 CA 7B  00 30 0F 02  ....@>-.LD.{.0..
0033B034: 5E 74 C4 7B  88 B0 33 00  F9 88 C4 7B  21 86 C4 7B  ^t.{..3....{!..{
0033B044: 30 32 79 03  02 00 00 00  F8 30 79 03  4C 44 CA 7B  02y......0y.LD.{
0033B054: 3F 5A C3 7B  78 00 00 00  70 B0 33 00  16 88 C4 7B  ?Z.{x...p.3....{
0033B064: 48 01 00 00  68 30 79 03  4C 44 CA 7B  D0 B0 33 00  H...h0y.LD.{..3.
0033B074: 36 97 C4 7B  60 00 11 00  4C 44 CA 7B  00 00 11 00  6..{`...LD.{....
0033B084: 4C 44 CA 7B  E8 B0 33 00  23 8C C4 7B  60 00 11 00  LD.{..3.#..{`...
0033B094: DC B0 33 00  78 00 00 00  00 00 00 00  00 00 00 00  ..3.x...........
0033B0A4: 00 00 11 00  59 BA 5F F7  00 00 00 00  B9 6A C5 7B  ....Y._......j.{
0033B0B4: 00 00 75 03  5E 74 C4 7B  21 86 C4 7B  BB 94 C4 7B  ..u.^t.{!..{...{
0033B0C4: C0 38 1B 7E  54 B1 33 00  70 00 00 00  F0 B0 33 00  .8.~T.3.p.....3.
0033B0D4: A7 C2 16 7E  00 00 11 00  00 00 00 00  74 00 00 00  ...~........t...
0033B0E4: 68 0F 00 00  00 00 00 00  54 B1 33 00  D8 B1 33 00  h.......T.3...3.
0033B0F4: FF E3 45 00  74 00 00 00  54 B1 33 00  C3 E4 45 00  ..E.t...T.3...E.
0033B104: 98 17 14 00  5E 74 C4 7B  D0 15 87 7B  54 B1 33 00  ....^t.{...{T.3.
0033B114: 21 86 C4 7B  68 B5 90 03  02 00 00 00  B0 B4 90 03  !..{h...........
0033B124: 4C 44 CA 7B  3F 5A C3 7B  78 00 00 00  44 B1 33 00  LD.{?Z.{x...D.3.
0033B134: 16 88 C4 7B  C8 00 00 00  20 B4 90 03  4C 44 CA 7B  ...{.... ...LD.{
0033B144: A4 B1 33 00  36 97 C4 7B  60 00 11 00  54 B1 33 00  ..3.6..{`...T.3.
0033B154: 08 00 00 00  4C 44 CA 7B  70 00 00 00  00 00 00 00  ....LD.{p.......
0033B164: 74 30 79 03  00 00 00 00  78 00 00 00  00 00 00 00  t0y.....x.......
0033B174: 00 00 00 00  00 00 11 00  A0 AA 90 03  02 00 00 00  ................
0033B184: 00 00 11 00  00 00 75 03  02 00 00 00  B0 B4 90 03  ......u.........
0033B194: BB 94 C4 7B  21 86 C4 7B  20 93 90 03  02 00 00 00  ...{!..{ .......
0033B1A4: 78 6D 90 03  4C 44 CA 7B  00 00 75 03  68 6D 90 03  xm..LD.{..u.hm..


------------------------------------------------------------------------------

======================================================================
Hardware/Driver Information:
Processor:              0x0
Page Size:              4096
Min App Address:        0x10000
Max App Address:        0x7ffeffff
Processor Mask:         0xff
Number of Processors:   8
Processor Type:         586
Allocation Granularity: 65536
Processor Level:        6
Processor Revision:     10759
Os Version:             5.1
Os Service Pack:        3.0
Os Bit Size:            32

Percent memory used:    13
Total physical memory:  8356511744
Free Memory:            7225405440
Page file:              16926519296
Total virtual memory:   2147352575
```

Any ideas?

My system specs are as follows:
Ubuntu 12.04
ASRock Extreme4 Gen3 Motherboard
Two HD Radeon 6870s
Intel i7 2600k
8GB RAM

---

