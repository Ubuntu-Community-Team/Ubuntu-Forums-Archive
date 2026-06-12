---
title: "Does world of warcraft run on  the i945 chipset?"
date: 2007-12-25
forum: Wine
---

### Post by mjkelly on 2007-12-25
I'm trying to find someone out there who has this working at all. I've been trying to get this to work but people in #opengl are telling me its impossible so before i spend a few more hours reinstalling libraries and such, i'm trying to find out if it is indeed impossible or not?

---

### Post by Daimoneze on 2007-12-25
I got it to work until it's time to enter the game environment, at which point the system just locks (I've worked my way up from extreme tearing and lag). In other words, I get as far as the loading screen and the bar moves all the way across, that's it.

I'm using a Lenovo 3000 N100 with a 945GM chipset. 

One thing I did learn with all my experimenting is to NOT use opengl. Setting the config.wtf to use direct3d actually resulted in a vast improvement in frame rate although I'm still having issues with retaining my desired resolution (1280x800) as well the above.

I get the feeling the solution is going to come from properly setting up the config.wtf file since the game actually starts and runs and even renders the toon.

---

### Post by cogadh on 2007-12-25
The Linux drivers for Intel 950 or lower chipsets aren't the best. Unless significant improvements are made to the driver (unlikely to happen, those chipsets are pretty much legacy), you probably won't get any better performance out of that graphics card on any game through Wine.

---

### Post by Daimoneze on 2007-12-25
I wouldn't even go as far as to say I want anything even resembling "performance" out of this machine. I would be satisfied to simply get the game to work at this point. Considering the results I've had so far (I got in once but the poor toon was so horribly artifacted it looked like his arms were pulled from their sockets and reinserted on his chest and head) I'm fairly confident it can work, somehow.

---

### Post by mjkelly on 2007-12-25
Im pretty confident it can work too. I found on the warcraft forums players speaking about using the i945 chipset and getting between 15-30 fps with windows and lower graphics settings. So theres a definite possibility it can be done, im just not sure if it can be done now with the linux drivers or if we are going to have to sit and wait for them to get as good as the windows drivers...

---

### Post by -gabe-noob- on 2007-12-25
I was about to post the same thing, and the game can run under d3d for me but its soo laggy and the coloring is off, this is the only thing I miss from vista, lol stupid E1505

---

### Post by Daimoneze on 2007-12-29
Look into configuring your "Config.wtf" file in the WoW folder [here.]("http://www.wowwiki.com/Config.wtf_defaults") I suggest considering ffx, gxDepthBits and gxColorBits for color isssues.

---

### Post by Caedis on 2007-12-29
> **Daimoneze said:**
> I got it to work until it's time to enter the game environment, at which point the system just locks (I've worked my way up from extreme tearing and lag). In other words, I get as far as the loading screen and the bar moves all the way across, that's it.

I'm using a Lenovo 3000 N100 with a 945GM chipset. 

One thing I did learn with all my experimenting is to NOT use opengl. Setting the config.wtf to use direct3d actually resulted in a vast improvement in frame rate although I'm still having issues with retaining my desired resolution (1280x800) as well the above.

I get the feeling the solution is going to come from properly setting up the config.wtf file since the game actually starts and runs and even renders the toon.

Yea, had that too. The game looks like it would be stable if I could just login. Mine locks as I'm loading into the world. The progress bar just stops. 

My system is Kubuntu 7.10 Gutsy with a Intel 945GM chipset and 3GB of ram.

Really, I'd love it if I could just run WoW SOMEHOW in Linux. Not even VMware worked. I'm using Crossover instead of Wine at the hope that it will be slightly more complete.

Here's my crash dump data.... not sure it will help at all. But I want to be through.

```

==============================================================================
World of WarCraft (build 7561)

Exe:      Z:\apps\World of Warcraft\WoW.exe
Time:     Dec 29, 2007  9:02:54.882 PM
User:     caedis
Computer: laptop
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	Z:\apps\World of Warcraft\WoW.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:0059C1E7

The instruction at "0x0059C1E7" referenced memory at "0x0000002C".
The memory could not be "read".


WoWBuild: 7561
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=0027DA44  EBX=00001000  ECX=027A8F40  EDX=00000000  ESI=013A4E48
EDI=013A4BC8  EBP=0034F010  ESP=0034EFC8  EIP=0059C1E7  FLG=00010246
CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

Showing 6/6 threads...

--- Thread ID: 23 ---
7EFC5318 788DC958 0001:00044318 c:\windows\system32\ntdll.dll
7EFC5404 788DC998 0001:00044404 c:\windows\system32\ntdll.dll
7EFC545A 788DC9C8 0001:0004445A c:\windows\system32\ntdll.dll
7EFC8DD1 788DCA28 0001:00047DD1 c:\windows\system32\ntdll.dll
7EFC64EE 788DCA38 0001:000454EE c:\windows\system32\ntdll.dll
7EFC7189 788DCAD8 0001:00046189 c:\windows\system32\ntdll.dll
7EFC7C5A 788DD3D8 0001:00046C5A c:\windows\system32\ntdll.dll
B7E0346B 788DD4C8 0000:00000000 Z:\apps\World of Warcraft\WoW.exe

--- Thread ID: 22 ---
7EFC5318 789ED958 0001:00044318 c:\windows\system32\ntdll.dll
7EFC5404 789ED998 0001:00044404 c:\windows\system32\ntdll.dll
7EFC545A 789ED9C8 0001:0004445A c:\windows\system32\ntdll.dll
7EFC8DD1 789EDA28 0001:00047DD1 c:\windows\system32\ntdll.dll
7EFC64EE 789EDA38 0001:000454EE c:\windows\system32\ntdll.dll
7EFC7189 789EDAD8 0001:00046189 c:\windows\system32\ntdll.dll
7EFC7C5A 789EE3D8 0001:00046C5A c:\windows\system32\ntdll.dll
B7E0346B 789EE4C8 0000:00000000 Z:\apps\World of Warcraft\WoW.exe

--- Thread ID: 21 ---
7EFC5318 78ADE7E4 0001:00044318 c:\windows\system32\ntdll.dll
7EFC5404 78ADE824 0001:00044404 c:\windows\system32\ntdll.dll
7EEA653C 78ADE974 0001:0006553C c:\windows\system32\kernel32.dll
7EEA661A 78ADE9A4 0001:0006561A c:\windows\system32\kernel32.dll
0072BC26 78AFE9FC 0001:0032AC26 Z:\apps\World of Warcraft\WoW.exe
0072B4F8 78AFEA0C 0001:0032A4F8 Z:\apps\World of Warcraft\WoW.exe
0063AF27 78AFEA28 0001:00239F27 Z:\apps\World of Warcraft\WoW.exe
7EFC64EE 78AFEA38 0001:000454EE c:\windows\system32\ntdll.dll
7EFC7189 78AFEAD8 0001:00046189 c:\windows\system32\ntdll.dll
7EFC7C5A 78AFF3D8 0001:00046C5A c:\windows\system32\ntdll.dll
B7E0346B 78AFF4C8 0000:00000000 Z:\apps\World of Warcraft\WoW.exe

--- Thread ID: 20 ---
7EFC5318 7C6E4818 0001:00044318 c:\windows\system32\ntdll.dll
7EFC5404 7C6E4858 0001:00044404 c:\windows\system32\ntdll.dll
7EEA653C 7C6E49A8 0001:0006553C c:\windows\system32\kernel32.dll
7EEA7049 7C6E49D8 0001:00066049 c:\windows\system32\kernel32.dll
006472B0 7C6E49E8 0001:002462B0 Z:\apps\World of Warcraft\WoW.exe
0072B3E5 7C6E4A00 0001:0032A3E5 Z:\apps\World of Warcraft\WoW.exe
0072B521 7C6E4A0C 0001:0032A521 Z:\apps\World of Warcraft\WoW.exe
0063AF27 7C6E4A28 0001:00239F27 Z:\apps\World of Warcraft\WoW.exe
7EFC64EE 7C6E4A38 0001:000454EE c:\windows\system32\ntdll.dll
7EFC7189 7C6E4AD8 0001:00046189 c:\windows\system32\ntdll.dll
7EFC7C5A 7C6E53D8 0001:00046C5A c:\windows\system32\ntdll.dll
B7E0346B 7C6E54C8 0000:00000000 Z:\apps\World of Warcraft\WoW.exe

--- Thread ID: 19 ---
7EFC5318 7C83A420 0001:00044318 c:\windows\system32\ntdll.dll
7EFC5404 7C83A460 0001:00044404 c:\windows\system32\ntdll.dll
7EEA653C 7C83A5B0 0001:0006553C c:\windows\system32\kernel32.dll
7EEA7049 7C83A5E0 0001:00066049 c:\windows\system32\kernel32.dll
006472B0 7C83A5F0 0001:002462B0 Z:\apps\World of Warcraft\WoW.exe
004598BF 7C83AA0C 0001:000588BF Z:\apps\World of Warcraft\WoW.exe
0063AF27 7C83AA28 0001:00239F27 Z:\apps\World of Warcraft\WoW.exe
7EFC64EE 7C83AA38 0001:000454EE c:\windows\system32\ntdll.dll
7EFC7189 7C83AAD8 0001:00046189 c:\windows\system32\ntdll.dll
7EFC7C5A 7C83B3D8 0001:00046C5A c:\windows\system32\ntdll.dll
B7E0346B 7C83B4C8 0000:00000000 Z:\apps\World of Warcraft\WoW.exe

--- Thread ID: 17 [Current Thread] ---
0059C1E7 0034F010 0001:0019B1E7 Z:\apps\World of Warcraft\WoW.exe
0059C2D8 0034F024 0001:0019B2D8 Z:\apps\World of Warcraft\WoW.exe
0058E6AE 0034F088 0001:0018D6AE Z:\apps\World of Warcraft\WoW.exe
0058EAD9 0034F0BC 0001:0018DAD9 Z:\apps\World of Warcraft\WoW.exe
004086C6 0034F1B0 0001:000076C6 Z:\apps\World of Warcraft\WoW.exe
00408D21 0034F818 0001:00007D21 Z:\apps\World of Warcraft\WoW.exe
004A858A 0034F930 0001:000A758A Z:\apps\World of Warcraft\WoW.exe
00404689 0034F944 0001:00003689 Z:\apps\World of Warcraft\WoW.exe
00471537 0034FDA0 0001:00070537 Z:\apps\World of Warcraft\WoW.exe
0042D87B 0034FDD0 0001:0002C87B Z:\apps\World of Warcraft\WoW.exe
0042AD47 0034FDF0 0001:00029D47 Z:\apps\World of Warcraft\WoW.exe
0042C104 0034FE54 0001:0002B104 Z:\apps\World of Warcraft\WoW.exe
0042C1E1 0034FE6C 0001:0002B1E1 Z:\apps\World of Warcraft\WoW.exe
00406008 0034FF08 0001:00005008 Z:\apps\World of Warcraft\WoW.exe
7EE91D11 0034FFE8 0001:00050D11 c:\windows\system32\kernel32.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

Showing 6/6 threads...

--- Thread ID: 23 ---
7EFC5318 ntdll.dll    NTDLL_wait_for_multiple_objects+584 (0x00000001,0x788DC9D0,0x0000000C,0x788DC9F8)
7EFC5404 ntdll.dll    NtWaitForMultipleObjects+84 (0x00000001,0x788DC9D0,0x00000000,0x00000000)
7EFC545A ntdll.dll    NtWaitForSingleObject+42 (0x0000217C,0x00000000,0x788DC9F8,0x7EFC8C90)
7EFC8DD1 ntdll.dll    <unknown symbol>+0 (0x00000000,0x7EFC8C90,0x788DCAD8,0x7EFC7189)
7EFC64EE ntdll.dll    call_thread_entry_point+14 (0x7EFC8C90,0x00000000,0x788DDD84,0x7C366800)
7EFC7189 ntdll.dll    <unknown symbol>+0 (0x00000000,0x788DCAFC,0x7EFFE6A0,0x00001000)
7EFC7C5A ntdll.dll    <unknown symbol>+0 (0x7FFD2F98,0x788DD490,0x788DD490,0x788DD490)
B7E0346B              start_thread+203 (0x788DDB90,0x00000000,0x00000000,0x00000000)
B7D866DE              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 22 ---
7EFC5318 ntdll.dll    NTDLL_wait_for_multiple_objects+584 (0x00000001,0x789ED9D0,0x0000000C,0x789ED9F8)
7EFC5404 ntdll.dll    NtWaitForMultipleObjects+84 (0x00000001,0x789ED9D0,0x00000000,0x00000000)
7EFC545A ntdll.dll    NtWaitForSingleObject+42 (0x0000217C,0x00000000,0x789ED9F8,0x7EFEA920)
7EFC8DD1 ntdll.dll    <unknown symbol>+0 (0x00000000,0x7EFC8C90,0x789EDAD8,0x7EFC7189)
7EFC64EE ntdll.dll    call_thread_entry_point+14 (0x7EFC8C90,0x00000000,0x789EED84,0x7C366950)
7EFC7189 ntdll.dll    <unknown symbol>+0 (0x00000000,0x789EDAFC,0x7EFFE6A0,0x00001000)
7EFC7C5A ntdll.dll    <unknown symbol>+0 (0x7FFD4F98,0x789EE490,0x789EE490,0x789EE490)
B7E0346B              start_thread+203 (0x789EEB90,0x00000000,0x00000000,0x00000000)
B7D866DE              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 21 ---
7EFC5318 ntdll.dll    NTDLL_wait_for_multiple_objects+584 (0x00000002,0x78ADE85C,0x0000000C,0x78ADE854)
7EFC5404 ntdll.dll    NtWaitForMultipleObjects+84 (0x00000002,0x78ADE85C,0x00000000,0x00000000)
7EEA653C kernel32.dll WaitForMultipleObjectsEx+172 (0x00000002,0x78AEE9C8,0x00000000,0x000001F4)
7EEA661A kernel32.dll WaitForMultipleObjects+42 (0x00000002,0x78AEE9C8,0x00000000,0x000001F4)
0072BC26 WoW.exe      <unknown symbol>+0 (0x0072B530,0x0072B53B,0x78AFEA28,0x0063AF27)
0072B4F8 WoW.exe      <unknown symbol>+0 (0x04E27008,0x0063AEF0,0x04E12388,0x7EFECB88)
0063AF27 WoW.exe      <unknown symbol>+0 (0x00002168,0x0063AEF0,0x78AFEAD8,0x7EFC7189)
7EFC64EE ntdll.dll    call_thread_entry_point+14 (0x0063AEF0,0x04E12388,0x78AFFD84,0x7C366CD0)
7EFC7189 ntdll.dll    <unknown symbol>+0 (0x00000000,0x78AFEAFC,0x7EFFE6A0,0x00001000)
7EFC7C5A ntdll.dll    <unknown symbol>+0 (0x7FFD6F98,0x78AFF490,0x78AFF490,0x78AFF490)
B7E0346B              start_thread+203 (0x78AFFB90,0x00000000,0x00000000,0x00000000)
B7D866DE              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 20 ---
7EFC5318 ntdll.dll    NTDLL_wait_for_multiple_objects+584 (0x00000001,0x7C6E4890,0x0000000C,0x7C6E4888)
7EFC5404 ntdll.dll    NtWaitForMultipleObjects+84 (0x00000001,0x7C6E4890,0x00000000,0x00000000)
7EEA653C kernel32.dll WaitForMultipleObjectsEx+172 (0x00000001,0x7C6E49E0,0x00000000,0x000003E8)
7EEA7049 kernel32.dll WaitForSingleObject+57 (0x000020D8,0x000003E8,0x7C6E4A00,0x0072B3E5)
006472B0 WoW.exe      <unknown symbol>+0 (0x000003E8,0x04E27018,0x0072B510,0x00000014)
0072B3E5 WoW.exe      <unknown symbol>+0 (0x00000000,0x7C6E4A28,0x0063AF27,0x04E27018)
0072B521 WoW.exe      <unknown symbol>+0 (0x04E27018,0x0063AEF0,0x04E26568,0x7EFECB88)
0063AF27 WoW.exe      <unknown symbol>+0 (0x00002164,0x0063AEF0,0x7C6E4AD8,0x7EFC7189)
7EFC64EE ntdll.dll    call_thread_entry_point+14 (0x0063AEF0,0x04E26568,0x7C6E5D84,0x7C366CD0)
7EFC7189 ntdll.dll    <unknown symbol>+0 (0x00000000,0x7C6E4AFC,0x7EFFE6A0,0x00001000)
7EFC7C5A ntdll.dll    <unknown symbol>+0 (0x7FFD8F98,0x7C6E5490,0x7C6E5490,0x7C6E5490)
B7E0346B              start_thread+203 (0x7C6E5B90,0x00000000,0x00000000,0x00000000)
B7D866DE              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 19 ---
7EFC5318 ntdll.dll    NTDLL_wait_for_multiple_objects+584 (0x00000001,0x7C83A498,0x0000000C,0x7C83A490)
7EFC5404 ntdll.dll    NtWaitForMultipleObjects+84 (0x00000001,0x7C83A498,0x00000000,0x00000000)
7EEA653C kernel32.dll WaitForMultipleObjectsEx+172 (0x00000001,0x7C83A5E8,0x00000000,0x000001F4)
7EEA7049 kernel32.dll WaitForSingleObject+57 (0x00002088,0x000001F4,0x7C83AA0C,0x004598BF)
006472B0 WoW.exe      <unknown symbol>+0 (0x000001F4,0x00000000,0x00459870,0x00000013)
004598BF WoW.exe      <unknown symbol>+0 (0x00000000,0x0063AEF0,0x01B335E8,0x7EFECB88)
0063AF27 WoW.exe      <unknown symbol>+0 (0x000020D0,0x01B335E8,0x7C83AAD8,0x7EFC7189)
7EFC64EE ntdll.dll    call_thread_entry_point+14 (0x0063AEF0,0x01B335E8,0x7EECF770,0x7EFDF15D)
7EFC7189 ntdll.dll    <unknown symbol>+0 (0x00000000,0x7C83AAFC,0x7EFFE6A0,0x00001000)
7EFC7C5A ntdll.dll    <unknown symbol>+0 (0x7FFDAF98,0x7C83B490,0x7C83B490,0x7C83B490)
B7E0346B              start_thread+203 (0x7C83BB90,0x00000000,0x00000000,0x00000000)
B7D866DE              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 17 [Current Thread] ---
0059C1E7 WoW.exe      <unknown symbol>+0 (0x013A4E48,0x00000000,0x00000014,0x0034F088)
0059C2D8 WoW.exe      <unknown symbol>+0 (0x013A4E48,0x00883010,0x013B3970,0x0034F820)
0058E6AE WoW.exe      <unknown symbol>+0 (0x00000004,0x00BB03F0,0x0000000C,0x00000000)
0058EAD9 WoW.exe      <unknown symbol>+0 (0x00000004,0x00BB03F0,0x0000000C,0x00000000)
004086C6 WoW.exe      <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
00408D21 WoW.exe      <unknown symbol>+0 (0x00883010,0x0034F88C,0x0034F86C,0x00409200)
004A858A WoW.exe      <unknown symbol>+0 (0x00000001,0x013ACCA0,0x00000001,0x0034FDA0)
00404689 WoW.exe      <unknown symbol>+0 (0x00000001,0x4253FCB9,0xC380FD71,0xC5365948)
00471537 WoW.exe      <unknown symbol>+0 (0x0034FDE4,0x00000000,0x013ACC08,0x00000000)
0042D87B WoW.exe      <unknown symbol>+0 (0x013ACC08,0x00000005,0x0034FDE4,0x3D916873)
0042AD47 WoW.exe      <unknown symbol>+0 (0x000088AE,0x00000001,0x00000001,0x00009AD9)
0042C104 WoW.exe      <unknown symbol>+0 (0x00000001,0x00405FC8,0x00000001,0x00000001)
0042C1E1 WoW.exe      <unknown symbol>+0 (0x00409B99,0x00400000,0x00000000,0x001164D2)
00406008 WoW.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)
7EE91D11 kernel32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
B7E2D5F7              wine_switch_to_stack+23 (0x00000000,0x00000000,0x00000000,0x00000000)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00400000 - 0x00E65000  Z:\apps\World of Warcraft\WoW.exe
0x10000000 - 0x10069000  Z:\apps\World of Warcraft\DivxDecoder.dll
0x7BF40000 - 0x7BF7F000  c:\windows\system32\dbghelp.dll
0x7C5B0000 - 0x7C5BF000  c:\windows\system32\psapi.dll
0x7C6F0000 - 0x7C72B000  c:\windows\system32\dsound.dll
0x7C990000 - 0x7C994000  c:\windows\system32\midimap.dll
0x7C9A0000 - 0x7C9AC000  c:\windows\system32\msacm32.drv
0x7C9B0000 - 0x7C9E7000  c:\windows\system32\wineoss.drv
0x7E080000 - 0x7E0F6000  c:\windows\system32\winex11.drv
0x7E180000 - 0x7E18F000  c:\windows\system32\lz32.dll
0x7E1A0000 - 0x7E1A8000  c:\windows\system32\version.dll
0x7E1B0000 - 0x7E201000  c:\windows\system32\rpcrt4.dll
0x7E220000 - 0x7E2D8000  c:\windows\system32\ole32.dll
0x7E2F0000 - 0x7E309000  c:\windows\system32\iphlpapi.dll
0x7E310000 - 0x7E333000  c:\windows\system32\ws2_32.dll
0x7E340000 - 0x7E358000  c:\windows\system32\msacm32.dll
0x7E360000 - 0x7E406000  c:\windows\system32\comctl32.dll
0x7E420000 - 0x7E4FC000  c:\windows\system32\shell32.dll
0x7E510000 - 0x7E550000  c:\windows\system32\shlwapi.dll
0x7E560000 - 0x7E56F000  c:\windows\system32\mpr.dll
0x7E580000 - 0x7E5B4000  c:\windows\system32\wininet.dll
0x7E5C0000 - 0x7E5D0000  c:\windows\system32\imm32.dll
0x7E5E0000 - 0x7E67E000  c:\windows\system32\wined3d.dll
0x7E690000 - 0x7E6A9000  c:\windows\system32\d3d9.dll
0x7E9E0000 - 0x7EA47000  c:\windows\system32\opengl32.dll
0x7EA50000 - 0x7EA88000  c:\windows\system32\advapi32.dll
0x7EAA0000 - 0x7EB17000  c:\windows\system32\gdi32.dll
0x7EB30000 - 0x7EC41000  c:\windows\system32\user32.dll
0x7EC50000 - 0x7ECCB000  c:\windows\system32\winmm.dll
0x7EE40000 - 0x7EF48000  c:\windows\system32\kernel32.dll
0x7EF80000 - 0x7F000000  c:\windows\system32\ntdll.dll


----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = 0059C1E7)

0059C1E7: 8B 4A 2C FF  D1 85 C0 7C  51 83 7E 14  00 74 47 C7  .J,....|Q.~..tG.


Stack: 1024 bytes starting at (ESP = 0034EFC8)

* = addr                            **                                *       
0034EFC0: F0 EF 34 00  11 C4 5F 7E  40 8F 7A 02  44 DA 27 00  ..4..._~@.z.D.'.
0034EFD0: 50 00 00 00  F4 EF 34 00  00 10 00 00  69 91 DF 64  P.....4.....i..d
0034EFE0: 48 4E 3A 01  08 00 AE 01  00 00 00 00  C8 4B 3A 01  HN:..........K:.
0034EFF0: 08 00 AE 01  00 00 00 00  DC EF 34 00  40 EB 34 00  ..........4.@.4.
0034F000: F8 FE 34 00  40 C3 40 00  81 33 65 64  FE FF FF FF  ..4.@.@..3ed....
0034F010: 24 F0 34 00  D8 C2 59 00  48 4E 3A 01  00 00 00 00  $.4...Y.HN:.....
0034F020: 14 00 00 00  88 F0 34 00  AE E6 58 00  48 4E 3A 01  ......4...X.HN:.
0034F030: 10 30 88 00  70 39 3B 01  20 F8 34 00  EC 55 F4 7E  .0..p9;. .4..U.~
0034F040: 80 AD 12 05  24 F1 34 00  00 00 00 00  78 F0 34 00  ....$.4.....x.4.
0034F050: 00 40 00 00  60 00 78 02  48 4E 3A 01  00 00 00 00  .@..`.x.HN:.....
0034F060: 01 00 00 00  94 F0 34 00  32 5B 69 7E  F0 1D 18 00  ......4.2[i~....
0034F070: 00 00 00 00  00 00 00 00  14 00 00 00  00 00 00 00  ................
0034F080: 00 00 80 3F  0A 00 00 00  BC F0 34 00  D9 EA 58 00  ...?......4...X.
0034F090: 04 00 00 00  F0 03 BB 00  0C 00 00 00  00 00 00 00  ................
0034F0A0: 00 00 00 00  00 00 00 00  00 00 00 00  40 A3 8E 00  ............@...
0034F0B0: 08 00 00 00  00 00 00 00  00 00 00 00  B0 F1 34 00  ..............4.
0034F0C0: C6 86 40 00  04 00 00 00  F0 03 BB 00  0C 00 00 00  ..@.............
0034F0D0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0034F0E0: 00 00 00 00  00 00 00 00  40 A3 8E 00  08 00 00 00  ........@.......
0034F0F0: 00 00 00 00  00 00 00 00  81 88 40 00  FA 8A 40 00  ..........@...@.
0034F100: 00 00 00 00  00 00 80 3F  00 00 00 00  00 00 00 00  .......?........
0034F110: 00 00 00 00  00 00 00 00  00 00 80 3F  00 00 00 00  ...........?....
0034F120: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 80 3F  ...............?
0034F130: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0034F140: 00 00 80 3F  00 00 00 40  00 00 00 00  00 00 00 00  ...?...@........
0034F150: 00 00 00 00  00 00 00 00  00 00 00 40  00 00 00 00  ...........@....
0034F160: 00 00 00 00  00 00 00 00  00 00 00 00  6F 12 83 3B  ............o..;
0034F170: 00 00 00 00  00 00 80 BF  00 00 80 BF  00 00 80 BF  ................
0034F180: 00 00 80 3F  00 00 80 3F  00 00 00 00  00 00 00 00  ...?...?........
0034F190: 00 00 80 3F  00 00 80 3F  00 00 00 00  00 00 80 3F  ...?...?.......?
0034F1A0: 00 00 00 00  00 00 00 00  00 00 80 3F  00 00 80 3F  ...........?...?
0034F1B0: 18 F8 34 00  21 8D 40 00  00 00 00 00  00 00 00 00  ..4.!.@.........
0034F1C0: 00 00 00 00  00 00 00 00  7B 1A 6E 00  C1 09 1C 3C  ........{.n....<
0034F1D0: 00 00 00 00  01 00 00 00  69 00 00 00  00 00 00 00  ........i.......
0034F1E0: FE 07 00 00  60 9C 86 00  08 00 00 00  EC F1 34 00  ....`.........4.
0034F1F0: ED F1 34 00  00 00 00 00  54 B0 08 05  8C F8 34 00  ..4.....T.....4.
0034F200: 6C F8 34 00  C1 09 1C 3C  08 B0 08 05  47 6C 6F 62  l.4....<....Glob
0034F210: 61 6C 53 74  72 69 6E 67  73 2E 6C 75  61 00 30 00  alStrings.lua.0.
0034F220: 66 6F 6C 6C  6F 77 69 6E  67 20 6C 69  6E 65 21 00  following line!.
0034F230: 00 00 00 00  9C F3 34 00  19 84 E0 B7  00 00 00 00  ......4.........
0034F240: FF FF 00 00  10 00 00 43  88 CB FE 7E  8C F3 34 00  .......C...~..4.
0034F250: 13 03 FC 7E  20 A8 FE 7E  F4 F2 34 00  03 2A 01 10  ...~ ..~..4..*..
0034F260: 00 00 00 00  F4 F2 34 00  20 A8 FE 7E  96 FD FB 7E  ......4. ..~...~
0034F270: 04 00 00 00  80 F3 34 00  40 00 00 00  00 00 00 00  ......4.@.......
0034F280: 80 F3 34 00  D0 F2 34 00  68 F3 34 00  03 FF FB 7E  ..4...4.h.4....~
0034F290: 02 00 00 00  D0 F2 34 00  00 00 00 00  00 00 00 00  ......4.........
0034F2A0: EC F2 34 00  84 F3 34 00  03 FF FB 7E  02 00 00 00  ..4...4....~....
0034F2B0: 00 00 00 00  00 00 00 00  B4 59 F9 7E  14 F3 34 00  .........Y.~..4.
0034F2C0: 40 2D D2 00  E0 F2 34 00  88 CB FE 7E  9C F3 34 00  @-....4....~..4.
0034F2D0: 13 00 00 00  F4 F2 34 00  AF FF FB 7E  02 00 00 00  ......4....~....
0034F2E0: 9C F3 34 00  00 00 00 00  88 CB FE 7E  2C F3 34 00  ..4........~,.4.
0034F2F0: 98 F3 34 00  00 00 00 00  50 F4 34 00  19 84 E0 B7  ..4.....P.4.....
0034F300: 9C F3 34 00  40 00 00 00  78 F4 34 00  9C F3 34 00  ..4.@...x.4...4.
0034F310: 20 A8 FE 7E  EC 55 F4 7E  00 A8 12 05  40 2D D2 00   ..~.U.~....@-..
0034F320: C0 F3 34 00  00 00 00 00  03 F9 D0 C2  00 00 00 00  ..4.............
0034F330: 00 00 00 00  01 00 00 00  00 00 00 00  00 00 00 00  ................
0034F340: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0034F350: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0034F360: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0034F370: 8A 67 D8 B7  EC 55 F4 7E  B8 F3 34 00  07 00 00 00  .g...U.~..4.....
0034F380: 00 10 00 00  69 34 D8 B7  D7 02 00 00  88 CB FE 7E  ....i4.........~
0034F390: 00 10 00 00  00 10 00 00  B8 F3 34 00  AF FF FB 7E  ..........4....~
0034F3A0: 02 00 00 00  50 F4 34 00  00 00 00 00  88 CB FE 7E  ....P.4........~
0034F3B0: 00 10 00 00  88 CB FE 7E  E8 F4 34 00  4E E7 FC 7E  .......~..4.N..~
0034F3C0: C0 C9 FE 7E  50 F4 34 00  E8 F4 34 00  83 E6 FC 7E  ...~P.4...4....~


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
Processor Revision:     3592

Percent memory used:    18
Total physical memory:  3181252608
Free Memory:            2592092160
Page file:              7277432832
Total virtual memory:   2147352575



```

---

