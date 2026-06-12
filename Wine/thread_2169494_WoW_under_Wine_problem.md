---
title: "WoW under Wine problem"
date: 2013-08-22
forum: Wine
---

### Post by mf0rn on 2013-08-22
Hello!

I have World of Warcraft version 4.3.4 (15595) that I want to run on Ubuntu 12.04 LTS 32 bit
```

raresian@raresian-desktop:~$ uname -a
Linux raresian-desktop 3.2.0-51-generic-pae #77-Ubuntu SMP Wed Jul 24 20:40:32 UTC 2013 i686 athlon i386 GNU/Linux

```
under Wine 1.6 .

The problem is, when I get ingame, I enter my account and password and hit Login, I get the following error in WoW:
```

==============================================================================
World of WarCraft: Retail Build (build 15595)


Exe:      Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
Time:     Aug 22, 2013  3:22:11.355 PM
User:     raresian
Computer: raresian-desktop
------------------------------------------------------------------------------


This application has encountered a critical error:


ERROR #132 (0x85100084) Fatal exception!


Program:    Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
ProcessID:    1151
Exception:    0xC0000096 (PRIV_INSTRUCTION) at 0073:7E32AEA5








WoWBuild: 15595
Version: 4.3.4
Type:  WoW
Platform: X86


Patch data download failed.
Failed to parse patch data from server 'http://localhost'
InstallID: 'WoW'
Manifest is valid.




Settings: 
SET locale "enUS"
SET realmlist "wow.freakz.ro"
SET patchlist "localhost"
SET hwDetect "0"
SET videoOptionsVersion "4"
SET playIntroMovie "4"
SET showToolsUI "1"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET terrainMipLevel "0"
SET farclip "1250"
SET groundEffectDensity "128"
SET groundEffectDist "260"
SET environmentDetail "150"
SET projectedTextures "1"
SET shadowTextureSize "2048"
SET textureFilteringMode "5"
SET componentTextureLevel "9"
SET weatherDensity "3"
SET gxWindow "1"
SET gxResolution "1360x1024"
SET Gamma "1.000000"
SET readTOS "1"
SET readEULA "1"
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"


----------------------------------------
               GxInfo
----------------------------------------
GxApi: OpenGL
Shader Model: 2_0
  Vertex: arbvp1
  Pixel: arbfp1
Vendor: ATI Technologies Inc.
Renderer: ATI Radeon HD 5800 Series 
Version: 4.2.12172 Compatibility Profile Context 12.104


------------------------------------------------------------------------------


----------------------------------------
    x86 Registers
----------------------------------------


EAX=0000240C  EBX=00000010  ECX=0032F3D4  EDX=00000000  ESI=0669B5D0
EDI=0032F414  EBP=0032F3D8  ESP=0032F3C0  EIP=7E32AEA5  FLG=00010206
CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B




----------------------------------------
    Stack Trace (Manual)
----------------------------------------


Address  Frame    Logical addr  Module


Showing 21/21 threads...


--- Thread ID: 1894 ---
7BC80533 015FE7A8 0001:0006F533 C:\windows\system32\ntdll.dll
7BC8063A 015FE7D8 0001:0006F63A C:\windows\system32\ntdll.dll
7B872309 015FE948 0001:00061309 C:\windows\system32\KERNEL32.dll
7B872580 015FE988 0001:00061580 C:\windows\system32\KERNEL32.dll
7B872698 015FE9C8 0001:00061698 C:\windows\system32\KERNEL32.dll
004BB4B0 015FE9E0 0001:000BA4B0 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
00B05E56 015FE9F0 0001:00704E56 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
004B7819 015FEA18 0001:000B6819 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
7BC78E30 015FEA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 015FEAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 015FEB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 015FF368 0001:000710F9 C:\windows\system32\ntdll.dll
B75B6D4C 015FF468 0000:00000000 <unknown>


--- Thread ID: 1175 ---
7BC80533 07F9E388 0001:0006F533 C:\windows\system32\ntdll.dll
7BC8063A 07F9E3B8 0001:0006F63A C:\windows\system32\ntdll.dll
7BC8069B 07F9E3E8 0001:0006F69B C:\windows\system32\ntdll.dll
7BC667EF 07F9E508 0001:000557EF C:\windows\system32\ntdll.dll
7EAC12E9 07F9E588 0001:000202E9 C:\windows\system32\advapi32.dll
B408786B 07F9EA08 0001:0000686B C:\windows\system32\mmdevapi.dll
7BC78E30 07F9EA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 07F9EAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 07F9EB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 07F9F368 0001:000710F9 C:\windows\system32\ntdll.dll
B75B6D4C 07F9F468 0000:00000000 <unknown>


--- Thread ID: 1564 ---
7BC80533 0529E7A8 0001:0006F533 C:\windows\system32\ntdll.dll
7BC8063A 0529E7D8 0001:0006F63A C:\windows\system32\ntdll.dll
7B872309 0529E948 0001:00061309 C:\windows\system32\KERNEL32.dll
7B872580 0529E988 0001:00061580 C:\windows\system32\KERNEL32.dll
7B872698 0529E9C8 0001:00061698 C:\windows\system32\KERNEL32.dll
00AD4965 0529E9F4 0001:006D3965 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
00A910A9 0529EA04 0001:006900A9 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
00A91330 0529EA18 0001:00690330 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
7BC78E30 0529EA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 0529EAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 0529EB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 0529F368 0001:000710F9 C:\windows\system32\ntdll.dll
B75B6D4C 0529F468 0000:00000000 <unknown>


--- Thread ID: 1525 ---
7BC80533 07C9E7A8 0001:0006F533 C:\windows\system32\ntdll.dll
7BC8063A 07C9E7D8 0001:0006F63A C:\windows\system32\ntdll.dll
7B872309 07C9E948 0001:00061309 C:\windows\system32\KERNEL32.dll
7B872580 07C9E988 0001:00061580 C:\windows\system32\KERNEL32.dll
7B872698 07C9E9C8 0001:00061698 C:\windows\system32\KERNEL32.dll
00AD4965 07C9E9F4 0001:006D3965 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
00A910A9 07C9EA04 0001:006900A9 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
00A91330 07C9EA18 0001:00690330 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
7BC78E30 07C9EA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 07C9EAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 07C9EB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 07C9F368 0001:000710F9 C:\windows\system32\ntdll.dll
B75B6D4C 07C9F468 0000:00000000 <unknown>


--- Thread ID: 1376 ---
7BC80533 0740E7A8 0001:0006F533 C:\windows\system32\ntdll.dll
7BC8063A 0740E7D8 0001:0006F63A C:\windows\system32\ntdll.dll
7B872309 0740E948 0001:00061309 C:\windows\system32\KERNEL32.dll
7B872580 0740E988 0001:00061580 C:\windows\system32\KERNEL32.dll
7B872698 0740E9C8 0001:00061698 C:\windows\system32\KERNEL32.dll
004BB4B0 0740E9E4 0001:000BA4B0 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
007023DB 0740EA18 0001:003013DB Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
7BC78E30 0740EA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 0740EAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 0740EB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 0740F368 0001:000710F9 C:\windows\system32\ntdll.dll
B75B6D4C 0740F468 0000:00000000 <unknown>


--- Thread ID: 1505 ---
7BC80533 0689E548 0001:0006F533 C:\windows\system32\ntdll.dll
7BC8063A 0689E578 0001:0006F63A C:\windows\system32\ntdll.dll
7B872309 0689E6E8 0001:00061309 C:\windows\system32\KERNEL32.dll
7B872580 0689E728 0001:00061580 C:\windows\system32\KERNEL32.dll
7B8725DB 0689E778 0001:000615DB C:\windows\system32\KERNEL32.dll
00550C14 0689E9E4 0001:0014FC14 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
0055033E 0689E9F0 0001:0014F33E Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
004B7819 0689EA18 0001:000B6819 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
7BC78E30 0689EA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 0689EAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 0689EB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 0689F368 0001:000710F9 C:\windows\system32\ntdll.dll
B75B6D4C 0689F468 0000:00000000 <unknown>


--- Thread ID: 1591 ---
7BC80533 0679E798 0001:0006F533 C:\windows\system32\ntdll.dll
7BC8063A 0679E7C8 0001:0006F63A C:\windows\system32\ntdll.dll
7B872309 0679E938 0001:00061309 C:\windows\system32\KERNEL32.dll
7B872580 0679E978 0001:00061580 C:\windows\system32\KERNEL32.dll
7B872698 0679E9B8 0001:00061698 C:\windows\system32\KERNEL32.dll
004BB4B0 0679E9CC 0001:000BA4B0 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
00550475 0679E9E4 0001:0014F475 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
005505E1 0679E9F0 0001:0014F5E1 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
004B7819 0679EA18 0001:000B6819 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
7BC78E30 0679EA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 0679EAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 0679EB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 0679F368 0001:000710F9 C:\windows\system32\ntdll.dll
B75B6D4C 0679F468 0000:00000000 <unknown>


--- Thread ID: 1620 ---
7B87246F 0559E9B8 0001:0006146F C:\windows\system32\KERNEL32.dll
7B8724E9 0559E9E8 0001:000614E9 C:\windows\system32\KERNEL32.dll
00A90F0D 0559EA04 0001:0068FF0D Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
00A9136C 0559EA18 0001:0069036C Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
7BC78E30 0559EA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 0559EAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 0559EB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 0559F368 0001:000710F9 C:\windows\system32\ntdll.dll
B75B6D4C 0559F468 0000:00000000 <unknown>


--- Thread ID: 1174 ---
7B87246F 0549E9B8 0001:0006146F C:\windows\system32\KERNEL32.dll


--- Thread ID: 1303 ---
7BC80533 0539E768 0001:0006F533 C:\windows\system32\ntdll.dll
7BC8063A 0539E798 0001:0006F63A C:\windows\system32\ntdll.dll
7B872309 0539E908 0001:00061309 C:\windows\system32\KERNEL32.dll
7B872580 0539E948 0001:00061580 C:\windows\system32\KERNEL32.dll
7B872698 0539E988 0001:00061698 C:\windows\system32\KERNEL32.dll
B40B83B5 0539EA08 0001:000173B5 C:\windows\system32\dsound.dll
7BC78E30 0539EA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 0539EAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 0539EB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 0539F368 0001:000710F9 C:\windows\system32\ntdll.dll
B75B6D4C 0539F468 0000:00000000 <unknown>


--- Thread ID: 1515 ---
7BC80533 0519E908 0001:0006F533 C:\windows\system32\ntdll.dll
7BC8063A 0519E938 0001:0006F63A C:\windows\system32\ntdll.dll
7BC8069B 0519E968 0001:0006F69B C:\windows\system32\ntdll.dll
7BC853FF 0519EA08 0001:000743FF C:\windows\system32\ntdll.dll
7BC78E30 0519EA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 0519EAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 0519EB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 0519F368 0001:000710F9 C:\windows\system32\ntdll.dll
B75B6D4C 0519F468 0000:00000000 <unknown>


--- Thread ID: 758 ---
7BC80533 0509E908 0001:0006F533 C:\windows\system32\ntdll.dll
7BC8063A 0509E938 0001:0006F63A C:\windows\system32\ntdll.dll
7BC8069B 0509E968 0001:0006F69B C:\windows\system32\ntdll.dll
7BC853FF 0509EA08 0001:000743FF C:\windows\system32\ntdll.dll
7BC78E30 0509EA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 0509EAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 0509EB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 0509F368 0001:000710F9 C:\windows\system32\ntdll.dll
B75B6D4C 0509F468 0000:00000000 <unknown>


--- Thread ID: 1105 ---


--- Thread ID: 1556 ---
7BC80533 036DE798 0001:0006F533 C:\windows\system32\ntdll.dll
7BC8063A 036DE7C8 0001:0006F63A C:\windows\system32\ntdll.dll
7B872309 036DE938 0001:00061309 C:\windows\system32\KERNEL32.dll
7B872580 036DE978 0001:00061580 C:\windows\system32\KERNEL32.dll
7B872698 036DE9B8 0001:00061698 C:\windows\system32\KERNEL32.dll
004BB4B0 036DE9D8 0001:000BA4B0 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
00812052 036DE9F0 0001:00411052 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
004B7819 036DEA18 0001:000B6819 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
7BC78E30 036DEA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 036DEAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 036DEB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 036DF368 0001:000710F9 C:\windows\system32\ntdll.dll
B75B6D4C 036DF468 0000:00000000 <unknown>


--- Thread ID: 1589 ---
7B87246F 035DE968 0001:0006146F C:\windows\system32\KERNEL32.dll
7B8724E9 035DE998 0001:000614E9 C:\windows\system32\KERNEL32.dll
007C4814 035DE9C0 0001:003C3814 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
007E393A 035DE9D4 0001:003E293A Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
00A12A8E 035DEA0C 0001:00611A8E Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
00A12B36 035DEA18 0001:00611B36 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
7BC78E30 035DEA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 035DEAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 035DEB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 035DF368 0001:000710F9 C:\windows\system32\ntdll.dll
B75B6D4C 035DF468 0000:00000000 <unknown>


--- Thread ID: 1508 ---
7B87246F 02ABE968 0001:0006146F C:\windows\system32\KERNEL32.dll
7B872698 02ABE998 0001:00061698 C:\windows\system32\KERNEL32.dll
004BB4B0 02ABE9B0 0001:000BA4B0 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
0053FDF4 02ABE9F0 0001:0013EDF4 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
004B7819 02ABEA18 0001:000B6819 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
7BC78E30 02ABEA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 02ABEAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 02ABEB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 02ABF368 0001:000710F9 C:\windows\system32\ntdll.dll
B75B6D4C 02ABF468 0000:00000000 <unknown>


--- Thread ID: 1493 ---
7B87246F 029BE968 0001:0006146F C:\windows\system32\KERNEL32.dll
7B872698 029BE998 0001:00061698 C:\windows\system32\KERNEL32.dll
004BB4B0 029BE9B0 0001:000BA4B0 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
0053FDF4 029BE9F0 0001:0013EDF4 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
004B7819 029BEA18 0001:000B6819 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
7BC78E30 029BEA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 029BEAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 029BEB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 029BF368 0001:000710F9 C:\windows\system32\ntdll.dll
B75B6D4C 029BF468 0000:00000000 <unknown>


--- Thread ID: 1264 ---
7BC80533 019FE758 0001:0006F533 C:\windows\system32\ntdll.dll
7BC8063A 019FE788 0001:0006F63A C:\windows\system32\ntdll.dll
7B872309 019FE8F8 0001:00061309 C:\windows\system32\KERNEL32.dll
7B872580 019FE938 0001:00061580 C:\windows\system32\KERNEL32.dll
7B872698 019FE978 0001:00061698 C:\windows\system32\KERNEL32.dll
007DF69B 019FE9C0 0001:003DE69B Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
007E393A 019FE9D4 0001:003E293A Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
00A12A8E 019FEA0C 0001:00611A8E Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
00A12B36 019FEA18 0001:00611B36 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
7BC78E30 019FEA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 019FEAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 019FEB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 019FF368 0001:000710F9 C:\windows\system32\ntdll.dll
B75B6D4C 019FF468 0000:00000000 <unknown>


--- Thread ID: 1358 ---
7BC80533 018FE758 0001:0006F533 C:\windows\system32\ntdll.dll
7BC8063A 018FE788 0001:0006F63A C:\windows\system32\ntdll.dll
7B872309 018FE8F8 0001:00061309 C:\windows\system32\KERNEL32.dll
7B872580 018FE938 0001:00061580 C:\windows\system32\KERNEL32.dll
7B872698 018FE978 0001:00061698 C:\windows\system32\KERNEL32.dll
007DF17F 018FE9C0 0001:003DE17F Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
007E393A 018FE9D4 0001:003E293A Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
00A12A8E 018FEA0C 0001:00611A8E Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
00A12B36 018FEA18 0001:00611B36 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
7BC78E30 018FEA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 018FEAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 018FEB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 018FF368 0001:000710F9 C:\windows\system32\ntdll.dll
B75B6D4C 018FF468 0000:00000000 <unknown>


--- Thread ID: 1372 ---
7BC80533 016FE758 0001:0006F533 C:\windows\system32\ntdll.dll
7BC8063A 016FE788 0001:0006F63A C:\windows\system32\ntdll.dll
7B872309 016FE8F8 0001:00061309 C:\windows\system32\KERNEL32.dll
7B872580 016FE938 0001:00061580 C:\windows\system32\KERNEL32.dll
7B872698 016FE978 0001:00061698 C:\windows\system32\KERNEL32.dll
007DF69B 016FE9C0 0001:003DE69B Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
007E393A 016FE9D4 0001:003E293A Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
00A12A8E 016FEA0C 0001:00611A8E Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
00A12B36 016FEA18 0001:00611B36 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
7BC78E30 016FEA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 016FEAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 016FEB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 016FF368 0001:000710F9 C:\windows\system32\ntdll.dll
B75B6D4C 016FF468 0000:00000000 <unknown>


--- Thread ID: 1155 [Current Thread] ---
7E32AEA5 0032F3D8 0001:00019EA5 C:\windows\system32\ws2_32.dll
0054FF22 0032F42C 0001:0014EF22 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
005500DF 0032F454 0001:0014F0DF Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
00B02C9D 0032F470 0001:00701C9D Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
00626908 0032F484 0001:00225908 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
004D1C4A 0032F99C 0001:000D0C4A Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
0080035A 0032F9C4 0001:003FF35A Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
00805F16 0032F9D8 0001:00404F16 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
00420B2C 0032F9F4 0001:0001FB2C Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
00422FE7 0032FA80 0001:00021FE7 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
00420E03 0032FA9C 0001:0001FE03 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
0042CA46 0032FAB0 0001:0002BA46 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
00420153 0032FB0C 0001:0001F153 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
00420FF9 0032FB34 0001:0001FFF9 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
0042CA9D 0032FB60 0001:0002BA9D Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
0083DF39 0032FB94 0001:0043CF39 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
0083E012 0032FBB4 0001:0043D012 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
00514BF4 0032FBD4 0001:00113BF4 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
00515421 0032FBEC 0001:00114421 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
005152C4 0032FC10 0001:001142C4 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
004FFDD3 0032FC64 0001:000FEDD3 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
008A3E09 0032FC94 0001:004A2E09 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
008A30B9 0032FCD4 0001:004A20B9 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
008A343F 0032FD18 0001:004A243F Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
008A361F 0032FD40 0001:004A261F Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
008A1C7D 0032FD60 0001:004A0C7D Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
008A240A 0032FDB4 0001:004A140A Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
008A2451 0032FDCC 0001:004A1451 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
00408458 0032FE60 0001:00007458 Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe
7B85F22C 0032FE78 0001:0004E22C C:\windows\system32\KERNEL32.dll
7B8604AB 0032FEB8 0001:0004F4AB C:\windows\system32\KERNEL32.dll
7BC78E30 0032FED8 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 0032FFA8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 0032FFC8 0001:00067E0E C:\windows\system32\ntdll.dll
7BC4E0CE 0032FFE8 0001:0003D0CE C:\windows\system32\ntdll.dll


----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------


Showing 21/21 threads...


--- Thread ID: 1894 ---
B75BD9DB              <unknown symbol>+0 (015FE71C,00000000,00000000,00000000)
7BC7DE28 ntdll.dll    <unknown symbol>+0 (015FE71C,00000000,00000000,00000000)
7BC80533 ntdll.dll    <unknown symbol>+0 (00000001,015FE828,00000004,015FE928)
7BC8063A ntdll.dll    NtWaitForMultipleObjects+90 (00000001,015FE828,00000000,00000000)
7B872309 KERNEL32.dll InterlockedDecrement+321 (015FE99C,00000000,015FE978,7B872580)
7B872580 KERNEL32.dll WaitForMultipleObjectsEx+96 (015FE9B0,0669AEF4,015FE9C8,7B872698)
7B872698 KERNEL32.dll WaitForSingleObject+72 (0669AEF4,004BB4B0,000023C0,00000064)
004BB4B0 Wow.exe      <unknown symbol>+0 (00000064,05DAB748,015FEA18,004B7819)
00B05E56 Wow.exe      <unknown symbol>+0 (0669AF08,004B7780,81FFCF10,7BCBCFF4)
004B7819 Wow.exe      <unknown symbol>+0 (00D9C5F8,7BCBCFF4,015FEAF8,7BC7BE3D)
7BC78E30 ntdll.dll    call_thread_func_wrapper+12 (004B7780,05DAB748,00000000,00000000)
7BC7BE3D ntdll.dll    call_thread_func+125 (004B7780,05DAB748,015FEB18,004B7780)
7BC78E0E ntdll.dll    RtlRaiseException+34 (004B7780,05DAB748,00000000,00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (81FFCFB8,015FFB40,015FFB40,015FFB40)
B75B6D4C              start_thread+204 (015FFB40,00000000,00000000,00000000)


--- Thread ID: 1175 ---
B75BD9DB              <unknown symbol>+0 (07F9E2FC,00000000,00000000,00000000)
7BC7DE28 ntdll.dll    <unknown symbol>+0 (07F9E2FC,00000000,00000000,00000000)
7BC80533 ntdll.dll    <unknown symbol>+0 (00000001,07F9E400,00000004,00000000)
7BC8063A ntdll.dll    NtWaitForMultipleObjects+90 (00000001,07F9E400,00000000,00000000)
7BC8069B ntdll.dll    NtWaitForSingleObject+75 (00000000,07F9E4BC,07F9E508,7BC667EF)
7BC667EF ntdll.dll    NtNotifyChangeKey+399 (00000000,07F9E568,7EAA7BA1,7EAC12E9)
7EAC12E9 advapi32.dll RegNotifyChangeKeyValue+185 (81FA0C00,00000000,B4084CB5,B408786B)
B408786B mmdevapi.dll <unknown symbol>+0 (00000000,00000000,00000000,7BC78E30)
7BC78E30 ntdll.dll    call_thread_func_wrapper+12 (B4087510,00000000,00000000,00000000)
7BC7BE3D ntdll.dll    call_thread_func+125 (B4087510,00000000,07F9EB18,B4087510)
7BC78E0E ntdll.dll    RtlRaiseException+34 (B4087510,00000000,00000000,00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (81FA0FB8,07F9FB40,07F9FB40,07F9FB40)
B75B6D4C              start_thread+204 (07F9FB40,00000000,00000000,00000000)


--- Thread ID: 1564 ---
B75BD9DB              <unknown symbol>+0 (0529E71C,00000000,0529E688,7BC4E84F)
7BC7DE28 ntdll.dll    <unknown symbol>+0 (0529E71C,00000000,0529E688,7BC4E84F)
7BC80533 ntdll.dll    <unknown symbol>+0 (00000001,0529E828,00000004,00000000)
7BC8063A ntdll.dll    NtWaitForMultipleObjects+90 (00000001,0529E828,00000000,00000000)
7B872309 KERNEL32.dll InterlockedDecrement+321 (00000000,00000000,00000000,7B872580)
7B872580 KERNEL32.dll WaitForMultipleObjectsEx+96 (0529E9B0,00716558,00000001,7B872698)
7B872698 KERNEL32.dll WaitForSingleObject+72 (0529E9E4,05B54030,0529E9F4,00AD4965)
00AD4965 Wow.exe      <unknown symbol>+0 (05B54030,FFFFFFFF,0529EA18,00A91330)
00A910A9 Wow.exe      <unknown symbol>+0 (05B54030,81FCCF10,0000061C,0529EA28)
00A91330 Wow.exe      <unknown symbol>+0 (06364C24,7BCBCFF4,0529EAF8,7BC7BE3D)
7BC78E30 ntdll.dll    call_thread_func_wrapper+12 (00A912F0,06364C24,00000000,00000000)
7BC7BE3D ntdll.dll    call_thread_func+125 (00A912F0,06364C24,0529EB18,00A912F0)
7BC78E0E ntdll.dll    RtlRaiseException+34 (00A912F0,06364C24,00000000,00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (81FCCFB8,0529FB40,0529FB40,0529FB40)
B75B6D4C              start_thread+204 (0529FB40,00000000,00000000,00000000)


--- Thread ID: 1525 ---
B75BD9DB              <unknown symbol>+0 (07C9E71C,00411BB0,1C3B3B04,7BC376ED)
7BC7DE28 ntdll.dll    <unknown symbol>+0 (07C9E71C,00411BB0,1C3B3B04,7BC376ED)
7BC80533 ntdll.dll    <unknown symbol>+0 (00000001,07C9E828,00000004,00000000)
7BC8063A ntdll.dll    NtWaitForMultipleObjects+90 (00000001,07C9E828,00000000,00000000)
7B872309 KERNEL32.dll InterlockedDecrement+321 (00000000,00000000,00000000,7B872580)
7B872580 KERNEL32.dll WaitForMultipleObjectsEx+96 (06364D78,06363AE8,FFFFD8F0,7B872698)
7B872698 KERNEL32.dll WaitForSingleObject+72 (07C9E9E4,06363C88,07C9E9F4,00AD4965)
00AD4965 Wow.exe      <unknown symbol>+0 (06363C88,FFFFFFFF,07C9EA18,00A91330)
00A910A9 Wow.exe      <unknown symbol>+0 (06363C88,81FACF10,000005F5,07C9EA28)
00A91330 Wow.exe      <unknown symbol>+0 (06363AF4,7BCBCFF4,07C9EAF8,7BC7BE3D)
7BC78E30 ntdll.dll    call_thread_func_wrapper+12 (00A912F0,06363AF4,00000000,00000000)
7BC7BE3D ntdll.dll    call_thread_func+125 (00A912F0,06363AF4,07C9EB18,00A912F0)
7BC78E0E ntdll.dll    RtlRaiseException+34 (00A912F0,06363AF4,00000000,00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (81FACFB8,07C9FB40,07C9FB40,07C9FB40)
B75B6D4C              start_thread+204 (07C9FB40,00000000,00000000,00000000)


--- Thread ID: 1376 ---
B75BD9DB              <unknown symbol>+0 (0740E71C,00000000,00000000,00000000)
7BC7DE28 ntdll.dll    <unknown symbol>+0 (0740E71C,00000000,00000000,00000000)
7BC80533 ntdll.dll    <unknown symbol>+0 (00000001,0740E828,00000004,00000000)
7BC8063A ntdll.dll    NtWaitForMultipleObjects+90 (00000001,0740E828,00000000,00000000)
7B872309 KERNEL32.dll InterlockedDecrement+321 (00000000,05A7F770,00000000,7B872580)
7B872580 KERNEL32.dll WaitForMultipleObjectsEx+96 (05A7F770,00000560,0740E9F0,7B872698)
7B872698 KERNEL32.dll WaitForSingleObject+72 (025E35A8,0740E9E4,004BB4B0,00000098)
004BB4B0 Wow.exe      <unknown symbol>+0 (FFFFFFFF,00002374,004B7819,00000000)
007023DB Wow.exe      <unknown symbol>+0 (00D9C5D8,7BCBCFF4,0740EAF8,7BC7BE3D)
7BC78E30 ntdll.dll    call_thread_func_wrapper+12 (004B7780,05A7F770,00000000,00000000)
7BC7BE3D ntdll.dll    call_thread_func+125 (004B7780,05A7F770,0740EB18,004B7780)
7BC78E0E ntdll.dll    RtlRaiseException+34 (004B7780,05A7F770,00000000,00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (81FB4FB8,0740FB40,0740FB40,0740FB40)
B75B6D4C              start_thread+204 (0740FB40,00000000,00000000,00000000)


--- Thread ID: 1505 ---
B75BD9DB              <unknown symbol>+0 (0689E4BC,00000000,00000000,00000000)
7BC7DE28 ntdll.dll    <unknown symbol>+0 (0689E4BC,00000000,00000000,00000000)
7BC80533 ntdll.dll    <unknown symbol>+0 (00000002,0689E5C8,00000004,0689E6C8)
7BC8063A ntdll.dll    NtWaitForMultipleObjects+90 (00000002,0689E5C8,00000000,00000000)
7B872309 KERNEL32.dll InterlockedDecrement+321 (00000000,00000000,00000000,7B872580)
7B872580 KERNEL32.dll WaitForMultipleObjectsEx+96 (00000000,00000000,00000000,7B8725DB)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)
7B8725DB KERNEL32.dll WaitForMultipleObjects+75 (F21BC000,F21BC000,F21BC000,F21BC000)


--- Thread ID: 1591 ---
B75BD9DB              <unknown symbol>+0 (0679E70C,0679E5B4,0679E5A8,7BC7BC77)
7BC7DE28 ntdll.dll    <unknown symbol>+0 (0679E70C,0679E5B4,0679E5A8,7BC7BC77)
7BC80533 ntdll.dll    <unknown symbol>+0 (00000001,0679E818,00000004,0679E918)
7BC8063A ntdll.dll    NtWaitForMultipleObjects+90 (00000001,0679E818,00000000,00000000)
7B872309 KERNEL32.dll InterlockedDecrement+321 (00003139,0A6AE1EA,00D9C598,7B872580)
7B872580 KERNEL32.dll WaitForMultipleObjectsEx+96 (0679E998,0679E99C,0679E9D0,7B872698)
7B872698 KERNEL32.dll WaitForSingleObject+72 (004BB4B0,000022E0,000003E8,0679E9E4)
004BB4B0 Wow.exe      <unknown symbol>+0 (000003E8,00000637,025EAA38,0000236C)
00550475 Wow.exe      <unknown symbol>+0 (00000000,0679EA18,004B7819,04E978A0)
005505E1 Wow.exe      <unknown symbol>+0 (04E978A0,004B7780,81FBCF10,7BCBCFF4)
004B7819 Wow.exe      <unknown symbol>+0 (00D9C598,7BCBCFF4,0679EAF8,7BC7BE3D)
7BC78E30 ntdll.dll    call_thread_func_wrapper+12 (004B7780,025EAA38,00000000,00000000)
7BC7BE3D ntdll.dll    call_thread_func+125 (004B7780,025EAA38,0679EB18,004B7780)
7BC78E0E ntdll.dll    RtlRaiseException+34 (004B7780,025EAA38,00000000,00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (81FBCFB8,0679FB40,0679FB40,0679FB40)
B75B6D4C              start_thread+204 (0679FB40,00000000,00000000,00000000)


--- Thread ID: 1620 ---
B74EDE01              select+97 (0559E998,0559E9BC,7B826019,7B87246F)
7BC809FC ntdll.dll    NtDelayExecution+300 (0559E998,0559E9BC,7B826019,7B87246F)
7B87246F KERNEL32.dll SleepEx+63 (00000000,57353B46,00000002,7B8724E9)
7B8724E9 KERNEL32.dll Sleep+57 (3F733333,00A912F0,0559EA04,00A90F0D)
00A90F0D Wow.exe      <unknown symbol>+0 (0000000A,81FC0F10,00000654,0559EA28)
00A9136C Wow.exe      <unknown symbol>+0 (0472E6A8,7BCBCFF4,0559EAF8,7BC7BE3D)
7BC78E30 ntdll.dll    call_thread_func_wrapper+12 (00A912F0,0472E6A8,00000000,00000000)
7BC7BE3D ntdll.dll    call_thread_func+125 (00A912F0,0472E6A8,0559EB18,00A912F0)
7BC78E0E ntdll.dll    RtlRaiseException+34 (00A912F0,0472E6A8,00000000,00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (81FC0FB8,0559FB40,0559FB40,0559FB40)
B75B6D4C              start_thread+204 (0559FB40,00000000,00000000,00000000)


--- Thread ID: 1174 ---
B74EDE01              select+97 (04727068,00000000,7B826019,7B87246F)
7BC809FC ntdll.dll    NtDelayExecution+300 (04727068,00000000,7B826019,7B87246F)
7B87246F KERNEL32.dll SleepEx+63 (4148D2BF,48451EBE,0549EA08,7B8724E9)
7B8724E9 KERNEL32.dll Sleep+57 (00164598,00000002,0549EA04,00A90F0D)
7B8724E9 KERNEL32.dll Sleep+57 (0000000A,81FC4F10,00000496,0549EA28)
00B85208 Wow.exe      <unknown symbol>+0 (04730480,7BCBCFF4,0549EAF8,7BC7BE3D)
7BC78E30 ntdll.dll    call_thread_func_wrapper+12 (00A912F0,04730480,00000000,00000000)
7BC7BE3D ntdll.dll    call_thread_func+125 (00A912F0,04730480,0549EB18,00A912F0)
7BC78E0E ntdll.dll    RtlRaiseException+34 (00A912F0,04730480,00000000,00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (81FC4FB8,0549FB40,0549FB40,0549FB40)
B75B6D4C              start_thread+204 (0549FB40,00000000,00000000,00000000)


--- Thread ID: 1303 ---
B75BD9DB              <unknown symbol>+0 (0539E6DC,00000000,00000000,00000000)
7BC7DE28 ntdll.dll    <unknown symbol>+0 (0539E6DC,00000000,00000000,00000000)
7BC80533 ntdll.dll    <unknown symbol>+0 (00000001,0539E7E8,00000004,0539E8E8)
7BC8063A ntdll.dll    NtWaitForMultipleObjects+90 (00000001,0539E7E8,00000000,00000000)
7B872309 KERNEL32.dll InterlockedDecrement+321 (000029B0,00000000,00157170,7B872580)
7B872580 KERNEL32.dll WaitForMultipleObjectsEx+96 (B3F3E5E4,AF6BF028,000029B0,7B872698)
7B872698 KERNEL32.dll WaitForSingleObject+72 (001570C8,00157174,B40A7531,B40B83B5)
B40B83B5 dsound.dll   <unknown symbol>+0 (00000000,00000000,00000000,7BC78E30)
7BC78E30 ntdll.dll    call_thread_func_wrapper+12 (B40B8140,001570C8,00000000,00000000)
7BC7BE3D ntdll.dll    call_thread_func+125 (B40B8140,001570C8,0539EB18,B40B8140)
7BC78E0E ntdll.dll    RtlRaiseException+34 (B40B8140,001570C8,00000000,00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (81FC8FB8,0539FB40,0539FB40,0539FB40)
B75B6D4C              start_thread+204 (0539FB40,00000000,00000000,00000000)


--- Thread ID: 1515 ---
B75BD9DB              <unknown symbol>+0 (0519E87C,00000000,00000000,00000000)
7BC7DE28 ntdll.dll    <unknown symbol>+0 (0519E87C,00000000,00000000,00000000)
7BC80533 ntdll.dll    <unknown symbol>+0 (00000001,0519E980,00000004,00000000)
7BC8063A ntdll.dll    NtWaitForMultipleObjects+90 (00000001,0519E980,00000000,00000000)
7BC8069B ntdll.dll    NtWaitForSingleObject+75 (00352AFC,0519E978,0519E998,7BC853FF)
7BC853FF ntdll.dll    <unknown symbol>+0 (00000000,00000000,00000000,7BC78E30)
7BC78E30 ntdll.dll    call_thread_func_wrapper+12 (7BC853B0,00156A58,00000000,00000000)
7BC7BE3D ntdll.dll    call_thread_func+125 (7BC853B0,00156A58,0519EB18,7BC853B0)
7BC78E0E ntdll.dll    RtlRaiseException+34 (7BC853B0,00156A58,00000000,00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (81FD0FB8,0519FB40,0519FB40,0519FB40)
B75B6D4C              start_thread+204 (0519FB40,00000000,00000000,00000000)


--- Thread ID: 758 ---
B75BD9DB              <unknown symbol>+0 (0509E87C,00000000,00000000,00000000)
7BC7DE28 ntdll.dll    <unknown symbol>+0 (0509E87C,00000000,00000000,00000000)
7BC80533 ntdll.dll    <unknown symbol>+0 (00000001,0509E980,00000004,00000000)
7BC8063A ntdll.dll    NtWaitForMultipleObjects+90 (00000001,0509E980,00000000,00000000)
7BC8069B ntdll.dll    NtWaitForSingleObject+75 (00352AFC,0509E978,0509E998,7BC853FF)
7BC853FF ntdll.dll    <unknown symbol>+0 (00000000,00000000,00000000,7BC78E30)
7BC78E30 ntdll.dll    call_thread_func_wrapper+12 (7BC853B0,00156918,0509EA98,7BC3741C)
7BC7BE3D ntdll.dll    call_thread_func+125 (7BC853B0,00156918,0509EB18,7BC853B0)
7BC78E0E ntdll.dll    RtlRaiseException+34 (7BC853B0,00156918,00000000,00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (81FD4FB8,0509FB40,0509FB40,0509FB40)
B75B6D4C              start_thread+204 (0509FB40,00000000,00000000,00000000)


--- Thread ID: 1105 ---
B74E6690              poll+128 (B3600558,00000002,00000525,00000000)
B3F2C521 winepulse.drv <unknown symbol>+0 (B3600558,00000002,00000525,00000000)
B3EEC75A              pa_mainloop_poll+202 (F21BC000,F21BC000,F21BC000,F21BC000)
B3EECFB7              pa_mainloop_iterate+71 (00000000,00000000,00000000,7BC78E30)
B3EED094              pa_mainloop_run+52 (00000000,00000000,00000000,7BC78E30)
B3F2C49A winepulse.drv <unknown symbol>+0 (00000000,00000000,00000000,7BC78E30)
7BC78E30 ntdll.dll    call_thread_func_wrapper+12 (B3F2C420,00000000,00000000,00000000)
7BC7BE3D ntdll.dll    call_thread_func+125 (B3F2C420,00000000,04F9EB18,B3F2C420)
7BC78E0E ntdll.dll    RtlRaiseException+34 (B3F2C420,00000000,00000000,00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (81FD8FB8,04F9FB40,04F9FB40,04F9FB40)
B75B6D4C              start_thread+204 (04F9FB40,00000000,00000000,00000000)


--- Thread ID: 1556 ---
B75BD9DB              <unknown symbol>+0 (036DE70C,036DE75C,036DE7A8,7BC80533)
7BC7DE28 ntdll.dll    <unknown symbol>+0 (036DE70C,036DE75C,036DE7A8,7BC80533)
7BC80533 ntdll.dll    <unknown symbol>+0 (00000001,036DE818,00000004,00000000)
7BC8063A ntdll.dll    NtWaitForMultipleObjects+90 (00000001,036DE818,00000000,00000000)
7B872309 KERNEL32.dll InterlockedDecrement+321 (00000000,00000000,00000000,7B872580)
7B872580 KERNEL32.dll WaitForMultipleObjectsEx+96 (00EBC4D0,00EBD4E0,036DE9C8,7B872698)
7B872698 KERNEL32.dll WaitForSingleObject+72 (036DE9DC,00EBC4D0,036DE9F0,004BB4B0)
004BB4B0 Wow.exe      <unknown symbol>+0 (FFFFFFFF,00002290,00000614,025EA8A0)
00812052 Wow.exe      <unknown symbol>+0 (00EBC4D0,004B7780,81FDCF10,7BCBCFF4)
004B7819 Wow.exe      <unknown symbol>+0 (00D9C578,7BCBCFF4,036DEAF8,7BC7BE3D)
7BC78E30 ntdll.dll    call_thread_func_wrapper+12 (004B7780,025EA8A0,00000000,00000000)
7BC7BE3D ntdll.dll    call_thread_func+125 (004B7780,025EA8A0,036DEB18,004B7780)
7BC78E0E ntdll.dll    RtlRaiseException+34 (004B7780,025EA8A0,00000000,00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (81FDCFB8,036DFB40,036DFB40,036DFB40)
B75B6D4C              start_thread+204 (036DFB40,00000000,00000000,00000000)


--- Thread ID: 1589 ---
B74EDE01              select+97 (00000004,035DE950,7B826019,7B87246F)
7BC809FC ntdll.dll    NtDelayExecution+300 (00000004,035DE950,7B826019,7B87246F)
7B87246F KERNEL32.dll SleepEx+63 (00C03E6B,7B8724B0,035DE998,7B8724E9)
7B8724E9 KERNEL32.dll Sleep+57 (035DE9C0,007C4814,00000064,00A12AB4)
007C4814 Wow.exe      <unknown symbol>+0 (00000000,00A12AB4,02731330,035DEA0C)
007E393A Wow.exe      <unknown symbol>+0 (0272EBA8,1FAE2628,00A12AB4,02731330)
00A12A8E Wow.exe      <unknown symbol>+0 (81FE0F10,035DEA28,7BC78E30,02731330)
00A12B36 Wow.exe      <unknown symbol>+0 (02731330,7BCBCFF4,035DEAF8,7BC7BE3D)
7BC78E30 ntdll.dll    call_thread_func_wrapper+12 (00A12AB4,02731330,00000000,00000000)
7BC7BE3D ntdll.dll    call_thread_func+125 (00A12AB4,02731330,035DEB18,00A12AB4)
7BC78E0E ntdll.dll    RtlRaiseException+34 (00A12AB4,02731330,00000000,00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (81FE0FB8,035DFB40,035DFB40,035DFB40)
B75B6D4C              start_thread+204 (035DFB40,00000000,00000000,00000000)


--- Thread ID: 1508 ---
B74EDE01              select+97 (00000000,00000000,7B826019,7B87246F)
7BC809FC ntdll.dll    NtDelayExecution+300 (00000000,00000000,7B826019,7B87246F)
7B87246F KERNEL32.dll SleepEx+63 (00000001,02ABE9A8,00000000,7B8724E9)
7B8724E9 KERNEL32.dll Sleep+57 (02ABE9B4,02ABE9B0,008755DD,00000001)
008755DD Wow.exe      <unknown symbol>+0 (00000001,025E51C8,00002284,000005E4)
0053FDF4 Wow.exe      <unknown symbol>+0 (025E5148,004B7780,81FE4F10,7BCBCFF4)
004B7819 Wow.exe      <unknown symbol>+0 (00D9C558,7BCBCFF4,02ABEAF8,7BC7BE3D)
7BC78E30 ntdll.dll    call_thread_func_wrapper+12 (004B7780,025E51C8,00000000,00000000)
7BC7BE3D ntdll.dll    call_thread_func+125 (004B7780,025E51C8,02ABEB18,004B7780)
7BC78E0E ntdll.dll    RtlRaiseException+34 (004B7780,025E51C8,00000000,00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (81FE4FB8,02ABFB40,02ABFB40,02ABFB40)
B75B6D4C              start_thread+204 (02ABFB40,00000000,00000000,00000000)


--- Thread ID: 1493 ---
B74EDE01              select+97 (00000000,00000000,7B826019,7B87246F)
7BC809FC ntdll.dll    NtDelayExecution+300 (00000000,00000000,7B826019,7B87246F)
7B87246F KERNEL32.dll SleepEx+63 (00000001,029BE9A8,00000000,7B8724E9)
7B8724E9 KERNEL32.dll Sleep+57 (029BE9B4,029BE9B0,008755DD,00000001)
008755DD Wow.exe      <unknown symbol>+0 (00000001,025E5130,00002280,000005D5)
0053FDF4 Wow.exe      <unknown symbol>+0 (025E50B0,004B7780,81FE8F10,7BCBCFF4)
004B7819 Wow.exe      <unknown symbol>+0 (00D9C538,7BCBCFF4,029BEAF8,7BC7BE3D)
7BC78E30 ntdll.dll    call_thread_func_wrapper+12 (004B7780,025E5130,00000000,00000000)
7BC7BE3D ntdll.dll    call_thread_func+125 (004B7780,025E5130,029BEB18,004B7780)
7BC78E0E ntdll.dll    RtlRaiseException+34 (004B7780,025E5130,00000000,00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (81FE8FB8,029BFB40,029BFB40,029BFB40)
B75B6D4C              start_thread+204 (029BFB40,00000000,00000000,00000000)


--- Thread ID: 1264 ---
B75BD9DB              <unknown symbol>+0 (019FE6CC,019FE560,00000000,08455355)
7BC7DE28 ntdll.dll    <unknown symbol>+0 (019FE6CC,019FE560,00000000,08455355)
7BC80533 ntdll.dll    <unknown symbol>+0 (00000001,019FE7D8,00000004,00000000)
7BC8063A ntdll.dll    NtWaitForMultipleObjects+90 (00000001,019FE7D8,00000000,00000000)
7B872309 KERNEL32.dll InterlockedDecrement+321 (00000000,00000000,00000000,7B872580)
7B872580 KERNEL32.dll WaitForMultipleObjectsEx+96 (1D6C2548,00000000,063E3238,7B872698)
7B872698 KERNEL32.dll WaitForSingleObject+72 (019FE994,012A5798,019FE9C0,007DF69B)
007DF69B Wow.exe      <unknown symbol>+0 (01233038,00A12AB4,01232E18,019FEA0C)
007E393A Wow.exe      <unknown symbol>+0 (01232DB0,1D6C2628,00A12AB4,01232E18)
00A12A8E Wow.exe      <unknown symbol>+0 (81FECF10,019FEA28,7BC78E30,01232E18)
00A12B36 Wow.exe      <unknown symbol>+0 (01232E18,7BCBCFF4,019FEAF8,7BC7BE3D)
7BC78E30 ntdll.dll    call_thread_func_wrapper+12 (00A12AB4,01232E18,00000000,00000000)
7BC7BE3D ntdll.dll    call_thread_func+125 (00A12AB4,01232E18,019FEB18,00A12AB4)
7BC78E0E ntdll.dll    RtlRaiseException+34 (00A12AB4,01232E18,00000000,00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (81FECFB8,019FFB40,019FFB40,019FFB40)
B75B6D4C              start_thread+204 (019FFB40,00000000,00000000,00000000)


--- Thread ID: 1358 ---
B75BD9DB              <unknown symbol>+0 (018FE6CC,00000000,00000000,00000000)
7BC7DE28 ntdll.dll    <unknown symbol>+0 (018FE6CC,00000000,00000000,00000000)
7BC80533 ntdll.dll    <unknown symbol>+0 (00000001,018FE7D8,00000004,00000000)
7BC8063A ntdll.dll    NtWaitForMultipleObjects+90 (00000001,018FE7D8,00000000,00000000)
7B872309 KERNEL32.dll InterlockedDecrement+321 (FFFFFFFF,018FE99C,00000000,7B872580)
7B872580 KERNEL32.dll WaitForMultipleObjectsEx+96 (00000000,00A12AB4,018FE970,7B872698)
7B872698 KERNEL32.dll WaitForSingleObject+72 (018FE990,007E1BD6,00EBA788,007DF17F)
007DF17F Wow.exe      <unknown symbol>+0 (00000000,00A12AB4,01232B90,018FEA0C)
007E393A Wow.exe      <unknown symbol>+0 (01204810,1D7C2628,00A12AB4,01232B90)
00A12A8E Wow.exe      <unknown symbol>+0 (81FF0F10,018FEA28,7BC78E30,01232B90)
00A12B36 Wow.exe      <unknown symbol>+0 (01232B90,7BCBCFF4,018FEAF8,7BC7BE3D)
7BC78E30 ntdll.dll    call_thread_func_wrapper+12 (00A12AB4,01232B90,00000000,00000000)
7BC7BE3D ntdll.dll    call_thread_func+125 (00A12AB4,01232B90,018FEB18,00A12AB4)
7BC78E0E ntdll.dll    RtlRaiseException+34 (00A12AB4,01232B90,00000000,00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (81FF0FB8,018FFB40,018FFB40,018FFB40)
B75B6D4C              start_thread+204 (018FFB40,00000000,00000000,00000000)


--- Thread ID: 1372 ---
B75BD9DB              <unknown symbol>+0 (016FE6CC,016FE560,00000000,0A0D3D68)
7BC7DE28 ntdll.dll    <unknown symbol>+0 (016FE6CC,016FE560,00000000,0A0D3D68)
7BC80533 ntdll.dll    <unknown symbol>+0 (00000001,016FE7D8,00000004,00000000)
7BC8063A ntdll.dll    NtWaitForMultipleObjects+90 (00000001,016FE7D8,00000000,00000000)
7B872309 KERNEL32.dll InterlockedDecrement+321 (00000000,00000000,00000000,7B872580)
7B872580 KERNEL32.dll WaitForMultipleObjectsEx+96 (1D9C2548,00000000,01204CE8,7B872698)
7B872698 KERNEL32.dll WaitForSingleObject+72 (016FE994,01205140,016FE9C0,007DF69B)
007DF69B Wow.exe      <unknown symbol>+0 (01205650,00A12AB4,012051F8,016FEA0C)
007E393A Wow.exe      <unknown symbol>+0 (01205170,1D9C2628,00A12AB4,012051F8)
00A12A8E Wow.exe      <unknown symbol>+0 (81FF8F10,016FEA28,7BC78E30,012051F8)
00A12B36 Wow.exe      <unknown symbol>+0 (012051F8,7BCBCFF4,016FEAF8,7BC7BE3D)
7BC78E30 ntdll.dll    call_thread_func_wrapper+12 (00A12AB4,012051F8,00000000,00000000)
7BC7BE3D ntdll.dll    call_thread_func+125 (00A12AB4,012051F8,016FEB18,00A12AB4)
7BC78E0E ntdll.dll    RtlRaiseException+34 (00A12AB4,012051F8,00000000,00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (81FF8FB8,016FFB40,016FFB40,016FFB40)
B75B6D4C              start_thread+204 (016FFB40,00000000,00000000,00000000)


--- Thread ID: 1155 [Current Thread] ---
7E32AEA5 ws2_32.dll   WS_connect+5 (0000240C,0032F414,00000010,0669B5D0)
00550D74 Wow.exe      <unknown symbol>+0 (0000240C,0032F414,00000010,0669B5D0)
0054FF22 Wow.exe      <unknown symbol>+0 (011F2D98,0669AEB0,00000000,0A0D2759)
005500DF Wow.exe      <unknown symbol>+0 (011F2D98,00000E8C,00001388,00EBB9B8)
00B02C9D Wow.exe      <unknown symbol>+0 (011F2D98,00B88CC3,00000090,0032F99C)
00626908 Wow.exe      <unknown symbol>+0 (011F2D98,00B88CC3,06167DF4,06167DDD)
004D1C4A Wow.exe      <unknown symbol>+0 (00EBB9B8,06167DF4,00000003,00B874A4)
0080035A Wow.exe      <unknown symbol>+0 (06167DD4,06167DF4,04723AE8,0032F9F4)
00805F16 Wow.exe      <unknown symbol>+0 (04723AE8,00805ED0,00000000,063B4028)
00420B2C Wow.exe      <unknown symbol>+0 (00000090,063B4028,00000000,00000000)
00422FE7 Wow.exe      <unknown symbol>+0 (05AB0CC4,00000002,04723AE8,00110000)
00420E03 Wow.exe      <unknown symbol>+0 (04723AE8,063B3FD8,00000000,0032FB0C)
0042CA46 Wow.exe      <unknown symbol>+0 (04723AE8,0032FB58,04723AE8,00000000)
00420153 Wow.exe      <unknown symbol>+0 (04723AE8,0042CA30,0032FB58,00000000)
00420FF9 Wow.exe      <unknown symbol>+0 (01723AE8,0042CA30,0032FB58,00000040)
0042CA9D Wow.exe      <unknown symbol>+0 (04723AE8,00000003,00000000,FFFFFFFB)
0083DF39 Wow.exe      <unknown symbol>+0 (000004A0,05D37BD4,00000003,00000000)
0083E012 Wow.exe      <unknown symbol>+0 (05D37E09,00000002,00000000,00000000)
00514BF4 Wow.exe      <unknown symbol>+0 (00BA4328,00000000,00C03EBF,05D37BD4)
00515421 Wow.exe      <unknown symbol>+0 (00BA4328,00000000,0032FCB0,05AAA590)
005152C4 Wow.exe      <unknown symbol>+0 (0032FC2C,00000000,025E3330,025E3444)
004FFDD3 Wow.exe      <unknown symbol>+0 (0032FCB0,00000000,0032FD5C,0032FD2C)
008A3E09 Wow.exe      <unknown symbol>+0 (025E3330,0000000E,0032FCB0,0032FCC4)
008A30B9 Wow.exe      <unknown symbol>+0 (025E3330,0000026C,000002C2,00000000)
008A343F Wow.exe      <unknown symbol>+0 (025E3330,00C03EBE,00000102,00000001)
008A361F Wow.exe      <unknown symbol>+0 (0000000D,0032FD5C,FFFFFFFE,00000000)
008A1C7D Wow.exe      <unknown symbol>+0 (00000000,3C83126F,00000000,69676E45)
008A240A Wow.exe      <unknown symbol>+0 (00000000,004083FF,00000001,00000001)
008A2451 Wow.exe      <unknown symbol>+0 (0040E4D5,00400000,00000000,00143EFA)
00408458 Wow.exe      <unknown symbol>+0 (7FFDF000,7BC503DA,7B8B4FF4,7FFDF000)
7B85F22C KERNEL32.dll call_process_entry+12 (7FFDF000,00401190,00000000,00000000)
7B8604AB KERNEL32.dll <unknown symbol>+0 (00000000,00000000,00000000,7BC78E30)
7BC78E30 ntdll.dll    call_thread_func_wrapper+12 (7B860440,7FFDF000,00000000,00000000)
7BC7BE3D ntdll.dll    call_thread_func+125 (7B860440,7FFDF000,0032FFC8,00110A58)
7BC78E0E ntdll.dll    RtlRaiseException+34 (7B860440,7FFDF000,00000000,00000000)
7BC4E0CE ntdll.dll    call_dll_entry_point+830 (7B860440,00000000,00000000,00000000)
B75EF66D              wine_call_on_stack+29 (F21BC000,F21BC000,F21BC000,F21BC000)
B75EF72B              wine_switch_to_stack+43 (7BC4E0B0,7B860440,00330000,BFDFED7C)
7BC53F30 ntdll.dll    LdrInitializeThunk+944 (BFDFF612,00110878,7B825EF9,7B866A82)
7B866A82 KERNEL32.dll __wine_kernel_init+2594 (7BCBCFF4,BFDFFFA0,BFDFFFD8,7BC546EB)
7BC546EB ntdll.dll    <unknown symbol>+0 (7D2F12A8,B777AEBD,BFE0007C,00000400)
B75ECBCC              wine_init+732 (00000002,BFE00534,BFE0007C,00000400)
7BF00D0B              main+139 (00000002,BFE00534,BFE00540,B779D920)
B741F4D3              __libc_start_main+243 (F21BC000,F21BC000,F21BC000,F21BC000)






----------------------------------------
    Loaded Modules
----------------------------------------


DBG-MODULE<00350000 0000C000 "freakz.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 708992537>
DBG-MODULE<00400000 00CDD000 "Wow.exe" "Wow.pdb" 0 {9a9fe68a-1174-4bdf-b51a0cab2be97eae} 1 1334105658>
DBG-MODULE<7B810000 0024B000 "KERNEL32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7BC10000 000C9000 "ntdll.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7DB70000 0002E000 "uxtheme.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7DDA0000 00088000 "winex11.drv" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7DFE0000 00021000 "msacm32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E010000 000AB000 "winmm.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E0D0000 0005B000 "setupapi.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E140000 0006C000 "rpcrt4.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E1C0000 00128000 "ole32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E2F0000 00014000 "dinput8.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E310000 0002A000 "ws2_32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E340000 00102000 "comctl32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E450000 00225000 "shell32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E680000 0006F000 "shlwapi.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E700000 00016000 "mpr.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E740000 00007000 "hid.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E750000 00072000 "wininet.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E7D0000 00016000 "imm32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E7F0000 00137000 "wined3d.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E930000 00034000 "d3d9.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E980000 000F2000 "opengl32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7EA80000 0000C000 "version.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7EAA0000 0005B000 "advapi32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7EB10000 00109000 "gdi32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7EC30000 00144000 "user32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<AF570000 0008F000 "msvcrt.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<B3750000 00065000 "dbghelp.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<B3F20000 0001F000 "winepulse.drv" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<B3F50000 00123000 "oleaut32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<B4080000 00015000 "mmdevapi.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<B40A0000 0003D000 "dsound.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<B73B0000 0000E000 "psapi.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<B73C0000 00024000 "iphlpapi.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<B73F0000 00010000 "wsock32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>


----------------------------------------
    Memory Dump
----------------------------------------


Code: 16 bytes starting at (EIP = 7E32AEA5)


7E32AEA5: E4 F0 FF 71  FC 55 89 E5  57 56 53 51  E8 41 C7 FE  ...q.U..WVSQ.A..




Stack: 1024 bytes starting at (ESP = 0032F3C0)


* = addr  **                                                  *               
0032F3C0: D4 F3 32 00  90 78 E9 04  DC F3 32 00  74 0D 55 00  ..2..x....2.t.U.
0032F3D0: 74 0D 55 00  10 00 00 00  2C F4 32 00  22 FF 54 00  t.U.....,.2.".T.
0032F3E0: 0C 24 00 00  14 F4 32 00  10 00 00 00  D0 B5 69 06  .$....2.......i.
0032F3F0: 50 B6 69 06  98 2D 1F 01  00 00 00 00  00 00 00 00  P.i..-..........
0032F400: 28 F4 32 00  0F 9D 87 00  99 2D 1F 01  18 F4 32 00  (.2......-....2.
0032F410: D0 B5 69 06  02 00 0E 8C  59 27 0D 0A  00 00 00 00  ..i.....Y'......
0032F420: 00 00 00 00  01 00 00 00  C8 39 14 00  54 F4 32 00  .........9..T.2.
0032F430: DF 00 55 00  98 2D 1F 01  B0 AE 69 06  00 00 00 00  ..U..-....i.....
0032F440: 59 27 0D 0A  00 00 00 00  00 00 00 00  00 00 00 00  Y'..............
0032F450: 01 00 00 00  70 F4 32 00  9D 2C B0 00  98 2D 1F 01  ....p.2..,...-..
0032F460: 8C 0E 00 00  88 13 00 00  B8 B9 EB 00  28 99 69 06  ............(.i.
0032F470: 84 F4 32 00  08 69 62 00  98 2D 1F 01  C3 8C B8 00  ..2..ib..-......
0032F480: 90 00 00 00  9C F9 32 00  4A 1C 4D 00  98 2D 1F 01  ......2.J.M..-..
0032F490: C3 8C B8 00  F4 7D 16 06  DD 7D 16 06  41 53 44 41  .....}...}..ASDA
0032F4A0: 53 44 41 53  44 00 40 41  00 00 A8 41  00 00 98 41  SDASD.@A...A...A
0032F4B0: 00 00 8A 42  00 00 80 3F  C4 F5 32 00  B4 F5 32 00  ...B...?..2...2.
0032F4C0: 6C 00 00 00  00 00 00 00  00 00 33 40  01 00 00 00  l.........3@....
0032F4D0: 00 00 80 3F  90 A5 AA 05  54 73 B1 05  01 00 00 00  ...?....Ts......
0032F4E0: 42 E0 61 00  00 00 00 00  00 60 7E 40  01 00 00 00  B.a......`~@....
0032F4F0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0032F500: 00 00 00 00  00 00 00 00  00 00 00 00  28 F5 32 00  ............(.2.
0032F510: 32 08 50 00  10 00 00 00  00 00 00 00  10 C6 50 00  2.P...........P.
0032F520: 54 73 B1 05  A0 02 00 00  40 F5 32 00  CE 22 50 00  Ts......@.2.."P.
0032F530: 10 C6 50 00  E8 3A 72 04  A0 02 00 00  00 00 00 00  ..P..:r.........
0032F540: 5C F5 32 00  4C 0B 42 00  E8 3A 72 04  58 42 3B 06  \.2.L.B..:r.XB;.
0032F550: 10 00 00 00  28 42 3B 06  E8 3A 72 04  00 00 00 00  ....(B;..:r.....
0032F560: E8 F5 32 00  D3 36 42 00  E8 3A 72 04  28 42 3B 06  ..2..6B..:r.(B;.
0032F570: A8 00 00 00  E8 3A 72 04  00 01 00 00  00 00 00 00  .....:r.........
0032F580: 00 00 DA 05  00 00 00 00  43 00 00 00  FF FF FF FF  ........C.......
0032F590: 00 C7 FF FF  00 00 98 41  81 80 80 3A  22 22 A2 3C  .......A...:"".<
0032F5A0: 00 00 00 00  FF FF FF FF  01 00 00 00  08 4F 6B 04  .............Ok.
0032F5B0: 77 AA 5D 3D  05 00 00 00  00 00 00 00  00 00 00 00  w.]=............
0032F5C0: 01 00 00 00  77 AA 5D 3D  E4 F5 32 00  BF EB 52 00  ....w.]=..2...R.
0032F5D0: 00 00 00 00  D0 4D B6 05  00 00 00 00  F8 56 AF 05  .....M.......V..
0032F5E0: 38 57 AF 05  28 42 3B 06  04 F6 32 00  03 0E 42 00  8W..(B;...2...B.
0032F5F0: D0 B5 6F 04  00 00 00 00  E8 3A 72 04  42 33 A0 3E  ..o......:r.B3.>
0032F600: 02 9F F8 3E  18 F6 32 00  46 CA 42 00  E8 3A 72 04  ...>..2.F.B..:r.
0032F610: 18 42 3B 06  00 00 00 00  74 F6 32 00  53 01 42 00  .B;.....t.2.S.B.
0032F620: E8 3A 72 04  C0 F6 32 00  E8 3A 72 04  48 F8 32 00  .:r...2..:r.H.2.
0032F630: 74 F6 32 00  00 01 00 00  A8 00 00 00  E8 3A 72 04  t.2..........:r.
0032F640: 18 F6 32 00  41 01 42 00  50 FE 32 00  01 00 00 00  ..2.A.B.P.2.....
0032F650: 30 32 43 56  00 00 00 00  01 34 BA 05  D0 4D B6 05  02CV.....4...M..
0032F660: 63 8C 4F 00  6A 8C 4F 00  D0 4D B6 05  09 8F 4F 00  c.O.j.O..M....O.
0032F670: 00 00 00 00  9C F6 32 00  F9 0F 42 00  E8 3A 72 04  ......2...B..:r.
0032F680: 30 CA 42 00  C0 F6 32 00  00 00 00 00  E8 3A 72 04  0.B...2......:r.
0032F690: 00 00 00 00  00 01 00 00  02 00 00 00  C8 F6 32 00  ..............2.
0032F6A0: 9D CA 42 00  E8 3A 72 01  30 CA 42 00  C0 F6 32 00  ..B..:r.0.B...2.
0032F6B0: 80 02 00 00  00 00 00 00  00 00 00 00  E8 3A 72 04  .............:r.
0032F6C0: 18 42 3B 06  00 00 00 00  FC F6 32 00  39 DF 83 00  .B;.......2.9...
0032F6D0: FC F6 32 00  91 DF 83 00  E8 3A 72 04  FF FF FF FF  ..2......:r.....
0032F6E0: 54 73 B1 05  00 00 00 00  00 00 00 00  00 00 00 00  Ts..............
0032F6F0: 00 00 00 00  00 00 00 00  02 00 00 00  1C F7 32 00  ..............2.
0032F700: 12 E0 83 00  8C 00 00 00  54 73 B1 05  01 00 00 00  ........Ts......
0032F710: 00 00 00 00  E8 3A 72 04  00 00 00 00  00 00 00 00  .....:r.........
0032F720: 34 F7 32 00  4C F7 32 00  C2 EE 52 00  E8 3A 72 04  4.2.L.2...R..:r.
0032F730: FE FF FF FF  E8 3A 72 04  FF FF FF FF  54 B1 B1 05  .....:r.....T...
0032F740: 74 B1 B1 05  5C F7 32 00  28 FD 50 00  F0 C4 50 00  t...\.2.(.P...P.
0032F750: E8 3A 72 04  A0 01 00 00  00 00 00 00  78 F7 32 00  .:r.........x.2.
0032F760: 4C 0B 42 00  E8 3A 72 04  58 41 3B 06  10 00 00 00  L.B..:r.XA;.....
0032F770: E8 40 3B 06  E8 3A 72 04  00 00 00 00  04 F8 32 00  .@;..:r.......2.
0032F780: D3 36 42 00  E8 3A 72 04  E8 40 3B 06  48 00 00 00  .6B..:r..@;.H...
0032F790: E8 3A 72 04  30 00 00 00  49 00 01 82  7C 7C 01 00  .:r.0...I...||..
0032F7A0: 28 5E EA 05  90 F6 32 00  01 00 00 00  13 00 00 00  (^....2.........
0032F7B0: B8 F8 32 00  17 C4 62 00  20 03 00 00  00 00 00 00  ..2...b. .......




------------------------------------------------------------------------------
Percent memory used:    48
Total physical memory:  4200558592
Free physical memory:   2176045056
Page file:              13462183936
Total virtual memory:   3221159935
Free virtual memory:    3221094399
------------------------------------------------------------------------------


List of running WoW processes:


Process: Z:\home\raresian\Games\World of Warcraft 4.3.4.15595 FREAKZ Edition\World of Warcraft 4.3.4.15595 FREAKZ Edition\Wow.exe; pid: 1151


======================================================================
Hardware/Driver Information:
Processor:              0x0
Page Size:              4096
Min App Address:        0x10000
Max App Address:        0xbfffffff
Processor Mask:         0x3f
Number of Processors:   6
Processor Type:         586
Allocation Granularity: 65536
Processor Level:        16
Processor Revision:     2560
Os Version:             5.1
Os Service Pack:        3.0



```

and this is what I get in the terminal:
```

archive Data/Cache/SoundCache-1.MPQ opened
archive Data/Cache/SoundCache-2.MPQ opened
archive Data/Cache/SoundCache-3.MPQ opened
archive Data/Cache/SoundCache-0.MPQ opened
archive Data/Cache/enUS/SoundCache-enUS.MPQ opened
archive Data/wow-update-base-15211.MPQ opened
archive Data/enUS/wow-update-enUS-15211.MPQ opened
archive Data/Cache/patch-base-15211.MPQ opened
archive Data/Cache/enUS/patch-enUS-15211.MPQ opened
archive Data/Cache/SoundCache-patch-15211.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-15211.MPQ opened
archive Data/wow-update-base-15354.MPQ opened
archive Data/enUS/wow-update-enUS-15354.MPQ opened
archive Data/Cache/patch-base-15354.MPQ opened
archive Data/Cache/enUS/patch-enUS-15354.MPQ opened
archive Data/Cache/SoundCache-patch-15354.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-15354.MPQ opened
archive Data/wow-update-base-15595.MPQ opened
archive Data/enUS/wow-update-enUS-15595.MPQ opened
archive Data/Cache/patch-base-15595.MPQ opened
archive Data/Cache/enUS/patch-enUS-15595.MPQ opened
archive Data/Cache/SoundCache-patch-15595.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-15595.MPQ opened
archive Data\world2.MPQ opened
archive Data\enUS\expansion3-speech-enUS.MPQ opened
archive Data\enUS\expansion3-locale-enUS.MPQ opened
archive Data\expansion3.MPQ opened
archive Data\enUS\expansion2-speech-enUS.MPQ opened
archive Data\enUS\expansion2-locale-enUS.MPQ opened
archive Data\expansion2.MPQ opened
archive Data\enUS\expansion1-speech-enUS.MPQ opened
archive Data\enUS\expansion1-locale-enUS.MPQ opened
archive Data\expansion1.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\sound.MPQ opened
archive Data\world.MPQ opened
archive Data\art.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x32ed00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32eb48,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f028,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32eff0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32ee28,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32efd0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32ee08,0x00000000), stub!
fixme:winediag:AUDDRV_GetAudioEndpoint Winepulse is not officially supported by the wine project
fixme:winediag:AUDDRV_GetAudioEndpoint For sound related feedback and support, please visit http://ubuntuforums.org/showthread.php?t=1960599
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x32f730): stub
fixme:imm:ImmReleaseContext (0x50110, 0x151580): stub
err:dbghelp_dwarf:eval_expression Couldn't read memory at fffffff4
err:dbghelp_dwarf:eval_expression Couldn't read memory at fffffff4
err:dbghelp_dwarf:eval_expression Couldn't read memory at fffffff4
err:dbghelp_dwarf:eval_expression Couldn't read memory at fffffff4
err:dbghelp_dwarf:eval_expression Couldn't read memory at fffffff4
err:dbghelp_dwarf:eval_expression Couldn't read memory at fffffff4
fixme:dbghelp:i386_stack_walk new PC=7bc80465 different from Eip=7bc8057c






fixme:dbghelp:i386_stack_walk new PC=7b87246f different from Eip=7b872309
fixme:dbghelp:i386_stack_walk new PC=7b872309 different from Eip=7b87246f

```

I read a lot about this error but I couldn't manage finding a fix or a workaround. "-opengl" option makes no difference. I updated my video drivers and nothing changed.
My computer has the following specs. :
```

raresian@raresian-desktop:~$ cat /proc/meminfo | grep "MemTotal"
MemTotal:        4102108 kB
raresian@raresian-desktop:~$ sudo lscpu
Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                6
On-line CPU(s) list:   0-5
Thread(s) per core:    1
Core(s) per socket:    6
Socket(s):             1
Vendor ID:             AuthenticAMD
CPU family:            16
Model:                 10
Stepping:              0
CPU MHz:               2800.000
BogoMIPS:              5625.76
Virtualization:        AMD-V
L1d cache:             64K
L1i cache:             64K
L2 cache:              512K
L3 cache:              6144K
raresian@raresian-desktop:~$ sudo lspci -v -s 04:
04:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cypress PRO [Radeon HD 5850] (prog-if 00 [VGA controller])
    Subsystem: Gigabyte Technology Co., Ltd Device 21e4
    Flags: bus master, fast devsel, latency 0, IRQ 75
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at fe820000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at d000 [size=256]
    Expansion ROM at fe800000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [150] Advanced Error Reporting
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx_experimental_12, radeon

raresian@raresian-desktop:~$ wine --version
wine-1.6

```
If you need any more information please ask. I hope someone has an ideea and help me out :D

Thank you !

---

### Post by jjaison-daniel on 2013-08-22
I don't have any idea but I can share my thought.

If the program is 32 bit windows program then better try on 32 bit environment.
to set 32 bit in 64 bit linux for wine. just set WINEARCH=win32
But it won't work on existing wine profile. in this case you can create a new profile as set WINEPREFIX=<path for wine profile directory>
default the wine profile directory is ~/.wine
If you are trying with WINEARCH=win32 then don't try to create the ${WINEPREFIX} folder just only create the parent directory.
If you run wine with "WINEARCH=win32" it will automatically create the folder WINEPREFIX if not exist.

---

### Post by mf0rn on 2013-08-22
Thanks for you opinion but I still get the same error.

I have to mention that I did not install the game under linux, I got a "download-and-play" version from the internet.

---

### Post by Gilad_Pellaeon on 2013-08-22
> **mf0rn said:**
> Thanks for you opinion but I still get the same error.

I have to mention that I did not install the game under linux, I got a "download-and-play" version from the internet.

No suprise you are having issues seeing as you are trying to run a non-official Cataclysm private server client and which if caught by blizzard doing so your real account is banned for breaking the terms of the TOS you agreed too seeing as the official servers are now at v5.3 I believe right smack in the middle of the Mists of Pandaria expansion.

---

### Post by mf0rn on 2013-08-22
That should be no problem considering that on Windows this client is working flawlessly. It's the original client with server's "realmlist.wtf", everything else being unthouched.

---

### Post by mf0rn on 2013-08-23
I got another copy of WoW and works perfect. But the only problem is I have low FPS, around 13.

---

