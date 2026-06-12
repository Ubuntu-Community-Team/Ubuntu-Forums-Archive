---
title: "WoW Wine Crash"
date: 2008-06-04
forum: Wine
---

### Post by Skeet on 2008-06-04
I'm trying to run WoW Trial Client on Ubuntu Hardy. Its the latest 2.4.2 version (just downloaded today).

It installed fine, no hitches. But when I try to run the game I get a crash report and the game crashes.

This is the error dump I get in the Error folder in the game directory

```

==============================================================================

World of WarCraft (build 8301)



Exe:      Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

Time:     Jun  4, 2008 11:19:48.200 PM

User:     sjcurran

Computer: Sean-Ubuntu

------------------------------------------------------------------------------



This application has encountered a critical error:



ERROR #132 (0x85100084) Fatal Exception

Program:	Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:7DD15F50



The instruction at "0x7DD15F50" referenced memory at "0x00000000".

The memory could not be "read".





WoWBuild: 8301

------------------------------------------------------------------------------



----------------------------------------

    x86 Registers

----------------------------------------



EAX=0013B8A0  EBX=7DDAAC84  ECX=7D70FB64  EDX=7DDAB920  ESI=00000000

EDI=0013B920  EBP=0033D610  ESP=0033D608  EIP=7DD15F50  FLG=00090202

CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B





----------------------------------------

    Stack Trace (Manual)

----------------------------------------



Address  Frame    Logical addr  Module



Showing 22/22 threads...



--- Thread ID: 69 ---

7BC68F2B 7B1CB868 0001:00057F2B C:\windows\system32\ntdll.dll

7BC69202 7B1CB898 0001:00058202 C:\windows\system32\ntdll.dll

7B88BAB2 7B1CB9E8 0001:0006AAB2 C:\windows\system32\KERNEL32.dll

7B88BCAC 7B1CBA08 0001:0006ACAC C:\windows\system32\KERNEL32.dll

0046CBFF 7B1CBA38 0001:0006BBFF Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

7BC6AEAE 7B1CBA48 0001:00059EAE C:\windows\system32\ntdll.dll

7BC6B542 7B1CBAE8 0001:0005A542 C:\windows\system32\ntdll.dll

7BC6B772 7B1CC3D8 0001:0005A772 C:\windows\system32\ntdll.dll

B7D974FB 7B1CC4C8 0000:00000000 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe



--- Thread ID: 67 ---

7BC68F2B 7B4DC63C 0001:00057F2B C:\windows\system32\ntdll.dll

7BC69202 7B4DC66C 0001:00058202 C:\windows\system32\ntdll.dll

7B88BAB2 7B4DC7BC 0001:0006AAB2 C:\windows\system32\KERNEL32.dll

7D6BC23E 7B4DC7EC 0001:0002B23E C:\windows\system32\winex11.drv

7ED35B8E 7B4DC99C 0001:00074B8E C:\windows\system32\user32.dll

7ED35BEF 7B4DC9BC 0001:00074BEF C:\windows\system32\user32.dll

00585C38 7B4DCA30 0001:00184C38 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

00811F44 7B4DCA48 0001:00410F44 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

7BC6B542 7B4DCAE8 0001:0005A542 C:\windows\system32\ntdll.dll

7BC6B772 7B4DD3D8 0001:0005A772 C:\windows\system32\ntdll.dll

B7D974FB 7B4DD4C8 0000:00000000 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe



--- Thread ID: 66 ---

004A0479 7B6ED128 0001:0009F479 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe



--- Thread ID: 63 ---

7BC68F2B 7B7FE63C 0001:00057F2B C:\windows\system32\ntdll.dll

7BC69202 7B7FE66C 0001:00058202 C:\windows\system32\ntdll.dll

7B88BAB2 7B7FE7BC 0001:0006AAB2 C:\windows\system32\KERNEL32.dll

7D6BC23E 7B7FE7EC 0001:0002B23E C:\windows\system32\winex11.drv

7ED35B8E 7B7FE99C 0001:00074B8E C:\windows\system32\user32.dll

7ED35BEF 7B7FE9BC 0001:00074BEF C:\windows\system32\user32.dll

00585C38 7B7FEA30 0001:00184C38 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

00811F44 7B7FEA48 0001:00410F44 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

7BC6B542 7B7FEAE8 0001:0005A542 C:\windows\system32\ntdll.dll

7BC6B772 7B7FF3D8 0001:0005A772 C:\windows\system32\ntdll.dll

B7D974FB 7B7FF4C8 0000:00000000 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe



--- Thread ID: 62 ---

7BC68F2B 7BAED614 0001:00057F2B C:\windows\system32\ntdll.dll

7BC69202 7BAED644 0001:00058202 C:\windows\system32\ntdll.dll

7B88BAB2 7BAED794 0001:0006AAB2 C:\windows\system32\KERNEL32.dll

7B88BC0A 7BAED7B4 0001:0006AC0A C:\windows\system32\KERNEL32.dll

00802D4B 7BAEDA0C 0001:00401D4B Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

008025A8 7BAEDA1C 0001:004015A8 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

00550477 7BAEDA38 0001:0014F477 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

7BC6AEAE 7BAEDA48 0001:00059EAE C:\windows\system32\ntdll.dll

7BC6B542 7BAEDAE8 0001:0005A542 C:\windows\system32\ntdll.dll

7BC6B772 7BAEE3D8 0001:0005A772 C:\windows\system32\ntdll.dll

B7D974FB 7BAEE4C8 0000:00000000 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe



--- Thread ID: 61 ---

7BC68F2B 7BBFE848 0001:00057F2B C:\windows\system32\ntdll.dll

7BC69202 7BBFE878 0001:00058202 C:\windows\system32\ntdll.dll

7B88BAB2 7BBFE9C8 0001:0006AAB2 C:\windows\system32\KERNEL32.dll

7B88BCAC 7BBFE9E8 0001:0006ACAC C:\windows\system32\KERNEL32.dll

005541F0 7BBFE9F8 0001:001531F0 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

00802495 7BBFEA10 0001:00401495 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

008025D1 7BBFEA1C 0001:004015D1 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

00550477 7BBFEA38 0001:0014F477 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

7BC6AEAE 7BBFEA48 0001:00059EAE C:\windows\system32\ntdll.dll

7BC6B542 7BBFEAE8 0001:0005A542 C:\windows\system32\ntdll.dll

7BC6B772 7BBFF3D8 0001:0005A772 C:\windows\system32\ntdll.dll

B7D974FB 7BBFF4C8 0000:00000000 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe



--- Thread ID: 60 ---

7B88DCF4 7BDED9FC 0001:0006CCF4 C:\windows\system32\KERNEL32.dll

7B88DD45 7BDEDA1C 0001:0006CD45 C:\windows\system32\KERNEL32.dll

00435158 7BDEDA38 0001:00034158 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

7BC6AEAE 7BDEDA48 0001:00059EAE C:\windows\system32\ntdll.dll

7BC6B542 7BDEDAE8 0001:0005A542 C:\windows\system32\ntdll.dll

7BC6B772 7BDEE3D8 0001:0005A772 C:\windows\system32\ntdll.dll

B7D974FB 7BDEE4C8 0000:00000000 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe



--- Thread ID: 59 ---

7B88DCF4 7BEFE9FC 0001:0006CCF4 C:\windows\system32\KERNEL32.dll

7B88DD45 7BEFEA1C 0001:0006CD45 C:\windows\system32\KERNEL32.dll

00435158 7BEFEA38 0001:00034158 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

7BC6AEAE 7BEFEA48 0001:00059EAE C:\windows\system32\ntdll.dll

7BC6B542 7BEFEAE8 0001:0005A542 C:\windows\system32\ntdll.dll

7BC6B772 7BEFF3D8 0001:0005A772 C:\windows\system32\ntdll.dll

B7D974FB 7BEFF4C8 0000:00000000 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe



--- Thread ID: 58 ---

7B88DCF4 7C3289FC 0001:0006CCF4 C:\windows\system32\KERNEL32.dll

7B88DD45 7C328A1C 0001:0006CD45 C:\windows\system32\KERNEL32.dll

00435158 7C328A38 0001:00034158 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

7BC6AEAE 7C328A48 0001:00059EAE C:\windows\system32\ntdll.dll

7BC6B542 7C328AE8 0001:0005A542 C:\windows\system32\ntdll.dll

7BC6B772 7C3293D8 0001:0005A772 C:\windows\system32\ntdll.dll

B7D974FB 7C3294C8 0000:00000000 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe



--- Thread ID: 57 ---

7B88DCF4 7C4399FC 0001:0006CCF4 C:\windows\system32\KERNEL32.dll

7B88DD45 7C439A1C 0001:0006CD45 C:\windows\system32\KERNEL32.dll

00435158 7C439A38 0001:00034158 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

7BC6AEAE 7C439A48 0001:00059EAE C:\windows\system32\ntdll.dll

7BC6B542 7C439AE8 0001:0005A542 C:\windows\system32\ntdll.dll

7BC6B772 7C43A3D8 0001:0005A772 C:\windows\system32\ntdll.dll

B7D974FB 7C43A4C8 0000:00000000 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe



--- Thread ID: 56 ---

7EE22965 7C54AA38 0001:00021965 C:\windows\system32\winmm.dll

7BC6AEAE 7C54AA48 0001:00059EAE C:\windows\system32\ntdll.dll

7BC6B542 7C54AAE8 0001:0005A542 C:\windows\system32\ntdll.dll

7BC6B772 7C54B3D8 0001:0005A772 C:\windows\system32\ntdll.dll

B7D974FB 7C54B4C8 0000:00000000 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe



--- Thread ID: 55 ---

7BC68F2B 7C6B5854 0001:00057F2B C:\windows\system32\ntdll.dll

7BC69202 7C6B5884 0001:00058202 C:\windows\system32\ntdll.dll

7B88BAB2 7C6B59D4 0001:0006AAB2 C:\windows\system32\KERNEL32.dll

7B88BCAC 7C6B59F4 0001:0006ACAC C:\windows\system32\KERNEL32.dll

005541F0 7C6B5A04 0001:001531F0 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

004A5ED2 7C6B5A1C 0001:000A4ED2 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

00550477 7C6B5A38 0001:0014F477 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

7BC6AEAE 7C6B5A48 0001:00059EAE C:\windows\system32\ntdll.dll

7BC6B542 7C6B5AE8 0001:0005A542 C:\windows\system32\ntdll.dll

7BC6B772 7C6B63D8 0001:0005A772 C:\windows\system32\ntdll.dll

B7D974FB 7C6B64C8 0000:00000000 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe



--- Thread ID: 54 ---

7B88DCF4 7C7C65C8 0001:0006CCF4 C:\windows\system32\KERNEL32.dll

7B88DD45 7C7C65E8 0001:0006CD45 C:\windows\system32\KERNEL32.dll

004A2FBD 7C7C65F4 0001:000A1FBD Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

0079D94C 7C7C6A1C 0001:0039C94C Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

00550477 7C7C6A38 0001:0014F477 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

7BC6AEAE 7C7C6A48 0001:00059EAE C:\windows\system32\ntdll.dll

7BC6B542 7C7C6AE8 0001:0005A542 C:\windows\system32\ntdll.dll

7BC6B772 7C7C73D8 0001:0005A772 C:\windows\system32\ntdll.dll

B7D974FB 7C7C74C8 0000:00000000 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe



--- Thread ID: 53 ---

7B88DCF4 7C8D75C8 0001:0006CCF4 C:\windows\system32\KERNEL32.dll

7B88DD45 7C8D75E8 0001:0006CD45 C:\windows\system32\KERNEL32.dll

004A2FBD 7C8D75F4 0001:000A1FBD Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

0079D94C 7C8D7A1C 0001:0039C94C Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

00550477 7C8D7A38 0001:0014F477 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

7BC6AEAE 7C8D7A48 0001:00059EAE C:\windows\system32\ntdll.dll

7BC6B542 7C8D7AE8 0001:0005A542 C:\windows\system32\ntdll.dll

7BC6B772 7C8D83D8 0001:0005A772 C:\windows\system32\ntdll.dll

B7D974FB 7C8D84C8 0000:00000000 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe



--- Thread ID: 52 ---

7B88DCF4 7C9E85C8 0001:0006CCF4 C:\windows\system32\KERNEL32.dll

7B88DD45 7C9E85E8 0001:0006CD45 C:\windows\system32\KERNEL32.dll

004A2FBD 7C9E85F4 0001:000A1FBD Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

0079D94C 7C9E8A1C 0001:0039C94C Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

00550477 7C9E8A38 0001:0014F477 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

7BC6AEAE 7C9E8A48 0001:00059EAE C:\windows\system32\ntdll.dll

7BC6B542 7C9E8AE8 0001:0005A542 C:\windows\system32\ntdll.dll

7BC6B772 7C9E93D8 0001:0005A772 C:\windows\system32\ntdll.dll

B7D974FB 7C9E94C8 0000:00000000 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe



--- Thread ID: 51 ---

7BC68F2B 7CB5D82C 0001:00057F2B C:\windows\system32\ntdll.dll

7BC69202 7CB5D85C 0001:00058202 C:\windows\system32\ntdll.dll

7B88BAB2 7CB5D9AC 0001:0006AAB2 C:\windows\system32\KERNEL32.dll

7B88BCAC 7CB5D9CC 0001:0006ACAC C:\windows\system32\KERNEL32.dll



--- Thread ID: 49 ---

7B88DCF4 7CC6E9B4 0001:0006CCF4 C:\windows\system32\KERNEL32.dll

7B88DD45 7CC6E9D4 0001:0006CD45 C:\windows\system32\KERNEL32.dll

00569CD4 7CC6EA30 0001:00168CD4 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

00811F44 7CC6EA48 0001:00410F44 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

7BC6B542 7CC6EAE8 0001:0005A542 C:\windows\system32\ntdll.dll

7BC6B772 7CC6F3D8 0001:0005A772 C:\windows\system32\ntdll.dll

B7D974FB 7CC6F4C8 0000:00000000 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe



--- Thread ID: 47 ---

7BC68F2B 7CD7F7F4 0001:00057F2B C:\windows\system32\ntdll.dll

7BC69202 7CD7F824 0001:00058202 C:\windows\system32\ntdll.dll

7B88BAB2 7CD7F974 0001:0006AAB2 C:\windows\system32\KERNEL32.dll

7B88BCAC 7CD7F994 0001:0006ACAC C:\windows\system32\KERNEL32.dll

0058EB13 7CD7FA30 0001:0018DB13 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

00811F44 7CD7FA48 0001:00410F44 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

7BC6B542 7CD7FAE8 0001:0005A542 C:\windows\system32\ntdll.dll

7BC6B772 7CD803D8 0001:0005A772 C:\windows\system32\ntdll.dll

B7D974FB 7CD804C8 0000:00000000 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe



--- Thread ID: 46 ---

7BC68F2B 7CE907F4 0001:00057F2B C:\windows\system32\ntdll.dll

7BC69202 7CE90824 0001:00058202 C:\windows\system32\ntdll.dll

7B88BAB2 7CE90974 0001:0006AAB2 C:\windows\system32\KERNEL32.dll

7B88BCAC 7CE90994 0001:0006ACAC C:\windows\system32\KERNEL32.dll



--- Thread ID: 43 ---

7BC68F2B 7CFA1988 0001:00057F2B C:\windows\system32\ntdll.dll

7BC69202 7CFA19B8 0001:00058202 C:\windows\system32\ntdll.dll

7BC6925C 7CFA19D8 0001:0005825C C:\windows\system32\ntdll.dll

7BC6DDB0 7CFA1A38 0001:0005CDB0 C:\windows\system32\ntdll.dll

7BC6AEAE 7CFA1A48 0001:00059EAE C:\windows\system32\ntdll.dll

7BC6B542 7CFA1AE8 0001:0005A542 C:\windows\system32\ntdll.dll

7BC6B772 7CFA23D8 0001:0005A772 C:\windows\system32\ntdll.dll

B7D974FB 7CFA24C8 0000:00000000 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe



--- Thread ID: 41 ---

7BC68F2B 7D0B2988 0001:00057F2B C:\windows\system32\ntdll.dll

7BC69202 7D0B29B8 0001:00058202 C:\windows\system32\ntdll.dll

7BC6925C 7D0B29D8 0001:0005825C C:\windows\system32\ntdll.dll

7BC6DDB0 7D0B2A38 0001:0005CDB0 C:\windows\system32\ntdll.dll

7BC6AEAE 7D0B2A48 0001:00059EAE C:\windows\system32\ntdll.dll

7BC6B542 7D0B2AE8 0001:0005A542 C:\windows\system32\ntdll.dll

7BC6B772 7D0B33D8 0001:0005A772 C:\windows\system32\ntdll.dll

B7D974FB 7D0B34C8 0000:00000000 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe



--- Thread ID: 40 [Current Thread] ---

7DD15F50 0033D610 0001:00054F50 C:\windows\system32\wined3d.dll

7DCF77C7 0033D690 0001:000367C7 C:\windows\system32\wined3d.dll

7DDC838E 0033D700 0001:0000738E C:\windows\system32\d3d9.dll

00650269 0033D74C 0001:0024F269 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

0064EA41 0033D7C4 0001:0024DA41 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

7ED6D4DA 0033D7F4 0001:000AC4DA C:\windows\system32\user32.dll

7ED6DBBE 0033D834 0001:000ACBBE C:\windows\system32\user32.dll

7ED72455 0033DD04 0001:000B1455 C:\windows\system32\user32.dll

7ED7301B 0033DD44 0001:000B201B C:\windows\system32\user32.dll

7ED360CA 0033DDB4 0001:000750CA C:\windows\system32\user32.dll

7ED3934D 0033DE14 0001:0007834D C:\windows\system32\user32.dll

7ED397BA 0033DE54 0001:000787BA C:\windows\system32\user32.dll

7ECFCD1F 0033DF24 0001:0003BD1F C:\windows\system32\user32.dll

7ECFE475 0033DF74 0001:0003D475 C:\windows\system32\user32.dll

004A26CD 0033DFA8 0001:000A16CD Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

0064EB56 0033E024 0001:0024DB56 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

7ED6D4DA 0033E054 0001:000AC4DA C:\windows\system32\user32.dll

7ED6DBBE 0033E094 0001:000ACBBE C:\windows\system32\user32.dll

7ED72455 0033E564 0001:000B1455 C:\windows\system32\user32.dll

7ED7301B 0033E5A4 0001:000B201B C:\windows\system32\user32.dll

7ED360CA 0033E614 0001:000750CA C:\windows\system32\user32.dll

7ED3934D 0033E674 0001:0007834D C:\windows\system32\user32.dll

7ED397BA 0033E6B4 0001:000787BA C:\windows\system32\user32.dll

7ED6A19B 0033E7E4 0001:000A919B C:\windows\system32\user32.dll

7ED692EE 0033E854 0001:000A82EE C:\windows\system32\user32.dll

7DCEFCAD 0033E8A4 0001:0002ECAD C:\windows\system32\wined3d.dll

7DCF7D16 0033E924 0001:00036D16 C:\windows\system32\wined3d.dll

7DDC838E 0033E994 0001:0000738E C:\windows\system32\d3d9.dll

00650269 0033E9E0 0001:0024F269 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

0064EA41 0033EA58 0001:0024DA41 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

7ED6D4DA 0033EA88 0001:000AC4DA C:\windows\system32\user32.dll

7ED6DBBE 0033EAC8 0001:000ACBBE C:\windows\system32\user32.dll

7ED72455 0033EF98 0001:000B1455 C:\windows\system32\user32.dll

7ED7301B 0033EFD8 0001:000B201B C:\windows\system32\user32.dll

7ED360CA 0033F048 0001:000750CA C:\windows\system32\user32.dll

7ED3934D 0033F0A8 0001:0007834D C:\windows\system32\user32.dll

7ED397BA 0033F0E8 0001:000787BA C:\windows\system32\user32.dll

7ECFCD1F 0033F1B8 0001:0003BD1F C:\windows\system32\user32.dll

7ECFE475 0033F208 0001:0003D475 C:\windows\system32\user32.dll

004A26CD 0033F23C 0001:000A16CD Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

0064EB56 0033F2B8 0001:0024DB56 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

7ED6D4DA 0033F2E8 0001:000AC4DA C:\windows\system32\user32.dll

7ED6DBBE 0033F328 0001:000ACBBE C:\windows\system32\user32.dll

7ED72455 0033F7F8 0001:000B1455 C:\windows\system32\user32.dll

7ED7301B 0033F838 0001:000B201B C:\windows\system32\user32.dll

7ED360CA 0033F8A8 0001:000750CA C:\windows\system32\user32.dll

7ED3934D 0033F908 0001:0007834D C:\windows\system32\user32.dll

7ED397BA 0033F948 0001:000787BA C:\windows\system32\user32.dll

7ED6A19B 0033FA78 0001:000A919B C:\windows\system32\user32.dll

7ED692EE 0033FAE8 0001:000A82EE C:\windows\system32\user32.dll

7D6B9FCA 0033FB68 0001:00028FCA C:\windows\system32\winex11.drv

7D6BBE3F 0033FC98 0001:0002AE3F C:\windows\system32\winex11.drv

7D6BC25F 0033FCC8 0001:0002B25F C:\windows\system32\winex11.drv

7ED37FC8 0033FD28 0001:00076FC8 C:\windows\system32\user32.dll

7ED3842E 0033FD58 0001:0007742E C:\windows\system32\user32.dll

004A1DA0 0033FDAC 0001:000A0DA0 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

007EE356 0033FDE4 0001:003ED356 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

007ED1B7 0033FE54 0001:003EC1B7 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

007ED2E1 0033FE6C 0001:003EC2E1 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

00406478 0033FF08 0001:00005478 Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

7B8773A7 0033FFE8 0001:000563A7 C:\windows\system32\KERNEL32.dll



----------------------------------------

    Stack Trace (Using DBGHELP.DLL)

----------------------------------------



Showing 22/22 threads...



--- Thread ID: 69 ---

7BC68F2B ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7B1CB8D0,0x00000004,0x00000000)

7BC69202 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7B1CB8D0,0x00000000,0x00000000)

7B88BAB2 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000001,0x7B1CBA10,0x00000000,0xFFFFFFFF)

7B88BCAC KERNEL32.dll WaitForSingleObject+60 (0x00002244,0xFFFFFFFF,0x07EF3024,0x00435283)

0046CBFF WoW.exe      <unknown symbol>+0 (0x07EF3024,0x0043971F,0x7B1CBAE8,0x7BC6B542)

7BC6AEAE ntdll.dll    call_thread_entry_point+14 (0x0043971F,0x07EF3024,0x10012A03,0x00000000)

7BC6B542 ntdll.dll    <unknown symbol>+0 (0x7B1CBB1C,0x00000000,0x00000000,0x00000000)

7BC6B772 ntdll.dll    <unknown symbol>+0 (0x7FF84FB8,0x7B1CC490,0x7B1CC490,0x7B1CC490)

B7D974FB              start_thread+203 (0x7B1CCB90,0x00000000,0x00000000,0x00000000)



--- Thread ID: 67 ---

7BC68F2B ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000003,0x7B4DC6A4,0x00000004,0x00000000)

7BC69202 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000003,0x7B4DC6A4,0x00000000,0x00000000)

7B88BAB2 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000003,0x7B4DC820,0x00000000,0xFFFFFFFF)

7D6BC23E winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+126 (0x00000003,0x7B4DC820,0xFFFFFFFF,0x00000000)

7ED35B8E user32.dll   MsgWaitForMultipleObjectsEx+238 (0x00000002,0x7B4DC9E4,0xFFFFFFFF,0x00000000)

7ED35BEF user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x7B4DC9E4,0x00000000,0xFFFFFFFF)

00585C38 WoW.exe      <unknown symbol>+0 (0x06068DA0,0x7BC6AEAE,0x06068DA0,0x00811EC5)

00811F44 WoW.exe      <unknown symbol>+0 (0x00811EC5,0x06068DA0,0x10012A03,0x00000000)

7BC6B542 ntdll.dll    <unknown symbol>+0 (0x7B4DCB1C,0x00000000,0x00000000,0x00000000)

7BC6B772 ntdll.dll    <unknown symbol>+0 (0x7FF88FB8,0x7B4DD490,0x7B4DD490,0x7B4DD490)

B7D974FB              start_thread+203 (0x7B4DDB90,0x00000000,0x00000000,0x00000000)



--- Thread ID: 66 ---

7BC68F2B ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7B6ED8D0,0x00000004,0x00000000)

7BC69202 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7B6ED8D0,0x00000000,0x00000000)

7B88BAB2 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000001,0x7B6EDA10,0x00000000,0xFFFFFFFF)

7B88BCAC KERNEL32.dll WaitForSingleObject+60 (0x0000220C,0xFFFFFFFF,0x07CF4624,0x00435283)

0046CBFF WoW.exe      <unknown symbol>+0 (0x07CF4624,0x0043971F,0x7B6EDAE8,0x7BC6B542)

7BC6AEAE ntdll.dll    call_thread_entry_point+14 (0x0043971F,0x07CF4624,0x10012A03,0x00000000)

7BC6B542 ntdll.dll    <unknown symbol>+0 (0x7B6EDB1C,0x00000000,0x00000000,0x00000000)

7BC6B772 ntdll.dll    <unknown symbol>+0 (0x7FF8CFB8,0x7B6EE490,0x7B6EE490,0x7B6EE490)

B7D974FB              start_thread+203 (0x7B6EEB90,0x00000000,0x00000000,0x00000000)



--- Thread ID: 63 ---

7BC68F2B ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000003,0x7B7FE6A4,0x00000004,0x00000000)

7BC69202 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000003,0x7B7FE6A4,0x00000000,0x00000000)

7B88BAB2 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000003,0x7B7FE820,0x00000000,0xFFFFFFFF)

7D6BC23E winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+126 (0x00000003,0x7B7FE820,0xFFFFFFFF,0x00000000)

7ED35B8E user32.dll   MsgWaitForMultipleObjectsEx+238 (0x00000002,0x7B7FE9E4,0xFFFFFFFF,0x00000000)

7ED35BEF user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x7B7FE9E4,0x00000000,0xFFFFFFFF)

00585C38 WoW.exe      <unknown symbol>+0 (0x06066110,0x7BC6AEAE,0x06066110,0x00811EC5)

00811F44 WoW.exe      <unknown symbol>+0 (0x00811EC5,0x06066110,0x10012A03,0x00000000)

7BC6B542 ntdll.dll    <unknown symbol>+0 (0x7B7FEB1C,0x00000000,0x00000000,0x00000000)

7BC6B772 ntdll.dll    <unknown symbol>+0 (0x7FF90FB8,0x7B7FF490,0x7B7FF490,0x7B7FF490)

B7D974FB              start_thread+203 (0x7B7FFB90,0x00000000,0x00000000,0x00000000)



--- Thread ID: 62 ---

7BC68F2B ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7BAED67C,0x00000004,0x7BAED77C)

7BC69202 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7BAED67C,0x00000000,0x00000000)

7B88BAB2 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000001,0x7BAED8D8,0x00000000,0x000001F4)

7B88BC0A KERNEL32.dll WaitForMultipleObjects+58 (0x00000001,0x7BAED8D8,0x00000000,0x000001F4)

00802D4B WoW.exe      <unknown symbol>+0 (0x008025E0,0x008025EB,0x7BAEDA38,0x00550477)

008025A8 WoW.exe      <unknown symbol>+0 (0x05B0C808,0x00550420,0x05B0C1E8,0x7BC88444)

00550477 WoW.exe      <unknown symbol>+0 (0x000021E8,0x00550420,0x7BAEDAE8,0x7BC6B542)

7BC6AEAE ntdll.dll    call_thread_entry_point+14 (0x00550420,0x05B0C1E8,0x10012A03,0x00000000)

7BC6B542 ntdll.dll    <unknown symbol>+0 (0x7BAEDB1C,0x00000000,0x00000000,0x00000000)

7BC6B772 ntdll.dll    <unknown symbol>+0 (0x7FF94FB8,0x7BAEE490,0x7BAEE490,0x7BAEE490)

B7D974FB              start_thread+203 (0x7BAEEB90,0x00000000,0x00000000,0x00000000)



--- Thread ID: 61 ---

7BC68F2B ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7BBFE8B0,0x00000004,0x7BBFE9B0)

7BC69202 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7BBFE8B0,0x00000000,0x00000000)

7B88BAB2 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000001,0x7BBFE9F0,0x00000000,0x000003E8)

7B88BCAC KERNEL32.dll WaitForSingleObject+60 (0x00002158,0x000003E8,0x7BBFEA10,0x00802495)

005541F0 WoW.exe      <unknown symbol>+0 (0x000003E8,0x0000003D,0x008025C0,0x05B0C818)

00802495 WoW.exe      <unknown symbol>+0 (0x00000000,0x7BBFEA38,0x00550477,0x05B0C818)

008025D1 WoW.exe      <unknown symbol>+0 (0x05B0C818,0x00550420,0x05B0C1C8,0x7BC88444)

00550477 WoW.exe      <unknown symbol>+0 (0x000021E4,0x00550420,0x7BBFEAE8,0x7BC6B542)

7BC6AEAE ntdll.dll    call_thread_entry_point+14 (0x00550420,0x05B0C1C8,0x10012A03,0x00000000)

7BC6B542 ntdll.dll    <unknown symbol>+0 (0x7BBFEB1C,0x00000000,0x00000000,0x00000000)

7BC6B772 ntdll.dll    <unknown symbol>+0 (0x7FF98FB8,0x7BBFF490,0x7BBFF490,0x7BBFF490)

B7D974FB              start_thread+203 (0x7BBFFB90,0x00000000,0x00000000,0x00000000)



--- Thread ID: 60 ---

7B88DCF4 KERNEL32.dll SleepEx+68 (0x0000000A,0x00000000,0x7BDEDA24,0x0042AD32)

7B88DD45 KERNEL32.dll Sleep+37 (0x0000000A,0x0043978D,0x0000000A,0x053D7FA8)

00435158 WoW.exe      <unknown symbol>+0 (0x053D7FA8,0x0043971F,0x7BDEDAE8,0x7BC6B542)

7BC6AEAE ntdll.dll    call_thread_entry_point+14 (0x0043971F,0x053D7FA8,0x10012A03,0x00000000)

7BC6B542 ntdll.dll    <unknown symbol>+0 (0x7BDEDB1C,0x00000000,0x00000000,0x00000000)

7BC6B772 ntdll.dll    <unknown symbol>+0 (0x7FF9CFB8,0x7BDEE490,0x7BDEE490,0x7BDEE490)

B7D974FB              start_thread+203 (0x7BDEEB90,0x00000000,0x00000000,0x00000000)



--- Thread ID: 59 ---

7B88DCF4 KERNEL32.dll SleepEx+68 (0x0000000A,0x00000000,0x00000000,0x00000002)

7B88DD45 KERNEL32.dll Sleep+37 (0x0000000A,0x0043978D,0x0000000A,0x05419288)

00435158 WoW.exe      <unknown symbol>+0 (0x05419288,0x0043971F,0x7BEFEAE8,0x7BC6B542)

7BC6AEAE ntdll.dll    call_thread_entry_point+14 (0x0043971F,0x05419288,0x10012A03,0x00000000)

7BC6B542 ntdll.dll    <unknown symbol>+0 (0x7BEFEB1C,0x00000000,0x00000000,0x00000000)

7BC6B772 ntdll.dll    <unknown symbol>+0 (0x7FFA0FB8,0x7BEFF490,0x7BEFF490,0x7BEFF490)

B7D974FB              start_thread+203 (0x7BEFFB90,0x00000000,0x00000000,0x00000000)



--- Thread ID: 58 ---

7B88DCF4 KERNEL32.dll SleepEx+68 (0x0000000A,0x00000000,0x7C328A24,0x0042AD32)

7B88DD45 KERNEL32.dll Sleep+37 (0x0000000A,0x0043978D,0x0000000A,0x053E7FA8)

00435158 WoW.exe      <unknown symbol>+0 (0x053E7FA8,0x0043971F,0x7C328AE8,0x7BC6B542)

7BC6AEAE ntdll.dll    call_thread_entry_point+14 (0x0043971F,0x053E7FA8,0x10012A03,0x00000000)

7BC6B542 ntdll.dll    <unknown symbol>+0 (0x7C328B1C,0x00000000,0x00000000,0x00000000)

7BC6B772 ntdll.dll    <unknown symbol>+0 (0x7FFA4FB8,0x7C329490,0x7C329490,0x7C329490)

B7D974FB              start_thread+203 (0x7C329B90,0x00000000,0x00000000,0x00000000)



--- Thread ID: 57 ---

7B88DCF4 KERNEL32.dll SleepEx+68 (0x0000000A,0x00000000,0x00000000,0x00000002)

7B88DD45 KERNEL32.dll Sleep+37 (0x0000000A,0x0043978D,0x0000000A,0x052AA288)

00435158 WoW.exe      <unknown symbol>+0 (0x052AA288,0x0043971F,0x7C439AE8,0x7BC6B542)

7BC6AEAE ntdll.dll    call_thread_entry_point+14 (0x0043971F,0x052AA288,0x10012A03,0x00000000)

7BC6B542 ntdll.dll    <unknown symbol>+0 (0x7C439B1C,0x00000000,0x00000000,0x00000000)

7BC6B772 ntdll.dll    <unknown symbol>+0 (0x7FFA8FB8,0x7C43A490,0x7C43A490,0x7C43A490)

B7D974FB              start_thread+203 (0x7C43AB90,0x00000000,0x00000000,0x00000000)



--- Thread ID: 56 ---

7EE22965 winmm.dll    <unknown symbol>+0 (0x00000000,0x7EE22740,0x7C54AAE8,0x7BC6B542)

7BC6AEAE ntdll.dll    call_thread_entry_point+14 (0x7EE22740,0x00000000,0x10012A03,0x00000000)

7BC6B542 ntdll.dll    <unknown symbol>+0 (0x7C54AB1C,0x00000000,0x00000000,0x00000000)

7BC6B772 ntdll.dll    <unknown symbol>+0 (0x7FFACFB8,0x7C54B490,0x7C54B490,0x7C54B490)

B7D974FB              start_thread+203 (0x7C54BB90,0x00000000,0x00000000,0x00000000)



--- Thread ID: 55 ---

7BC68F2B ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7C6B58BC,0x00000004,0x00000000)

7BC69202 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7C6B58BC,0x00000000,0x00000000)

7B88BAB2 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000001,0x7C6B59FC,0x00000000,0xFFFFFFFF)

7B88BCAC KERNEL32.dll WaitForSingleObject+60 (0x00002078,0xFFFFFFFF,0x7C6B5A1C,0x004A5ED2)

005541F0 WoW.exe      <unknown symbol>+0 (0xFFFFFFFF,0x00C83010,0x00000037,0x004A5E70)

004A5ED2 WoW.exe      <unknown symbol>+0 (0x00C83010,0x00550420,0x02B66068,0x7BC88444)

00550477 WoW.exe      <unknown symbol>+0 (0x00002120,0x00550420,0x7C6B5AE8,0x7BC6B542)

7BC6AEAE ntdll.dll    call_thread_entry_point+14 (0x00550420,0x02B66068,0x10012A03,0x00000000)

7BC6B542 ntdll.dll    <unknown symbol>+0 (0x7C6B5B1C,0x00000000,0x00000000,0x00000000)

7BC6B772 ntdll.dll    <unknown symbol>+0 (0x7FFB0FB8,0x7C6B6490,0x7C6B6490,0x7C6B6490)

B7D974FB              start_thread+203 (0x7C6B6B90,0x00000000,0x00000000,0x00000000)



--- Thread ID: 54 ---

7B88DCF4 KERNEL32.dll SleepEx+68 (0x00000001,0x00000000,0x00000000,0x00000000)

7B88DD45 KERNEL32.dll Sleep+37 (0x00000001,0x7C7C6A1C,0x0079D94C,0x00000001)

004A2FBD WoW.exe      <unknown symbol>+0 (0x00000001,0x0079D6F0,0x02B64D28,0x00000036)

0079D94C WoW.exe      <unknown symbol>+0 (0x02B64D28,0x00550420,0x02B64D48,0x7BC88444)

00550477 WoW.exe      <unknown symbol>+0 (0x0000211C,0x00550420,0x7C7C6AE8,0x7BC6B542)

7BC6AEAE ntdll.dll    call_thread_entry_point+14 (0x00550420,0x02B64D48,0x10012A03,0x00000000)

7BC6B542 ntdll.dll    <unknown symbol>+0 (0x7C7C6B1C,0x00000000,0x00000000,0x00000000)

7BC6B772 ntdll.dll    <unknown symbol>+0 (0x7FFB4FB8,0x7C7C7490,0x7C7C7490,0x7C7C7490)

B7D974FB              start_thread+203 (0x7C7C7B90,0x00000000,0x00000000,0x00000000)



--- Thread ID: 53 ---

7B88DCF4 KERNEL32.dll SleepEx+68 (0x00000001,0x00000000,0x00000000,0x00000000)

7B88DD45 KERNEL32.dll Sleep+37 (0x00000001,0x7C8D7A1C,0x0079D94C,0x00000001)

004A2FBD WoW.exe      <unknown symbol>+0 (0x00000001,0x0079D6F0,0x02B64D08,0x00000035)

0079D94C WoW.exe      <unknown symbol>+0 (0x02B64D08,0x00550420,0x02B64D28,0x7BC88444)

00550477 WoW.exe      <unknown symbol>+0 (0x00002118,0x00550420,0x7C8D7AE8,0x7BC6B542)

7BC6AEAE ntdll.dll    call_thread_entry_point+14 (0x00550420,0x02B64D28,0x10012A03,0x00000000)

7BC6B542 ntdll.dll    <unknown symbol>+0 (0x7C8D7B1C,0x00000000,0x00000000,0x00000000)

7BC6B772 ntdll.dll    <unknown symbol>+0 (0x7FFB8FB8,0x7C8D8490,0x7C8D8490,0x7C8D8490)

B7D974FB              start_thread+203 (0x7C8D8B90,0x00000000,0x00000000,0x00000000)



--- Thread ID: 52 ---

7B88DCF4 KERNEL32.dll SleepEx+68 (0x00000001,0x00000000,0x00000000,0x00000000)

7B88DD45 KERNEL32.dll Sleep+37 (0x00000001,0x7C9E8A1C,0x0079D94C,0x00000001)

004A2FBD WoW.exe      <unknown symbol>+0 (0x00000001,0x0079D6F0,0x02B64CC8,0x00000034)

0079D94C WoW.exe      <unknown symbol>+0 (0x02B64CC8,0x00550420,0x02B64CE8,0x7BC88444)

00550477 WoW.exe      <unknown symbol>+0 (0x00002114,0x00550420,0x7C9E8AE8,0x7BC6B542)

7BC6AEAE ntdll.dll    call_thread_entry_point+14 (0x00550420,0x02B64CE8,0x10012A03,0x00000000)

7BC6B542 ntdll.dll    <unknown symbol>+0 (0x7C9E8B1C,0x00000000,0x00000000,0x00000000)

7BC6B772 ntdll.dll    <unknown symbol>+0 (0x7FFBCFB8,0x7C9E9490,0x7C9E9490,0x7C9E9490)

B7D974FB              start_thread+203 (0x7C9E9B90,0x00000000,0x00000000,0x00000000)



--- Thread ID: 51 ---

7BC68F2B ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7CB5D894,0x00000004,0x00000000)

7BC69202 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7CB5D894,0x00000000,0x00000000)

7B88BAB2 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000001,0x7CB5D9D4,0x00000000,0xFFFFFFFF)

7B88BCAC KERNEL32.dll WaitForSingleObject+60 (0x000020F8,0xFFFFFFFF,0x7BC88444,0x00811EC5)



--- Thread ID: 49 ---

7B88DCF4 KERNEL32.dll SleepEx+68 (0x00000064,0x00000000,0x7CC6E9D4,0x7B854DC7)

7B88DD45 KERNEL32.dll Sleep+37 (0x00000064,0x00811EC5,0x7BC88444,0x01420010)

00569CD4 WoW.exe      <unknown symbol>+0 (0x01421910,0x7BC6AEAE,0x01421910,0x00811EC5)

00811F44 WoW.exe      <unknown symbol>+0 (0x00811EC5,0x01421910,0x10012A03,0x00000000)

7BC6B542 ntdll.dll    <unknown symbol>+0 (0x7CC6EB1C,0x00000000,0x00000000,0x00000000)

7BC6B772 ntdll.dll    <unknown symbol>+0 (0x7FFC4FB8,0x7CC6F490,0x7CC6F490,0x7CC6F490)

B7D974FB              start_thread+203 (0x7CC6FB90,0x00000000,0x00000000,0x00000000)



--- Thread ID: 47 ---

7BC68F2B ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7CD7F85C,0x00000004,0x00000000)

7BC69202 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7CD7F85C,0x00000000,0x00000000)

7B88BAB2 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000001,0x7CD7F99C,0x00000000,0xFFFFFFFF)

7B88BCAC KERNEL32.dll WaitForSingleObject+60 (0x000020A4,0xFFFFFFFF,0x00811EC5,0x01420050)

0058EB13 WoW.exe      <unknown symbol>+0 (0x01421BC0,0x7BC6AEAE,0x01421BC0,0x00811EC5)

00811F44 WoW.exe      <unknown symbol>+0 (0x00811EC5,0x01421BC0,0x10012A03,0x00000000)

7BC6B542 ntdll.dll    <unknown symbol>+0 (0x7CD7FB1C,0x00000000,0x00000000,0x00000000)

7BC6B772 ntdll.dll    <unknown symbol>+0 (0x7FFC8FB8,0x7CD80490,0x7CD80490,0x7CD80490)

B7D974FB              start_thread+203 (0x7CD80B90,0x00000000,0x00000000,0x00000000)



--- Thread ID: 46 ---

7BC68F2B ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7CE9085C,0x00000004,0x00000000)

7BC69202 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7CE9085C,0x00000000,0x00000000)

7B88BAB2 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000001,0x7CE9099C,0x00000000,0xFFFFFFFF)

7B88BCAC KERNEL32.dll WaitForSingleObject+60 (0x0000001C,0xFFFFFFFF,0x01420090,0x00811EC5)



--- Thread ID: 43 ---

7BC68F2B ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7CFA19E0,0x00000004,0x7CFA1A20)

7BC69202 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7CFA19E0,0x00000000,0x00000000)

7BC6925C ntdll.dll    NtWaitForSingleObject+60 (0x000020AC,0x00000000,0x7CFA1A20,0x7BC728BF)

7BC6DDB0 ntdll.dll    <unknown symbol>+0 (0x00000000,0x7BC6DC80,0x7CFA1AE8,0x7BC6B542)

7BC6AEAE ntdll.dll    call_thread_entry_point+14 (0x7BC6DC80,0x00000000,0x10012A03,0x00000000)

7BC6B542 ntdll.dll    <unknown symbol>+0 (0x7CFA1B1C,0x00000000,0x00000000,0x00000000)

7BC6B772 ntdll.dll    <unknown symbol>+0 (0x7FFD0FB8,0x7CFA2490,0x7CFA2490,0x7CFA2490)

B7D974FB              start_thread+203 (0x7CFA2B90,0x00000000,0x00000000,0x00000000)



--- Thread ID: 41 ---

7BC68F2B ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7D0B29E0,0x00000004,0x7D0B2A20)

7BC69202 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7D0B29E0,0x00000000,0x00000000)

7BC6925C ntdll.dll    NtWaitForSingleObject+60 (0x000020AC,0x00000000,0x7D0B2A20,0x7BC859F6)

7BC6DDB0 ntdll.dll    <unknown symbol>+0 (0x00000000,0x00000000,0x7D0B2AE8,0x7BC6B542)

7BC6AEAE ntdll.dll    call_thread_entry_point+14 (0x7BC6DC80,0x00000000,0x10012A03,0x00000000)

7BC6B542 ntdll.dll    <unknown symbol>+0 (0x7D0B2B1C,0x00000000,0x00000000,0x00000000)

7BC6B772 ntdll.dll    <unknown symbol>+0 (0x7FFD4FB8,0x7D0B3490,0x7D0B3490,0x7D0B3490)

B7D974FB              start_thread+203 (0x7D0B3B90,0x00000000,0x00000000,0x00000000)



--- Thread ID: 40 [Current Thread] ---

7DD15F50 wined3d.dll  <unknown symbol>+0 (0x0013B8A0,0x7DCE3350,0x00000000,0x00000006)

7DCF77C7 wined3d.dll  <unknown symbol>+0 (0x0013B8A0,0x0033D6B8,0x0033D6F0,0x00000000)

7DDC838E d3d9.dll     <unknown symbol>+0 (0x0013B298,0x0033D714,0x03000400,0x00000400)

00650269 WoW.exe      <unknown symbol>+0 (0x00000000,0x0033D770,0x00000000,0x0003004C)

0064EA41 WoW.exe      <unknown symbol>+0 (0x0003004C,0x00000005,0x00000000,0x03000400)

7ED6D4DA user32.dll   WINPROC_wrapper+26 (0x0064E8E0,0x0003004C,0x00000005,0x00000000)

7ED6DBBE user32.dll   WINPROC_wrapper+1790 (0x0003004C,0x00000005,0x00000000,0x03000400)

7ED72455 user32.dll   <unknown symbol>+0 (0x00000000,0x03000400,0x0033DDA8,0x0064E8E0)

7ED7301B user32.dll   <unknown symbol>+0 (0x0003004C,0x00000005,0x00000000,0x03000400)

7ED360CA user32.dll   <unknown symbol>+0 (0x03000400,0x00000001,0x00000001,0x7ED66FD9)

7ED3934D user32.dll   <unknown symbol>+0 (0x00000000,0x00000000,0x00000001,0x00000028)

7ED397BA user32.dll   SendMessageW+74 (0x0003004C,0x00000005,0x00000000,0x03000400)

7ECFCD1F user32.dll   <unknown symbol>+0 (0x0033E82C,0x0003004C,0x00000047,0x00000000)

7ECFE475 user32.dll   DefWindowProcA+149 (0x0003004C,0x00000047,0x00000000,0x0033E82C)

004A26CD WoW.exe      <unknown symbol>+0 (0x0003004C,0x00000047,0x00000000,0x0033E82C)

0064EB56 WoW.exe      <unknown symbol>+0 (0x0003004C,0x00000047,0x00000000,0x0033E82C)

7ED6D4DA user32.dll   WINPROC_wrapper+26 (0x0064E8E0,0x0003004C,0x00000047,0x00000000)

7ED6DBBE user32.dll   WINPROC_wrapper+1790 (0x0003004C,0x00000047,0x00000000,0x0033E82C)

7ED72455 user32.dll   <unknown symbol>+0 (0x00000000,0x0033E82C,0x0033E608,0x0064E8E0)

7ED7301B user32.dll   <unknown symbol>+0 (0x0003004C,0x00000047,0x00000000,0x0033E82C)

7ED360CA user32.dll   <unknown symbol>+0 (0x0033E82C,0x00000001,0x00000001,0x7ED92548)

7ED3934D user32.dll   <unknown symbol>+0 (0x0003004C,0x00000400,0x00000001,0x00000028)

7ED397BA user32.dll   SendMessageW+74 (0x0003004C,0x00000047,0x00000000,0x0033E82C)

7ED6A19B user32.dll   <unknown symbol>+0 (0x0033E82C,0x0013B4B8,0x00000068,0x00110014)

7ED692EE user32.dll   SetWindowPos+158 (0x0003004C,0x00000000,0x00000000,0x00000000)

7DCEFCAD wined3d.dll  <unknown symbol>+0 (0x00110000,0x00000000,0x0013B4A8,0x00000006)

7DCF7D16 wined3d.dll  <unknown symbol>+0 (0x0013B8A0,0x0033E94C,0x0033E984,0x00000000)

7DDC838E d3d9.dll     <unknown symbol>+0 (0x0013B298,0x0033E9A8,0x02CE0400,0x00000400)

00650269 WoW.exe      <unknown symbol>+0 (0x00000000,0x0033EA04,0x00000000,0x0003004C)

0064EA41 WoW.exe      <unknown symbol>+0 (0x0003004C,0x00000005,0x00000000,0x02CE0400)

7ED6D4DA user32.dll   WINPROC_wrapper+26 (0x0064E8E0,0x0003004C,0x00000005,0x00000000)

7ED6DBBE user32.dll   WINPROC_wrapper+1790 (0x0003004C,0x00000005,0x00000000,0x02CE0400)

7ED72455 user32.dll   <unknown symbol>+0 (0x00000000,0x02CE0400,0x0033F03C,0x0064E8E0)

7ED7301B user32.dll   <unknown symbol>+0 (0x0003004C,0x00000005,0x00000000,0x02CE0400)

7ED360CA user32.dll   <unknown symbol>+0 (0x02CE0400,0x00000001,0x00000001,0x7ED66FD9)

7ED3934D user32.dll   <unknown symbol>+0 (0x00000000,0x00000019,0x00000001,0x00000028)

7ED397BA user32.dll   SendMessageW+74 (0x0003004C,0x00000005,0x00000000,0x02CE0400)

7ECFCD1F user32.dll   <unknown symbol>+0 (0x0033FAC0,0x0003004C,0x00000047,0x00000000)

7ECFE475 user32.dll   DefWindowProcA+149 (0x0003004C,0x00000047,0x00000000,0x0033FAC0)

004A26CD WoW.exe      <unknown symbol>+0 (0x0003004C,0x00000047,0x00000000,0x0033FAC0)

0064EB56 WoW.exe      <unknown symbol>+0 (0x0003004C,0x00000047,0x00000000,0x0033FAC0)

7ED6D4DA user32.dll   WINPROC_wrapper+26 (0x0064E8E0,0x0003004C,0x00000047,0x00000000)

7ED6DBBE user32.dll   WINPROC_wrapper+1790 (0x0003004C,0x00000047,0x00000000,0x0033FAC0)

7ED72455 user32.dll   <unknown symbol>+0 (0x00000000,0x0033FAC0,0x0033F89C,0x0064E8E0)

7ED7301B user32.dll   <unknown symbol>+0 (0x0003004C,0x00000047,0x00000000,0x0033FAC0)

7ED360CA user32.dll   <unknown symbol>+0 (0x0033FAC0,0x00000001,0x00000001,0x0003004C)

7ED3934D user32.dll   <unknown symbol>+0 (0x00000000,0x00000000,0x00000001,0x00000028)

7ED397BA user32.dll   SendMessageW+74 (0x0003004C,0x00000047,0x00000000,0x0033FAC0)

7ED6A19B user32.dll   <unknown symbol>+0 (0x0033FAC0,0x0033FAD0,0x0033FAB8,0x7ED92548)

7ED692EE user32.dll   SetWindowPos+158 (0x0003004C,0x00000000,0x00000000,0x00000019)

7D6B9FCA winex11.drv  <unknown symbol>+0 (0x0003004C,0x0033FBC8,0xFFFFFFFD,0x0033FBC4)

7D6BBE3F winex11.drv  <unknown symbol>+0 (0x00000002,0x00000000,0x00000000,0x00000000)

7D6BC25F winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+159 (0x00000000,0x00000000,0x00000000,0x000004FF)

7ED37FC8 user32.dll   PeekMessageW+88 (0x0033FD80,0x00000000,0x00000000,0x00000000)

7ED3842E user32.dll   PeekMessageA+110 (0x0033FD80,0x00000000,0x00000000,0x00000000)

004A1DA0 WoW.exe      <unknown symbol>+0 (0x0033FDEC,0x0033FDD4,0x0033FDD8,0x0033FDDC)

007EE356 WoW.exe      <unknown symbol>+0 (0xFFFFFFFF,0x0033FE08,0x000088AE,0x00000001)

007ED1B7 WoW.exe      <unknown symbol>+0 (0x00000001,0x00406438,0x00000001,0x00000001)

007ED2E1 WoW.exe      <unknown symbol>+0 (0x0040A169,0x00400000,0x00000000,0x00111B12)

00406478 WoW.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)

7B8773A7 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)





----------------------------------------

    Loaded Modules

----------------------------------------



0x00400000 - 0x00ED2000  Z:\home\sjcurran\Desktop\World of Warcraft Trial\WoW.exe

0x10000000 - 0x10069000  Z:\home\sjcurran\Desktop\World of Warcraft Trial\DivxDecoder.dll

0x7B820000 - 0x7B92D000  C:\windows\system32\KERNEL32.dll

0x7BC10000 - 0x7BCA4000  C:\windows\system32\ntdll.dll

0x7C560000 - 0x7C5A6000  C:\windows\system32\dsound.dll

0x7C9F0000 - 0x7CA04000  C:\windows\system32\psapi.dll

0x7CA10000 - 0x7CA4E000  C:\windows\system32\dbghelp.dll

0x7D490000 - 0x7D4BD000  C:\windows\system32\uxtheme.dll

0x7D530000 - 0x7D53B000  C:\windows\system32\midimap.dll

0x7D540000 - 0x7D552000  C:\windows\system32\msacm32.drv

0x7D630000 - 0x7D659000  C:\windows\system32\winealsa.drv

0x7D690000 - 0x7D714000  C:\windows\system32\winex11.drv

0x7D840000 - 0x7D848000  C:\windows\system32\lz32.dll

0x7D850000 - 0x7D861000  C:\windows\system32\version.dll

0x7D870000 - 0x7D8C2000  C:\windows\system32\rpcrt4.dll

0x7D8D0000 - 0x7D966000  C:\windows\system32\ole32.dll

0x7D990000 - 0x7D9A5000  C:\windows\system32\iphlpapi.dll

0x7D9B0000 - 0x7D9D1000  C:\windows\system32\ws2_32.dll

0x7D9E0000 - 0x7D9F7000  C:\windows\system32\msacm32.dll

0x7DA00000 - 0x7DAB6000  C:\windows\system32\comctl32.dll

0x7DAD0000 - 0x7DBC5000  C:\windows\system32\shell32.dll

0x7DBD0000 - 0x7DC1E000  C:\windows\system32\shlwapi.dll

0x7DC20000 - 0x7DC3F000  C:\windows\system32\mpr.dll

0x7DC50000 - 0x7DC8D000  C:\windows\system32\wininet.dll

0x7DC90000 - 0x7DCAD000  C:\windows\system32\imm32.dll

0x7DCC0000 - 0x7DDAF000  C:\windows\system32\wined3d.dll

0x7DDC0000 - 0x7DDDF000  C:\windows\system32\d3d9.dll

0x7EB50000 - 0x7EBB8000  C:\windows\system32\opengl32.dll

0x7EBC0000 - 0x7EC0A000  C:\windows\system32\advapi32.dll

0x7EC20000 - 0x7ECA5000  C:\windows\system32\gdi32.dll

0x7ECC0000 - 0x7EDEC000  C:\windows\system32\user32.dll

0x7EE00000 - 0x7EE7E000  C:\windows\system32\winmm.dll





----------------------------------------

    Memory Dump

----------------------------------------



Code: 16 bytes starting at (EIP = 7DD15F50)



7DD15F50: 8B 06 85 C0  74 0F 89 04  24 FF 92 7C  05 00 00 C7  ....t...$..|....





Stack: 1024 bytes starting at (ESP = 0033D608)



* = addr                            **                                *       

0033D600: 10 D6 33 00  90 4A 6E 7D  60 FB 70 7D  A0 B8 13 00  ..3..Jn}`.p}....

0033D610: 90 D6 33 00  C7 77 CF 7D  A0 B8 13 00  50 33 CE 7D  ..3..w.}....P3.}

0033D620: 00 00 00 00  06 00 00 00  58 D6 33 00  84 38 8B 7B  ........X.3..8.{

0033D630: 80 B4 13 00  00 00 00 00  00 03 00 00  16 00 00 00  ................

0033D640: 5A 00 00 00  85 5E D8 7D  68 4B 15 00  58 D6 33 00  Z....^.}hK..X.3.

0033D650: 90 D6 33 00  F8 30 CE 7D  00 04 00 00  00 03 00 00  ..3..0.}........

0033D660: 38 00 00 00  16 00 00 00  A0 B8 13 00  7C D6 33 00  8...........|.3.

0033D670: 84 AC DA 7D  21 3D C3 7B  00 00 00 00  87 53 D8 7D  ...}!=.{.....S.}

0033D680: 10 A1 13 00  78 E6 DD 7D  7C EE DD 7D  98 B2 13 00  ....x..}|..}....

0033D690: 00 D7 33 00  8E 83 DC 7D  A0 B8 13 00  B8 D6 33 00  ..3....}......3.

0033D6A0: F0 D6 33 00  00 00 00 00  00 00 00 00  8C 02 00 00  ..3.............

0033D6B0: CF 36 C3 7B  98 B2 13 00  00 04 00 00  00 03 00 00  .6.{............

0033D6C0: 16 00 00 00  01 00 00 00  00 00 00 00  00 00 00 00  ................

0033D6D0: 01 00 00 00  4C 00 03 00  00 00 00 00  01 00 00 00  ....L...........

0033D6E0: 4D 00 00 00  01 00 00 00  38 00 00 00  01 00 00 00  M.......8.......

0033D6F0: 01 00 00 00  4C 00 03 00  08 00 AE 02  08 00 AE 02  ....L...........

0033D700: 4C D7 33 00  69 02 65 00  98 B2 13 00  14 D7 33 00  L.3.i.e.......3.

0033D710: 00 04 00 03  00 04 00 00  00 03 00 00  16 00 00 00  ................

0033D720: 01 00 00 00  00 00 00 00  00 00 00 00  01 00 00 00  ................

0033D730: 4C 00 03 00  00 00 00 00  01 00 00 00  4D 00 00 00  L...........M...

0033D740: 01 00 00 00  38 00 00 00  01 00 00 00  C4 D7 33 00  ....8.........3.

0033D750: 41 EA 64 00  00 00 00 00  70 D7 33 00  00 00 00 00  A.d.....p.3.....

0033D760: 4C 00 03 00  00 04 00 03  48 25 D9 7E  00 04 00 00  L.......H%.~....

0033D770: 00 00 00 00  00 00 00 00  00 00 40 44  00 00 80 44  ..........@D...D

0033D780: 10 A3 13 00  B4 D7 33 00  54 44 C6 7E  00 4C C9 7E  ......3.TD.~.L.~

0033D790: 00 00 00 00  D8 7C 21 00  21 3D C3 7B  00 4C C9 7E  .....|!.!=.{.L.~

0033D7A0: C8 00 00 00  00 4C C9 7E  CF 36 C3 7B  F9 43 C6 7E  .....L.~.6.{.C.~

0033D7B0: 84 38 8B 7B  F4 D7 33 00  DF F0 88 7B  20 1E DB 7E  .8.{..3....{ ..~

0033D7C0: 5C 6C E7 E3  F4 D7 33 00  DA D4 D6 7E  4C 00 03 00  \l....3....~L...

0033D7D0: 05 00 00 00  00 00 00 00  00 04 00 03  E8 A2 13 00  ................

0033D7E0: 48 25 D9 7E  F4 D7 33 00  48 25 D9 7E  00 04 00 03  H%.~..3.H%.~....

0033D7F0: 4C 00 03 00  34 D8 33 00  BE DB D6 7E  E0 E8 64 00  L...4.3....~..d.

0033D800: 4C 00 03 00  05 00 00 00  00 00 00 00  00 04 00 03  L...............

0033D810: 00 00 00 00  44 D8 33 00  68 47 C6 7E  C8 00 00 00  ....D.3.hG.~....

0033D820: 28 03 00 00  02 00 00 00  48 25 D9 7E  00 04 00 03  (.......H%.~....

0033D830: 05 00 00 00  04 DD 33 00  55 24 D7 7E  4C 00 03 00  ......3.U$.~L...

0033D840: 05 00 00 00  00 00 00 00  00 04 00 03  A8 DD 33 00  ..............3.

0033D850: E0 E8 64 00  41 00 01 00  02 00 00 00  00 00 00 00  ..d.A...........

0033D860: 00 00 00 00  D4 DC 33 00  00 00 00 00  00 00 00 00  ......3.........

0033D870: E0 E8 64 00  A8 DD 33 00  4C 00 03 00  50 DB D6 7E  ..d...3.L...P..~

0033D880: 28 03 00 00  04 00 00 00  00 00 04 00  00 00 00 00  (...............

0033D890: 00 00 00 00  00 00 00 00  00 00 00 00  00 03 00 00  ................

0033D8A0: 00 00 00 00  02 00 00 00  00 00 00 00  00 01 00 00  ................

0033D8B0: 00 01 00 00  01 00 00 00  00 00 00 00  00 00 00 00  ................

0033D8C0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

0033D8D0: 08 4E 0E 7C  24 D9 33 00  7B F9 9E 7E  5E 00 D0 C1  .N.|$.3.{..~^...

0033D8E0: 97 18 EF BF  FC D8 33 00  14 D9 33 00  01 00 00 00  ......3...3.....

0033D8F0: 00 00 00 00  00 00 00 00  78 E6 06 7C  5E 00 D0 C1  ........x..|^...

0033D900: F4 CF D8 B7  00 00 00 00  00 00 00 00  01 02 EF BE  ................

0033D910: 00 10 00 00  00 10 00 00  08 4E 0E 7C  01 00 00 00  .........N.|....

0033D920: 24 00 00 00  02 00 00 00  00 4E 0E 7C  03 00 00 00  $........N.|....

0033D930: 03 00 EF BE  97 18 EF BF  A6 18 EF BF  D8 89 15 7C  ...............|

0033D940: 10 8A 15 7C  70 8B 15 7C  39 B7 9B 7E  80 9C 15 7C  ...|p..|9..~...|

0033D950: F0 A5 45 7D  00 00 00 00  A6 18 EF BF  00 00 00 00  ..E}............

0033D960: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

0033D970: 00 00 00 00  00 00 00 00  08 00 00 00  80 00 40 00  ..............@.

0033D980: 5C 60 41 7D  00 00 00 00  0D 00 00 00  08 60 41 7D  \`A}.........`A}

0033D990: 00 00 00 00  01 00 00 00  84 2E 60 7E  08 60 41 7D  ..........`~.`A}

0033D9A0: CE 02 00 00  01 00 00 00  0A 00 00 00  00 30 3B 5D  .............0;]

0033D9B0: 00 00 00 00  02 00 00 00  DF F0 88 7B  78 A1 41 7D  ...........{x.A}

0033D9C0: 0D 03 00 00  01 00 00 00  00 00 CE 02  04 00 00 00  ................

0033D9D0: 00 00 00 00  00 00 00 00  00 00 00 00  04 00 00 00  ................

0033D9E0: 48 25 D9 7E  F4 D9 33 00  F0 F1 D5 7E  20 1E DB 7E  H%.~..3....~ ..~

0033D9F0: 48 25 D9 7E  44 DD 33 00  B6 6B D1 7E  04 00 00 00  H%.~D.3..k.~....

0033DA00: 00 00 00 00  00 00 00 00  CF 00 00 00  00 00 00 00  ................





------------------------------------------------------------------------------

```

Does anyone know why this is happening? :confused:

---

### Post by thisismalhotra on 2008-06-04
Did you install wine and run wincfg?? (I suppose yes just making sure)

Try the troubleshooting link below

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting)

---

### Post by kavmac on 2008-06-22
i'm having the same issue as the op (but i'm  not running trial version, i'm running full version + tbc).  and yes, i installed wine and ran wincfg.  the links you provided didn't seem to be of much assistance...


any other suggestions?

---

### Post by johnl on 2008-06-22
This is what the WoW tech support people would tell you to do:

First run the "Repair.exe" located in your WoW folder -- it scans all the data files and fixes any corrupt information.

Second, if that doesn't fix your problems permanently, run a memory check (There should be one included in your grub list -- memtest86 or some such).  If it starts spitting out errors, you've got some bad areas in your memory stick(s) and you'll probably need to replace them :(

I know no one wants to hear the second part, but it happened to me.  WoW was continuously crashing while the rest of the system ran fine.  I did a memory test and found that the upper area of my memory (>1 gig) was completely fried.   Apparently WoW was the only program I ran that tried to use that much memory or ran into error with it.

---

### Post by kavmac on 2008-06-22
thanks for that info!  i ended up doing an uninstall with the intention of reinstalling as something else was going wrong... but the something else forced me to do a fresh reinstall of ubuntu....  however, if i still get the same issue when i reinstall wow later, i'll definitely run repair and memtest.  i hope it's not memory stick issues... although i'm still within my first 30 days with my new laptop....

---

### Post by kavmac on 2008-06-26
so, i've reinstalled ubuntu and wow.  having the same problem again, as soon as i go to load wow it crashes with the same error message each and every time.  ran repair.exe and all was good.  ran mem test and all is good.  any other suggestions?  and of course i upgraded/extended my latest subscription for a month... and haven't had a chance to play at all :(  i really don't want to put vista back on here just so i can play (friend has identical computer and has no issues).... but i guess if that's what it takes.... i'll also mention that the crash DOES NOT occur when i disable my graphics drivers.  it just runs really really really really slowly.  and graphics are horrid (obviously).


thanks :)

---

### Post by thisismalhotra on 2008-06-26
Can you please post/attach you config.wtf, xorg.conf and output of following command.

```
lspci -v
```

Some more suggestion, I assume you dont have a windows partition running WoW but if you had you could just take the whole WoW folder form there and put it into your wine directory. This also can be done using your friends install who has the same config as you mentioned. So I would try to get his complete WoW installation and see if that work. 

On a personal note I have tried to install WoW from scratch in my system but has never worked for(I know many many for them it has worked just fine).

Also try running following command just in case you have an update whihc affects WoW (Highly unlikely).

Last please turn off your compiz before you play WoW. Also, I don't understand what do you mean when you say disable graphics card, cause you wont be able to play if you disable graphics card.

If you have an ATi card this might help you

ATI enter game world crash

For users with an ATI video card: certain cards have trouble rendering games and video in opengl using current flgrx drivers which will cause your computer to hard locks when you attempt to enter a domain. This error will occur just after character creation/selection, as the game environment is loading, or possibly after a short period of play. In order to fix this error, add the following three lines of code to your xorg.conf file in the ATI device section:

    *

       Option "Capabilities" "0x00000800"
       Option "UseFastTLS" "off"
       Option "KernelModuleParm" "locked-userpages=0"

      You edit the file by doing this command:

       gksudo gedit /etc/X11/xorg.conf

      The section should look something similar to this after editing:

       Section "Device"
         Identifier  "aticonfig-Device[0]"
         Driver      "fglrx"
         Option       "Capabilities" "0x00000800"
         Option       "UseFastTLS" "off"
         Option       "KernelModuleParm" "locked-userpages=0"
       EndSection

---

### Post by flytripper on 2008-06-26
Try changing  the WTF/config.wtf file 

ADD:        

SET gxApi "opengl"

worked for me

---

### Post by kavmac on 2008-06-26
here's the out put for 

config.wtf

```
SET locale "enUS"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET pixelShaders "1"
SET movie "0"
SET expansionMovie "0"
SET readEULA "1"
SET showToolsUI "0"
SET Sound_OutputDriverName "System Default"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET farclip "450.000000"
SET specular "1"
SET particleDensity "1.000000"
SET spellEffectLevel "3"
SET groundEffectDensity "24"
SET accountName "kavmac"
SET readTOS "1"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET realmName "Drak'thul"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "45"
```



xorg.conf

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
```


lspci -v

```
kris@Mater:~$ lspci -v
00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 1d00 [size=256]

00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at 3080 [size=64]
	I/O ports at 3040 [size=64]
	I/O ports at 3000 [size=64]
	Capabilities: <access denied>

00:01.3 Co-processor: nVidia Corporation MCP65 SMU (rev a1)
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 255
	Memory at f2200000 (32-bit, non-prefetchable) [size=512K]

00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at f2486000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	Memory at f2488000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:06.0 Ethernet controller: nVidia Corporation MCP65 Ethernet (rev a3)
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at f2487000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 30e0 [size=8]
	Capabilities: <access denied>

00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at f2480000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=64
	Memory behind bridge: f2100000-f21fffff
	Capabilities: <access denied>

00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device f03c:30cf
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at 30c0 [size=16]
	Capabilities: <access denied>

00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	I/O ports at 30f8 [size=8]
	I/O ports at 30ec [size=4]
	I/O ports at 30f0 [size=8]
	I/O ports at 30e8 [size=4]
	I/O ports at 30d0 [size=16]
	Memory at f2484000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation Unknown device 045b (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: f2000000-f20fffff
	Prefetchable memory behind bridge: 00000000f2500000-00000000f25fffff
	Capabilities: <access denied>

00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: cc000000-ceffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>

00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: f0000000-f1ffffff
	Prefetchable memory behind bridge: 00000000f2600000-00000000f27fffff
	Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 1366
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f2000000 (64-bit, non-prefetchable) [size=16K]
	Memory at f2500000 (64-bit, prefetchable) [size=1M]
	Capabilities: <access denied>

05:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at cc000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 4000 [size=128]
	Capabilities: <access denied>

07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, medium devsel, latency 64, IRQ 5
	Memory at f2100000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, medium devsel, latency 64, IRQ 7
	Memory at f2100800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at f2100c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at f2101000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
	!!! Unknown header type 7f


```


sorry, when i said enable/disable graphics i meant the proprietary drivers for my nvidia card that ubuntu has disabled by default...

i had a windows partition for about a week after i got my laptop... but i ended up doing a clean install of ubuntu, for a completely different reason.  i might reinstall a partition this weekend.... but i'll try the other suggestion first, as i don't really want to do that at the moment (yeah, i know, probably better off doing so...)

oh, and i always ensure compiz is off before i start :)


thanks :)

---

### Post by kavmac on 2008-06-26
> **flytripper said:**
> Try changing  the WTF/config.wtf file 

ADD:        

SET gxApi "opengl"

worked for me


hey it worked for me too!  thanks!  makes me feel much better knowing that i don't have to "waste" my one month subscription (or at least the days that drag by where i don't get to play)...

---

### Post by byzantines2000 on 2008-06-26
I am having the same troubles, but I do not have config.wtf in my world of warcraft folder. Another forum says we need to log in the game and a file will be made, but I cannot even get that far. lol   Should I make a config.wtf file?

---

### Post by darkknight045 on 2008-06-26
I had this problem with Hardy as well.

Alternate fix:  Go and install Wine vers. ~9.53-; for some reason I was able to run WoW just fine with that.  

Once you edit the Config.wtf, and regedit for the Opengl extensions the latest version of Wine should run it just fine.

---

### Post by byzantines2000 on 2008-06-26
I went and copied what a config.wtf file was supposed to be, then I added

SET gxApi "opengl"

added the file in the world of warcraft folder, and it works =D. Now i have to download the 756 meg patch again =(

---

### Post by thisismalhotra on 2008-06-27
> **byzantines2000 said:**
> I went and copied what a config.wtf file was supposed to be, then I added

SET gxApi "opengl"

added the file in the world of warcraft folder, and it works =D. Now i have to download the 756 meg patch again =(

By any chance if you have a windows partition just copy the whole folder over :lolflag:

---

