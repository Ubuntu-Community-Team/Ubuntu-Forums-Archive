---
title: "What am I doing wrong with playing Skyrim on my mac?"
date: 2013-05-21
forum: Wine
---

### Post by Djbower79 on 2013-05-21
I have a Macbook, updated to Lion, 2 GHz Intel Core Duo processor, 4 gigs ram, and a NVIDIA GeForce 9 series graphics card. 
For a while now I have been messing with how to get Skyrim to work on my computer. I would just install it onto a Windows computer then transfer the files into a wrapper but I don't have a windows computer. So, I gave my computer to my tech guy who set up wine, installed the game and said it was good to go. 
But this is not the case.
When I try to play the game, I get this error:

Unhandled exception: unimplemented function msvcp90.dll.??0?$basic_ifstream@_WU?$char_traits@_W@std@@@std@@QAE@PB_WHH@Z called in 32-bit code (0x7b82c782).
Register dump:
 CS:001b SS:0023 DS:0023 ES:0023 FS:1007 GS:000f
 EIP:7b82c782 ESP:0033f7c4 EBP:0033f838 EFLAGS:00200246(   - --  I  Z- -P- )
 EAX:7b819335 EBX:7b82c726 ECX:00000000 EDX:00000000
 ESI:00000002 EDI:00429ef0
Stack dump:
0x0033f7c4:  0033f864 00000008 4351be74 80000100
0x0033f7d4:  00000001 00000000 7b82c782 00000002
0x0033f7e4:  435273a0 4352ab38 00000000 001355ec
0x0033f7f4:  00429ef0 0033f818 004050b6 0033f8fc
0x0033f804:  004050b6 00000004 0033f830 0033fc1c
0x0033f814:  0033f8fc 0033f82c 00403e52 00000001
0200: sel=1007 base=7ffc0000 limit=00000fff 32-bit rw-
Backtrace:
=>0 0x7b82c782 in kernel32 (+0x1c782) (0x0033f838)
  1 0x43527399 (0x0033f874)
  2 0x434f16d5 (0x0033fd78)
  3 0x00412633 in skyrimlauncher (+0x12632) (0x0033fe20)
  4 0x00407acf in skyrimlauncher (+0x7ace) (0x0033feb0)
  5 0x7b84c98c in kernel32 (+0x3c98b) (0x0033fec8)
  6 0x7b84f813 in kernel32 (+0x3f812) (0x0033ff08)
  7 0x7bc619dc (0x0033ff28)
  8 0x7bc62804 (0x0033ffa8)
  9 0x7bc619a2 (0x0033ffc8)
  10 0x7bc3d4fd (0x0033ffe8)
0x7b82c782: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (23 modules)
PE      400000-  5d2000    Export          skyrimlauncher
PE    10000000-10099000    Deferred        gameoverlayrenderer
PE    3b400000-3b41e000    Deferred        steam_api
PE    402e0000-402e4000    Deferred        version
PE    40710000-40714000    Deferred        advapi32
PE    40780000-40788000    Deferred        shlwapi
PE    42c30000-42d89000    Deferred        shell32
PE    42e70000-42eaa000    Deferred        user32
PE    42fd0000-42fd6000    Deferred        gdi32
PE    430a0000-430a4000    Deferred        msvcr90
PE    430d0000-430d9000    Deferred        msacm32
PE    43210000-4323e000    Deferred        comctl32
PE    43320000-43328000    Deferred        ole32
PE    43460000-43464000    Deferred        rpcrt4
PE    434e0000-434e3000    Deferred        msvcp90
PE    435f0000-435f4000    Deferred        msvcrt
PE    43680000-43684000    Deferred        dsound
PE    436e0000-43751000    Deferred        winmm
PE    43790000-43794000    Deferred        imm32
PE    43830000-43834000    Deferred        winex11
PE    43b50000-43b54000    Deferred        uxtheme
PE    7b810000-7b99b000    Export          kernel32
PE    7bc10000-7bc14000    Deferred        ntdll
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000007d    0
    0000001e    0
    00000015    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001c    0
    00000019    0
    00000014    0
    00000013    0
0000001a plugplay.exe
    00000020    0
    0000001d    0
    0000001b    0
00000021 explorer.exe
    00000022    0
00000037 steam.exe
    0000005d    0
    00000051    0
    00000050    0
    0000004f    0
    00000053    0
    00000052    0
    0000004c    0
    00000044    0
    00000029    0
    0000002b    0
    00000040    0
    0000003b    0
    00000039    0
    0000003f    0
    0000002d    0
    00000017    0
    00000045    0
    0000000b    0
    00000024    0
    00000028    0
    00000009    0
    00000041    0
    00000032    0
    00000033    0
    0000003a    0
    0000003d    0
    00000046    0
    0000002e    0
    0000003c    0
    00000025    0
    00000026    0
    0000002a    0
    00000031    0
    00000038    0
    0000002f    0
    00000030    0
    0000002c    0
    0000000d    0
    00000035    0
    00000034    0
    00000036    0
    00000043    0
    00000023    0
    00000047    0
    00000018    0
    0000003e    0
00000077 (D) C:\Program Files\Steam\steamapps\common\Skyrim\SkyrimLauncher.exe
    00000078    0 <==
System information:
    Wine build: wine-1.4.1
    Platform: i386
    Host system: Darwin
    Host version: 12.3.0



What is wrong? I have tried so many different ways of getting this to work, I even tried to go onto a windows computer and install it but that computer only had 2 gigs of ram (It was my mothers computer. She never uses it) so the game wouldn't even install without crashing.

Any input is amazing.

Thanks!

---

### Post by Mark Phelps on 2013-05-21
The link is to the WineHQ website compatibility page for your game.  You need to read through the test results to see if any of the advice works:  [http://appdb.winehq.org/objectManager.php?sClass=application&iId=13667]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=13667")

---

