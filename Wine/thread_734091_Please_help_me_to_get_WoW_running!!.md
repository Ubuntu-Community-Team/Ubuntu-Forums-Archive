---
title: "Please help me to get WoW running!!"
date: 2008-03-24
forum: Wine
---

### Post by TekMuzik on 2008-03-24
I've searched all over, tried like 5 different walk throughs, but still can't get WoW running. I'm going to put all the info I can in this post in the hopes someone can help me.
 
Basics: Ubuntu 7.10, Wine 0.9.58 running as Windows XP, Nvidia GeForce4 MX 4000 using restricted Nvidia driver.

The error I get from Wow is:
```

==============================================================================
World of WarCraft (build 6080)

Exe:      C:\Program Files\World of Warcraft\WoW.exe
Time:     Mar 24, 2008 12:30:21.406 PM
User:     kyle
Computer: kyle-linux
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\WoW.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:7D468311

The instruction at "0x7D468311" referenced memory at "0x00000000".
The memory could not be "read".


WoWBuild: 6080
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=0034F0F8  EBX=7D47C2B0  ECX=7D47BBE0  EDX=00000000  ESI=00CCD286
EDI=7D47CABC  EBP=0034F140  ESP=0034F0E8  EIP=7D468311  FLG=00210206
CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

7D468311 0034F140 0001:00017311 C:\windows\system32\d3d9.dll
005C1EA1 0034F764 0001:001C0EA1 C:\Program Files\World of Warcraft\WoW.exe
005BFCE0 0034F774 0001:001BECE0 C:\Program Files\World of Warcraft\WoW.exe
00682A62 0034FBAC 0001:00281A62 C:\Program Files\World of Warcraft\WoW.exe
0067B7E0 0034FC14 0001:0027A7E0 C:\Program Files\World of Warcraft\WoW.exe
004028DF 0034FE68 0001:000018DF C:\Program Files\World of Warcraft\WoW.exe
00402477 0034FE78 0001:00001477 C:\Program Files\World of Warcraft\WoW.exe
0040447E 0034FF08 0001:0000347E C:\Program Files\World of Warcraft\WoW.exe
7B86F7F9 0034FFE8 0001:0004E7F9 C:\windows\system32\KERNEL32.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

7D468311 d3d9.dll     <unknown symbol>+0 (0x00138BA8,0x00000000,0x00000000,0x0034F164)
005C1EA1 WoW.exe      <unknown symbol>+0 (0x00CCD288,0x00CCD28C,0x0034FBAC,0x00682A62)
005BFCE0 WoW.exe      <unknown symbol>+0 (0x00CCD288,0x00CCD28C,0x7FFDF000,0x00000000)
00682A62 WoW.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x7B8AC8A0,0x00CD0830)
0067B7E0 WoW.exe      <unknown symbol>+0 (0x00000001,0x6C726F57,0x666F2064,0x72615720)
004028DF WoW.exe      <unknown symbol>+0 (0x00000001,0x00000001,0x0034FF08,0x0040447E)
00402477 WoW.exe      <unknown symbol>+0 (0x0040A380,0x00400000,0x00000000,0x001118FC)
0040447E WoW.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)
7B86F7F9 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
B7E6C1CF              wine_switch_to_stack+23 (0x00000000,0x00000000,0x00000000,0x00000000)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00350000 - 0x003E0000  C:\Program Files\World of Warcraft\fmod.dll
0x00400000 - 0x00D89000  C:\Program Files\World of Warcraft\WoW.exe
0x10000000 - 0x10069000  C:\Program Files\World of Warcraft\DivxDecoder.dll
0x7B820000 - 0x7B926000  C:\windows\system32\KERNEL32.dll
0x7BC10000 - 0x7BCA2000  C:\windows\system32\ntdll.dll
0x7D300000 - 0x7D30E000  C:\windows\system32\psapi.dll
0x7D320000 - 0x7D356000  C:\windows\system32\dbghelp.dll
0x7D450000 - 0x7D47D000  C:\windows\system32\d3d9.dll
0x7D6A0000 - 0x7D6B3000  C:\windows\system32\midimap.dll
0x7D6C0000 - 0x7D6CA000  C:\windows\system32\msacm32.drv
0x7D7B0000 - 0x7D7D3000  C:\windows\system32\winealsa.drv
0x7D830000 - 0x7D858000  C:\windows\system32\uxtheme.dll
0x7D890000 - 0x7D913000  C:\windows\system32\winex11.drv
0x7DA70000 - 0x7DA87000  C:\windows\system32\mpr.dll
0x7DA90000 - 0x7DAD3000  C:\windows\system32\wininet.dll
0x7DAE0000 - 0x7DB31000  C:\windows\system32\rpcrt4.dll
0x7DB40000 - 0x7DBD1000  C:\windows\system32\ole32.dll
0x7DBE0000 - 0x7DC36000  C:\windows\system32\msvcrt.dll
0x7DC40000 - 0x7DC5C000  C:\windows\system32\msacm32.dll
0x7DC60000 - 0x7DC70000  C:\windows\system32\lz32.dll
0x7DC80000 - 0x7DC89000  C:\windows\system32\version.dll
0x7DC90000 - 0x7DD15000  C:\windows\system32\winmm.dll
0x7DD20000 - 0x7DD32000  C:\windows\system32\imm32.dll
0x7E970000 - 0x7E9D1000  C:\windows\system32\opengl32.dll
0x7E9F0000 - 0x7EA02000  C:\windows\system32\iphlpapi.dll
0x7EA10000 - 0x7EA2D000  C:\windows\system32\ws2_32.dll
0x7EA30000 - 0x7EA46000  C:\windows\system32\wsock32.dll
0x7EA50000 - 0x7EA9C000  C:\windows\system32\shlwapi.dll
0x7EAB0000 - 0x7EBA2000  C:\windows\system32\shell32.dll
0x7EBB0000 - 0x7EC3A000  C:\windows\system32\gdi32.dll
0x7EC50000 - 0x7ED76000  C:\windows\system32\user32.dll
0x7ED80000 - 0x7EE35000  C:\windows\system32\comctl32.dll
0x7EE40000 - 0x7EE7F000  C:\windows\system32\advapi32.dll


----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = 7D468311)

7D468311: 8B 0A 89 44  24 0C 8B 45  10 89 44 24  08 8B 45 0C  ...D$..E..D$..E.


Stack: 1024 bytes starting at (ESP = 0034F0E8)

* = addr                            **                                *       
0034F0E0: 40 F1 34 00  05 83 46 7D  BC CA 47 7D  A0 BC 44 7D  @.4...F}..G}..D}
0034F0F0: 7C 4F 44 7D  10 50 44 7D  64 F1 34 00  64 F3 34 00  |OD}.PD}d.4.d.4.
0034F100: 64 F5 34 00  84 F5 34 00  8C F5 34 00  90 F5 34 00  d.4...4...4...4.
0034F110: 94 F5 34 00  98 F5 34 00  9C F5 34 00  AC F5 34 00  ..4...4...4...4.
0034F120: A8 8B 13 00  31 33 86 7B  19 20 46 7D  0F 00 10 00  ....13.{. F}....
0034F130: 98 82 46 7D  84 D2 CC 00  86 D2 CC 00  59 F6 34 00  ..F}........Y.4.
0034F140: 64 F7 34 00  A1 1E 5C 00  A8 8B 13 00  00 00 00 00  d.4...\.........
0034F150: 00 00 00 00  64 F1 34 00  86 D2 CC 00  84 D2 CC 00  ....d.4.........
0034F160: 00 00 00 00  F8 90 06 7C  5C B1 E3 B7  80 00 00 00  .......|\.......
0034F170: A0 01 E2 B7  88 00 00 00  11 00 00 00  29 EA 01 00  ............)...
0034F180: 00 00 00 00  F0 30 C4 7B  EF 2E C3 7B  B8 20 00 00  .....0.{...{. ..
0034F190: E0 00 00 00  B4 85 F8 B7  70 B1 E3 B7  80 93 06 7C  ........p......|
0034F1A0: 90 F1 34 00  C0 00 00 00  F4 9F E3 B7  F4 9F E3 B7  ..4.............
0034F1B0: 40 B1 E3 B7  00 91 06 7C  F0 F1 34 00  00 18 D6 B7  @......|..4.....
0034F1C0: 40 B1 E3 B7  00 91 06 7C  C5 39 E4 B7  B0 F6 CE B7  @......|.9......
0034F1D0: 20 41 E5 B7  F8 90 06 7C  20 41 E5 B7  B0 F6 CE B7   A.....| A......
0034F1E0: 60 61 E5 B7  F4 5F F9 B7  00 00 00 00  00 91 06 7C  `a..._.........|
0034F1F0: 50 F4 34 00  B1 CF F8 B7  00 91 06 7C  94 48 01 00  P.4........|.H..
0034F200: 40 00 00 00  10 F3 34 00  B0 F2 34 00  00 00 00 00  @.....4...4.....
0034F210: 68 66 F9 B7  48 69 F9 B7  E8 A8 F7 B7  98 AB F7 B7  hf..Hi..........
0034F220: 00 E0 E3 B7  A8 E2 E3 B7  A0 62 F9 B7  68 31 00 7C  .........b..h1.|
0034F230: 48 34 00 7C  28 3B 00 7C  98 AA 00 7C  08 AD 00 7C  H4.|(;.|...|...|
0034F240: 88 B0 00 7C  50 B3 00 7C  30 C4 00 7C  50 C8 00 7C  ...|P..|0..|P..|
0034F250: E8 CC 00 7C  E0 D1 00 7C  10 D6 00 7C  E0 DA 00 7C  ...|...|...|...|
0034F260: A0 DE 00 7C  70 E2 00 7C  20 EE 00 7C  A8 F0 00 7C  ...|p..| ..|...|
0034F270: F0 F4 00 7C  90 F7 00 7C  30 FA 00 7C  D8 FC 00 7C  ...|...|0..|...|
0034F280: 88 FF 00 7C  38 02 01 7C  D8 04 01 7C  88 07 01 7C  ...|8..|...|...|
0034F290: A0 0A 01 7C  70 0D 01 7C  50 10 01 7C  18 13 01 7C  ...|p..|P..|...|
0034F2A0: 28 16 01 7C  D0 18 01 7C  B0 27 01 7C  B8 2B 01 7C  (..|...|.'.|.+.|
0034F2B0: D8 2F 01 7C  28 34 01 7C  08 38 01 7C  A0 3B 01 7C  ./.|(4.|.8.|.;.|
0034F2C0: C8 3F 01 7C  20 44 01 7C  E8 47 01 7C  80 4C 01 7C  .?.| D.|.G.|.L.|
0034F2D0: F8 81 01 7C  68 84 01 7C  B8 D7 01 7C  28 DA 01 7C  ...|h..|...|(..|
0034F2E0: 30 5E 04 7C  E0 BE 04 7C  50 C1 04 7C  78 C6 04 7C  0^.|...|P..|x..|
0034F2F0: E8 C8 04 7C  10 11 05 7C  88 14 05 7C  20 79 05 7C  ...|...|...| y.|
0034F300: A8 7B 05 7C  40 FD 05 7C  A8 01 06 7C  00 91 06 7C  .{.|@..|...|...|
0034F310: 1F 12 CA 7B  07 16 CA 7B  00 00 00 00  00 00 00 00  ...{...{........
0034F320: 01 01 01 01  01 01 01 01  01 01 01 01  01 01 01 01  ................
0034F330: 01 01 01 01  01 01 01 01  01 01 01 01  01 01 01 01  ................
0034F340: 01 01 01 01  01 01 01 01  01 01 01 01  01 01 01 01  ................
0034F350: 01 01 01 01  01 01 01 01  01 01 01 01  01 01 01 00  ................
0034F360: 90 F3 34 00  B0 89 C3 7B  40 99 E3 B7  00 00 00 00  ..4....{@.......
0034F370: 01 01 01 01  01 01 01 01  01 01 01 01  01 01 01 01  ................
0034F380: 01 01 01 01  01 01 01 01  01 01 01 01  01 01 01 01  ................
0034F390: 01 01 01 01  01 01 01 01  01 01 01 01  01 01 01 01  ................
0034F3A0: 01 01 01 01  01 01 01 01  01 01 01 01  01 01 01 00  ................
0034F3B0: 14 00 11 00  FC 6A C8 7B  D8 04 01 7C  04 00 00 00  .....j.{...|....
0034F3C0: 32 36 F9 B7  14 2A F9 B7  0C 03 06 7C  60 03 06 7C  26...*.....|`..|
0034F3D0: 10 F2 34 00  20 F3 34 00  70 F3 34 00  00 00 00 00  ..4. .4.p.4.....
0034F3E0: A8 F3 34 00  00 00 00 00  20 60 F9 B7  5C E2 E3 00  ..4..... `..\...
0034F3F0: 40 00 00 00  4C 04 01 00  00 00 00 00  07 00 00 00  @...L...........
0034F400: 50 66 F9 B7  00 00 00 00  00 00 00 00  40 00 00 00  Pf..........@...
0034F410: 00 91 06 7C  8C F4 34 00  00 00 00 00  88 F4 34 00  ...|..4.......4.
0034F420: 00 36 00 7C  24 57 E6 B7  02 00 00 00  AC 78 E4 B7  .6.|$W.......x..
0034F430: 58 F4 34 00  40 00 00 00  01 00 00 00  10 F3 34 00  X.4.@.........4.
0034F440: B0 F3 34 00  F4 5F F9 B7  60 62 F9 B7  00 91 06 7C  ..4.._..`b.....|
0034F450: 80 F4 34 00  F0 D5 F8 B7  60 62 F9 B7  00 00 00 00  ..4.....`b......
0034F460: 01 00 00 00  24 00 00 00  F0 E6 E3 B7  A8 E2 E3 B7  ....$...........
0034F470: 8D 64 E6 B7  F4 2F CF B7  00 00 00 00  28 31 00 7C  .d.../......(1.|
0034F480: 90 F4 34 00  B4 0C CF B7  00 91 06 7C  F4 5F F9 B7  ..4........|._..
0034F490: 70 F5 34 00  16 80 F8 B7  00 91 06 7C  00 00 00 00  p.4........|....
0034F4A0: 04 00 00 00  F0 E6 E3 B7  30 31 00 7C  38 31 00 7C  ........01.|81.|
0034F4B0: 34 31 00 7C  AC F6 CE B7  60 F5 34 00  7C F5 34 00  41.|....`.4.|.4.
0034F4C0: 00 00 00 00  24 57 E6 B7  F4 5F F9 B7  E0 5C F9 B7  ....$W..._...\..
0034F4D0: 28 31 00 7C  70 F5 34 00  98 F4 34 00  F9 7F F8 B7  (1.|p.4...4.....
0034F4E0: EB 16 A9 18  00 00 00 00  00 00 00 00  F0 F5 34 00  ..............4.


------------------------------------------------------------------------------

======================================================================
Hardware/Driver Information:
Processor:              0x0
Page Size:              4096
Min App Address:        0x10000
Max App Address:        0x7ffeffff
Processor Mask:         0x1
Number of Processors:   1
Processor Type:         586
Allocation Granularity: 65536
Processor Level:        6
Processor Revision:     521

Percent memory used:    48
Total physical memory:  793038848
Free Memory:            408694784
Page file:              -1182441472
Total virtual memory:   2147352575

```

The d3d9.dll seems to be causing the crash to me at least. Tried the .dll from Wine, one from the internet, and one for a Windows Vista install. All had same crash.
4 of the "loaded" modules aren't actually in the c:\windows\system32\  directory. wined3d.dll, winealsa.drv, winex11.drv. and mpr.dll.
 But i did find *.dll.so files for the 2 dll files in usr/lib/wine. No idea what .so files are or how to use them. Can't fnd anything for the 2 .drv files though.

Running wine wow.exe from terminal results in:
```
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7d470000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d470000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x34edd8,0x00000000), stub!
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set

```

My Config.wtf file contains
```

SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "OpenGL"

```
Anything anybody? Any help would be greatly appreciated!!! I'll give you cookies and gold stars.

---

### Post by Resonance378 on 2008-03-24
Are you certain you have 3D acceleration enabled and working appropriately for your video card?

This:
"err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set"

would indicate no.

Are you using the supplied nVidia drivers or are you using the ones from nVidia?

Additionally it's best to post these sorts of questions to:
[http://ubuntuforums.org/showthread.php?t=579378](http://ubuntuforums.org/showthread.php?t=579378)

I recommend reposting this message there and letting this thread die as your issue is not unique within the 1500+ posts made to that thread and more likely to get a response there.

---

