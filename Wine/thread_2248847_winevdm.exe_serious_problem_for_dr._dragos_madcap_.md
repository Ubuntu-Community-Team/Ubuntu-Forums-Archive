---
title: "winevdm.exe serious problem for dr. dragos madcap escape"
date: 2014-10-17
forum: Wine
---

### Post by lorebion on 2014-10-17
Hi I need help for this winevdm.exe error. 

I can enter the game and set options etc. but when I start a game it crashes.

The report says:

> Unhandled exception: page fault on read access to 0x45c0fbc3 in 32-bit code (0x442f9238).
Register dump:
 CS:001b SS:0023 DS:0023 ES:0023 FS:13f7 GS:000f
 EIP:442f9238 ESP:00fbe610 EBP:00fbe688 EFLAGS:00010206(  R- --  I   - -P- )
 EAX:00000001 EBX:442f91fe ECX:00fbe6d0 EDX:45c0fbc3
 ESI:0000001b EDI:45c0fbc3
Stack dump:
0x00fbe610:  0000001b 00fbe640 4071fa40 4022beb0
0x00fbe620:  7ff80c00 00000000 4022c0c0 4c010100
0x00fbe630:  00545349 00002430 0008257e 65766177
0x00fbe640:  4022c0c0 4c010100 00000001 00002430
0x00fbe650:  0008257e 00007d00 00002800 7bc41431
0x00fbe660:  00007d03 00007c00 00007d00 00007d00
027e: sel=13f7 base=7ff80000 limit=00000fff 32-bit rw-
Backtrace:
=>0 0x442f9238 (0x00fbe688)
  1 0x442fa4cc (0x00fbe6b8)
  2 0x7bc372f8 (0x00fbe748)
  3 0x7bc6df5b (0x00fbe7e8)
  4 0x7bc6f9b5 (0x00fbee18)
  5 0x7bc6fc4b (0x00fbee88)
  6 0xdeadbabe (0x00fbf678)
  7 0x7bc6dc6c (0x00fbf698)
  8 0x7bc6ed1a (0x00fbf718)
  9 0x7bc6dc32 (0x00fbf738)
  10 0x7bc7652c (0x00fbff88)
  11 0x9902a5fb (0x00fbffa8)
  12 0x9902a485 (0x00fbffc8)
  13 0x9902fcf2 (0x00fbffec)
0x442f9238: movzbl	0x0(%edx),%esi
Modules:
Module	Address			Debug info	Name (21 modules)
PE	40510000-40513000	Deferred        mciseq
PE	405a0000-405a3000	Deferred        winevdm
PE	422d0000-422d4000	Deferred        version
PE	44010000-4403e000	Deferred        user32
PE	44150000-44154000	Deferred        gdi32
PE	44270000-44274000	Deferred        advapi32
PE	444c0000-444c4000	Deferred        mpr
PE	44650000-4465b000	Deferred        winmm
PE	446a0000-446a8000	Deferred        ole32
PE	45010000-45014000	Deferred        rpcrt4
PE	450a0000-450a4000	Deferred        msacm32
PE	450f0000-450f4000	Deferred        winex11
PE	453c0000-453c4000	Deferred        mmdevapi
PE	453f0000-453f7000	Deferred        oleaut32
PE	45530000-45533000	Deferred        winecoreaudio
PE	45960000-45963000	Deferred        msacm32
PE	45970000-45973000	Deferred        midimap
PE	45b20000-45b24000	Deferred        imm32
PE	462e0000-462e3000	Deferred        usp10
PE	7b810000-7b866000	Deferred        kernel32
PE	7bc10000-7bc14000	Deferred        ntdll
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	0000001c    0
	0000001b    0
	00000016    0
	00000014    0
	00000010    0
	0000000f    0
00000012 winedevice.exe
	0000001f    0
	00000018    0
	00000017    0
	00000013    0
00000019 plugplay.exe
	0000001e    0
	0000001d    0
	0000001a    0
00000020 explorer.exe
	00000021    0
00000022 (D) C:\windows\system32\winevdm.exe
	0000002c   15
	0000002b    0
	00000028   15
	00000027   15 <==
	00000026    0
	00000025    0
	00000024    0
	00000023    0
System information:
    Wine build: wine-1.7.28
    Platform: i386
    Host system: Darwin
    Host version: 13.4.0




Any sirs who know how I can fix this? Much appreciated!

---

