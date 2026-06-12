---
title: "can't seem to open wow..."
date: 2008-11-15
forum: Wine
---

### Post by fignig on 2008-11-15
i've spent about 2 full days trying to upgrade wow. and now i can't even open it. this error keeps popping up:

```

World of WarCraft (build 9183)

Exe:      C:\Program Files\World of Warcraft\Wow.exe
Time:     Nov 15, 2008  7:46:07.470 PM
User:     pete
Computer: pete
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\Wow.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0023:004118F0

The instruction at "0x004118F0" referenced memory at "0x00000000".
The memory could not be "read".


WoWBuild: 9183
Settings: 
SET readTOS "-1"
SET readEULA "-1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET installType "Retail"
SET locale "enUS"
SET showToolsUI "1"
SET portal "us"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxMultisample "1"
SET gxMultisampleQuality "0.000000"
SET videoOptionsVersion "1"
SET Sound_OutputDriverName "System Default"
SET farclip "450.000000"
SET specular "1"
SET particleDensity "1.000000"
SET groundEffectDensity "24"
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=003AFD44  EBX=017FCAE0  ECX=00000000  EDX=00000000  ESI=00000000
EDI=00000000  EBP=003AFD1C  ESP=003AFCF0  EIP=004118F0  FLG=00010246
CS =0023      DS =002B      ES =002B      SS =002B      FS =0063      GS =006B


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

Showing 14/14 threads...

--- Thread ID: 55 ---

--- Thread ID: 54 ---
7BC683AB 7B0C9604 0001:000573AB C:\windows\system32\ntdll.dll

--- Thread ID: 53 ---

--- Thread ID: 52 ---

--- Thread ID: 51 ---

--- Thread ID: 50 ---

--- Thread ID: 48 ---

--- Thread ID: 47 ---

--- Thread ID: 44 ---

--- Thread ID: 41 ---

--- Thread ID: 40 ---

--- Thread ID: 39 ---

--- Thread ID: 38 ---
7BC683AB 7C79A814 0001:000573AB C:\windows\system32\ntdll.dll

--- Thread ID: 37 [Current Thread] ---
004118F0 003AFD1C 0001:000108F0 C:\Program Files\World of Warcraft\Wow.exe
007E76CF 003AFD60 0001:003E66CF C:\Program Files\World of Warcraft\Wow.exe
00470680 003AFD6C 0001:0006F680 C:\Program Files\World of Warcraft\Wow.exe
00472F5D 003AFDA8 0001:00071F5D C:\Program Files\World of Warcraft\Wow.exe
00403834 003AFDE8 0001:00002834 C:\Program Files\World of Warcraft\Wow.exe
00426360 003AFE54 0001:00025360 C:\Program Files\World of Warcraft\Wow.exe
00426501 003AFE6C 0001:00025501 C:\Program Files\World of Warcraft\Wow.exe
00406AE8 003AFF08 0001:00005AE8 C:\Program Files\World of Warcraft\Wow.exe
7B879478 003AFFE8 0001:00058478 C:\windows\system32\KERNEL32.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

Showing 14/14 threads...

--- Thread ID: 55 ---
7BC683AB ntdll.dll    wine_server_call+11 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 54 ---
7BC683AB ntdll.dll    wine_server_call+11 (0x7B0C954C,0x00000000,0x00000000,0x7BC97460)
7BC6E6E3 ntdll.dll    NTDLL_wait_for_multiple_objects+547 (0x00000001,0x7B0C9670,0x00000004,0x7B0C9770)
7BC6E9D2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7B0C9670,0x00000000,0x00000000)
7B890E52 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000001,0x7B0C98CC,0x00000000,0x000001F4)
7B890FAA KERNEL32.dll WaitForMultipleObjects+58 (0x00000001,0x7B0C98CC,0x00000000,0x000001F4)
004224DB Wow.exe      <unknown symbol>+0 (0x00421DE0,0x7B0C9A28,0x006A1F57,0x0651A508)
00421DEE Wow.exe      <unknown symbol>+0 (0x0651A508,0x006A1F00,0x063AC588,0x7BC8EFF4)
006A1F57 Wow.exe      <unknown symbol>+0 (0x000021B0,0x006A1F00,0x7B0C9AD8,0x7BC717A2)
7BC7013E ntdll.dll    call_thread_entry_point+14 (0x006A1F00,0x063AC588,0x7B0C9AD8,0xF7D7F541)
7BC717A2 ntdll.dll    <unknown symbol>+0 (0x7B0C9B0C,0x00000000,0x00000000,0x00000000)
7BC7199D ntdll.dll    <unknown symbol>+0 (0x7FFA8FB8,0x7B0CAB90,0x7B0CAB90,0x7B0CAB90)
F7D7A50F              start_thread+191 (0x7B0CAB90,0x00000000,0x00000000,0x00000000)
F7CF8ECE              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 53 ---
7BC683AB ntdll.dll    wine_server_call+11 (0x7B23A77C,0x7B84F7CC,0x7B23A758,0x13893EC2)
7BC6E6E3 ntdll.dll    NTDLL_wait_for_multiple_objects+547 (0x00000001,0x7B23A8A0,0x00000004,0x7B23A9A0)
7BC6E9D2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7B23A8A0,0x00000000,0x00000000)
7B890E52 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000001,0x7B23A9E0,0x00000000,0x000003E8)
7B89104C KERNEL32.dll WaitForSingleObject+60 (0x00002120,0x000003E8,0x7B23AA00,0x00421CB5)
006A5C40 Wow.exe      <unknown symbol>+0 (0x000003E8,0x00000035,0x00421DC0,0x0651A518)
00421CB5 Wow.exe      <unknown symbol>+0 (0x00000000,0x7B23AA28,0x006A1F57,0x0651A518)
00421DD1 Wow.exe      <unknown symbol>+0 (0x0651A518,0x006A1F00,0x063AC570,0x7BC8EFF4)
006A1F57 Wow.exe      <unknown symbol>+0 (0x000021AC,0x006A1F00,0x7B23AAD8,0x7BC717A2)
7BC7013E ntdll.dll    call_thread_entry_point+14 (0x006A1F00,0x063AC570,0x7B23AAD8,0xF7D7F541)
7BC717A2 ntdll.dll    <unknown symbol>+0 (0x7B23AB0C,0x00000000,0x00000000,0x00000000)
7BC7199D ntdll.dll    <unknown symbol>+0 (0x7FFACFB8,0x7B23BB90,0x7B23BB90,0x7B23BB90)
F7D7A50F              start_thread+191 (0x7B23BB90,0x00000000,0x00000000,0x00000000)
F7CF8ECE              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 52 ---

--- Thread ID: 51 ---

--- Thread ID: 50 ---

--- Thread ID: 48 ---

--- Thread ID: 47 ---

--- Thread ID: 44 ---

--- Thread ID: 41 ---
7BC683AB ntdll.dll    wine_server_call+11 (0x00000000,0x00000000,0x00000000,0x00000000)
01390110 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x01390090,0x01390070)
07340030 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900A0,0x01390080)
01390070 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900B0,0x01390090)
01390080 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900C0,0x013900A0)
01390090 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900D0,0x013900B0)
013900A0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900E0,0x013900C0)
013900B0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900F0,0x013900D0)
013900C0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x01390100,0x013900E0)
013900D0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x01390110,0x013900F0)
013900E0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x01496D18,0x01390100)
013900F0 <unknown module> <unknown symbol>+0 (0x00002F80,0x00455355,0x0001454E,0x00001D90)
01390100 <unknown module> <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
01390110 <unknown module> <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
01496D18 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x01390090,0x01390070)
07340030 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900A0,0x01390080)
01390070 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900B0,0x01390090)
01390080 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900C0,0x013900A0)
01390090 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900D0,0x013900B0)
013900A0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900E0,0x013900C0)
013900B0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900F0,0x013900D0)
013900C0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x01390100,0x013900E0)
013900D0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x01390110,0x013900F0)
013900E0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x01496D18,0x01390100)
013900F0 <unknown module> <unknown symbol>+0 (0x00002F80,0x00455355,0x0001454E,0x00001D90)
01390100 <unknown module> <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
01390110 <unknown module> <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
01496D18 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x01390090,0x01390070)
07340030 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900A0,0x01390080)
01390070 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900B0,0x01390090)
01390080 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900C0,0x013900A0)
01390090 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900D0,0x013900B0)
013900A0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900E0,0x013900C0)
013900B0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900F0,0x013900D0)
013900C0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x01390100,0x013900E0)
013900D0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x01390110,0x013900F0)
013900E0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x01496D18,0x01390100)
013900F0 <unknown module> <unknown symbol>+0 (0x00002F80,0x00455355,0x0001454E,0x00001D90)
01390100 <unknown module> <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
01390110 <unknown module> <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
01496D18 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x01390090,0x01390070)
07340030 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900A0,0x01390080)
01390070 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900B0,0x01390090)
01390080 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900C0,0x013900A0)
01390090 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900D0,0x013900B0)
013900A0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900E0,0x013900C0)
013900B0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900F0,0x013900D0)
013900C0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x01390100,0x013900E0)
013900D0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x01390110,0x013900F0)
013900E0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x01496D18,0x01390100)
013900F0 <unknown module> <unknown symbol>+0 (0x00002F80,0x00455355,0x0001454E,0x00001D90)
01390100 <unknown module> <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
01390110 <unknown module> <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
01496D18 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x01390090,0x01390070)
07340030 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900A0,0x01390080)
01390070 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900B0,0x01390090)
01390080 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900C0,0x013900A0)
01390090 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900D0,0x013900B0)
013900A0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900E0,0x013900C0)
013900B0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900F0,0x013900D0)
013900C0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x01390100,0x013900E0)
013900D0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x01390110,0x013900F0)
013900E0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x01496D18,0x01390100)
013900F0 <unknown module> <unknown symbol>+0 (0x00002F80,0x00455355,0x0001454E,0x00001D90)
01390100 <unknown module> <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
01390110 <unknown module> <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
01496D18 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x01390090,0x01390070)
07340030 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900A0,0x01390080)
01390070 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900B0,0x01390090)
01390080 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900C0,0x013900A0)
01390090 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900D0,0x013900B0)
013900A0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900E0,0x013900C0)
013900B0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900F0,0x013900D0)
013900C0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x01390100,0x013900E0)
013900D0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x01390110,0x013900F0)
013900E0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x01496D18,0x01390100)
013900F0 <unknown module> <unknown symbol>+0 (0x00002F80,0x00455355,0x0001454E,0x00001D90)
01390100 <unknown module> <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
01390110 <unknown module> <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
01496D18 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x01390090,0x01390070)
07340030 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900A0,0x01390080)
01390070 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900B0,0x01390090)
01390080 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900C0,0x013900A0)
01390090 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900D0,0x013900B0)
013900A0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900E0,0x013900C0)
013900B0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900F0,0x013900D0)
013900C0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x01390100,0x013900E0)
013900D0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x01390110,0x013900F0)
013900E0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x01496D18,0x01390100)
013900F0 <unknown module> <unknown symbol>+0 (0x00002F80,0x00455355,0x0001454E,0x00001D90)
01390100 <unknown module> <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
01390110 <unknown module> <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
01496D18 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x01390090,0x01390070)
07340030 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900A0,0x01390080)
01390070 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900B0,0x01390090)
01390080 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900C0,0x013900A0)
01390090 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900D0,0x013900B0)
013900A0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900E0,0x013900C0)
013900B0 <unknown module> <unknown symbol>+0 (0x00000001,0x45455246,0x013900F0,0x013900D0)

--- Thread ID: 40 ---

--- Thread ID: 39 ---

--- Thread ID: 38 ---
7BC683AB ntdll.dll    wine_server_call+11 (0x7BC8EFF4,0x00000000,0x00000001,0x7C79A858)
7BC48950 ntdll.dll    <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 37 [Current Thread] ---
004118F0 Wow.exe      <unknown symbol>+0 (0x007EB0E3,0x0093AA64,0x00000000,0x003AFD44)
007E76CF Wow.exe      <unknown symbol>+0 (0x003AFD80,0x003AFDA8,0x00472F5D,0x003AFD80)
00470680 Wow.exe      <unknown symbol>+0 (0x003AFD80,0x000000AF,0x00000001,0x00932614)
00472F5D Wow.exe      <unknown symbol>+0 (0x00403DA9,0x00000102,0x017FE990,0x00427AE9)
00403834 Wow.exe      <unknown symbol>+0 (0x017FE8E0,0x00000007,0x00000000,0x00000A28)
00426360 Wow.exe      <unknown symbol>+0 (0x00000000,0x00406A80,0x00000001,0x00000001)
00426501 Wow.exe      <unknown symbol>+0 (0x0040AD49,0x00400000,0x00000000,0x00114E04)
00406AE8 Wow.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)
7B879478 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
F7DAFD77              wine_switch_to_stack+23 (0x00000000,0x00000000,0x00000000,0x00000000)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00400000 - 0x01390000  C:\Program Files\World of Warcraft\Wow.exe
0x10000000 - 0x10069000  C:\Program Files\World of Warcraft\DivxDecoder.dll
0x7B820000 - 0x7B93E000  C:\windows\system32\KERNEL32.dll
0x7BC10000 - 0x7BCAB000  C:\windows\system32\ntdll.dll
0x7C080000 - 0x7C08E000  C:\windows\system32\psapi.dll
0x7C0A0000 - 0x7C0DC000  C:\windows\system32\dbghelp.dll
0x7C0E0000 - 0x7C128000  C:\windows\system32\dsound.dll
0x7C9F0000 - 0x7CA7C000  C:\windows\system32\winex11.drv
0x7CBD0000 - 0x7CBF4000  C:\windows\system32\uxtheme.dll
0x7D250000 - 0x7D262000  C:\windows\system32\midimap.dll
0x7D270000 - 0x7D29F000  C:\windows\system32\wineoss.drv
0x7D2D0000 - 0x7D2E6000  C:\windows\system32\msacm32.drv
0x7D580000 - 0x7D59E000  C:\windows\system32\iphlpapi.dll
0x7D5B0000 - 0x7D605000  C:\windows\system32\rpcrt4.dll
0x7D620000 - 0x7D718000  C:\windows\system32\ole32.dll
0x7D720000 - 0x7D741000  C:\windows\system32\msacm32.dll
0x7D750000 - 0x7D76E000  C:\windows\system32\ws2_32.dll
0x7D780000 - 0x7D835000  C:\windows\system32\comctl32.dll
0x7D850000 - 0x7D961000  C:\windows\system32\shell32.dll
0x7D970000 - 0x7D9BE000  C:\windows\system32\shlwapi.dll
0x7D9C0000 - 0x7D9E1000  C:\windows\system32\mpr.dll
0x7D9F0000 - 0x7DA32000  C:\windows\system32\wininet.dll
0x7DA40000 - 0x7DA53000  C:\windows\system32\imm32.dll
0x7DA60000 - 0x7DA6E000  C:\windows\system32\version.dll
0x7DA80000 - 0x7DB91000  C:\windows\system32\wined3d.dll
0x7DBA0000 - 0x7DBC2000  C:\windows\system32\d3d9.dll
0x7EB10000 - 0x7EB8E000  C:\windows\system32\opengl32.dll
0x7EBA0000 - 0x7EBE3000  C:\windows\system32\advapi32.dll
0x7EBF0000 - 0x7EC83000  C:\windows\system32\gdi32.dll
0x7ECA0000 - 0x7EDD0000  C:\windows\system32\user32.dll
0x7EDE0000 - 0x7EE64000  C:\windows\system32\winmm.dll
0x7EE90000 - 0x7EE9D000  C:\windows\system32\lz32.dll


----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = 004118F0)

004118F0: 8B 01 BA FF  FE FE 7E 03  D0 83 F0 FF  33 C2 83 C1  ......~.....3...


Stack: 1024 bytes starting at (ESP = 003AFCF0)

* = addr  **                                                  *               
003AFCF0: 5A 76 7E 00  00 00 00 00  00 00 00 00  0F 12 6A 00  Zv~...........j.
003AFD00: 98 7C 7F 01  6C AA 93 00  FF FF FF 7F  7A DE 98 76  .|..l.......z..v
003AFD10: 60 BB 1F 01  34 FD 3A 00  8F 65 43 00  60 FD 3A 00  `...4.:..eC.`.:.
003AFD20: CF 76 7E 00  E3 B0 7E 00  64 AA 93 00  00 00 00 00  .v~...~.d.......
003AFD30: 44 FD 3A 00  20 66 7E 01  D6 05 47 00  00 00 00 00  D.:. f~...G.....
003AFD40: 64 AA 93 00  54 FD 3A 00  5F FD 3A 00  58 FD 3A 00  d...T.:._.:.X.:.
003AFD50: 00 04 00 00  04 00 00 00  03 00 00 00  D2 3A 42 00  .............:B.
003AFD60: 6C FD 3A 00  80 06 47 00  80 FD 3A 00  A8 FD 3A 00  l.:...G...:...:.
003AFD70: 5D 2F 47 00  80 FD 3A 00  AF 00 00 00  01 00 00 00  ]/G...:.........
003AFD80: 14 26 93 00  00 00 00 00  FF FF FF FF  00 00 00 00  .&..............
003AFD90: 00 04 00 00  00 03 00 00  00 00 00 00  00 00 00 00  ................
003AFDA0: 00 00 40 44  00 00 80 44  E8 FD 3A 00  34 38 40 00  ..@D...D..:.48@.
003AFDB0: A9 3D 40 00  02 01 00 00  90 E9 7F 01  E9 7A 42 00  .=@..........zB.
003AFDC0: 00 00 00 00  00 00 00 00  01 00 00 00  E0 E8 7F 01  ................
003AFDD0: E0 CA 7F 01  95 E9 7F 01  F4 FD 3A 00  F9 A5 7C 00  ..........:...|.
003AFDE0: E0 E8 7F 01  01 00 00 00  54 FE 3A 00  60 63 42 00  ........T.:.`cB.
003AFDF0: E0 E8 7F 01  07 00 00 00  00 00 00 00  28 0A 00 00  ............(...
003AFE00: 02 00 00 00  01 00 00 00  45 6E 67 69  6E 65 20 32  ........Engine 2
003AFE10: 35 00 00 00  10 37 13 00  00 00 00 00  00 00 11 00  5....7..........
003AFE20: 06 00 00 00  44 FE 3A 00  01 00 00 00  28 0A 00 00  ....D.:.....(...
003AFE30: 50 FE 3A 00  2A 07 89 7B  6C 20 00 00  00 00 00 00  P.:.*..{l ......
003AFE40: 02 00 00 00  B8 40 6F 01  B3 2D 00 00  02 00 00 00  .....@o..-......
003AFE50: 00 00 00 00  6C FE 3A 00  01 65 42 00  00 00 00 00  ....l.:..eB.....
003AFE60: 80 6A 40 00  01 00 00 00  01 00 00 00  08 FF 3A 00  .j@...........:.
003AFE70: E8 6A 40 00  49 AD 40 00  00 00 40 00  00 00 00 00  .j@.I.@...@.....
003AFE80: 04 4E 11 00  0A 00 00 00  12 7F CB B2  00 F0 FD 7F  .N..............
003AFE90: 00 10 40 00  F4 6F 8B 7B  44 00 00 00  00 00 00 00  ..@..o.{D.......
003AFEA0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003AFEB0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003AFEC0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003AFED0: 0C 00 00 00  10 00 00 00  14 00 00 00  05 00 00 C0  ................
003AFEE0: 01 00 00 00  05 00 00 00  00 00 00 00  00 F0 FD 7F  ................
003AFEF0: 88 FE 3A 00  38 F8 3A 00  2C FF 3A 00  C0 D6 40 00  ..:.8.:.,.:...@.
003AFF00: 62 E0 6A B2  01 00 00 00  E8 FF 3A 00  78 94 87 7B  b.j.......:.x..{
003AFF10: 00 F0 FD 7F  00 00 00 00  00 00 00 00  00 00 00 00  ................
003AFF20: 00 00 00 00  00 00 00 00  00 00 00 00  FF FF FF FF  ................
003AFF30: 00 95 87 7B  C0 61 84 7B  F4 6F 8B 7B  52 E1 AF FF  ...{.a.{.o.{R...
003AFF40: 00 F0 FD 7F  E8 FF 3A 00  2A 71 D3 83  DD 1B 05 F9  ......:.*q......
003AFF50: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003AFF60: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003AFF70: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003AFF80: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003AFF90: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003AFFA0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003AFFB0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003AFFC0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003AFFD0: 00 00 00 00  00 00 00 00  EB 93 87 7B  F4 6F 8B 7B  ...........{.o.{
003AFFE0: 52 E1 AF FF  00 F0 FD 7F  00 00 00 00  77 FD DA F7  R...........w...
003AFFF0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003B0000: 01 00 00 00  00 00 00 00  4C 6F 67 73  5C 67 78 2E  ........Logs\gx.
003B0010: 6C 6F 67 00  00 00 00 00  00 00 00 00  00 00 00 00  log.............
003B0020: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003B0030: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003B0040: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003B0050: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003B0060: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003B0070: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003B0080: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003B0090: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003B00A0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003B00B0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003B00C0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003B00D0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003B00E0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................


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
Processor Revision:     19202
Os Version:             5.1
Os Service Pack:        4.0

Percent memory used:    62
Total physical memory:  1049722880
Free Memory:            390553600
Page file:              4134162432
Total virtual memory:   2147352575

```

i've had the same computer for awhile. it's in my signature. and when i used windows, i used to play it flawlessly, no lag or anything. now when i switch i can't even open it. wats the deal?

---

### Post by fignig on 2008-11-15
is there anyway for my memory to get "read" anyone know a solution?

---

