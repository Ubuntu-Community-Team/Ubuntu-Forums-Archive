---
title: "Please dont make me go through this agony.. (WoW on Ubuntu)"
date: 2008-07-25
forum: Wine
---

### Post by tye959 on 2008-07-25
Hi,
I have a Dell Vostro 1400 and just booted Ubuntu 7.10 Gusty. I am a die hard WoW fan, and it would be perfect if I could have WoW running on Ubuntu. Now, I heard that this was possible through wine. The installation went fine, but when I try to open it I get this message in an error screen.


[I]==============================================================================
World of WarCraft (build 6080)

Exe:      C:\Program Files\World of Warcraft\WoW.exe
Time:     Jul 25, 2008  9:30:07.546 PM
User:     matt
Computer: matt-laptop
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\WoW.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:7E0776F5

The instruction at "0x7E0776F5" referenced memory at "0x00000010".
The memory could not be "read".


WoWBuild: 6080
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=00000000  EBX=7C09D5F0  ECX=7C31E170  EDX=00000005  ESI=0033E9A8
EDI=7CA41911  EBP=0033E8F0  ESP=0033E8EC  EIP=7E0776F5  FLG=00210202
CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

7E0776F5 0033E8F0 0000:00000000 C:\Program Files\World of Warcraft\WoW.exe
7C9BA1A6 0033EBF0 0001:000391A6 C:\windows\system32\wined3d.dll
7C9C3D5C 0033F0E0 0001:00042D5C C:\windows\system32\wined3d.dll
7CA33BDE 0033F110 0001:000B2BDE C:\windows\system32\wined3d.dll
7CA7A090 0033F140 0001:00009090 C:\windows\system32\d3d9.dll
005CF295 0033F764 0001:001CE295 C:\Program Files\World of Warcraft\WoW.exe
005BFCE0 0033F774 0001:001BECE0 C:\Program Files\World of Warcraft\WoW.exe
00682A62 0033FBAC 0001:00281A62 C:\Program Files\World of Warcraft\WoW.exe
0067B7E0 0033FC14 0001:0027A7E0 C:\Program Files\World of Warcraft\WoW.exe
004028DF 0033FE68 0001:000018DF C:\Program Files\World of Warcraft\WoW.exe
00402477 0033FE78 0001:00001477 C:\Program Files\World of Warcraft\WoW.exe
0040447E 0033FF08 0001:0000347E C:\Program Files\World of Warcraft\WoW.exe
7B87086C 0033FFE8 0001:0004F86C C:\windows\system32\KERNEL32.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

7E0776F5              <unknown symbol>+0 (0x7C09D5F0,0x00008620,0x7C31E170,0x7CA41878)
7C9BA1A6 wined3d.dll  IWineD3DImpl_FillGLCaps+34819 (0x7CA61C90,0x0012F090,0x0033ECE8,0x0033ECE8)
7C9C3D5C wined3d.dll  InitAdapters+8090 (0x0000000C,0x001104A0,0x001104A0,0x7BC32F3D)
7CA33BDE wined3d.dll  WineDirect3DCreate+34 (0x00000020,0x00000009,0x0012CB90,0x7B863C41)
7CA7A090 d3d9.dll     Direct3DCreate9+119 (0x00000020,0x0033F659,0x00CCD286,0x005C1E89)
005CF295 WoW.exe      <unknown symbol>+0 (0x00CCD288,0x00CCD28C,0x0033FBAC,0x00682A62)
005BFCE0 WoW.exe      <unknown symbol>+0 (0x00CCD288,0x00CCD28C,0x00401000,0x00000000)
00682A62 WoW.exe      <unknown symbol>+0 (0x00401000,0x00000000,0x7B8AE97C,0x00CD0830)
0067B7E0 WoW.exe      <unknown symbol>+0 (0x00000001,0x6C726F57,0x666F2064,0x72615720)
004028DF WoW.exe      <unknown symbol>+0 (0x00000001,0x00000001,0x0033FF08,0x0040447E)
00402477 WoW.exe      <unknown symbol>+0 (0x0040A380,0x00400000,0x00000000,0x001118FC)
0040447E WoW.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)
7B87086C KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
B7E2B29F              wine_switch_to_stack+23 (0x00000000,0x00000000,0x00000000,0x00000000)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00340000 - 0x003D0000  C:\Program Files\World of Warcraft\fmod.dll
0x00400000 - 0x00D89000  C:\Program Files\World of Warcraft\WoW.exe
0x10000000 - 0x10069000  C:\Program Files\World of Warcraft\DivxDecoder.dll
0x7B820000 - 0x7B929000  C:\windows\system32\KERNEL32.dll
0x7BC10000 - 0x7BCA2000  C:\windows\system32\ntdll.dll
0x7C680000 - 0x7C692000  C:\windows\system32\psapi.dll
0x7C6A0000 - 0x7C6DA000  C:\windows\system32\dbghelp.dll
0x7C980000 - 0x7CA65000  C:\windows\system32\wined3d.dll
0x7CA70000 - 0x7CA95000  C:\windows\system32\d3d9.dll
0x7CCD0000 - 0x7CCE0000  C:\windows\system32\midimap.dll
0x7CCF0000 - 0x7CCF7000  C:\windows\system32\msacm32.drv
0x7CD00000 - 0x7CD32000  C:\windows\system32\wineoss.drv
0x7E2A0000 - 0x7E2D1000  C:\windows\system32\uxtheme.dll
0x7E300000 - 0x7E389000  C:\windows\system32\winex11.drv
0x7E4C0000 - 0x7E4DC000  C:\windows\system32\mpr.dll
0x7E4F0000 - 0x7E529000  C:\windows\system32\wininet.dll
0x7E530000 - 0x7E588000  C:\windows\system32\rpcrt4.dll
0x7E5A0000 - 0x7E629000  C:\windows\system32\ole32.dll
0x7E640000 - 0x7E68E000  C:\windows\system32\msvcrt.dll
0x7E690000 - 0x7E6B4000  C:\windows\system32\msacm32.dll
0x7E6C0000 - 0x7E6C8000  C:\windows\system32\lz32.dll
0x7E6D0000 - 0x7E6E1000  C:\windows\system32\version.dll
0x7E6F0000 - 0x7E771000  C:\windows\system32\winmm.dll
0x7E780000 - 0x7E791000  C:\windows\system32\imm32.dll
0x7E940000 - 0x7E9AC000  C:\windows\system32\opengl32.dll
0x7E9D0000 - 0x7E9DD000  C:\windows\system32\iphlpapi.dll
0x7E9E0000 - 0x7EA08000  C:\windows\system32\ws2_32.dll
0x7EA10000 - 0x7EA21000  C:\windows\system32\wsock32.dll
0x7EA30000 - 0x7EA78000  C:\windows\system32\shlwapi.dll
0x7EA90000 - 0x7EB89000  C:\windows\system32\shell32.dll
0x7EBA0000 - 0x7EC22000  C:\windows\system32\gdi32.dll
0x7EC40000 - 0x7ED63000  C:\windows\system32\user32.dll
0x7ED70000 - 0x7EE23000  C:\windows\system32\comctl32.dll
0x7EE30000 - 0x7EE72000  C:\windows\system32\advapi32.dll


----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = 7E0776F5)

7E0776F5: 8B 40 10 89  81 9C 08 00  00 89 4D 10  C7 45 0C 20  .@........M..E. 


Stack: 1024 bytes starting at (ESP = 0033E8EC)

* = addr                                         **                       *   
0033E8E0: 98 00 00 00  E0 0F A6 7C  A8 E9 33 00  E0 0F A6 7C  .......|..3....|
0033E8F0: F0 EB 33 00  A6 A1 9B 7C  F0 D5 09 7C  20 86 00 00  ..3....|...| ...
0033E900: 70 E1 31 7C  78 18 A4 7C  90 1C A6 7C  02 00 00 00  p.1|x..|...|....
0033E910: 40 E9 33 00  9D FF 0A 7E  F0 D5 09 7C  AC A8 E0 B7  @.3....~...|....
0033E920: 20 03 00 00  21 00 00 00  01 00 00 00  C0 D4 23 7E   ...!.........#~
0033E930: 41 95 E0 B7  18 D9 02 7C  F0 D5 09 7C  00 00 80 79  A......|...|...y
0033E940: 70 E9 33 00  06 29 05 7E  C0 D4 23 7E  AC A8 E0 B7  p.3..).~..#~....
0033E950: 41 95 E0 B7  C8 EA 33 00  C0 03 00 00  01 00 00 00  A.....3.........
0033E960: AC 1C A6 7C  C8 EB 33 00  C4 E9 33 00  60 C9 A5 7C  ...|..3...3.`..|
0033E970: 90 E9 33 00  47 38 05 7E  F0 D5 09 7C  F2 19 00 00  ..3.G8.~...|....
0033E980: 0B 02 00 00  78 18 A4 7C  00 00 00 00  18 00 00 00  ....x..|........
0033E990: 53 E1 31 7C  00 00 00 00  FF FF FF FF  00 00 00 00  S.1|............
0033E9A0: 07 00 00 00  3C 18 05 7E  01 00 00 00  19 29 D8 B7  ....<..~.....)..
0033E9B0: 08 00 00 00  A6 62 08 7E  00 00 80 3F  00 00 40 40  .....b.~...?..@@
0033E9C0: D0 E9 33 00  80 00 00 00  C0 D4 23 7E  AC A8 E0 B7  ..3.......#~....
0033E9D0: F0 E9 33 00  C2 77 05 7E  01 00 00 00  AC A8 E0 B7  ..3..w.~........
0033E9E0: 20 EA 33 00  D3 5E 0C 7E  78 DA 0A 7C  00 00 00 00   .3..^.~x..|....
0033E9F0: 00 00 00 00  02 00 00 00  E5 3C CE B7  28 88 1E 7E  .........<..(..~
0033EA00: 00 00 80 3F  00 FF 7F 47  2A 88 1E 7E  F0 D5 09 7C  ...?...G*..~...|
0033EA10: 40 EA 33 00  E4 61 08 7E  60 4B 0B 7C  78 DA 01 7C  @.3..a.~`K.|x..|
0033EA20: 60 EA 33 00  D4 37 09 7E  28 88 1E 7E  08 DA 01 7C  `.3..7.~(..~...|
0033EA30: 78 DA 01 7C  C4 4A 0B 7C  F0 D5 09 7C  88 53 0E 7C  x..|.J.|...|.S.|
0033EA40: 60 EA 33 00  F0 69 05 7E  64 4B 0B 7C  08 DA 01 7C  `.3..i.~dK.|...|
0033EA50: 08 DA 01 7C  F0 D5 09 7C  F0 D5 09 7C  88 53 0E 7C  ...|...|...|.S.|
0033EA60: 80 EA 33 00  6F 73 05 7E  F0 D5 09 7C  05 04 00 00  ..3.os.~...|....
0033EA70: F0 53 0E 7C  00 00 00 00  00 00 00 00  E8 00 02 7C  .S.|...........|
0033EA80: 41 95 E0 B7  DA DC 04 7E  88 FA 02 7C  88 53 0E 7C  A......~...|.S.|
0033EA90: 88 53 0E 7C  0A C3 E0 B7  01 00 00 00  AC A8 E0 B7  .S.|............
0033EAA0: C0 EA 33 00  00 00 00 00  01 00 00 00  8F 00 00 00  ..3.............
0033EAB0: C0 EA 33 00  01 00 00 00  10 5E 02 7C  8F 00 00 00  ..3......^.|....
0033EAC0: 30 EB 33 00  60 D6 7C 7E  47 4C 5F 53  55 4E 5F 6D  0.3.`.|~GL_SUN_m
0033EAD0: 75 6C 74 69  5F 64 72 61  77 5F 61 72  72 61 79 73  ulti_draw_arrays
0033EAE0: 00 70 00 70  00 74 00 31  00 00 03 7C  10 5E 02 7C  .p.p.t.1...|.^.|
0033EAF0: 30 EB 33 00  BB A3 7C 7E  70 F0 03 7C  78 09 03 7C  0.3...|~p..|x..|
0033EB00: 00 00 00 00  00 00 00 00  C0 5E 02 7C  10 5E 02 7C  .........^.|.^.|
0033EB10: 00 00 00 00  38 C6 0F 7C  70 F0 03 7C  E8 9C C0 8F  ....8..|p..|....
0033EB20: 00 00 00 00  14 16 38 7E  E0 DA 12 00  90 F0 12 00  ......8~........
0033EB30: 50 EB 33 00  83 D7 7C 7E  03 30 C3 7B  14 16 38 7E  P.3...|~.0.{..8~
0033EB40: 50 EB 33 00  65 A4 35 7E  40 4B 38 7E  14 16 38 7E  P.3.e.5~@K8~..8~
0033EB50: C0 EB 33 00  C4 7F 34 7E  70 F0 03 7C  06 00 40 03  ..3...4~p..|..@.
0033EB60: 10 5E 02 7C  01 00 00 00  E0 1B C1 7E  14 16 38 7E  .^.|.......~..8~
0033EB70: 80 EB 33 00  65 A4 35 7E  40 4B 38 7E  01 00 00 00  ..3.e.5~@K8~....
0033EB80: E0 1B C1 7E  06 00 40 03  03 00 00 00  28 03 00 00  ...~..@.....(...
0033EB90: C0 EB 33 00  F4 6D BB 7E  28 03 00 00  FF FF 00 00  ..3..m.~(.......
0033EBA0: C0 EB 33 00  42 6F BB 7E  28 03 00 00  28 03 00 00  ..3.Bo.~(...(...
0033EBB0: 10 00 00 00  E8 9C C0 7E  A9 6E BB 7E  E8 9C C0 7E  .......~.n.~...~
0033EBC0: F0 EB 33 00  37 AC BE 7E  30 00 12 00  90 F0 12 00  ..3.7..~0.......
0033EBD0: 00 7C C0 7E  CA F9 BF 7E  28 03 00 00  E8 EC 33 00  .|.~...~(.....3.
0033EBE0: AE 19 9B 7C  E0 0F A6 7C  00 1A A6 7C  01 00 00 00  ...|...|...|....
0033EBF0: E0 F0 33 00  5C 3D 9C 7C  90 1C A6 7C  90 F0 12 00  ..3.\=.|...|....
0033EC00: E8 EC 33 00  E8 EC 33 00  0A 00 00 00  0A 00 00 00  ..3...3.........
0033EC10: 0A 00 00 00  0A 00 00 00  00 00 00 00  00 00 00 00  ................
0033EC20: 00 00 00 00  00 00 00 00  04 EC C8 7B  00 00 98 7C  ...........{...|
0033EC30: 40 EC 33 00  90 43 A9 7C  00 00 00 00  01 00 00 00  @.3..C.|........
0033EC40: 50 EC 33 00  44 24 86 7B  90 1C A6 7C  01 00 00 00  P.3.D$.{...|....
0033EC50: 80 EC 33 00  59 A2 A7 7C  00 00 A7 7C  8C 4B A9 7C  ..3.Y..|...|.K.|
0033EC60: 2F D5 A8 7C  C1 CB A8 7C  01 00 00 00  E8 EC 33 00  /..|...|......3.
0033EC70: 90 F0 12 00  62 80 A7 7C  90 43 A9 7C  00 00 A7 7C  ....b..|.C.|...|
0033EC80: A0 EC 33 00  D8 BD A8 7C  00 00 A7 7C  01 00 00 00  ..3....|...|....
0033EC90: 00 00 00 00  9C 69 C8 7B  00 00 A7 7C  C8 CA 12 00  .....i.{...|....
0033ECA0: C0 EC 33 00  09 30 C4 7B  00 00 A7 7C  01 00 00 00  ..3..0.{...|....
0033ECB0: 00 00 00 00  01 00 00 00  9C 69 C8 7B  9C 69 C8 7B  .........i.{.i.{
0033ECC0: 10 EE 33 00  FC 56 C4 7B  A0 BD A8 7C  00 00 A7 7C  ..3..V.{...|...|
0033ECD0: 01 00 00 00  00 00 00 00  B8 CB 12 00  B8 CB 12 00  ................
0033ECE0: D0 ED 33 00  FE 11 D9 73  28 00 01 00  25 00 00 00  ..3....s(...%...


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
Processor Level:        6
Processor Revision:     3853

Percent memory used:    25
Total physical memory:  1050525696
Free Memory:            783904768
Page file:              -168230912
Total virtual memory:   2147352575
[/I]




Anyone have this problem. Anyone know how to fix this. I'm going to have to switch back to dreadful Vista if not :(

---

### Post by Shadowhack on 2008-07-25
for me i just reboot my computer and it works fine

---

### Post by tye959 on 2008-07-25
> **Shadowhack said:**
> for me i just reboot my computer and it works fine

reboot as in completely reboot or just restart? 
(It took way too long to install WoW.lol)

---

### Post by DoktorSeven on 2008-07-25
What version of Wine (**wine --version**)?  What graphics card?  Do you have proper 3d drivers installed (**glxinfo | grep direct** should return "direct rendering: Yes")?  Checked [this guide](http://www.wowwiki.com/Linux/Wine) for any tips (particularly editing Config.wtf)?

---

### Post by desertboy on 2008-07-26
Rebooting Ubuntu would do nothing but you could try
wineboot in terminal to "reboot" wine doubt it'll make any difference.

---

### Post by YokoZar on 2008-07-26
I would try Wine 1.0 and/or Ubuntu 8.04 before going back to Vista.

---

### Post by Mahinva on 2008-07-26
Aside from upgrading both Wine and Ubuntu, did this error occur right after installation?

I've had to install WoW a few times now - only one reinstall was caused by an error. To remedy it, I had to manually put in a Config.wtf file into my WTF folder. This was because the game would crash with a big error even before I could log in, so no Config.wtf file could be made.

After putting in a new Config.wtf file, I made sure to manually change the resolution to match that of my monitor since I noticed that my resolution dramatically skewed after I launched the game, but before the game popped up full-screen. Aside from changing the resolution, I made sure that the video mode was set to OpenGL.

DoktorSeven mentions checking for: (glxinfo | grep direct should return "direct rendering: Yes"

You will want to type "glxinfo | grep direct" into your Terminal, without the quotation marks. If you get a return of Yes, then you should be able to play WoW, it will just take some tweaking.

Another link you may want to look into for troubleshooting is: 

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

As a note, when you come to the section on winecfg, look at step 6. Where it says DisabledExtensions, try adding that with quotation marks. For me, I noticed that without quotation marks, the winecfg tweak did nothing, however it seemed to improve my fps as claimed after putting that value in quotation marks.

---

### Post by tye959 on 2008-07-26
Well what I thought was that: I tweaked a lot of files and stuff. So maybe I did one of them wrong? What I'm going to do first is reinstall WoW, then if that doesnt work, I'm going to reset Ubuntu. (Probably get 8.10 and get the latest version of wine. I'll get back to you all.

---

### Post by tye959 on 2008-07-26
> **DoktorSeven said:**
> What version of Wine (**wine --version**)?  What graphics card?  Do you have proper 3d drivers installed (**glxinfo | grep direct** should return "direct rendering: Yes")?  Checked [this guide](http://www.wowwiki.com/Linux/Wine) for any tips (particularly editing Config.wtf)?

Um I dont know what WINE version I have, but I do have 2 Mobile GM965/GL960 Integrated Graphics Controllers. And when I ran that command I got a yes.

---

### Post by unicorn_2003_1 on 2008-07-26
Have you read through the guide at Wineapp? 
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329)

You need to do some registry tweak. WoW is well supported on wine and so is RoC and TFT. Good luck.

---

### Post by Spydr4590 on 2008-07-26
Just follow this guide I made for installing wow. [http://ubuntuforums.org/showthread.php?t=654681](http://ubuntuforums.org/showthread.php?t=654681) There is some specific information about ATI cards in here but you can still use this guide on Intel, Nvidia, and ATI cards.

---

### Post by Dunrobin on 2008-07-26
> **tye959 said:**
> Hi,
I have a Dell Vostro 1400 and just booted Ubuntu 7.10 Gusty. I am a die hard WoW fan, and it would be perfect if I could have WoW running on Ubuntu. Now, I heard that this was possible through wine. The installation went fine, but when I try to open it I get this message in an error screen.


[I]==============================================================================
World of WarCraft (build 6080)

Exe:      C:\Program Files\World of Warcraft\WoW.exe
Time:     Jul 25, 2008  9:30:07.546 PM
User:     matt
Computer: matt-laptop
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\WoW.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:7E0776F5

The instruction at "0x7E0776F5" referenced memory at "0x00000010".
The memory could not be "read".

{...}

Anyone have this problem. Anyone know how to fix this. I'm going to have to switch back to dreadful Vista if not :(

I'm running 8.04.1 64-bit, and I was having the same problem.  I discovered by accident that if I switched my screen resolution from 1440 x 900 down to 1024 x 768 *before* I launch WoW it runs just fine.  If I forget to switch before starting the game it crashes every time.

I don't know if that will solve your problem, but it can't hurt to try it.  :)

---

### Post by tye959 on 2008-07-26
Ok, could you tell me how to change my screen resolution? lol

---

### Post by tye959 on 2008-07-26
Wait, nevermind, I changed it. I'm going to try now.

---

