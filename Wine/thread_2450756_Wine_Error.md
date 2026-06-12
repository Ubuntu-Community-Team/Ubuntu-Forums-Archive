---
title: "Wine Error"
date: 2020-09-20
forum: Wine
---

### Post by cesurabdurrahman on 2020-09-20
[COLOR=#000000]I am using Linux Lite 5.0 (Ubuntu 20.04). I get this error when I try to install something via wine


```
[/COLOR][COLOR=#000000][FONT=&quot]Unhandled exception: page fault on read access to 0x02fa03e2 in 32-bit code (0x009718d6).Register dump:[/FONT][/COLOR]
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:009718d6 ESP:0032fc2c EBP:0293a0fc EFLAGS:00210206(  R- --  I   - -P- )
 EAX:02fa004e EBX:7b420000 ECX:00000001 EDX:000000e5
 ESI:7b420040 EDI:028b0000
Stack dump:
0x0032fc2c:  027b0050 00bf1501 0000006d 003200e5
0x0032fc3c:  0008a0fc 7b430aa0 0096e501 00253000
0x0032fc4c:  000004b5 0032fc98 00bf15c8 7b420000
0x0032fc5c:  00bf15d4 0097dd4e 0032fcc0 0097ddf4
0x0032fc6c:  0032fc98 fffffffe 00000000 00000000
0x0032fc7c:  00000000 00000000 027b0050 027b000c
Backtrace:
=>0 0x009718d6 EntryPoint+0xffffffff() in kutuphane_3akvyyzt (0x0293a0fc)
  1 0x00650020 EntryPoint+0xffffffff() in kutuphane_3akvyyzt (0x00650063)
0x009718d6 EntryPoint+0xffffffff in kutuphane_3akvyyzt: movl	0x0(%eax,%edx,4),%ebp
Modules:
Module	Address			Debug info	Name (36 modules)
PE	  400000- 1f30000	Export          kutuphane_3akvyyzt
PE	7a840000-7a844000	Deferred        opengl32
PE	7b020000-7b023000	Deferred        kernelbase
PE	7b420000-7b5db000	Deferred        kernel32
PE	7bc30000-7bc34000	Deferred        ntdll
PE	7c6a0000-7c6a4000	Deferred        uxtheme
PE	7c740000-7c74f000	Deferred        setupapi
PE	7c9b0000-7c9b4000	Deferred        winex11
PE	7cd90000-7cd99000	Deferred        msacm32
PE	7cdd0000-7ce4d000	Deferred        winmm
PE	7ce90000-7ce96000	Deferred        winhttp
PE	7cee0000-7cee4000	Deferred        ws2_32
PE	7cf10000-7cf1b000	Deferred        mpr
PE	7cf60000-7cf65000	Deferred        jsproxy
PE	7cf90000-7cfaf000	Deferred        wininet
PE	7d030000-7d042000	Deferred        urlmon
PE	7d100000-7d108000	Deferred        oleaut32
PE	7d220000-7d224000	Deferred        ddraw
PE	7d2d0000-7d2d4000	Deferred        wined3d
PE	7d430000-7d434000	Deferred        d3d9
PE	7d470000-7d47b000	Deferred        winspool
PE	7d4e0000-7d4e4000	Deferred        rpcrt4
PE	7d590000-7d5b8000	Deferred        ole32
PE	7d710000-7d714000	Deferred        iphlpapi
PE	7d730000-7d733000	Deferred        shcore
PE	7d760000-7d768000	Deferred        shlwapi
PE	7d7f0000-7e0c6000	Deferred        shell32
PE	7e1e0000-7e2c2000	Deferred        comdlg32
PE	7e320000-7e324000	Deferred        imm32
PE	7e350000-7e353000	Deferred        usp10
PE	7e3b0000-7e3b4000	Deferred        msvcrt
PE	7e480000-7e487000	Deferred        gdi32
PE	7e5f0000-7e6d8000	Deferred        user32
PE	7e830000-7e8ae000	Deferred        comctl32
PE	7e9b0000-7e9b4000	Deferred        advapi32
PE	7eff0000-7eff4000	Deferred        version
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	00000023    0
	0000001a    0
	00000015    0
	00000014    0
	00000013    0
	00000010    0
	0000000f    0
00000011 plugplay.exe
	00000017    0
	00000016    0
	00000012    0
00000018 winedevice.exe
	00000020    0
	0000001d    0
	0000001c    0
	0000001b    0
	00000019    0
0000001e explorer.exe
	00000029    0
	00000028    0
	00000026    0
	0000001f    0
00000021 winedevice.exe
	00000027    0
	00000025    0
	00000024    0
	00000022    0
0000002a (D) Z:\home\linuxlite\Masaüstü\345 Yay&#305;nc&#305;l&#305;k - Z-Kitaplar\kutuphane_3AKVYYZT.exe
	0000002e    0
	0000002b    0 <==
System information:
    Wine build: wine-5.0 (Ubuntu 5.0-3ubuntu1)
    Platform: i386 (WOW64)
    Version: Windows 7
    Host system: Linux [COLOR=#000000][FONT=&quot]    Host version: 5.4.0-42-generic[/FONT][/COLOR][COLOR=#000000]
```



[/COLOR][ATTACH=CONFIG]286995[/ATTACH]

---

### Post by jeremy31 on 2020-09-20
Duplicate of [https://ubuntuforums.org/showthread.php?t=2450717&p=13987380](https://ubuntuforums.org/showthread.php?t=2450717&p=13987380)
Thread closed

---

