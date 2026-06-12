---
title: "classic wow on inspiron 1525"
date: 2012-10-04
forum: Wine
---

### Post by sorryforwastingyourtime on 2012-10-04
Hello everyone! I have been trying to get classic world of warcraft running  but the game crashes immediately. I have read that some people got it running on an inspiron 1525 so maybe there is someone here to help me.

  

 Dell inspiron 1525
 processor: intel celeron cup 550 @ 2.00GHz
 memory: 2052MB
 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)  (driver: i915)
 ubuntu: 10.04.4  
 wine: 1.2.3
 wow-version: 1.12.1 (same result for bc and wotlk, even after multiple reinstallations)
 

 wine output:
> $ env WINEPREFIX="/home/andreas1/.wine" wine "C:\Programme\World of Warcraft\Wow.exe" -opengl  
 fixme:advapi:SetSecurityInfo stub  
 fixme:win:EnumDisplayDevicesW ((null),0,0x32ee68,0x00000000), stub!  
 fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver  
 fixme:d3d_caps:init_driver_info Unhandled vendor 8086.


> glxinfo | grep rendering  
 direct rendering: Yes  


 > glxinfo | less  direct rendering: Yes> glxinfo | grep rende  
 direct rendering: Yes  


 > OpenGL renderer string: Mesa DRI Intel(R) 965GM GEM 20091221 2009Q4 x86/MMX/SSE2
 

 I have tried:
 
[LIST]
[*]adding a config.wtf file with:
[/LIST]
[INDENT]SET gxApi "opengl"
SET ffxDeath "0"
SET ffxglow "0"
SET SoundOutputSystem "1" 
SET SoundBufferSize "150"
[/INDENT]
[LIST]
[*]tried d3d instead of opengl
[*]added registry and deactivated compiz
[*]installing direcx 9.0c according to a guide but nothing happend for "wine ~/.wine/drive_c/windows/system32/dxdiag.exe"
[/LIST]
             

 output from wow:

 

> World of WarCraft (build 5875)
 

 This application has encountered a critical error:
 

 ERROR #132 (0x85100084) Fatal Exception
 Program:	C:\Programme\World of Warcraft\WoW.exe
 Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:413E4636
 

 The instruction at "0x413E4636" referenced memory at "0x00000059".
 The memory could not be "read".
 

 

 WoWBuild: 5875
 ------------------------------------------------------------------------------
 

 ----------------------------------------
     x86 Registers
 ----------------------------------------
 

 EAX=00000001  EBX=41421FF4  ECX=00000000  EDX=00000001  ESI=00000000
 EDI=00000000  EBP=0033EAA0  ESP=0033EA18  EIP=413E4636  FLG=00210246
 CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B
 

 

 ----------------------------------------
     Stack Trace (Manual)
 ----------------------------------------
 

 Address  Frame    Logical addr  Module
 

 413E4636 0033EAA0 0001:000E3636 C:\windows\system32\wined3d.dll
 413569AB 0033F140 0001:000559AB C:\windows\system32\wined3d.dll
 4136199A 0033F160 0001:0006099A C:\windows\system32\wined3d.dll
 413E907A 0033F1A0 0001:000E807A C:\windows\system32\wined3d.dll
 20013D2D 0033F1D0 0001:00002D2D C:\windows\system32\d3d9.dll
 00598E85 0033F7F4 0001:00197E85 C:\Programme\World of Warcraft\WoW.exe
 005899A0 0033F804 0001:001889A0 C:\Programme\World of Warcraft\WoW.exe
 006414F3 0033FC40 0001:002404F3 C:\Programme\World of Warcraft\WoW.exe
 0063A270 0033FCA8 0001:00239270 C:\Programme\World of Warcraft\WoW.exe
 004027EC 0033FDF0 0001:000017EC C:\Programme\World of Warcraft\WoW.exe
 004021E0 0033FE00 0001:000011E0 C:\Programme\World of Warcraft\WoW.exe
 0040411E 0033FE90 0001:0000311E C:\Programme\World of Warcraft\WoW.exe
 7B85552C 0033FEA8 0001:0004452C C:\windows\system32\KERNEL32.dll
 7B857C7B 0033FEE8 0001:00046C7B C:\windows\system32\KERNEL32.dll
 7BC704C0 0033FEF8 0001:0005F4C0 C:\windows\system32\ntdll.dll
 7BC70690 0033FFC8 0001:0005F690 C:\windows\system32\ntdll.dll
 7BC4BB4A 0033FFE8 0001:0003AB4A C:\windows\system32\ntdll.dll
 

 ----------------------------------------
     Stack Trace (Using DBGHELP.DLL)
 ----------------------------------------
 

 413E4636 wined3d.dll  <unknown symbol>+0 (0x0013902C,0x414013C0,0x00008086,0x000080E1)
 413569AB wined3d.dll  <unknown symbol>+0 (0x00110060,0x7BC48A8B,0x41421FF4,0x0033F1A0)
 4136199A wined3d.dll  <unknown symbol>+0 (0x00139008,0x001385A0,0x001385A0,0x0033F1A0)
 413E907A wined3d.dll  WineDirect3DCreate+90 (0x00000009,0x00000010,0x0010000F,0x20013CD0)
 20013D2D d3d9.dll     Direct3DCreate9+93 (0x00000020,0x00C4E6BE,0x00000000,0x00C4E6BC)
 00598E85 WoW.exe      <unknown symbol>+0 (0x00C4E6C0,0x0033FC40,0x00C4E6C0,0x00401000)
 005899A0 WoW.exe      <unknown symbol>+0 (0x00C4E6C0,0x00401000,0x7B884FF4,0x00000004)
 006414F3 WoW.exe      <unknown symbol>+0 (0x00401000,0x7B884FF4,0x0033FC78,0x0033FC78)
 0063A270 WoW.exe      <unknown symbol>+0 (0x00000001,0x464F2044,0x46415243,0x00000020)
 004027EC WoW.exe      <unknown symbol>+0 (0x00000001,0x0033FE90,0x004099A0,0x00000000)
 004021E0 WoW.exe      <unknown symbol>+0 (0x004099A0,0x00000000,0x0000000A,0x7FFDF000)
 0040411E WoW.exe      <unknown symbol>+0 (0x7FFDF000,0x7B884FF4,0x0033FEE8,0x7FFDF000)
 7B85552C KERNEL32.dll call_process_entry+12 (0x7FFDF000,0x00000000,0x00000000,0x00000000)
 7B857C7B KERNEL32.dll <unknown symbol>+0 (0x7FFDF000,0x0033FFC8,0x7B857C20,0x00000000)
 7BC704C0 ntdll.dll    call_thread_func+12 (0x7B857C20,0x00000000,0xFFFFFFFF,0x7B836F20)
 7BC70690 ntdll.dll    call_thread_entry_point+112 (0x7B857C20,0x00000000,0x00000000,0x00000000)
 7BC4BB4A ntdll.dll    <unknown symbol>+0 (0x7B857C20,0x00000000,0x00905A4D,0x00000004)
 

 

 ----------------------------------------
     Loaded Modules
 ----------------------------------------
 

 0x00340000 - 0x003D6000  C:\Programme\World of Warcraft\fmod.dll
 0x00400000 - 0x00D06000  C:\Programme\World of Warcraft\WoW.exe
 0x10000000 - 0x10069000  C:\Programme\World of Warcraft\DivxDecoder.dll
 0x20010000 - 0x20034000  C:\windows\system32\d3d9.dll
 0x20040000 - 0x2004A000  C:\windows\system32\psapi.dll
 0x41300000 - 0x41424000  C:\windows\system32\wined3d.dll
 0x4DE80000 - 0x4DEC5000  C:\windows\system32\dbghelp.dll
 0x682F0000 - 0x68342000  C:\windows\system32\advapi32.dll
 0x68350000 - 0x6842D000  C:\windows\system32\comctl32.dll
 0x68440000 - 0x6855F000  C:\windows\system32\user32.dll
 0x68570000 - 0x68739000  C:\windows\system32\shell32.dll
 0x68750000 - 0x6879B000  C:\windows\system32\shlwapi.dll
 0x687A0000 - 0x687C8000  C:\windows\system32\ws2_32.dll
 0x687D0000 - 0x687E9000  C:\windows\system32\iphlpapi.dll
 0x68800000 - 0x6888E000  C:\windows\system32\opengl32.dll
 0x68A70000 - 0x68A87000  C:\windows\system32\imm32.dll
 0x68A90000 - 0x68B1C000  C:\windows\system32\winmm.dll
 0x68B20000 - 0x68B43000  C:\windows\system32\msacm32.dll
 0x68B60000 - 0x68BC5000  C:\windows\system32\msvcrt.dll
 0x68BE0000 - 0x68CC5000  C:\windows\system32\ole32.dll
 0x68CD0000 - 0x68D3A000  C:\windows\system32\rpcrt4.dll
 0x68D40000 - 0x68D96000  C:\windows\system32\wininet.dll
 0x68DB0000 - 0x68DD0000  C:\windows\system32\mpr.dll
 0x68EB0000 - 0x68F41000  C:\windows\system32\winex11.drv
 0x68F70000 - 0x68F99000  C:\windows\system32\uxtheme.dll
 0x72580000 - 0x7259A000  C:\windows\system32\wsock32.dll
 0x72920000 - 0x72997000  C:\windows\system32\gdi32.dll
 0x7B810000 - 0x7B97E000  C:\windows\system32\KERNEL32.dll
 0x7BC10000 - 0x7BCB9000  C:\windows\system32\ntdll.dll
 

 

 ----------------------------------------
     Memory Dump
 ----------------------------------------
 

 Code: 16 bytes starting at (EIP = 413E4636)
 

 413E4636: F6 41 59 02  75 50 6B C8  68 8B 45 08  03 88 FC 07  .AY.uPk.h.E.....
 

 

 Stack: 1024 bytes starting at (ESP = 0033EA18)
 

 * = addr                            **                                *        
 0033EA10: A0 EA 33 00  74 45 3E 41  20 00 00 00  40 FF 3F 41  ..3.tE>A ...@.?A
 0033EA20: 60 EA 33 00  93 69 C3 7B  40 FF 3F 41  B8 EA 33 00  `.3..i.{@.?A..3.
 0033EA30: E9 2F 42 41  C0 13 40 41  A0 87 46 7C  01 00 00 00  ./BA..@A..F|....
 0033EA40: C6 0B 00 00  F4 CF 67 6E  10 00 00 00  00 97 41 7C  ......gn......A|
 0033EA50: A0 EA 33 00  F4 BF 12 68  00 00 00 00  E8 2F 42 41  ..3....h...../BA
 0033EA60: 8E E4 C7 7B  D1 74 36 41  86 80 00 00  9C EF 33 00  ...{.t6A......3.
 0033EA70: E0 F0 41 41  20 72 41 41  88 EE 33 00  F4 7F F3 68  ..AA rAA..3....h
 0033EA80: A0 EA 33 00  F0 A2 F0 68  40 BA F3 68  E8 2F 42 41  ..3....h@..h./BA
 0033EA90: 4B 45 3E 41  F4 1F 42 41  31 00 00 00  86 80 00 00  KE>A..BA1.......
 0033EAA0: 40 F1 33 00  AB 69 35 41  2C 90 13 00  86 80 00 00  @.3..i5A,.......
 0033EAB0: C0 13 40 41  40 FF 3F 41  86 80 00 00  04 00 00 00  ..@A@.?A........
 0033EAC0: E1 80 00 00  67 83 00 00  00 00 00 00  00 00 00 00  ....g...........
 0033EAD0: 00 00 00 00  00 00 00 00  01 00 00 00  B0 EB 33 00  ..............3.
 0033EAE0: A0 85 13 00  00 80 FD 7F  83 C4 F3 68  F7 07 40 41  ...........h..@A
 0033EAF0: 5C C4 3F 41  04 F0 33 00  CF 11 40 41  E8 2F 42 41  \.?A..3...@A./BA
 0033EB00: 8D 12 40 41  18 F0 33 00  10 F0 33 00  0C F0 33 00  ..@A..3...3...3.
 0033EB10: C8 EF 33 00  80 13 40 41  A9 FE 3F 41  86 80 00 00  ..3...@A..?A....
 0033EB20: 00 00 06 00  88 EE 33 00  2C 90 13 00  1C 90 13 00  ......3.,.......
 0033EB30: 82 25 00 00  08 90 13 00  00 01 00 00  A0 EB 33 00  .%............3.
 0033EB40: 00 8C FD 7F  20 00 00 00  00 00 EB 68  01 00 00 00  .... ......h....
 0033EB50: F0 EB 33 00  8B 28 79 D1  A4 EB 33 00  34 00 00 C0  ..3..(y...3.4...
 0033EB60: 01 00 00 00  0E 01 00 00  F8 8B FD 01  A4 EB 33 00  ..............3.
 0033EB70: A0 EB 33 00  A4 EB 33 00  D4 20 00 00  00 00 00 00  ..3...3.. ......
 0033EB80: 8C EB 33 00  01 00 00 00  B8 EB 33 00  00 00 00 00  ..3.......3.....
 0033EB90: 00 00 00 00  12 00 13 00  C7 94 41 41  08 00 00 00  ..........AA....
 0033EBA0: 14 00 00 00  00 00 00 00  01 00 00 00  10 00 00 00  ................
 0033EBB0: 65 00 6E 00  61 00 62 00  6C 00 65 00  64 00 00 00  e.n.a.b.l.e.d...
 0033EBC0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
 0033EBD0: 7B F9 C6 7B  F4 CF C9 7B  FF FF FF FF  38 EC 33 00  {..{...{....8.3.
 0033EBE0: 80 EC 33 00  4A 5F C5 7B  F8 EB 33 00  00 00 00 00  ..3.J_.{..3.....
 0033EBF0: 00 00 00 00  60 E8 C3 7B  00 00 00 00  00 00 00 00  ....`..{........
 0033EC00: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
 0033EC10: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
 0033EC20: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
 0033EC30: 00 00 00 00  00 00 00 00  00 00 00 00  F4 BF 33 68  ..............3h
 0033EC40: 90 EC 33 00  72 6C 31 68  34 00 00 C0  00 00 00 02  ..3.rl1h4.......
 0033EC50: 58 EC 33 00  14 00 11 00  18 00 00 00  D8 20 00 00  X.3.......... ..
 0033EC60: F8 8B FD 7F  00 00 00 00  00 00 00 00  00 00 00 00  ................
 0033EC70: 10 00 11 00  60 E8 C3 7B  D4 20 00 00  C2 93 41 41  ....`..{. ....AA
 0033EC80: A0 EC 33 00  8D 5F C5 7B  D4 20 00 00  00 00 30 41  ..3.._.{. ....0A
 0033EC90: C0 EC 33 00  68 72 31 68  F4 CF C9 7B  D4 20 00 00  ..3.hr1h...{. ..
 0033ECA0: C0 EC 33 00  8A E9 C3 7B  00 00 00 00  11 00 12 00  ..3....{........
 0033ECB0: 9B 4F 31 68  F4 1F 42 41  69 E9 C3 7B  F4 1F 42 41  .O1h..BAi..{..BA
 0033ECC0: 60 EE 33 00  2B 9B 3E 41  00 00 00 00  C7 94 41 41  `.3.+.>A......AA
 0033ECD0: 00 00 00 00  00 00 00 00  36 ED 33 00  20 ED 33 00  ........6.3. .3.
 0033ECE0: 60 EE 33 00  F4 CF C9 7B  18 F0 33 00  60 ED 33 00  `.3....{..3.`.3.
 0033ECF0: 20 ED 33 00  36 ED 33 00  03 00 00 00  2C 14 30 41   .3.6.3.....,.0A
 0033ED00: 00 00 00 00  00 00 00 00  00 00 30 41  4E 00 01 00  ..........0AN...
 0033ED10: 30 00 03 00  00 00 00 00  00 00 00 00  34 E2 3F 41  0...........4.?A
 0033ED20: 0E 01 00 00  00 00 00 00  E4 F0 33 00  00 00 00 00  ..........3.....
 0033ED30: D4 20 00 00  64 EE 65 6E  61 62 6C 65  64 00 00 6D  . ..d.enabled..m
 0033ED40: 6D 65 5C 57  6F 72 6C 64  20 6F 66 20  57 61 72 63  me\World of Warc
 0033ED50: 72 61 66 74  5C 57 6F 57  2E 65 78 65  5C 44 69 72  raft\WoW.exe\Dir
 0033ED60: 65 63 74 33  44 00 6C 6C  00 33 18 68  00 00 00 00  ect3D.ll.3.h....
 0033ED70: 00 00 00 00  00 00 00 00  F4 CF C9 7B  00 00 00 00  ...........{....
 0033ED80: 50 EE 33 00  23 28 C8 7B  A4 ED 33 00  00 00 00 00  P.3.#(.{..3.....
 0033ED90: D8 EE 33 00  40 00 00 00  E0 ED 33 00  64 CF 14 68  ..3.@.....3.d..h
 0033EDA0: 40 00 00 00  10 F5 C6 7B  04 00 00 00  D8 EE 33 00  @......{......3.
 0033EDB0: 40 00 00 00  8B 68 74 D1  7C 3E FF 26  00 00 00 00  @....ht.|>.&....
 0033EDC0: 24 EE 33 00  00 80 FD 7F  00 00 00 00  01 00 00 00  $.3.............
 0033EDD0: D8 EE 33 00  F4 CF C9 7B  00 00 00 00  F8 ED 33 00  ..3....{......3.
 0033EDE0: C0 EE 33 00  4E FA C6 7B  02 00 00 00  F8 ED 33 00  ..3.N..{......3.
 0033EDF0: 00 00 00 00  7E 51 00 68  00 00 00 00  00 00 00 00  ....~Q.h........
 0033EE00: 00 00 00 00  00 00 00 00  18 00 00 00  00 00 00 00  ................
 0033EE10: E1 7B C4 7B  B8 7F 13 00  F4 BF 12 68  03 00 00 00  .{.{.......h....
 

 

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
 Processor Revision:     5633
 

 Percent memory used:    21
 Total physical memory:  2101252096
 Free Memory:            1640046592
 Page file:              -1
 Total virtual memory:   2147352575


thanks,
sorryforwastingyourtime

---

### Post by cwwilson721 on 2012-10-04
Just search this forum for "wow+wine+intel"

And good luck. Intel/WoW/wine is a bugger (Blame it on Wintel)

---

