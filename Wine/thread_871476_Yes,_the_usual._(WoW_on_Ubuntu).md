---
title: "Yes, the usual. (WoW on Ubuntu)"
date: 2008-07-26
forum: Wine
---

### Post by tye959 on 2008-07-26
Ok,
This has been like my 3rd post on this. lol. Anyway, I've installed everything needed on WoW. I got WINE, all the patces, and the Config.WTF thing in there. I've tried changing my screen resolution. Didnt work. Any solutions? Thanks :)

---

### Post by aliayaz on 2008-07-27
umm more specs would help i mean what's the problem ? cause i might know it already

---

### Post by tye959 on 2008-07-27
Lets see, I have a Dell Vostro 1400, intel core 2 duo, 

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)


(please regard that I nothing about linux or basically computers)

---

### Post by tye959 on 2008-07-27
Oh yeah and I keep getting an error message saying

==============================================================================
World of WarCraft (build 8606)

Exe:      C:\Program Files\World of Warcraft\Wow.exe
Time:     Jul 27, 2008 10:19:15.368 AM
User:     matt
Computer: matt-laptop
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\Wow.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:7DFEC6F5

The instruction at "0x7DFEC6F5" referenced memory at "0x00000010".
The memory could not be "read".


WoWBuild: 8606
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=00000000  EBX=7C2E6998  ECX=7C1EA560  EDX=00000005  ESI=0033E95C
EDI=7E950911  EBP=0033E8A4  ESP=0033E8A0  EIP=7DFEC6F5  FLG=00210206
CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

Showing 3/3 threads...

--- Thread ID: 11 ---
7BC66B64 7CB0C80C 0001:00055B64 C:\windows\system32\ntdll.dll
7BC66C75 7CB0C83C 0001:00055C75 C:\windows\system32\ntdll.dll
7B88699C 7CB0C98C 0001:0006599C C:\windows\system32\KERNEL32.dll
7B886ADD 7CB0C9AC 0001:00065ADD C:\windows\system32\KERNEL32.dll

--- Thread ID: 19 ---
7B886882 7CC1D994 0001:00065882 C:\windows\system32\KERNEL32.dll
7B8868C6 7CC1D9B4 0001:000658C6 C:\windows\system32\KERNEL32.dll
0065EF34 7CC1DA10 0001:0025DF34 C:\Program Files\World of Warcraft\Wow.exe
0075FDD4 7CC1DA28 0001:0035EDD4 C:\Program Files\World of Warcraft\Wow.exe
7BC691B9 7CC1DAD8 0001:000581B9 C:\windows\system32\ntdll.dll
7BC69C64 7CC1E3D8 0001:00058C64 C:\windows\system32\ntdll.dll
B7DEE46B 7CC1E4C8 0000:00000000 <unknown>

--- Thread ID: 60 [Current Thread] ---
7DFEC6F5 0033E8A4 0000:00000000 C:\Program Files\World of Warcraft\Wow.exe
7E8C91A6 0033EBA4 0001:000481A6 C:\windows\system32\wined3d.dll
7E8D2D5C 0033F094 0001:00051D5C C:\windows\system32\wined3d.dll
7E942BDE 0033F0C4 0001:000C1BDE C:\windows\system32\wined3d.dll
7E989090 0033F0F4 0001:00008090 C:\windows\system32\d3d9.dll
005A437A 0033F108 0001:001A337A C:\Program Files\World of Warcraft\Wow.exe
0059EB57 0033F730 0001:0019DB57 C:\Program Files\World of Warcraft\Wow.exe
0064107A 0033FB64 0001:0024007A C:\Program Files\World of Warcraft\Wow.exe
0063D57F 0033FC14 0001:0023C57F C:\Program Files\World of Warcraft\Wow.exe
0040673D 0033FE5C 0001:0000573D C:\Program Files\World of Warcraft\Wow.exe
00406846 0033FE6C 0001:00005846 C:\Program Files\World of Warcraft\Wow.exe
00406898 0033FF08 0001:00005898 C:\Program Files\World of Warcraft\Wow.exe
7B87086C 0033FFE8 0001:0004F86C C:\windows\system32\KERNEL32.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

Showing 3/3 threads...

--- Thread ID: 11 ---
7BC66B64 ntdll.dll    NTDLL_wait_for_multiple_objects+540 (0x00000001,0x7CB0C874,0x00000004,0x00000000)
7BC66C75 ntdll.dll    NtWaitForMultipleObjects+105 (0x00000001,0x7CB0C874,0x00000000,0x00000000)
7B88699C KERNEL32.dll WaitForMultipleObjectsEx+180 (0x00000001,0x7CB0C9B4,0x00000000,0xFFFFFFFF)
7B886ADD KERNEL32.dll WaitForSingleObject+60 (0x000020C0,0xFFFFFFFF,0x7BC8699C,0x0075FD55)
0065D313 Wow.exe      <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 19 ---
7B886882 KERNEL32.dll SleepEx+67 (0x00000064,0x00000000,0x7CC1D9B4,0x7B851B34)
7B8868C6 KERNEL32.dll Sleep+37 (0x00000064,0x0075FD55,0x7BC8699C,0x01200BD8)
0065EF34 Wow.exe      <unknown symbol>+0 (0x01200C10,0x7BC68362,0x01200C10,0x01200C10)
0075FDD4 Wow.exe      <unknown symbol>+0 (0x0075FD55,0x01200C10,0x7BCA1CA0,0xB7DF3419)
7BC691B9 ntdll.dll    <unknown symbol>+0 (0x7CC1DB0C,0x00000000,0x00000000,0x00000000)
7BC69C64 ntdll.dll    NtQueueApcThread+0 (0x7FFD4FB8,0x7CC1E490,0x7CC1E490,0x7CC1E490)
B7DEE46B              start_thread+203 (0x7CC1EB90,0x00000000,0x00000000,0x00000000)
B7D7173E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 60 [Current Thread] ---
7DFEC6F5              <unknown symbol>+0 (0x7C2E6998,0x00008620,0x7C1EA560,0x7E950878)
7E8C91A6 wined3d.dll  IWineD3DImpl_FillGLCaps+34819 (0x7E970C90,0x0012E468,0x0033EC9C,0x0033EC9C)
7E8D2D5C wined3d.dll  InitAdapters+8090 (0x0000000C,0x001104A0,0x001104A0,0x7BC32F3D)
7E942BDE wined3d.dll  WineDirect3DCreate+34 (0x00000020,0x00000009,0x0012C150,0x7B863C41)
7E989090 d3d9.dll     Direct3DCreate9+119 (0x00000020,0x00D68F4C,0x00000000,0x0033F730)
005A437A Wow.exe      <unknown symbol>+0 (0x0033F128,0x0033F130,0x00D68F4C,0x00D68F4E)
0059EB57 Wow.exe      <unknown symbol>+0 (0x00D68F4C,0x00D68F4E,0x00D68F50,0x00D68F54)
0064107A Wow.exe      <unknown symbol>+0 (0x00D68F4C,0x00D6925D,0x008C9048,0x008C9054)
0063D57F Wow.exe      <unknown symbol>+0 (0x0033FC28,0x00000001,0x00000001,0x6C726F57)
0040673D Wow.exe      <unknown symbol>+0 (0x00000001,0x00000001,0x0033FF08,0x00406898)
00406846 Wow.exe      <unknown symbol>+0 (0x0040A4E9,0x00400000,0x00000000,0x00111A3C)
00406898 Wow.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)
7B87086C KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
B7E1329F              wine_switch_to_stack+23 (0x00000000,0x00000000,0x00000000,0x00000000)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00400000 - 0x00EC8000  C:\Program Files\World of Warcraft\Wow.exe
0x10000000 - 0x10069000  C:\Program Files\World of Warcraft\DivxDecoder.dll
0x7B820000 - 0x7B929000  C:\windows\system32\KERNEL32.dll
0x7BC10000 - 0x7BCA2000  C:\windows\system32\ntdll.dll
0x7C8A0000 - 0x7C8B2000  C:\windows\system32\psapi.dll
0x7C8C0000 - 0x7C8FA000  C:\windows\system32\dbghelp.dll
0x7CC50000 - 0x7CC7F000  C:\windows\system32\uxtheme.dll
0x7E1C0000 - 0x7E1D2000  C:\windows\system32\midimap.dll
0x7E1E0000 - 0x7E1E9000  C:\windows\system32\msacm32.drv
0x7E1F0000 - 0x7E224000  C:\windows\system32\wineoss.drv
0x7E260000 - 0x7E2DD000  C:\windows\system32\winex11.drv
0x7E420000 - 0x7E46C000  C:\windows\system32\rpcrt4.dll
0x7E480000 - 0x7E50D000  C:\windows\system32\ole32.dll
0x7E510000 - 0x7E533000  C:\windows\system32\msacm32.dll
0x7E550000 - 0x7E564000  C:\windows\system32\iphlpapi.dll
0x7E570000 - 0x7E58F000  C:\windows\system32\ws2_32.dll
0x7E5A0000 - 0x7E64F000  C:\windows\system32\comctl32.dll
0x7E660000 - 0x7E760000  C:\windows\system32\shell32.dll
0x7E770000 - 0x7E7B7000  C:\windows\system32\shlwapi.dll
0x7E7C0000 - 0x7E7D8000  C:\windows\system32\mpr.dll
0x7E7E0000 - 0x7E825000  C:\windows\system32\wininet.dll
0x7E830000 - 0x7E845000  C:\windows\system32\imm32.dll
0x7E850000 - 0x7E859000  C:\windows\system32\lz32.dll
0x7E860000 - 0x7E872000  C:\windows\system32\version.dll
0x7E880000 - 0x7E974000  C:\windows\system32\wined3d.dll
0x7E980000 - 0x7E9A4000  C:\windows\system32\d3d9.dll
0x7EB50000 - 0x7EBC1000  C:\windows\system32\opengl32.dll
0x7EBD0000 - 0x7EC10000  C:\windows\system32\advapi32.dll
0x7EC20000 - 0x7ECA9000  C:\windows\system32\gdi32.dll
0x7ECC0000 - 0x7EDEA000  C:\windows\system32\user32.dll
0x7EDF0000 - 0x7EE7A000  C:\windows\system32\winmm.dll


----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = 7DFEC6F5)

7DFEC6F5: 8B 40 10 89  81 9C 08 00  00 89 4D 10  C7 45 0C 20  .@........M..E. 


Stack: 1024 bytes starting at (ESP = 0033E8A0)

* = addr  **                                                  *               
0033E8A0: E0 FF 96 7E  A4 EB 33 00  A6 91 8C 7E  98 69 2E 7C  ...~..3....~.i.|
0033E8B0: 20 86 00 00  60 A5 1E 7C  78 08 95 7E  90 0C 97 7E   ...`..|x..~...~
0033E8C0: 02 00 00 00  F4 E8 33 00  9D 4F 02 7E  98 69 2E 7C  ......3..O.~.i.|
0033E8D0: AC 18 DF B7  20 03 00 00  21 00 00 00  01 00 00 00  .... ...!.......
0033E8E0: C0 24 1B 7E  41 05 DF B7  08 2D 03 7C  98 69 2E 7C  .$.~A....-.|.i.|
0033E8F0: 00 00 80 79  24 E9 33 00  06 79 FC 7D  C0 24 1B 7E  ...y$.3..y.}.$.~
0033E900: AC 18 DF B7  41 05 DF B7  7C EA 33 00  C0 03 00 00  ....A...|.3.....
0033E910: 01 00 00 00  AC 0C 97 7E  7C EB 33 00  78 E9 33 00  .......~|.3.x.3.
0033E920: 60 B9 96 7E  44 E9 33 00  47 88 FC 7D  98 69 2E 7C  `..~D.3.G..}.i.|
0033E930: BA 1D 00 00  0B 02 00 00  78 08 95 7E  00 00 00 00  ........x..~....
0033E940: 18 00 00 00  43 A5 1E 7C  00 00 00 00  FF FF FF FF  ....C..|........
0033E950: 00 00 00 00  07 00 00 00  3C 68 FC 7D  01 00 00 00  ........<h.}....
0033E960: 19 99 D6 B7  08 00 00 00  A6 B2 FF 7D  00 00 80 3F  ...........}...?
0033E970: 00 00 40 40  84 E9 33 00  80 00 00 00  C0 24 1B 7E  ..@@..3......$.~
0033E980: AC 18 DF B7  A4 E9 33 00  C2 C7 FC 7D  01 00 00 00  ......3....}....
0033E990: AC 18 DF B7  D4 E9 33 00  D3 AE 03 7E  20 6E 2F 7C  ......3....~ n/|
0033E9A0: 00 00 00 00  00 00 00 00  02 00 00 00  E5 AC CC B7  ................
0033E9B0: 28 D8 15 7E  00 00 80 3F  00 FF 7F 47  2A D8 15 7E  (..~...?...G*..~
0033E9C0: 98 69 2E 7C  F4 E9 33 00  E4 B1 FF 7D  08 DF 2F 7C  .i.|..3....}../|
0033E9D0: 98 2E 03 7C  14 EA 33 00  D4 87 00 7E  28 D8 15 7E  ...|..3....~(..~
0033E9E0: 28 2E 03 7C  98 2E 03 7C  6C DE 2F 7C  98 69 2E 7C  (..|...|l./|.i.|
0033E9F0: 88 8E 1E 7C  14 EA 33 00  F0 B9 FC 7D  0C DF 2F 7C  ...|..3....}../|
0033EA00: 28 2E 03 7C  28 2E 03 7C  98 69 2E 7C  98 69 2E 7C  (..|(..|.i.|.i.|
0033EA10: 88 8E 1E 7C  34 EA 33 00  6F C3 FC 7D  98 69 2E 7C  ...|4.3.o..}.i.|
0033EA20: 05 04 00 00  F0 8E 1E 7C  00 00 00 00  00 00 00 00  .......|........
0033EA30: 40 16 03 7C  41 05 DF B7  DA 2C FC 7D  38 59 03 7C  @..|A....,.}8Y.|
0033EA40: 88 8E 1E 7C  88 8E 1E 7C  0A 33 DF B7  01 00 00 00  ...|...|.3......
0033EA50: AC 18 DF B7  74 EA 33 00  00 00 00 00  01 00 00 00  ....t.3.........
0033EA60: 8F 00 00 00  74 EA 33 00  01 00 00 00  38 5F 02 7C  ....t.3.....8_.|
0033EA70: 8F 00 00 00  E4 EA 33 00  60 D6 9D 7E  47 4C 5F 53  ......3.`..~GL_S
0033EA80: 55 4E 5F 6D  75 6C 74 69  5F 64 72 61  77 5F 61 72  UN_multi_draw_ar
0033EA90: 72 61 79 73  00 70 00 70  00 74 00 31  00 00 03 7C  rays.p.p.t.1...|
0033EAA0: 38 5F 02 7C  E4 EA 33 00  BB A3 9D 7E  98 F1 03 7C  8_.|..3....~...|
0033EAB0: 90 A0 03 7C  00 00 00 00  00 00 00 00  E8 5F 02 7C  ...|........._.|
0033EAC0: 38 5F 02 7C  00 00 00 00  E0 16 2A 7C  98 F1 03 7C  8_.|......*|...|
0033EAD0: E8 0C C9 8F  00 00 00 00  14 56 2D 7E  B8 CE 12 00  .........V-~....
0033EAE0: 68 E4 12 00  04 EB 33 00  83 D7 9D 7E  03 30 C3 7B  h.....3....~.0.{
0033EAF0: 14 56 2D 7E  04 EB 33 00  65 E4 2A 7E  40 8B 2D 7E  .V-~..3.e.*~@.-~
0033EB00: 14 56 2D 7E  74 EB 33 00  C4 BF 29 7E  98 F1 03 7C  .V-~t.3...)~...|
0033EB10: 06 00 20 04  38 5F 02 7C  01 00 00 00  E0 8B C9 7E  .. .8_.|.......~
0033EB20: 14 56 2D 7E  34 EB 33 00  65 E4 2A 7E  40 8B 2D 7E  .V-~4.3.e.*~@.-~
0033EB30: 01 00 00 00  E0 8B C9 7E  06 00 20 04  03 00 00 00  .......~.. .....
0033EB40: 28 03 00 00  74 EB 33 00  F4 DD C3 7E  28 03 00 00  (...t.3....~(...
0033EB50: FF FF 00 00  74 EB 33 00  42 DF C3 7E  28 03 00 00  ....t.3.B..~(...
0033EB60: 28 03 00 00  10 00 00 00  E8 0C C9 7E  A9 DE C3 7E  (..........~...~
0033EB70: E8 0C C9 7E  A4 EB 33 00  37 1C C7 7E  30 00 12 00  ...~..3.7..~0...
0033EB80: 68 E4 12 00  00 EC C8 7E  CA 69 C8 7E  28 03 00 00  h......~.i.~(...
0033EB90: 9C EC 33 00  AE 09 8C 7E  E0 FF 96 7E  00 0A 97 7E  ..3....~...~...~
0033EBA0: 01 00 00 00  94 F0 33 00  5C 2D 8D 7E  90 0C 97 7E  ......3.\-.~...~
0033EBB0: 68 E4 12 00  9C EC 33 00  9C EC 33 00  0A 00 00 00  h.....3...3.....
0033EBC0: 0A 00 00 00  0A 00 00 00  0A 00 00 00  00 00 00 00  ................
0033EBD0: 00 00 00 00  00 00 00 00  00 00 00 00  2D 00 00 00  ............-...
0033EBE0: 00 00 00 00  55 8B C5 7B  00 00 00 00  00 00 00 00  ....U..{........
0033EBF0: 2D 00 00 00  E6 C1 12 00  2F 01 00 00  90 0C 97 7E  -......./......~
0033EC00: 54 EC 33 00  C8 C1 12 00  81 85 CC B7  FF FF FF FF  T.3.............
0033EC10: 00 00 00 00  9C 69 C8 7B  40 39 DE B7  00 00 00 00  .....i.{@9......
0033EC20: 9C EC 33 00  68 E4 12 00  48 0D 11 00  00 00 00 00  ..3.h...H.......
0033EC30: 50 C1 12 00  E6 C1 12 00  40 39 DE B7  00 00 00 00  P.......@9......
0033EC40: 54 ED 33 00  2B 0F CA 7B  F8 FE 33 00  4C 3C C3 7B  T.3.+..{..3.L<.{
0033EC50: 00 00 00 00  9C 69 C8 7B  00 00 00 00  90 ED 33 00  .....i.{......3.
0033EC60: 00 ED 33 00  9C 69 C8 7B  80 0C CA 7B  00 00 00 00  ..3..i.{...{....
0033EC70: A0 EC 33 00  F0 3E C3 7B  88 10 CA 7B  C0 EC 33 00  ..3..>.{...{..3.
0033EC80: 44 00 00 00  88 10 CA 7B  C0 EC 33 00  84 51 DF B7  D......{..3..Q..
0033EC90: 26 00 00 00  A0 3F C3 7B  88 10 CA 7B  28 00 01 00  &....?.{...{(...


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

Percent memory used:    36
Total physical memory:  1050525696
Free Memory:            669241344
Page file:              4126736384
Total virtual memory:   2147352575

---

### Post by yeaitsdark on 2008-07-27
Have you tried.
winecfg

Actually, what version of wine are you using?
wine --version

I assume you're using 1.0 or whatever the default deb pkg is.

OK just installed wine on this machine, so I could visualize it. Open winecfg. Click "Add Application", browse to "wow.exe". Make sure it's highlighted blue, then click the "Graphics" tab, select the checkbox "Emulate a Virtual Desktop" Click apply. Then try running it again. Let me know how that goes. That solved the problem for me once before. 

Also, perhaps unchecking "Allow Pixel Shader" may help you. Let me know how it goes.

Also, when in doubt.
sudo apt-get update
sudo apt-get upgrade

I had WoW working quite nicely in 1.0. However, I've since ended my addiction (12 step program, I'm up to making amends lol)

---

### Post by tye959 on 2008-07-27
GAH! I tried everything you said. Still doesn't work! Is it my computer?! I mean, when I had vista on here it ran, is it how I installed it?

---

### Post by Ferrat on 2008-07-27
Do you have 3D acceleration active?

---

### Post by flytripper on 2008-07-27
it is an integrated gpu. sorry there is prolly no chance of it working as it is intel and not nvidia or ati who do 3d cards. but who knows  you might geet lucky seeings as you said it worked with vista on it, still i doubt thast you will find it playable at all.

also you said you did the wtf thing. did you SET GxApi="OpenGL"  ?
Is there any restricted drivers for it? look in system>admin>hardware drivers
it could be that there is no intel linux gpu driver for your card or that you need to check their site out to see if there is.

---

### Post by flytripper on 2008-07-27
after checking out the model number of the laptop you supplied it should be a nvidia 8400 card. this is capable of playable gameplay for wow. i would deffers recomend checking 3d acceleration by means of restricted drivers

---

### Post by kdorf on 2008-07-27
Mine did this too on first install. You need to set it to OpenGL. Check the Wine AppDB.

---

### Post by tye959 on 2008-07-27
Ok, so what so I do to "enable" Open GL? (by the way, do I use the program "Envy" to do this?"

---

### Post by GSZX1337 on 2008-07-27
> **tye959 said:**
> Ok, so what so I do to "enable" Open GL? (by the way, do I use the program "Envy" to do this?"

Envy is used to update drivers for nVidia and ATi video cards.
As for the OpenGL enabling, I don't know how, as I don't have the game. Maybe it's an option in the game.

---

### Post by tye959 on 2008-07-27
> **GSZX1337 said:**
> Envy is used to update drivers for nVidia and ATi video cards.
As for the OpenGL enabling, I don't know how, as I don't have the game. Maybe it's an option in the game.

Yeah  but I cant open the game. lol. I'm kind of stuck..

---

### Post by gjoellee on 2008-07-27
you must set it to run OpenGl. 
can i please get a look at your Config.wtf ?(it is in WTF)

---

### Post by tye959 on 2008-07-27
> **gjoellee said:**
> you must set it to run OpenGl. 
can i please get a look at your Config.wtf ?(it is in WTF)


Uhh ok, how do I set it to OpenGL. Like what do I do?

And what do you mean by have a look at Config.wtf?

---

### Post by tye959 on 2008-07-27
Ok guys, thank you so much for your help, but I think I just did something wrong. So I'm just going to completely reboot and clear everything. Thanks for all the help! I'll tell you all how it goes! :(

---

### Post by hotballz87 on 2008-07-27
open the config.wtf file as a text file. 
if you dont have a line anywhere in there that says 

SET gxApi "opengl"

then put it in there, thats how you set your wow to opengl

---

### Post by darkknight045 on 2008-07-28
you can also enable opengl by running Wow as follows:

```
wine /home/<user name>/.wine/drive_c/Program\ Files/World\ of\ Warcraft/wow.exe -opengl
```

---

### Post by Axel1 on 2008-08-05
So I finally did what I had in mind for a long time, I broke free from microsoft's leash and installed UBUNTU. Well, I'm pretty HC WoW player aswell, and installed WoW asap. Now I think I have all the settings correctly in Wine, got the newest patch, everything's supposed to be set, but as soon as I start the game, the screen blinks between my desktop view and a black image with my mouse cursor showing as a brown square. Also the scroll bar in the License Agreement is brown. Any ideas?

---

### Post by Axel1 on 2008-08-05
Ok, nevermind, I got it to work by following a tutorial [here]("https://help.ubuntu.com/community/WorldofWarcraft#Config.wtf"). I edited the config file and everything works. Make sure you also check out the Troubleshooting page [here]("https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting"). Screen blinking was apparently because of the added visual effects in Ubuntu. I hope this helps anyone.

---

### Post by Mistrblank on 2008-08-05
This is all solvable by following directions @
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

