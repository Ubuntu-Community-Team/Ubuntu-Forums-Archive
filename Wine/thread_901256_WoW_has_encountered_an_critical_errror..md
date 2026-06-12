---
title: "WoW has encountered an critical errror."
date: 2008-08-26
forum: Wine
---

### Post by Kromgol on 2008-08-26
Hello! I get this when trying to start WoW: 

==============================================================================
World of WarCraft (build 8606)

Exe:      Z:\media\HP\Program Files\World of Warcraft\Wow.exe
Time:     Aug 26, 2008  2:45:49.522 PM
User:     albin
Computer: albin-desktop
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	Z:\media\HP\Program Files\World of Warcraft\Wow.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:00000001

The instruction at "0x00000001" referenced memory at "0x00000001".
The memory could not be "read".


WoWBuild: 8606
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=7BC8A3F4  EBX=7D719590  ECX=00000043  EDX=7BC8A544  ESI=0032F720
EDI=0000000C  EBP=0032F6F8  ESP=0032F6CC  EIP=00000001  FLG=00010206
CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

Showing 4/4 threads...

--- Thread ID: 26 ---
7B88E4A4 7CBE85D0 0001:0006D4A4 c:\windows\system32\KERNEL32.dll
7B88E4F5 7CBE85F0 0001:0006D4F5 c:\windows\system32\KERNEL32.dll
00749C3D 7CBE85FC 0001:00348C3D Z:\media\HP\Program Files\World of Warcraft\Wow.exe
004584BD 7CBE8A1C 0001:000574BD Z:\media\HP\Program Files\World of Warcraft\Wow.exe
00645617 7CBE8A38 0001:00244617 Z:\media\HP\Program Files\World of Warcraft\Wow.exe
7BC6B22E 7CBE8A48 0001:0005A22E c:\windows\system32\ntdll.dll
7BC6B8C2 7CBE8AE8 0001:0005A8C2 c:\windows\system32\ntdll.dll
7BC6BAF2 7CBE93D8 0001:0005AAF2 c:\windows\system32\ntdll.dll
B7E324FB 7CBE94C8 0000:00000000 <unknown>

--- Thread ID: 25 ---
7BC69582 7CD5D85C 0001:00058582 c:\windows\system32\ntdll.dll
7BC6B8C2 7CBE8AE8 0001:0005A8C2 c:\windows\system32\ntdll.dll
7BC6BAF2 7CBE93D8 0001:0005AAF2 c:\windows\system32\ntdll.dll
B7E324FB 7CBE94C8 0000:00000000 <unknown>

--- Thread ID: 25 ---
7BC692AB 7CD5D82C 0001:000582AB c:\windows\system32\ntdll.dll
7BC69582 7CD5D85C 0001:00058582 c:\windows\system32\ntdll.dll
7B88C272 7CD5D9AC 0001:0006B272 c:\windows\system32\KERNEL32.dll
7B88C46C 7CD5D9CC 0001:0006B46C c:\windows\system32\KERNEL32.dll

--- Thread ID: 24 ---
7B88E4A4 7CE6E9B4 0001:0006D4A4 c:\windows\system32\KERNEL32.dll
7B88E4F5 7CE6E9D4 0001:0006D4F5 c:\windows\system32\KERNEL32.dll
0065EF34 7CE6EA30 0001:0025DF34 Z:\media\HP\Program Files\World of Warcraft\Wow.exe
0075FDD4 7CE6EA48 0001:0035EDD4 Z:\media\HP\Program Files\World of Warcraft\Wow.exe
7BC6B8C2 7CE6EAE8 0001:0005A8C2 c:\windows\system32\ntdll.dll
7BC6BAF2 7CE6F3D8 0001:0005AAF2 c:\windows\system32\ntdll.dll
B7E324FB 7CE6F4C8 0000:00000000 <unknown>

--- Thread ID: 9 [Current Thread] ---
00000001 0032F6F8 0000:00000000 Z:\media\HP\Program Files\World of Warcraft\Wow.exe
008459A0 0032F790 0001:004449A0 Z:\media\HP\Program Files\World of Warcraft\Wow.exe

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

Showing 4/4 threads...
--- Thread ID: 26 ---
7B88E4A4 KERNEL32.dll SleepEx+68 (0x00000001,0x00000000,0x00000000,0x00000000)
7B88E4F5 KERNEL32.dll Sleep+37 (0x00000001,0x7CBE8A1C,0x004584BD,0x00000001)
00749C3D Wow.exe      <unknown symbol>+0 (0x00000001,0x00000000,0x004582E0,0x0000001A)
004584BD Wow.exe      <unknown symbol>+0 (0x00000000,0x006455E0,0x02534C48,0x7BC8A544)
00645617 Wow.exe      <unknown symbol>+0 (0x000020DC,0x006455E0,0x7CBE8AE8,0x7BC6B8C2)
7BC6B22E ntdll.dll    call_thread_entry_point+14 (0x006455E0,0x02534C48,0x10012A03,0x00000000)
7BC6B8C2 ntdll.dll    <unknown symbol>+0 (0x7CBE8B1C,0x00000000,0x00000000,0x00000000)
7BC6BAF2 ntdll.dll    <unknown symbol>+0 (0x7FFCCFB8,0x7CBE9490,0x7CBE9490,0x7CBE9490)
B7E324FB              start_thread+203 (0x7CBE9B90,0x00000000,0x00000000,0x00000000)
B7DB3E5E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 25 ---
7BC692AB ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7CD5D894,0x00000004,0x00000000)
7BC69582 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7CD5D894,0x00000000,0x00000000)
7B88C272 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000001,0x7CD5D9D4,0x00000000,0xFFFFFFFF)
7B88C46C KERNEL32.dll WaitForSingleObject+60 (0x000020C4,0xFFFFFFFF,0x7BC8A544,0x7B88E4D0)
0065D313 Wow.exe      <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 24 ---
7B88E4A4 KERNEL32.dll SleepEx+68 (0x00000064,0x00000000,0x7CE6E9D4,0x7B8550E7)
7B88E4F5 KERNEL32.dll Sleep+37 (0x00000064,0x7B88E4D0,0x7BC8A544,0x01200BD8)
0065EF34 Wow.exe      <unknown symbol>+0 (0x01200C10,0x7BC6B22E,0x01200C10,0x01200C10)
0075FDD4 Wow.exe      <unknown symbol>+0 (0x0075FD55,0x01200C10,0x10012A03,0x00000000)
7BC6B8C2 ntdll.dll    <unknown symbol>+0 (0x7CE6EB1C,0x00000000,0x00000000,0x00000000)
7BC6BAF2 ntdll.dll    <unknown symbol>+0 (0x7FFD4FB8,0x7CE6F490,0x7CE6F490,0x7CE6F490)
B7E324FB              start_thread+203 (0x7CE6FB90,0x00000000,0x00000000,0x00000000)
B7DB3E5E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 9 [Current Thread] ---
00000001 <unknown module> <unknown symbol>+0 (0x0032F720,0x00000400,0x04EA8018,0x00000000)
008459A0 Wow.exe      <unknown symbol>+0 (0x0064A8F6,0x00000000,0x00000000,0x7B8B4B88)
0000FFFF <unknown module> <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00400000 - 0x00EC8000  Z:\media\HP\Program Files\World of Warcraft\Wow.exe
0x10000000 - 0x10069000  Z:\media\HP\Program Files\World of Warcraft\DivxDecoder.dll
0x7B820000 - 0x7B93C000  c:\windows\system32\KERNEL32.dll
0x7BC10000 - 0x7BCA6000  c:\windows\system32\ntdll.dll
0x7C970000 - 0x7C97E000  c:\windows\system32\psapi.dll
0x7C990000 - 0x7C9C8000  c:\windows\system32\dbghelp.dll
0x7CE80000 - 0x7CEA3000  c:\windows\system32\uxtheme.dll
0x7D2C0000 - 0x7D2D6000  c:\windows\system32\msacm32.drv
0x7D3C0000 - 0x7D3E4000  c:\windows\system32\winealsa.drv
0x7D410000 - 0x7D41A000  c:\windows\system32\midimap.dll
0x7D430000 - 0x7D4B4000  c:\windows\system32\winex11.drv
0x7D600000 - 0x7D61B000  c:\windows\system32\iphlpapi.dll
0x7D630000 - 0x7D67F000  c:\windows\system32\rpcrt4.dll
0x7D690000 - 0x7D723000  c:\windows\system32\ole32.dll
0x7D730000 - 0x7D749000  c:\windows\system32\msacm32.dll
0x7D770000 - 0x7D793000  c:\windows\system32\ws2_32.dll
0x7D7A0000 - 0x7D853000  c:\windows\system32\comctl32.dll
0x7D860000 - 0x7D96C000  c:\windows\system32\shell32.dll
0x7D980000 - 0x7D9C5000  c:\windows\system32\shlwapi.dll
0x7D9D0000 - 0x7D9E6000  c:\windows\system32\mpr.dll
0x7D9F0000 - 0x7DA35000  c:\windows\system32\wininet.dll
0x7DA40000 - 0x7DA55000  c:\windows\system32\imm32.dll
0x7DA60000 - 0x7DA6E000  c:\windows\system32\version.dll
0x7DA80000 - 0x7DB7C000  c:\windows\system32\wined3d.dll
0x7DB80000 - 0x7DBAC000  c:\windows\system32\d3d9.dll
0x7EB30000 - 0x7EB38000  c:\windows\system32\lz32.dll
0x7EB50000 - 0x7EBB9000  c:\windows\system32\opengl32.dll
0x7EBD0000 - 0x7EC0B000  c:\windows\system32\advapi32.dll
0x7EC20000 - 0x7ECA9000  c:\windows\system32\gdi32.dll
0x7ECC0000 - 0x7EDF0000  c:\windows\system32\user32.dll
0x7EE00000 - 0x7EE82000  c:\windows\system32\winmm.dll


----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = 00000001)

00000001: <can't read from this address>


Stack: 1024 bytes starting at (ESP = 0032F6CC)

* = addr                                         **                       *   
0032F6C0: 90 95 71 7D  10 F7 32 00  F8 F6 32 00  08 93 6D 7D  ..q}..2...2...m}
0032F6D0: 44 A5 C8 7B  48 2A 72 7D  F0 F6 70 7D  15 98 70 7D  D..{H*r}..p}..p}
0032F6E0: 10 F7 32 00  A0 82 EA 04  90 F7 32 00  00 00 00 00  ..2.......2.....
0032F6F0: A0 90 6D 7D  0C 00 00 00  90 F7 32 00  A0 59 84 00  ..m}......2..Y..
0032F700: 20 F7 32 00  00 04 00 00  18 80 EA 04  00 00 00 00   .2.............
0032F710: F9 0A DB B7  01 00 00 00  47 39 C7 7B  57 5E E5 7B  ........G9.{W^.{
0032F720: 43 00 00 00  01 00 00 00  44 A5 C8 7B  78 53 E5 7B  C.......D..{xS.{
0032F730: 00 00 00 00  00 00 00 00  8F 32 C6 7B  00 00 00 00  .........2.{....
0032F740: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0032F750: 44 A5 C8 7B  74 F8 32 00  B5 56 C7 7B  80 2E C9 7B  D..{t.2..V.{...{
0032F760: 9C F7 32 00  00 A0 EA 04  00 10 00 00  FF FF 00 00  ..2.............
0032F770: 88 F7 32 00  00 00 00 00  00 00 00 00  00 00 3E 05  ..2...........>.
0032F780: E8 EE 8D 00  A4 F7 32 00  E9 A8 64 00  00 90 EA 04  ......2...d.....
0032F790: 00 10 00 00  FF FF 00 00  F6 A8 64 00  00 00 00 00  ..........d.....
0032F7A0: 00 00 00 00  88 4B 8B 7B  40 F8 32 00  00 00 00 00  .....K.{@.2.....
0032F7B0: 00 F8 32 00  B3 FD 85 7B  20 CE F7 B7  00 00 00 00  ..2....{ .......
0032F7C0: 40 F8 32 00  02 00 00 00  74 F9 32 00  80 00 00 00  @.2.....t.2.....
0032F7D0: 00 00 00 00  00 00 00 00  00 37 D7 00  0C F8 32 00  .........7....2.
0032F7E0: FB BD 89 7B  FF FF FF FF  08 F8 32 00  00 00 00 00  ...{......2.....
0032F7F0: FE 0F C7 7B  88 4B 8B 7B  60 F9 32 00  20 FA 32 00  ...{.K.{`.2. .2.
0032F800: 50 F9 32 00  DB B9 89 7B  00 00 00 00  00 00 00 00  P.2....{........
0032F810: 40 F8 32 00  78 53 E5 7B  88 4B 8B 7B  00 37 D7 00  @.2.xS.{.K.{.7..
0032F820: 00 37 D7 00  54 F8 32 00  FB BD 89 7B  FF FF FF FF  .7..T.2....{....
0032F830: 50 F8 32 00  00 00 00 00  64 F8 32 00  78 53 E5 7B  P.2.....d.2.xS.{
0032F840: 88 4B 8B 7B  00 37 D7 00  00 37 D7 00  7C F8 32 00  .K.{.7...7..|.2.
0032F850: FB BD 89 7B  FF FF FF FF  78 F8 32 00  00 00 00 00  ...{....x.2.....
0032F860: 8C F8 32 00  78 53 E5 7B  88 4B 8B 7B  00 37 D7 00  ..2.xS.{.K.{.7..
0032F870: 00 37 D7 00  A4 F8 32 00  FB BD 89 7B  FF FF FF FF  .7....2....{....
0032F880: A0 F8 32 00  00 00 00 00  B4 F8 32 00  00 10 00 00  ..2.......2.....
0032F890: 04 00 00 00  04 00 00 00  00 A0 EA 04  B8 F8 32 00  ..............2.
0032F8A0: 00 90 EA 04  C4 F8 32 00  6A BE 89 7B  FF FF FF FF  ......2.j..{....
0032F8B0: 00 90 EA 04  00 10 00 00  00 10 00 00  04 00 00 00  ................
0032F8C0: 00 90 EA 04  E0 F8 32 00  82 35 64 00  00 90 EA 04  ......2..5d.....
0032F8D0: 00 37 D7 00  00 80 EA 04  00 90 EA 04  CC 37 D7 00  .7...........7..
0032F8E0: 04 F9 32 00  0E 3B 64 00  00 90 EA 04  0C 3B D7 00  ..2..;d......;..
0032F8F0: 00 37 D7 00  00 00 00 00  00 37 D7 00  00 80 EA 04  .7.......7......
0032F900: 0B 00 00 00  2C F9 32 00  D1 3B 64 00  00 80 EA 04  ....,.2..;d.....
0032F910: 0B 00 00 00  E0 04 00 00  00 37 D7 00  E0 04 00 00  .........7......
0032F920: 2C 3B D7 00  BC 37 D7 00  DF 39 C3 7B  4C F9 32 00  ,;...7...9.{L.2.
0032F930: 2C 3B D7 00  00 00 00 00  58 F9 32 00  23 DC 40 00  ,;......X.2.#.@.
0032F940: 20 80 EA 04  80 04 00 00  00 00 00 00  48 00 00 00   ...........H...
0032F950: AF C5 85 A6  B8 F9 32 00  D7 5B 84 00  18 00 EC 04  ......2..[......
0032F960: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0032F970: 00 00 00 00  80 F9 32 00  70 04 EC 04  00 00 00 00  ......2.p.......
0032F980: D5 DB 7F 00  B4 FA 32 00  00 00 00 00  B4 2F E3 00  ......2....../..
0032F990: 18 43 3A 01  18 00 EC 04  00 00 00 00  AC 2F E3 00  .C:........../..
0032F9A0: F4 F9 32 00  D4 D4 7F 00  D0 04 00 00  CC 1A 90 00  ..2.............
0032F9B0: AB 06 00 00  87 CB 85 A6  EC F9 32 00  C9 6A 84 00  ..........2..j..
0032F9C0: 00 00 00 00  00 00 00 00  70 04 EC 04  02 00 00 00  ........p.......
0032F9D0: 6C 04 EC 04  B4 FA 32 00  00 04 00 00  04 00 00 00  l.....2.........
0032F9E0: 00 00 00 00  00 00 00 00  00 00 00 00  D0 FA 32 00  ..............2.
0032F9F0: C4 9C 7F 00  30 80 EA 04  00 00 00 00  00 00 00 00  ....0...........
0032FA00: 70 04 EC 04  02 00 00 00  6C 04 EC 04  B4 FA 32 00  p.......l.....2.
0032FA10: 00 04 00 00  04 00 00 00  00 00 00 00  00 00 00 00  ................
0032FA20: 00 00 00 00  EF C8 85 A6  01 00 00 00  00 00 00 00  ................
0032FA30: 00 00 00 00  18 00 EC 04  88 FA 32 00  FF 32 C4 7B  ..........2..2.{
0032FA40: 00 37 D7 00  00 40 3A 01  88 02 00 00  14 00 11 00  .7...@:.........
0032FA50: 78 BA 13 00  F0 BC 13 00  00 00 11 00  44 A5 C8 7B  x...........D..{
0032FA60: 40 BA 13 00  78 53 E5 7B  88 4B 8B 7B  00 10 EC 04  @...xS.{.K.{....
0032FA70: 00 90 EC 04  A4 FA 32 00  FB BD 89 7B  FF FF FF FF  ......2....{....
0032FA80: A0 FA 32 00  00 00 00 00  B4 FA 32 00  00 10 00 00  ..2.......2.....
0032FA90: 04 00 00 00  88 7F EC 04  BB 45 7F 00  C0 FA 32 00  .........E....2.
0032FAA0: 00 00 00 00  08 00 00 00  00 00 00 00  18 00 EC 04  ................
0032FAB0: 00 00 00 00  02 00 00 00  23 DC 40 00  00 00 00 00  ........#.@.....
0032FAC0: 30 80 EA 04  F8 FE 32 00  D3 7B 87 00  FF FF FF FF  0.....2..{......


------------------------------------------------------------------------------

======================================================================
Hardware/Driver Information:

Processor:              0x0
Page Size:              4096
Min App Address:        0x10000
Max App Address:        0x7ffeffff
Processor Mask:         0x3
Number of Processors:   2
Processor Type:         586
Allocation Granularity: 65536
Processor Level:        15
Processor Revision:     17155

Percent memory used:    13
Total physical memory:  3718176768
Free Memory:            3220262912
Page file:              5906059264
Total virtual memory:   2147352575

I use Wine 1.1.3 and getting really annoyed that i can't play WoW atm <_<

Help as fast as you can please ;)

---

### Post by Kromgol on 2008-08-28
Anyone? Please?

---

