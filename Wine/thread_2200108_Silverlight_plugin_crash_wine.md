---
title: "Silverlight plugin crash wine"
date: 2014-01-17
forum: Wine
---

### Post by nedkelly on 2014-01-17
Hi

I have got a, for me, strange Silverlight crash in ubuntu 13.10

I use silverlight to watch videos on Netflix. I get the same error/bug report if I use netflix-desktop or pipelight. I can play animation and video with silverlight like [http://www.iis.net/media/experiencesmoothstreaming]("http://www.iis.net/media/experiencesmoothstreaming") or [http://bubblemark.com/silverlight2.html]("http://bubblemark.com/silverlight2.html") in this pages silverlight works. But every time I try to play a DRM video the plugin crashes.

 The plugin also crashes with the same error on the danish site Filmstriben, ex [http://www.filmstriben.dk/fjernleje/film/details.aspx?filmid=2796339000]("http://www.filmstriben.dk/fjernleje/film/details.aspx?filmid=2796339000")
(Do not know if it is acceble outside Denmark)

Anyone can see what is wrong, this is the error/bug report I get???

```
Unhandled exception: page fault on write access to 0x002e006c in 32-bit code (0x7d9a03e6).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7d9a03e6 ESP:0066efa0 EBP:0066efd8 EFLAGS:00210206(  R- --  I   - -P- )
 EAX:002e006c EBX:7da01000 ECX:0066eff0 EDX:ffffffff
 ESI:002e006c EDI:00000000
Stack dump:
0x0066efa0:  00f9121c 00f92f80 0066f038 7dac8515
0x0066efb0:  00000002 00000010 7dac5e35 7dac8515
0x0066efc0:  00f9b5a8 0066eff8 0066eff0 7da01000
0x0066efd0:  001100d8 00000000 0066f028 7d98c8b7
0x0066efe0:  00000500 00000320 01018610 7d98c8b7
0x0066eff0:  002e006c 00110000 00000003 00000073
Backtrace:
=>0 0x7d9a03e6 (0x0066efd8)
  1 0x7d98c8b7 (0x0066f028)
  2 0x7d99c6dd (0x0066f108)
  3 0x7dad77e0 (0x0066f158)
  4 0x7dac838a (0x0066f1a8)
  5 0x7d91ad5c (0x0066f268)
  6 0x7dad1e86 (0x0066f448)
  7 0x7dad2549 (0x0066f4b8)
  8 0x0026645a in npctrl (+0x26459) (0x0066f4f0)
  9 0x00266545 in npctrl (+0x26544) (0x0066f508)
  10 0x002665c8 in npctrl (+0x265c7) (0x0066f56c)
  11 0x002662df in npctrl (+0x262de) (0x0066f598)
  12 0x00258293 in npctrl (+0x18292) (0x0066f5ac)
  13 0x002654a7 in npctrl (+0x254a6) (0x0066f5f0)
  14 0x002655b5 in npctrl (+0x255b4) (0x0066f61c)
  15 0x007812be in agcore (+0x1112bd) (0x0066f648)
  16 0x007813e1 in agcore (+0x1113e0) (0x0066f660)
  17 0x0078143d in agcore (+0x11143c) (0x0066f670)
  18 0x0078147f in agcore (+0x11147e) (0x0066f69c)
  19 0x0026df8e in npctrl (+0x2df8d) (0x0066f6c0)
  20 0x0026db75 in npctrl (+0x2db74) (0x0066f6dc)
  21 0x0026dbc8 in npctrl (+0x2dbc7) (0x0066f6fc)
  22 0x0026de90 in npctrl (+0x2de8f) (0x0066f714)
  23 0x0026dec0 in npctrl (+0x2debf) (0x0066f724)
  24 0x00269abd in npctrl (+0x29abc) (0x0066f748)
  25 0x002e0fab in npctrl (+0xa0faa) (0x0066f78c)
  26 0x002e0e8e in npctrl (+0xa0e8d) (0x0066f7a4)
  27 0x002d9cbb in npctrl (+0x99cba) (0x0066f7d0)
  28 0x002d8a2d in npctrl (+0x98a2c) (0x0066f808)
  29 0x0040c333 in pluginloader (+0xc332) (0x0066fb98)
  30 0x00402147 in pluginloader (+0x2146) (0x0066fbf8)
  31 0x0040a955 in pluginloader (+0xa954) (0x0066fd88)
  32 0x004013da __tmainCRTStartup+0x259() [/build/buildd/mingw-w64-3.0~svn5915/build/i686-w64-mingw32-i686-w64-mingw32-crt/../../mingw-w64-crt/crt/crtexe.c:332] in pluginloader (0x0066fe60)
  33 0x7b85ed0c in kernel32 (+0x4ed0b) (0x0066fe78)
  34 0x7b85fd93 in kernel32 (+0x4fd92) (0x0066feb8)
  35 0x7bc7dfb0 (0x0066fed8)
  36 0x7bc80f3d (0x0066ffa8)
  37 0x7bc7df8e (0x0066ffc8)
  38 0x7bc5219e (0x0066ffe8)
0x7d9a03e6: lock xaddl	%edx,0x0(%esi)
Modules:
Module	Address			Debug info	Name (33 modules)
PE	  240000-  371000	Export          npctrl
PE	  400000-  462000	Dwarf           pluginloader
PE	  670000-  d56000	Export          agcore
PE	7b810000-7b9ad000	Export          kernel32
PE	7bc10000-7bc14000	Deferred        ntdll
PE	7d7d0000-7d7d4000	Deferred        opengl32
PE	7d8d0000-7d8d4000	Deferred        wined3d
PE	7dac0000-7dac4000	Deferred        d3d9
PE	7db00000-7db04000	Deferred        uxtheme
PE	7db30000-7db34000	Deferred        iphlpapi
PE	7db50000-7db53000	Deferred        netapi32
PE	7db90000-7dbd0000	Deferred        crypt32
PE	7dc50000-7dc54000	Deferred        ws2_32
PE	7dc90000-7dc94000	Deferred        psapi
PE	7dca0000-7dcb1000	Deferred        urlmon
PE	7dd40000-7dd4a000	Deferred        mpr
PE	7dd70000-7dd88000	Deferred        wininet
PE	7dde0000-7dde9000	Deferred        msacm32
PE	7de10000-7de86000	Deferred        winmm
PE	7dee0000-7dee8000	Deferred        oleaut32
PE	7e000000-7e02f000	Deferred        comctl32
PE	7e110000-7e118000	Deferred        shlwapi
PE	7e180000-7e2de000	Deferred        shell32
PE	7e3b0000-7e3b4000	Deferred        imm32
PE	7e5e0000-7e5e3000	Deferred        msimg32
PE	7e5f0000-7e5f4000	Deferred        winex11
PE	7e820000-7e824000	Deferred        rpcrt4
PE	7e8a0000-7e8a4000	Deferred        version
PE	7e8c0000-7e8c7000	Deferred        gdi32
PE	7e9e0000-7ea1b000	Deferred        user32
PE	7eb40000-7eb48000	Deferred        ole32
PE	7ec80000-7ec84000	Deferred        msvcrt
PE	7ed20000-7ed24000	Deferred        advapi32
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	0000001e    0
	0000001d    0
	00000019    0
	00000016    0
	00000014    0
	00000010    0
	0000000f    0
00000012 winedevice.exe
	0000001c    0
	00000018    0
	00000017    0
	00000013    0
0000001a plugplay.exe
	00000020    0
	0000001f    0
	0000001b    0
00000021 explorer.exe
	00000022    0
00000027 pluginloader.exe
	00000028    0
00000029 (D) Z:\usr\share\pipelight\pluginloader.exe
	0000002b    0
	0000002a    0 <==
0000002e pluginloader.exe
	0000002f    0
System information:
    Wine build: wine-1.7.10
    Platform: i386
    Host system: Linux
    Host version: 3.11.0-15-generic

```

---

### Post by Mark Phelps on 2014-01-19
You won't be able to play DRM-protected media in Wine because the DRM features are not there.

---

### Post by jbahn on 2014-10-12
Nedkelly

Did you solve the problem - if so, I would lve to hear, as I've got the same issue.

---

### Post by coffeecat on 2014-10-13
Thread is about 13.10, now end-of-life and unsupported, so thread closed.

@jbahn, this is the second time you have posted to an old thread which is to do with a now unsupported version of Ubuntu. Please start your own thread in an appropriate sub-forum giving full details of your problem and detailing which version of Ubuntu you are using.

---

