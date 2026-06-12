---
title: "Crash with wow"
date: 2013-04-30
forum: Wine
---

### Post by kryption on 2013-04-30
I periodically run into this crash and it's starting to get annoying.

```
==============================================================================Agent:  (build 1737)


Exe:      C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
Time:     Apr 30, 2013 12:13:50.009 AM
------------------------------------------------------------------------------


This application has encountered a critical error:


ERROR #1 (0x13370001) Fatal Exception
Program:    C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
Exception:    0xE06D7363 (unknown exception) at 0073:7B83BC25






Crashed Thread:    0x0000005a


Project: 19130001
Build: 1737
Project Name: Agent


------------------------------------------------------------------------------


----------------------------------------
    x86 Registers
----------------------------------------


      EAX = 7b82684d      EBX = 7b8b4ff4      ECX = 008ab2b8      EDX = 0250dd60
      ESI = 00000003      EDI = e06d7363      EBP = 0250dda8      ESP = 0250dd34
      EIP = 7b83bc25      FLG = 00200283       CS = 0073       DS = 007b
       ES = 007b       FS = 0033       GS = 003b       SS = 007b




----------------------------------------
    Stack Trace (Manual)
----------------------------------------


Address  Frame    Logical addr  Module


Showing 17/17 threads...


--- Thread ID: 76 ---
7BC80533 015FE748 0001:0006F533 C:\windows\system32\ntdll.dll
7BC8063A 015FE778 0001:0006F63A C:\windows\system32\ntdll.dll
7B872299 015FE8E8 0001:00061299 C:\windows\system32\KERNEL32.dll
7B872510 015FE928 0001:00061510 C:\windows\system32\KERNEL32.dll
7B872628 015FE968 0001:00061628 C:\windows\system32\KERNEL32.dll
0040D3BF 015FE9C0 0001:0000C3BF C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
004D5268 015FE9D4 0001:000D4268 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773D90 015FEA0C 0001:00372D90 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773E1A 015FEA18 0001:00372E1A C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
7BC78E30 015FEA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 015FEAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 015FEB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 015FF368 0001:000710F9 C:\windows\system32\ntdll.dll
B75FFD4C 015FF468 0000:00000000 <unknown>


--- Thread ID: 98 ---
7BC77B78 03D1E7D8 0001:00066B78 C:\windows\system32\ntdll.dll
7BC77EB0 03D1E828 0001:00066EB0 C:\windows\system32\ntdll.dll
7ED70CF4 03D1E8C8 0001:0000FCF4 C:\windows\system32\ws2_32.dll
006E967C 03D1E904 0001:002E867C C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
006EA4FB 03D1E954 0001:002E94FB C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
006EA653 03D1E99C 0001:002E9653 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
006EA6CC 03D1E9A8 0001:002E96CC C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
006EDF49 03D1E9D4 0001:002ECF49 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773D90 03D1EA0C 0001:00372D90 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773E1A 03D1EA18 0001:00372E1A C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
7BC78E30 03D1EA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 03D1EAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 03D1EB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 03D1F368 0001:000710F9 C:\windows\system32\ntdll.dll
B75FFD4C 03D1F468 0000:00000000 <unknown>


--- Thread ID: 97 ---
7BC80533 0314E718 0001:0006F533 C:\windows\system32\ntdll.dll
7BC8063A 0314E748 0001:0006F63A C:\windows\system32\ntdll.dll
7BC8069B 0314E778 0001:0006F69B C:\windows\system32\ntdll.dll
7BC80E37 0314E878 0001:0006FE37 C:\windows\system32\ntdll.dll
7B876BA7 0314E8F8 0001:00065BA7 C:\windows\system32\KERNEL32.dll
006902F9 0314E964 0001:0028F2F9 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00690076 0314E998 0001:0028F076 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
006B1DDB 0314E9B0 0001:002B0DDB C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
0068FF07 0314E9D4 0001:0028EF07 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773D90 0314EA0C 0001:00372D90 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773E1A 0314EA18 0001:00372E1A C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
7BC78E30 0314EA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 0314EAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 0314EB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 0314F368 0001:000710F9 C:\windows\system32\ntdll.dll
B75FFD4C 0314F468 0000:00000000 <unknown>


--- Thread ID: 91 ---
7BC80533 0260E518 0001:0006F533 C:\windows\system32\ntdll.dll
7BC8063A 0260E548 0001:0006F63A C:\windows\system32\ntdll.dll
7B872299 0260E6B8 0001:00061299 C:\windows\system32\KERNEL32.dll
7B872510 0260E6F8 0001:00061510 C:\windows\system32\KERNEL32.dll
7B872628 0260E738 0001:00061628 C:\windows\system32\KERNEL32.dll
006642EA 0260E7EC 0001:002632EA C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00576E4B 0260E880 0001:00175E4B C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00577A65 0260E8A0 0001:00176A65 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
0057761B 0260E914 0001:0017661B C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00577123 0260E974 0001:00176123 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00576F7B 0260E9B4 0001:00175F7B C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00579A0C 0260E9C0 0001:00178A0C C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
004D5268 0260E9D4 0001:000D4268 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773D90 0260EA0C 0001:00372D90 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773E1A 0260EA18 0001:00372E1A C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
7BC78E30 0260EA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 0260EAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 0260EB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 0260F368 0001:000710F9 C:\windows\system32\ntdll.dll
B75FFD4C 0260F468 0000:00000000 <unknown>


--- Thread ID: 90 [Current Thread] ---
7B83BC25 0250DDA8 0001:0002AC25 C:\windows\system32\KERNEL32.dll
00774BBC 0250DDE4 0001:00373BBC C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
004026B6 0250DE9C 0001:000016B6 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00401513 0250DEF8 0001:00000513 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
007256C9 0250DF10 0001:003246C9 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
007255D7 0250DF38 0001:003245D7 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00688CA9 0250E010 0001:00287CA9 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
007084F5 0250E118 0001:003074F5 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00707804 0250E154 0001:00306804 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
0072F6E5 0250E7C4 0001:0032E6E5 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
0070DCAB 0250E83C 0001:0030CCAB C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
007198CE 0250E860 0001:003188CE C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
0071841F 0250E8F8 0001:0031741F C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00690377 0250E95C 0001:0028F377 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00690076 0250E990 0001:0028F076 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
006CA01B 0250E9B0 0001:002C901B C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
0068FF07 0250E9D4 0001:0028EF07 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773D90 0250EA0C 0001:00372D90 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773E1A 0250EA18 0001:00372E1A C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
7BC78E30 0250EA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 0250EAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 0250EB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 0250F368 0001:000710F9 C:\windows\system32\ntdll.dll
B75FFD4C 0250F468 0000:00000000 <unknown>


--- Thread ID: 89 ---
7BC80533 0240E768 0001:0006F533 C:\windows\system32\ntdll.dll
7BC8063A 0240E798 0001:0006F63A C:\windows\system32\ntdll.dll
7B872299 0240E908 0001:00061299 C:\windows\system32\KERNEL32.dll
7B872510 0240E948 0001:00061510 C:\windows\system32\KERNEL32.dll
7B872628 0240E988 0001:00061628 C:\windows\system32\KERNEL32.dll
0068FF9E 0240E9D4 0001:0028EF9E C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773D90 0240EA0C 0001:00372D90 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773E1A 0240EA18 0001:00372E1A C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
7BC78E30 0240EA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 0240EAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 0240EB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 0240F368 0001:000710F9 C:\windows\system32\ntdll.dll
B75FFD4C 0240F468 0000:00000000 <unknown>


--- Thread ID: 88 ---
7BC80533 01F0E258 0001:0006F533 C:\windows\system32\ntdll.dll
7BC8063A 01F0E288 0001:0006F63A C:\windows\system32\ntdll.dll
7B872299 01F0E3F8 0001:00061299 C:\windows\system32\KERNEL32.dll
7B872510 01F0E438 0001:00061510 C:\windows\system32\KERNEL32.dll
7B872628 01F0E478 0001:00061628 C:\windows\system32\KERNEL32.dll
006E2365 01F0E9B0 0001:002E1365 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
0068FF07 01F0E9D4 0001:0028EF07 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773D90 01F0EA0C 0001:00372D90 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773E1A 01F0EA18 0001:00372E1A C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
7BC78E30 01F0EA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 01F0EAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 01F0EB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 01F0F368 0001:000710F9 C:\windows\system32\ntdll.dll
B75FFD4C 01F0F468 0000:00000000 <unknown>


--- Thread ID: 37 ---
7BC80533 017FE748 0001:0006F533 C:\windows\system32\ntdll.dll
7BC8063A 017FE778 0001:0006F63A C:\windows\system32\ntdll.dll
7B872299 017FE8E8 0001:00061299 C:\windows\system32\KERNEL32.dll
7B872510 017FE928 0001:00061510 C:\windows\system32\KERNEL32.dll
7B872628 017FE968 0001:00061628 C:\windows\system32\KERNEL32.dll
004D5AB4 017FE9C0 0001:000D4AB4 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
004D5268 017FE9D4 0001:000D4268 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773D90 017FEA0C 0001:00372D90 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773E1A 017FEA18 0001:00372E1A C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
7BC78E30 017FEA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 017FEAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 017FEB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 017FF368 0001:000710F9 C:\windows\system32\ntdll.dll
B75FFD4C 017FF468 0000:00000000 <unknown>


--- Thread ID: 38 ---
7BC80533 014FE748 0001:0006F533 C:\windows\system32\ntdll.dll
7BC8063A 014FE778 0001:0006F63A C:\windows\system32\ntdll.dll
7B872299 014FE8E8 0001:00061299 C:\windows\system32\KERNEL32.dll
7B872510 014FE928 0001:00061510 C:\windows\system32\KERNEL32.dll
7B872628 014FE968 0001:00061628 C:\windows\system32\KERNEL32.dll
004D5AB4 014FE9C0 0001:000D4AB4 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
004D5268 014FE9D4 0001:000D4268 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773D90 014FEA0C 0001:00372D90 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773E1A 014FEA18 0001:00372E1A C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
7BC78E30 014FEA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 014FEAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 014FEB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 014FF368 0001:000710F9 C:\windows\system32\ntdll.dll
B75FFD4C 014FF468 0000:00000000 <unknown>


--- Thread ID: 42 ---
7BC80533 013FE748 0001:0006F533 C:\windows\system32\ntdll.dll
7BC8063A 013FE778 0001:0006F63A C:\windows\system32\ntdll.dll
7B872299 013FE8E8 0001:00061299 C:\windows\system32\KERNEL32.dll
7B872510 013FE928 0001:00061510 C:\windows\system32\KERNEL32.dll
7B872628 013FE968 0001:00061628 C:\windows\system32\KERNEL32.dll
004D5AB4 013FE9C0 0001:000D4AB4 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
004D5268 013FE9D4 0001:000D4268 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773D90 013FEA0C 0001:00372D90 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773E1A 013FEA18 0001:00372E1A C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
7BC78E30 013FEA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 013FEAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 013FEB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 013FF368 0001:000710F9 C:\windows\system32\ntdll.dll
B75FFD4C 013FF468 0000:00000000 <unknown>


--- Thread ID: 9 ---
0050509C 012FE9C0 0001:0010409C C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
004D5268 012FE9D4 0001:000D4268 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773D90 012FEA0C 0001:00372D90 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773E1A 012FEA18 0001:00372E1A C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
7BC78E30 012FEA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 012FEAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 012FEB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 012FF368 0001:000710F9 C:\windows\system32\ntdll.dll
B75FFD4C 012FF468 0000:00000000 <unknown>


--- Thread ID: 11 ---
7BC80533 011FE748 0001:0006F533 C:\windows\system32\ntdll.dll
7BC8063A 011FE778 0001:0006F63A C:\windows\system32\ntdll.dll
7B872299 011FE8E8 0001:00061299 C:\windows\system32\KERNEL32.dll
7B872510 011FE928 0001:00061510 C:\windows\system32\KERNEL32.dll
7B872628 011FE968 0001:00061628 C:\windows\system32\KERNEL32.dll
004D5AB4 011FE9C0 0001:000D4AB4 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
004D5268 011FE9D4 0001:000D4268 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773D90 011FEA0C 0001:00372D90 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773E1A 011FEA18 0001:00372E1A C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
7BC78E30 011FEA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 011FEAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 011FEB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 011FF368 0001:000710F9 C:\windows\system32\ntdll.dll
B75FFD4C 011FF468 0000:00000000 <unknown>


--- Thread ID: 71 ---
7BC80533 010FE748 0001:0006F533 C:\windows\system32\ntdll.dll
7BC8063A 010FE778 0001:0006F63A C:\windows\system32\ntdll.dll
7B872299 010FE8E8 0001:00061299 C:\windows\system32\KERNEL32.dll
7B872510 010FE928 0001:00061510 C:\windows\system32\KERNEL32.dll
7B872628 010FE968 0001:00061628 C:\windows\system32\KERNEL32.dll
004D5AB4 010FE9C0 0001:000D4AB4 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
004D5268 010FE9D4 0001:000D4268 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773D90 010FEA0C 0001:00372D90 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773E1A 010FEA18 0001:00372E1A C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
7BC78E30 010FEA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 010FEAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 010FEB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 010FF368 0001:000710F9 C:\windows\system32\ntdll.dll
B75FFD4C 010FF468 0000:00000000 <unknown>


--- Thread ID: 69 ---
7BC80533 00EFE758 0001:0006F533 C:\windows\system32\ntdll.dll
7BC8063A 00EFE788 0001:0006F63A C:\windows\system32\ntdll.dll
7B872299 00EFE8F8 0001:00061299 C:\windows\system32\KERNEL32.dll
7B872510 00EFE938 0001:00061510 C:\windows\system32\KERNEL32.dll
7B8725C7 00EFE978 0001:000615C7 C:\windows\system32\KERNEL32.dll
004D356E 00EFE9C0 0001:000D256E C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
004D5268 00EFE9D4 0001:000D4268 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773D90 00EFEA0C 0001:00372D90 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773E1A 00EFEA18 0001:00372E1A C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
7BC78E30 00EFEA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 00EFEAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 00EFEB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 00EFF368 0001:000710F9 C:\windows\system32\ntdll.dll
B75FFD4C 00EFF468 0000:00000000 <unknown>


--- Thread ID: 68 ---
7BC80533 00DFE728 0001:0006F533 C:\windows\system32\ntdll.dll
7BC8063A 00DFE758 0001:0006F63A C:\windows\system32\ntdll.dll
7B872299 00DFE8C8 0001:00061299 C:\windows\system32\KERNEL32.dll
7B872510 00DFE908 0001:00061510 C:\windows\system32\KERNEL32.dll
7B872628 00DFE948 0001:00061628 C:\windows\system32\KERNEL32.dll
00459115 00DFE990 0001:00058115 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
0045A7DA 00DFE9C0 0001:000597DA C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
004D5268 00DFE9D4 0001:000D4268 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773D90 00DFEA0C 0001:00372D90 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773E1A 00DFEA18 0001:00372E1A C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
7BC78E30 00DFEA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 00DFEAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 00DFEB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 00DFF368 0001:000710F9 C:\windows\system32\ntdll.dll
B75FFD4C 00DFF468 0000:00000000 <unknown>


--- Thread ID: 67 ---
7BC80533 00BEE778 0001:0006F533 C:\windows\system32\ntdll.dll
7BC8063A 00BEE7A8 0001:0006F63A C:\windows\system32\ntdll.dll
7B872299 00BEE918 0001:00061299 C:\windows\system32\KERNEL32.dll
7B872510 00BEE958 0001:00061510 C:\windows\system32\KERNEL32.dll
7B872628 00BEE998 0001:00061628 C:\windows\system32\KERNEL32.dll
004178B1 00BEE9C0 0001:000168B1 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
004D5268 00BEE9D4 0001:000D4268 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773D90 00BEEA0C 0001:00372D90 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00773E1A 00BEEA18 0001:00372E1A C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
7BC78E30 00BEEA28 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 00BEEAF8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 00BEEB18 0001:00067E0E C:\windows\system32\ntdll.dll
7BC820F9 00BEF368 0001:000710F9 C:\windows\system32\ntdll.dll
B75FFD4C 00BEF468 0000:00000000 <unknown>


--- Thread ID: 65 ---
7BC80533 0033FBB8 0001:0006F533 C:\windows\system32\ntdll.dll
7BC8063A 0033FBE8 0001:0006F63A C:\windows\system32\ntdll.dll
7B872299 0033FD58 0001:00061299 C:\windows\system32\KERNEL32.dll
7B872510 0033FD98 0001:00061510 C:\windows\system32\KERNEL32.dll
7B872628 0033FDD8 0001:00061628 C:\windows\system32\KERNEL32.dll
00401BEE 0033FE14 0001:00000BEE C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
00402D91 0033FE60 0001:00001D91 C:\users\Public\Application Data\Battle.net\Agent\Agent.1737\Agent.exe
7B85F1EC 0033FE78 0001:0004E1EC C:\windows\system32\KERNEL32.dll
7B86046B 0033FEB8 0001:0004F46B C:\windows\system32\KERNEL32.dll
7BC78E30 0033FED8 0001:00067E30 C:\windows\system32\ntdll.dll
7BC7BE3D 0033FFA8 0001:0006AE3D C:\windows\system32\ntdll.dll
7BC78E0E 0033FFC8 0001:00067E0E C:\windows\system32\ntdll.dll
7BC4E05E 0033FFE8 0001:0003D05E C:\windows\system32\ntdll.dll


----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------


Showing 17/17 threads...


--- Thread ID: 76 ---
B76069DB              <unknown symbol>+0 (0x015FE6BC,0x004D036A,0x009E36F8,0x015FE540)
7BC7DE28 ntdll.dll    <unknown symbol>+0 (0x015FE6BC,0x004D036A,0x009E36F8,0x015FE540)
7BC80533 ntdll.dll    <unknown symbol>+0 (0x00000001,0x015FE7C8,0x00000004,0x00000000)
7BC8063A ntdll.dll    <unknown symbol>+0 (0x00000001,0x015FE7C8,0x00000000,0x00000000)
7B872299 KERNEL32.dll <unknown symbol>+0 (0x015FE8DC,0x015FE8D4,0x015FE94C,0x7B872510)
7B872510 KERNEL32.dll <unknown symbol>+0 (0x00BF8234,0x00AAF36C,0x006A76D0,0x7B872628)
7B872628 KERNEL32.dll <unknown symbol>+0 (0x00A80884,0x015FE9B4,0x0040D3BF,0x00000138)
0040D3BF Agent.exe    <unknown symbol>+0 (0x033D2494,0x00773DB6,0x00AAEE50,0x015FEA0C)
004D5268 Agent.exe    <unknown symbol>+0 (0x00C08FE0,0x372371DC,0x00773DB6,0x00AAEE50)
00773D90 Agent.exe    <unknown symbol>+0 (0x7FFB0F10,0x015FEA28,0x7BC78E30,0x00AAEE50)
00773E1A Agent.exe    <unknown symbol>+0 (0x00AAEE50,0x7BCBDFF4,0x015FEAF8,0x7BC7BE3D)
7BC78E30 ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00AAEE50,0x00000000,0x00000000)
7BC7BE3D ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00AAEE50,0x015FEB18,0x00773DB6)
7BC78E0E ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00AAEE50,0x00000000,0x00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (0x7FFB0FB8,0x015FFB40,0x015FFB40,0x015FFB40)
B75FFD4C              <unknown symbol>+0 (0x015FFB40,0x00000000,0x00000000,0x00000000)


--- Thread ID: 98 ---
B752DDA2              <unknown symbol>+0 (0x00000370,0x00000000,0x03D1E8A8,0x00000000)
7BC77EDA ntdll.dll    <unknown symbol>+0 (0x00000370,0x00000000,0x03D1E8A8,0x00000000)
7ED70CF4 ws2_32.dll   <unknown symbol>+0 (0x00A8BD6C,0x0000037C,0x00AE607C,0x006E967C)
006E967C Agent.exe    <unknown symbol>+0 (0x00000000,0x03760B04,0x03761B14,0x03762B24)
006EA4FB Agent.exe    <unknown symbol>+0 (0x0075DA8C,0x03D1E980,0x35AD72B8,0x7B873310)
006EA653 Agent.exe    <unknown symbol>+0 (0x0375DA8C,0x03D1E9D4,0x006EDF49,0x0375DA8C)
006EA6CC Agent.exe    <unknown symbol>+0 (0x0375DA8C,0x0068FF07,0x35AD7204,0x00773DB6)
006EDF49 Agent.exe    <unknown symbol>+0 (0x00C651AC,0x35AD71DC,0x00773DB6,0x03763CD8)
00773D90 Agent.exe    <unknown symbol>+0 (0x7FF70F10,0x03D1EA28,0x7BC78E30,0x03763CD8)
00773E1A Agent.exe    <unknown symbol>+0 (0x03763CD8,0x7BCBDFF4,0x03D1EAF8,0x7BC7BE3D)
7BC78E30 ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x03763CD8,0x00000000,0x00000000)
7BC7BE3D ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x03763CD8,0x03D1EB18,0x00773DB6)
7BC78E0E ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x03763CD8,0x00000000,0x00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (0x7FF70FB8,0x03D1FB40,0x03D1FB40,0x03D1FB40)
B75FFD4C              <unknown symbol>+0 (0x03D1FB40,0x00000000,0x00000000,0x00000000)


--- Thread ID: 97 ---
B76069DB              <unknown symbol>+0 (0x0314E68C,0x00000000,0x00000002,0x33DE810C)
7BC7DE28 ntdll.dll    <unknown symbol>+0 (0x0314E68C,0x00000000,0x00000002,0x33DE810C)
7BC80533 ntdll.dll    <unknown symbol>+0 (0x00000001,0x0314E790,0x00000004,0x0314E8D0)
7BC8063A ntdll.dll    <unknown symbol>+0 (0x00000001,0x0314E790,0x00000000,0x00000000)
7BC8069B ntdll.dll    <unknown symbol>+0 (0x0314E7EC,0x0314E82C,0x0314E878,0x7BC80E37)
7BC80E37 ntdll.dll    <unknown symbol>+0 (0x00960718,0x00000000,0x7B826355,0x7B876BA7)
7B876BA7 KERNEL32.dll <unknown symbol>+0 (0x006902F9,0x0000019C,0x0314E950,0x0314E94C)
006902F9 Agent.exe    <unknown symbol>+0 (0x0314E9A8,0x35687248,0x00A957C4,0x7BCBDFF4)
00690076 Agent.exe    <unknown symbol>+0 (0x7B873310,0x00C1D094,0x00000000,0x00960718)
006B1DDB Agent.exe    <unknown symbol>+0 (0x35687204,0x00773DB6,0x0375C308,0x7BCBDFF4)
0068FF07 Agent.exe    <unknown symbol>+0 (0x00C1D094,0x356871DC,0x00773DB6,0x0375C308)
00773D90 Agent.exe    <unknown symbol>+0 (0x7FF74F10,0x0314EA28,0x7BC78E30,0x0375C308)
00773E1A Agent.exe    <unknown symbol>+0 (0x0375C308,0x7BCBDFF4,0x0314EAF8,0x7BC7BE3D)
7BC78E30 ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x0375C308,0x00000000,0x00000000)
7BC7BE3D ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x0375C308,0x0314EB18,0x00773DB6)
7BC78E0E ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x0375C308,0x00000000,0x00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (0x7FF74FB8,0x0314FB40,0x0314FB40,0x0314FB40)
B75FFD4C              <unknown symbol>+0 (0x0314FB40,0x00000000,0x00000000,0x00000000)


--- Thread ID: 91 ---
B76069DB              <unknown symbol>+0 (0x0260E48C,0x0260E2EC,0x0260E854,0x0000001D)
7BC7DE28 ntdll.dll    <unknown symbol>+0 (0x0260E48C,0x0260E2EC,0x0260E854,0x0000001D)
7BC80533 ntdll.dll    <unknown symbol>+0 (0x00000001,0x0260E598,0x00000004,0x00000000)
7BC8063A ntdll.dll    <unknown symbol>+0 (0x00000001,0x0260E598,0x00000000,0x00000000)
7B872299 KERNEL32.dll <unknown symbol>+0 (0x00667949,0x0260E6E8,0x00000000,0x7B872510)
7B872510 KERNEL32.dll <unknown symbol>+0 (0x0260E7A0,0x00667E95,0x341C7CF4,0x7B872628)
7B872628 KERNEL32.dll <unknown symbol>+0 (0x0260E7A0,0x006642EA,0x00000180,0xFFFFFFFF)
006642EA Agent.exe    <unknown symbol>+0 (0x0260E778,0x341C7350,0x00AC4CC4,0x00C1D714)
00576E4B Agent.exe    <unknown symbol>+0 (0x00AC4C6C,0x00BFE364,0x00AC4C6C,0x00000000)
00577A65 Agent.exe    <unknown symbol>+0 (0x00AC4C6C,0x04B6F4B4,0x341C72C4,0x0260E934)
0057761B Agent.exe    <unknown symbol>+0 (0x04B6F4B4,0x341C72A4,0x000003E8,0x0017540A)
00577123 Agent.exe    <unknown symbol>+0 (0x00AC4C6C,0x00773DB6,0x00ADD760,0x7BCBDFF4)
00576F7B Agent.exe    <unknown symbol>+0 (0x00AC4C6C,0x0260E9D4,0x004D5268,0x00AC4C6C)
00579A0C Agent.exe    <unknown symbol>+0 (0x00AC4C6C,0x00773DB6,0x00ADD7D0,0x0260EA0C)
004D5268 Agent.exe    <unknown symbol>+0 (0x00ADD760,0x341C71DC,0x00773DB6,0x00ADD7D0)
00773D90 Agent.exe    <unknown symbol>+0 (0x7FF78F10,0x0260EA28,0x7BC78E30,0x00ADD7D0)
00773E1A Agent.exe    <unknown symbol>+0 (0x00ADD7D0,0x7BCBDFF4,0x0260EAF8,0x7BC7BE3D)
7BC78E30 ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00ADD7D0,0x00000000,0x00000000)
7BC7BE3D ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00ADD7D0,0x0260EB18,0x00773DB6)
7BC78E0E ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00ADD7D0,0x00000000,0x00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (0x7FF78FB8,0x0260FB40,0x0260FB40,0x0260FB40)
B75FFD4C              <unknown symbol>+0 (0x0260FB40,0x00000000,0x00000000,0x00000000)


--- Thread ID: 90 [Current Thread] ---
7B83BC25 KERNEL32.dll <unknown symbol>+0 (0x00774BBC,0xE06D7363,0x00000001,0x00000003)
00774BBC Agent.exe    <unknown symbol>+0 (0x0250DE44,0x008AB2B8,0x342C454C,0x00002749)
004026B6 Agent.exe    <unknown symbol>+0 (0x342C4578,0x00000000,0x0250DFA8,0x0088B8D4)
00401513 Agent.exe    <unknown symbol>+0 (0x0250DF04,0x00002749,0x00960718,0x00000000)
007256C9 Agent.exe    <unknown symbol>+0 (0x04B00EDC,0x00000000,0x00BF8234,0x04B6E4F4)
007255D7 Agent.exe    <unknown symbol>+0 (0x0250DFA8,0x342C7BC0,0x00246A92,0x0375C854)
00688CA9 Agent.exe    <unknown symbol>+0 (0x04B6E4F4,0x342C7BF0,0x04B6E4F4,0x00AC513C)
007084F5 Agent.exe    <unknown symbol>+0 (0x04B6E4F4,0x0250E380,0x0250E140,0x342C7A84)
00707804 Agent.exe    <unknown symbol>+0 (0x0250E380,0x035BD4F0,0x342C7AB8,0x00001CB6)
0072F6E5 Agent.exe    <unknown symbol>+0 (0x0250E880,0x00000000,0x342C7C08,0x04B6E8DC)
0070DCAB Agent.exe    <unknown symbol>+0 (0x0250E880,0x00001CB6,0x342C73B0,0x342C738C)
007198CE Agent.exe    <unknown symbol>+0 (0x0070DB80,0x00000000,0x04B6E4F4,0x04B6E8A4)
0071841F Agent.exe    <unknown symbol>+0 (0x00AC60CC,0x04B6E8A4,0x0250E92C,0x00001CB6)
00690377 Agent.exe    <unknown symbol>+0 (0x0250E9A8,0x342C7240,0x00AC4D4C,0x7B872124)
00690076 Agent.exe    <unknown symbol>+0 (0x7B873310,0x00AC6A9C,0x7BCBDFF4,0x00AC6A9C)
006CA01B Agent.exe    <unknown symbol>+0 (0x342C7204,0x00773DB6,0x00C08AD0,0x7BCBDFF4)
0068FF07 Agent.exe    <unknown symbol>+0 (0x00AC6A9C,0x342C71DC,0x00773DB6,0x00C08AD0)
00773D90 Agent.exe    <unknown symbol>+0 (0x7FF7CF10,0x0250EA28,0x7BC78E30,0x00C08AD0)
00773E1A Agent.exe    <unknown symbol>+0 (0x00C08AD0,0x7BCBDFF4,0x0250EAF8,0x7BC7BE3D)
7BC78E30 ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00C08AD0,0x00000000,0x00000000)
7BC7BE3D ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00C08AD0,0x0250EB18,0x00773DB6)
7BC78E0E ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00C08AD0,0x00000000,0x00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (0x7FF7CFB8,0x0250FB40,0x0250FB40,0x0250FB40)
B75FFD4C              <unknown symbol>+0 (0x0250FB40,0x00000000,0x00000000,0x00000000)


--- Thread ID: 89 ---
B76069DB              <unknown symbol>+0 (0x0240E6DC,0x00000000,0x00000000,0x00000000)
7BC7DE28 ntdll.dll    <unknown symbol>+0 (0x0240E6DC,0x00000000,0x00000000,0x00000000)
7BC80533 ntdll.dll    <unknown symbol>+0 (0x00000001,0x0240E7E8,0x00000004,0x00000000)
7BC8063A ntdll.dll    <unknown symbol>+0 (0x00000001,0x0240E7E8,0x00000000,0x00000000)
7B872299 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x7B872510)
7B872510 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00142C0C,0x0240E980,0x7B872628)
7B872628 KERNEL32.dll <unknown symbol>+0 (0x0068FFBA,0x00000188,0x0068FF9E,0x00000190)
0068FF9E Agent.exe    <unknown symbol>+0 (0x00A96424,0x343C71DC,0x00773DB6,0x00AC6460)
00773D90 Agent.exe    <unknown symbol>+0 (0x7FF80F10,0x0240EA28,0x7BC78E30,0x00AC6460)
00773E1A Agent.exe    <unknown symbol>+0 (0x00AC6460,0x7BCBDFF4,0x0240EAF8,0x7BC7BE3D)
7BC78E30 ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00AC6460,0x00000000,0x00000000)
7BC7BE3D ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00AC6460,0x0240EB18,0x00773DB6)
7BC78E0E ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00AC6460,0x00000000,0x00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (0x7FF80FB8,0x0240FB40,0x0240FB40,0x0240FB40)
B75FFD4C              <unknown symbol>+0 (0x0240FB40,0x00000000,0x00000000,0x00000000)


--- Thread ID: 88 ---
B76069DB              <unknown symbol>+0 (0x01F0E1CC,0x004C9752,0x00004000,0x00000000)
7BC7DE28 ntdll.dll    <unknown symbol>+0 (0x01F0E1CC,0x004C9752,0x00004000,0x00000000)
7BC80533 ntdll.dll    <unknown symbol>+0 (0x00000001,0x01F0E2D8,0x00000004,0x00000000)
7BC8063A ntdll.dll    <unknown symbol>+0 (0x00000001,0x01F0E2D8,0x00000000,0x00000000)
7B872299 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x7B872510)
7B872510 KERNEL32.dll <unknown symbol>+0 (0x378C7FB8,0x00A86B24,0x00AC513C,0x7B872628)
7B872628 KERNEL32.dll <unknown symbol>+0 (0x00989680,0x006E2365,0x0000018C,0xFFFFFFFF)
006E2365 Agent.exe    <unknown symbol>+0 (0x378C7204,0x00773DB6,0x00AC6188,0x7BCBDFF4)
0068FF07 Agent.exe    <unknown symbol>+0 (0x00A97BF4,0x378C71DC,0x00773DB6,0x00AC6188)
00773D90 Agent.exe    <unknown symbol>+0 (0x7FF94F10,0x01F0EA28,0x7BC78E30,0x00AC6188)
00773E1A Agent.exe    <unknown symbol>+0 (0x00AC6188,0x7BCBDFF4,0x01F0EAF8,0x7BC7BE3D)
7BC78E30 ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00AC6188,0x00000000,0x00000000)
7BC7BE3D ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00AC6188,0x01F0EB18,0x00773DB6)
7BC78E0E ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00AC6188,0x00000000,0x00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (0x7FF94FB8,0x01F0FB40,0x01F0FB40,0x01F0FB40)
B75FFD4C              <unknown symbol>+0 (0x01F0FB40,0x00000000,0x00000000,0x00000000)


--- Thread ID: 37 ---
B76069DB              <unknown symbol>+0 (0x017FE6BC,0x00000000,0x017FE6FC,0x7BC776C9)
7BC7DE28 ntdll.dll    <unknown symbol>+0 (0x017FE6BC,0x00000000,0x017FE6FC,0x7BC776C9)
7BC80533 ntdll.dll    <unknown symbol>+0 (0x00000001,0x017FE7C8,0x00000004,0x00000000)
7BC8063A ntdll.dll    <unknown symbol>+0 (0x00000001,0x017FE7C8,0x00000000,0x00000000)
7B872299 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x7B872510)
7B872510 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x009E0014,0x7B872628)
7B872628 KERNEL32.dll <unknown symbol>+0 (0x004D5AB4,0x00000128,0xFFFFFFFF,0x00773DB6)
004D5AB4 Agent.exe    <unknown symbol>+0 (0x00AB18B4,0x00773DB6,0x00AB3038,0x017FEA0C)
004D5268 Agent.exe    <unknown symbol>+0 (0x00AB2FD0,0x370371DC,0x00773DB6,0x00AB3038)
00773D90 Agent.exe    <unknown symbol>+0 (0x7FFA8F10,0x017FEA28,0x7BC78E30,0x00AB3038)
00773E1A Agent.exe    <unknown symbol>+0 (0x00AB3038,0x7BCBDFF4,0x017FEAF8,0x7BC7BE3D)
7BC78E30 ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00AB3038,0x00000000,0x00000000)
7BC7BE3D ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00AB3038,0x017FEB18,0x00773DB6)
7BC78E0E ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00AB3038,0x00000000,0x00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (0x7FFA8FB8,0x017FFB40,0x017FFB40,0x017FFB40)
B75FFD4C              <unknown symbol>+0 (0x017FFB40,0x00000000,0x00000000,0x00000000)


--- Thread ID: 38 ---
B76069DB              <unknown symbol>+0 (0x014FE6BC,0x00000000,0x014FE6FC,0x7BC776C9)
7BC7DE28 ntdll.dll    <unknown symbol>+0 (0x014FE6BC,0x00000000,0x014FE6FC,0x7BC776C9)
7BC80533 ntdll.dll    <unknown symbol>+0 (0x00000001,0x014FE7C8,0x00000004,0x00000000)
7BC8063A ntdll.dll    <unknown symbol>+0 (0x00000001,0x014FE7C8,0x00000000,0x00000000)
7B872299 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x7B872510)
7B872510 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x009E0014,0x7B872628)
7B872628 KERNEL32.dll <unknown symbol>+0 (0x004D5AB4,0x000000FC,0xFFFFFFFF,0x00773DB6)
004D5AB4 Agent.exe    <unknown symbol>+0 (0x00AA4904,0x00773DB6,0x00A8E018,0x014FEA0C)
004D5268 Agent.exe    <unknown symbol>+0 (0x00A8E880,0x373371DC,0x00773DB6,0x00A8E018)
00773D90 Agent.exe    <unknown symbol>+0 (0x7FFB4F10,0x014FEA28,0x7BC78E30,0x00A8E018)
00773E1A Agent.exe    <unknown symbol>+0 (0x00A8E018,0x7BCBDFF4,0x014FEAF8,0x7BC7BE3D)
7BC78E30 ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00A8E018,0x00000000,0x00000000)
7BC7BE3D ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00A8E018,0x014FEB18,0x00773DB6)
7BC78E0E ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00A8E018,0x00000000,0x00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (0x7FFB4FB8,0x014FFB40,0x014FFB40,0x014FFB40)
B75FFD4C              <unknown symbol>+0 (0x014FFB40,0x00000000,0x00000000,0x00000000)


--- Thread ID: 42 ---
B76069DB              <unknown symbol>+0 (0x013FE6BC,0x00000000,0x013FE6FC,0x7BC776C9)
7BC7DE28 ntdll.dll    <unknown symbol>+0 (0x013FE6BC,0x00000000,0x013FE6FC,0x7BC776C9)
7BC80533 ntdll.dll    <unknown symbol>+0 (0x00000001,0x013FE7C8,0x00000004,0x00000000)
7BC8063A ntdll.dll    <unknown symbol>+0 (0x00000001,0x013FE7C8,0x00000000,0x00000000)
7B872299 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x7B872510)
7B872510 KERNEL32.dll <unknown symbol>+0 (0x00A8D0CC,0x00C009C4,0x013FE968,0x7B872628)
7B872628 KERNEL32.dll <unknown symbol>+0 (0x004D5AB4,0x000000F0,0xFFFFFFFF,0x00773DB6)
004D5AB4 Agent.exe    <unknown symbol>+0 (0x00C009C4,0x00773DB6,0x00AB8EC8,0x013FEA0C)
004D5268 Agent.exe    <unknown symbol>+0 (0x00AA5048,0x374371DC,0x00773DB6,0x00AB8EC8)
00773D90 Agent.exe    <unknown symbol>+0 (0x7FFB8F10,0x013FEA28,0x7BC78E30,0x00AB8EC8)
00773E1A Agent.exe    <unknown symbol>+0 (0x00AB8EC8,0x7BCBDFF4,0x013FEAF8,0x7BC7BE3D)
7BC78E30 ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00AB8EC8,0x00000000,0x00000000)
7BC7BE3D ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00AB8EC8,0x013FEB18,0x00773DB6)
7BC78E0E ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00AB8EC8,0x00000000,0x00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (0x7FFB8FB8,0x013FFB40,0x013FFB40,0x013FFB40)
B75FFD4C              <unknown symbol>+0 (0x013FFB40,0x00000000,0x00000000,0x00000000)


--- Thread ID: 9 ---
B752F690              <unknown symbol>+0 (0x0079C1B8,0xFFFFFFFF,0x0050509C,0x000000A0)
7ED6BB98 ws2_32.dll   <unknown symbol>+0 (0x0079C1B8,0xFFFFFFFF,0x0050509C,0x000000A0)
0050509C Agent.exe    <unknown symbol>+0 (0x00AAE8FC,0x00773DB6,0x00C010F0,0x012FEA0C)
004D5268 Agent.exe    <unknown symbol>+0 (0x00C01090,0x375371DC,0x00773DB6,0x00C010F0)
00773D90 Agent.exe    <unknown symbol>+0 (0x7FFBCF10,0x012FEA28,0x7BC78E30,0x00C010F0)
00773E1A Agent.exe    <unknown symbol>+0 (0x00C010F0,0x7BCBDFF4,0x012FEAF8,0x7BC7BE3D)
7BC78E30 ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00C010F0,0x00000000,0x00000000)
7BC7BE3D ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00C010F0,0x012FEB18,0x00773DB6)
7BC78E0E ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00C010F0,0x00000000,0x00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (0x7FFBCFB8,0x012FFB40,0x012FFB40,0x012FFB40)
B75FFD4C              <unknown symbol>+0 (0x012FFB40,0x00000000,0x00000000,0x00000000)


--- Thread ID: 11 ---
B76069DB              <unknown symbol>+0 (0x011FE6BC,0x00000000,0x011FE6FC,0x7BC776C9)
7BC7DE28 ntdll.dll    <unknown symbol>+0 (0x011FE6BC,0x00000000,0x011FE6FC,0x7BC776C9)
7BC80533 ntdll.dll    <unknown symbol>+0 (0x00000001,0x011FE7C8,0x00000004,0x00000000)
7BC8063A ntdll.dll    <unknown symbol>+0 (0x00000001,0x011FE7C8,0x00000000,0x00000000)
7B872299 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x7B872510)
7B872510 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00BF0000,0x7B872628)
7B872628 KERNEL32.dll <unknown symbol>+0 (0x004D5AB4,0x000000D0,0xFFFFFFFF,0x00773DB6)
004D5AB4 Agent.exe    <unknown symbol>+0 (0x00AAAD64,0x00773DB6,0x00C00E70,0x011FEA0C)
004D5268 Agent.exe    <unknown symbol>+0 (0x00A8D388,0x376371DC,0x00773DB6,0x00C00E70)
00773D90 Agent.exe    <unknown symbol>+0 (0x7FFC0F10,0x011FEA28,0x7BC78E30,0x00C00E70)
00773E1A Agent.exe    <unknown symbol>+0 (0x00C00E70,0x7BCBDFF4,0x011FEAF8,0x7BC7BE3D)
7BC78E30 ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00C00E70,0x00000000,0x00000000)
7BC7BE3D ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00C00E70,0x011FEB18,0x00773DB6)
7BC78E0E ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00C00E70,0x00000000,0x00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (0x7FFC0FB8,0x011FFB40,0x011FFB40,0x011FFB40)
B75FFD4C              <unknown symbol>+0 (0x011FFB40,0x00000000,0x00000000,0x00000000)


--- Thread ID: 71 ---
B76069DB              <unknown symbol>+0 (0x010FE6BC,0x00000000,0x010FE6FC,0x7BC776C9)
7BC7DE28 ntdll.dll    <unknown symbol>+0 (0x010FE6BC,0x00000000,0x010FE6FC,0x7BC776C9)
7BC80533 ntdll.dll    <unknown symbol>+0 (0x00000001,0x010FE7C8,0x00000004,0x00000000)
7BC8063A ntdll.dll    <unknown symbol>+0 (0x00000001,0x010FE7C8,0x00000000,0x00000000)
7B872299 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x7B872510)
7B872510 KERNEL32.dll <unknown symbol>+0 (0x00A8D0CC,0x00A8D50C,0x010FE968,0x7B872628)
7B872628 KERNEL32.dll <unknown symbol>+0 (0x004D5AB4,0x000000C0,0xFFFFFFFF,0x00773DB6)
004D5AB4 Agent.exe    <unknown symbol>+0 (0x00A8D50C,0x00773DB6,0x00A8D168,0x010FEA0C)
004D5268 Agent.exe    <unknown symbol>+0 (0x00A8D100,0x377371DC,0x00773DB6,0x00A8D168)
00773D90 Agent.exe    <unknown symbol>+0 (0x7FFC4F10,0x010FEA28,0x7BC78E30,0x00A8D168)
00773E1A Agent.exe    <unknown symbol>+0 (0x00A8D168,0x7BCBDFF4,0x010FEAF8,0x7BC7BE3D)
7BC78E30 ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00A8D168,0x00000000,0x00000000)
7BC7BE3D ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00A8D168,0x010FEB18,0x00773DB6)
7BC78E0E ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00A8D168,0x00000000,0x00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (0x7FFC4FB8,0x010FFB40,0x010FFB40,0x010FFB40)
B75FFD4C              <unknown symbol>+0 (0x010FFB40,0x00000000,0x00000000,0x00000000)


--- Thread ID: 69 ---
B76069DB              <unknown symbol>+0 (0x00EFE6CC,0x00136870,0x00EFE598,0x7BC490EB)
7BC7DE28 ntdll.dll    <unknown symbol>+0 (0x00EFE6CC,0x00136870,0x00EFE598,0x7BC490EB)
7BC80533 ntdll.dll    <unknown symbol>+0 (0x00000001,0x00EFE7D8,0x00000006,0x00EFE8D8)
7BC8063A ntdll.dll    <unknown symbol>+0 (0x00000001,0x00EFE7D8,0x00000000,0x00000001)
7B872299 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x7B872510)
7B872510 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x7B8725C7)
7B8725C7 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x004D356E,0x000000A4,0x00000064)
004D356E Agent.exe    <unknown symbol>+0 (0x00AA55AC,0x00773DB6,0x00C02B70,0x00EFEA0C)
004D5268 Agent.exe    <unknown symbol>+0 (0x00AA5748,0x369371DC,0x00773DB6,0x00C02B70)
00773D90 Agent.exe    <unknown symbol>+0 (0x7FFCCF10,0x00EFEA28,0x7BC78E30,0x00C02B70)
00773E1A Agent.exe    <unknown symbol>+0 (0x00C02B70,0x7BCBDFF4,0x00EFEAF8,0x7BC7BE3D)
7BC78E30 ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00C02B70,0x00000000,0x00000000)
7BC7BE3D ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00C02B70,0x00EFEB18,0x00773DB6)
7BC78E0E ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00C02B70,0x00000000,0x00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (0x7FFCCFB8,0x00EFFB40,0x00EFFB40,0x00EFFB40)
B75FFD4C              <unknown symbol>+0 (0x00EFFB40,0x00000000,0x00000000,0x00000000)


--- Thread ID: 68 ---
B76069DB              <unknown symbol>+0 (0x00DFE69C,0x00000000,0x00BF5374,0x7BC3767D)
7BC7DE28 ntdll.dll    <unknown symbol>+0 (0x00DFE69C,0x00000000,0x00BF5374,0x7BC3767D)
7BC80533 ntdll.dll    <unknown symbol>+0 (0x00000001,0x00DFE7A8,0x00000004,0x00DFE8A8)
7BC8063A ntdll.dll    <unknown symbol>+0 (0x00000001,0x00DFE7A8,0x00000000,0x00000000)
7B872299 KERNEL32.dll <unknown symbol>+0 (0x00DFE8F0,0x00A9CC01,0x00DFE8F8,0x7B872510)
7B872510 KERNEL32.dll <unknown symbol>+0 (0x00DFE950,0x36A372F4,0x00AB8DE4,0x7B872628)
7B872628 KERNEL32.dll <unknown symbol>+0 (0x00830580,0x00000000,0x00459115,0x0000008C)
00459115 Agent.exe    <unknown symbol>+0 (0x0043BC5B,0x36A37210,0x00773DB6,0x00A9CC70)
0045A7DA Agent.exe    <unknown symbol>+0 (0x00A9CBB4,0x00773DB6,0x00A9B290,0x00DFEA0C)
004D5268 Agent.exe    <unknown symbol>+0 (0x00A9CC70,0x36A371DC,0x00773DB6,0x00A9B290)
00773D90 Agent.exe    <unknown symbol>+0 (0x7FFD0F10,0x00DFEA28,0x7BC78E30,0x00A9B290)
00773E1A Agent.exe    <unknown symbol>+0 (0x00A9B290,0x7BCBDFF4,0x00DFEAF8,0x7BC7BE3D)
7BC78E30 ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00A9B290,0x00000000,0x00000000)
7BC7BE3D ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00A9B290,0x00DFEB18,0x00773DB6)
7BC78E0E ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00A9B290,0x00000000,0x00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (0x7FFD0FB8,0x00DFFB40,0x00DFFB40,0x00DFFB40)
B75FFD4C              <unknown symbol>+0 (0x00DFFB40,0x00000000,0x00000000,0x00000000)


--- Thread ID: 67 ---
B76069DB              <unknown symbol>+0 (0x00BEE6EC,0x00000000,0x00000000,0x00000000)
7BC7DE28 ntdll.dll    <unknown symbol>+0 (0x00BEE6EC,0x00000000,0x00000000,0x00000000)
7BC80533 ntdll.dll    <unknown symbol>+0 (0x00000001,0x00BEE7F8,0x00000004,0x00BEE8F8)
7BC8063A ntdll.dll    <unknown symbol>+0 (0x00000001,0x00BEE7F8,0x00000000,0x00000000)
7B872299 KERNEL32.dll <unknown symbol>+0 (0x0077061E,0x36C27280,0x00BFB1AC,0x7B872510)
7B872510 KERNEL32.dll <unknown symbol>+0 (0x00BEE980,0x36C2727C,0x00A81758,0x7B872628)
7B872628 KERNEL32.dll <unknown symbol>+0 (0x00BEE9FC,0x007B9A88,0x004178B1,0x00000080)
004178B1 Agent.exe    <unknown symbol>+0 (0x00A81734,0x00773DB6,0x00A81808,0x00BEEA0C)
004D5268 Agent.exe    <unknown symbol>+0 (0x00A81790,0x36C271DC,0x00773DB6,0x00A81808)
00773D90 Agent.exe    <unknown symbol>+0 (0x7FFD4F10,0x00BEEA28,0x7BC78E30,0x00A81808)
00773E1A Agent.exe    <unknown symbol>+0 (0x00A81808,0x7BCBDFF4,0x00BEEAF8,0x7BC7BE3D)
7BC78E30 ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00A81808,0x00000000,0x00000000)
7BC7BE3D ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00A81808,0x00BEEB18,0x00773DB6)
7BC78E0E ntdll.dll    <unknown symbol>+0 (0x00773DB6,0x00A81808,0x00000000,0x00000000)
7BC820F9 ntdll.dll    <unknown symbol>+0 (0x7FFD4FB8,0x00BEFB40,0x00BEFB40,0x00BEFB40)
B75FFD4C              <unknown symbol>+0 (0x00BEFB40,0x00000000,0x00000000,0x00000000)


--- Thread ID: 65 ---
B76069DB              <unknown symbol>+0 (0x0033FB2C,0x00000029,0x00000040,0x7FFD8000)
7BC7DE28 ntdll.dll    <unknown symbol>+0 (0x0033FB2C,0x00000029,0x00000040,0x7FFD8000)
7BC80533 ntdll.dll    <unknown symbol>+0 (0x00000001,0x0033FC38,0x00000004,0x0033FD38)
7BC8063A ntdll.dll    <unknown symbol>+0 (0x00000001,0x0033FC38,0x00000000,0x00000000)
7B872299 KERNEL32.dll <unknown symbol>+0 (0x3E63BCD3,0x00000000,0x04AF981C,0x7B872510)
7B872510 KERNEL32.dll <unknown symbol>+0 (0x009E3A18,0x364F6678,0x00A8171C,0x7B872628)
7B872628 KERNEL32.dll <unknown symbol>+0 (0x00401BEE,0x00000068,0x00000064,0x364F65C4)
00401BEE Agent.exe    <unknown symbol>+0 (0x007709CE,0x00000002,0x009E1C68,0x009E1D28)
00402D91 Agent.exe    <unknown symbol>+0 (0x7FFDF000,0x7BC5036A,0x7B8B4FF4,0x7FFDF000)
7B85F1EC KERNEL32.dll <unknown symbol>+0 (0x7FFDF000,0x00770A24,0x00000000,0x00000000)
7B86046B KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x7BC78E30)
7BC78E30 ntdll.dll    <unknown symbol>+0 (0x7B860400,0x7FFDF000,0x00000000,0x00000000)
7BC7BE3D ntdll.dll    <unknown symbol>+0 (0x7B860400,0x7FFDF000,0x0033FFC8,0x00110870)
7BC78E0E ntdll.dll    <unknown symbol>+0 (0x7B860400,0x7FFDF000,0x00000000,0x00000000)
7BC4E05E ntdll.dll    <unknown symbol>+0 (0x7B860400,0x00000000,0x00000000,0x00000000)
B762F4ED              <unknown symbol>+0 (0x7BC43387,0x7BC43387,0x7BC43387,0x7BC43387)
B762F5AB              <unknown symbol>+0 (0x7BC4E040,0x7B860400,0x00340000,0xBF89968C)
7BC53EC0 ntdll.dll    <unknown symbol>+0 (0xBF899F22,0x00110680,0x7B825F71,0x7B866A12)
7B866A12 KERNEL32.dll <unknown symbol>+0 (0x7BCBDFF4,0xBF89A8B0,0xBF89A8E8,0x7BC5467B)
7BC5467B ntdll.dll    <unknown symbol>+0 (0x7C405290,0xB774943D,0xBF89A98C,0x00000400)
B762CA4C              <unknown symbol>+0 (0x00000003,0xBF89AE44,0xBF89A98C,0x00000400)
7BF00D0B              <unknown symbol>+0 (0x00000003,0xBF89AE44,0xBF89AE54,0xB776B920)
B74684D3              <unknown symbol>+0 (0x7BC43387,0x7BC43387,0x7BC43387,0x7BC43387)




----------------------------------------
    Loaded Modules
----------------------------------------


DBG-MODULE<00400000 005e0000 "Agent.exe" "Agent.pdb" 0 {a6ad3dd9-3d35-4238-a5fa10bf829cbad8} 4 1364252864>
DBG-MODULE<7B810000 00235000 "KERNEL32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7BC10000 000ca000 "ntdll.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7D900000 00098000 "msvcrt.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7D9A0000 00060000 "dbghelp.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7DD10000 00008000 "psapi.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7DD40000 00019000 "hnetcfg.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7DDB0000 00025000 "uxtheme.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7DFD0000 00087000 "winex11.drv" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E1B0000 00037000 "winhttp.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E1F0000 0000c000 "mswsock.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E210000 0005b000 "setupapi.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E280000 00124000 "oleaut32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E3C0000 0011f000 "ole32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E4F0000 00070000 "rpcrt4.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E570000 000f8000 "comctl32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E680000 00217000 "shell32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E8A0000 00070000 "shlwapi.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E920000 0000a000 "version.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E940000 00105000 "gdi32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7EA60000 0013f000 "user32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7EBB0000 00016000 "mpr.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7EBF0000 00066000 "wininet.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7EC60000 00065000 "advapi32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7ECD0000 0001b000 "iphlpapi.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7ECF0000 00028000 "netapi32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7ED40000 00010000 "dnsapi.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7ED60000 00026000 "ws2_32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>


----------------------------------------
    Memory Dump
----------------------------------------


Code: 16 bytes starting at (EIP = 7B83BC25)


7B83BC25: 8B 4D F0 8B  5D F4 8B 75  F8 8B 7D FC  83 EC 04 89  .M..]..u..}.....




Stack: 1024 bytes starting at (ESP = 0250DD34)


0250DD34: D8 DD 50 02  0C 00 00 00  00 00 9E 00  63 73 6D E0  ..P.........csm.
0250DD44: 01 00 00 00  00 00 00 00  25 BC 83 7B  03 00 00 00  ........%..{....
0250DD54: 20 05 93 19  44 DE 50 02  B8 B2 8A 00  B8 44 AB 00   ...D.P......D..
0250DD64: FC DD 50 02  44 DE 50 02  80 DD 50 02  46 02 77 00  ..P.D.P...P.F.w.
0250DD74: B8 44 AB 00  FC DD 50 02  FC DD 50 02  44 DE 50 02  .D....P...P.D.P.
0250DD84: FC DD 50 02  B8 DD 50 02  2D 28 40 00  10 DE 50 02  ..P...P.-(@...P.
0250DD94: 00 00 00 00  B4 DD 50 02  A8 DF 50 02  FC DD 50 02  ......P...P...P.
0250DDA4: 18 07 96 00  E4 DD 50 02  BC 4B 77 00  BC 4B 77 00  ......P..Kw..Kw.
0250DDB4: 63 73 6D E0  01 00 00 00  03 00 00 00  D8 DD 50 02  csm...........P.
0250DDC4: 63 73 6D E0  01 00 00 00  00 00 00 00  00 00 00 00  csm.............
0250DDD4: 03 00 00 00  20 05 93 19  44 DE 50 02  B8 B2 8A 00  .... ...D.P.....
0250DDE4: 9C DE 50 02  B6 26 40 00  44 DE 50 02  B8 B2 8A 00  ..P..&@.D.P.....
0250DDF4: 4C 45 2C 34  49 27 00 00  4C 04 83 00  B8 44 AB 00  LE,4I'..L....D..
0250DE04: 01 00 00 00  49 27 00 00  18 07 96 00  00 00 00 00  ....I'..........
0250DE14: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0250DE24: 0F 00 00 00  00 00 00 00  58 04 83 00  00 00 00 00  ........X.......
0250DE34: 00 00 00 00  00 00 00 00  FF FF FF FF  10 00 00 00  ................
0250DE44: 60 04 83 00  10 AC AF 04  01 35 77 00  49 27 00 00  `........5w.I'..
0250DE54: 18 07 96 00  00 00 9E 00  00 00 00 00  10 00 00 00  ................
0250DE64: B4 DE 50 02  00 00 00 00  0F 00 00 00  CF 01 77 00  ..P...........w.
0250DE74: 6C 04 83 00  00 00 00 00  00 00 00 00  00 00 00 00  l...............
0250DE84: FF FF FF FF  74 04 83 00  1A 02 77 00  EC DE 50 02  ....t.....w...P.
0250DE94: FB DF 7A 00  00 00 00 00  F8 DE 50 02  13 15 40 00  ..z.......P...@.
0250DEA4: 78 45 2C 34  00 00 00 00  A8 DF 50 02  D4 B8 88 00  xE,4......P.....
0250DEB4: 00 04 83 00  F8 62 B6 04  01 DE 50 02  49 27 00 00  .....b....P.I'..
0250DEC4: 18 07 96 00  00 DF 50 02  6A 57 72 00  1C 00 00 00  ......P.jWr.....
0250DED4: 02 00 00 00  00 00 00 00  0F 00 00 00  00 00 00 00  ................
0250DEE4: 60 45 2C 34  00 00 00 00  04 E0 50 02  30 E0 7A 00  `E,4......P.0.z.
0250DEF4: 01 00 00 00  10 DF 50 02  C9 56 72 00  04 DF 50 02  ......P..Vr...P.
0250DF04: 49 27 00 00  18 07 96 00  00 00 00 00  38 DF 50 02  I'..........8.P.
0250DF14: D7 55 72 00  DC 0E B0 04  00 00 00 00  34 82 BF 00  .Ur.........4...
0250DF24: F4 E4 B6 04  01 00 00 00  04 E0 50 02  F5 73 7A 00  ..........P..sz.
0250DF34: 00 00 00 00  10 E0 50 02  A9 8C 68 00  A8 DF 50 02  ......P...h...P.
0250DF44: C0 7B 2C 34  92 6A 24 00  54 C8 75 03  F4 E4 B6 04  .{,4.j$.T.u.....
0250DF54: 40 E1 50 02  FC 53 AC 00  01 44 2C 34  01 00 00 00  @.P..S...D,4....
0250DF64: 00 00 F2 00  00 40 00 00  B4 4E A8 00  92 6A 00 00  .....@...N...j..
0250DF74: D4 0E B0 04  C4 49 B2 04  F7 3F 71 00  34 82 BF 00  .....I...?q.4...
0250DF84: 74 44 2C 34  00 00 00 00  0F 00 00 00  64 DF 50 02  tD,4........d.P.
0250DF94: 00 DF 50 02  E4 DF 50 02  04 E0 50 02  8A 85 70 00  ..P...P...P...p.
0250DFA4: 00 00 00 00  02 00 00 00  00 00 00 00  00 00 00 00  ................
0250DFB4: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0250DFC4: 18 07 96 00  00 00 00 00  20 44 2C 34  80 E3 50 02  ........ D,4..P.
0250DFD4: F4 E4 B6 04  92 6A 00 00  54 C8 75 03  78 5B A8 00  .....j..T.u.x[..
0250DFE4: 10 E0 50 02  89 0B 72 00  FC DF 50 02  54 C8 75 03  ..P...r...P.T.u.
0250DFF4: 92 6A 24 00  F4 E4 B6 04  C0 7B 2C 34  92 6A 00 00  .j$......{,4.j..
0250E004: 0C E1 50 02  B7 B1 7D 00  00 00 00 00  18 E1 50 02  ..P...}.......P.
0250E014: F5 84 70 00  F4 E4 B6 04  F0 7B 2C 34  F4 E4 B6 04  ..p......{,4....
0250E024: 3C 51 AC 00  80 E3 50 02  20 00 00 00  34 82 BF 00  <Q....P. ...4...
0250E034: 6C F3 AA 00  FC 53 AC 00  01 00 00 00  4C E1 50 02  l....S......L.P.
0250E044: C4 CD AF 04  38 A5 36 8F  03 00 00 00  5A E2 67 00  ....8.6.....Z.g.
0250E054: 00 00 3C 00  CE FF FF FF  00 00 00 00  92 6A 24 00  ..<..........j$.
0250E064: 54 C8 75 03  00 00 00 00  00 00 00 00  8A E2 67 00  T.u...........g.
0250E074: F4 DF 50 02  00 00 00 00  00 00 00 00  00 00 00 00  ..P.............
0250E084: 00 C1 5C 03  00 00 00 00  00 00 00 00  00 00 00 00  ..\.............
0250E094: 00 00 00 00  0F 00 00 00  08 E1 50 02  0F 00 00 00  ..........P.....
0250E0A4: 00 00 B8 9B  01 00 00 00  D5 8D 70 12  00 00 00 00  ..........p.....
0250E0B4: 00 00 00 00  00 00 00 00  93 75 C3 7B  00 00 00 00  .........u.{....
0250E0C4: 00 00 00 00  00 00 00 00  7D 76 C3 7B  00 00 00 00  ........}v.{....
0250E0D4: 00 00 00 00  F8 E0 50 02  C8 53 AC 00  F8 E0 50 02  ......P..S....P.
0250E0E4: C8 53 AC 00  24 E1 50 02  D4 BF 71 00  0F 00 00 00  .S..$.P...q.....
0250E0F4: D4 BF 71 00  C8 53 AC 00  F4 7A 2C 34  F4 E4 B6 04  ..q..S...z,4....
0250E104: 80 E3 50 02  F0 D4 5B 03  48 E1 50 02  39 D2 7F 00  ..P...[.H.P.9...
0250E114: 08 00 00 00  54 E1 50 02  04 78 70 00  F4 E4 B6 04  ....T.P..xp.....
0250E124: 80 E3 50 02  40 E1 50 02  84 7A 2C 34  08 E2 50 02  ..P.@.P..z,4..P.




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
Processor Revision:     3846
Os Version:             5.1
Os Service Pack:        3.0
Os Bit Size:            32

```

I'm not sure how to fix this or anything, if anyone could help it would be greatly appreciated. 

I'm running the newest wine version, under xp with pulseaudio. stock drivers for everything.

---

