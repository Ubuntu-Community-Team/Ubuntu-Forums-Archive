---
title: "Question/trouble w/gamehouse game"
date: 2013-01-27
forum: Wine
---

### Post by DougieFresh4U on 2013-01-27
It has been a few years since I have brought this issue up again, so here goes:
I purchased a game from** GameHouse** (Mah Jong Medley) back in 2005. I has run using wine and I believe it was Edgy/Fiesty Ubuntu 32 bit versions.
Ever since I have been using a 64 bit machines and cannot get it to run.
I am begining to think that 64 bit is the issue.
Tried installing today and I will post the error output I get.
Would be great if anyone can come up with a solution for me to play this
once again on my Ubuntu machine
Thanks
```
**Unhandled exception: page fault on read access to 0x3ff00000 in 32-bit code (0x7b84fa77)**.
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7b84fa77 ESP:0033f400 EBP:0033f464 EFLAGS:00010286(  R- --  I S - -P- )
 EAX:0033f5a4 EBX:7b8a2ff4 ECX:0033f4cc EDX:3ff00000
 ESI:ffffffff EDI:00000000
Stack dump:
0x0033f400:  00110060 0033f558 7e7b552d 7e7b7f1f
0x0033f410:  7e88d264 0033f558 0033f4a8 7dded04e
0x0033f420:  00782ea0 00000000 00110000 00000002
0x0033f430:  00001302 00782ea8 00000000 00000000
0x0033f440:  00000000 00000000 00000000 0074c000
0x0033f450:  00782eb8 3ff00000 00000000 80020009
Backtrace:
=>0 0x7b84fa77 WideCharToMultiByte+0x197() in kernel32 (0x0033f464)
  1 0x0034b7e7 in luacom (+0xb7e6) (0x0033f4d8)
  2 0x00345945 in luacom (+0x5944) (0x0033f5b0)
  3 0x00344c21 in luacom (+0x4c20) (0x0033f630)
0x7b84fa77 WideCharToMultiByte+0x197 in kernel32: cmpw	$0,0x0(%edx)
Modules:
Module	Address			Debug info	Name (91 modules)
PE	  340000-  364000	Export          luacom
PE	  380000-  386000	Deferred        core
PE	  400000-  41c000	Deferred        gameinstaller
PE	10000000-10017000	Export          lua50
PE	60020000-60033000	Deferred        gchrome
PE	600b0000-600c0000	Deferred        rainstallerpaths
PE	600c0000-6012c000	Deferred        installerdlg
ELF	7b800000-7ba33000	Dwarf           kernel32<elf>
  \-PE	7b810000-7ba33000	\               kernel32
ELF	7bc00000-7bcca000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcca000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7dd5d000-7dd80000	Deferred        imm32<elf>
  \-PE	7dd60000-7dd80000	\               imm32
ELF	7dd80000-7dd97000	Deferred        libresolv.so.2
ELF	7dd97000-7dd9e000	Deferred        libnss_dns.so.2
ELF	7ddbc000-7ddd7000	Deferred        wsock32<elf>
  \-PE	7ddc0000-7ddd7000	\               wsock32
ELF	7ddd7000-7ddfd000	Deferred        scrrun<elf>
  \-PE	7dde0000-7ddfd000	\               scrrun
ELF	7ddfd000-7de11000	Deferred        msimg32<elf>
  \-PE	7de00000-7de11000	\               msimg32
ELF	7de11000-7de44000	Deferred        ws2_32<elf>
  \-PE	7de20000-7de44000	\               ws2_32
ELF	7de44000-7de68000	Deferred        iphlpapi<elf>
  \-PE	7de50000-7de68000	\               iphlpapi
ELF	7de68000-7de93000	Deferred        netapi32<elf>
  \-PE	7de70000-7de93000	\               netapi32
ELF	7de93000-7deb9000	Deferred        mpr<elf>
  \-PE	7dea0000-7deb9000	\               mpr
ELF	7deb9000-7df2d000	Deferred        wininet<elf>
  \-PE	7dec0000-7df2d000	\               wininet
ELF	7df2d000-7df61000	Deferred        uxtheme<elf>
  \-PE	7df30000-7df61000	\               uxtheme
ELF	7df61000-7e05e000	Deferred        comctl32<elf>
  \-PE	7df70000-7e05e000	\               comctl32
ELF	7e05e000-7e278000	Deferred        shell32<elf>
  \-PE	7e070000-7e278000	\               shell32
ELF	7e278000-7e28c000	Deferred        psapi<elf>
  \-PE	7e280000-7e28c000	\               psapi
ELF	7e307000-7e30e000	Deferred        libxfixes.so.3
ELF	7e30e000-7e319000	Deferred        libxcursor.so.1
ELF	7e319000-7e329000	Deferred        libxi.so.6
ELF	7e329000-7e32d000	Deferred        libxcomposite.so.1
ELF	7e32d000-7e338000	Deferred        libxrandr.so.2
ELF	7e338000-7e342000	Deferred        libxrender.so.1
ELF	7e342000-7e348000	Deferred        libxxf86vm.so.1
ELF	7e348000-7e34f000	Deferred        libxdmcp.so.6
ELF	7e34f000-7e371000	Deferred        libxcb.so.1
ELF	7e371000-7e377000	Deferred        libuuid.so.1
ELF	7e377000-7e391000	Deferred        libice.so.6
ELF	7e391000-7e4c7000	Deferred        libx11.so.6
ELF	7e4c7000-7e4d9000	Deferred        libxext.so.6
ELF	7e4d9000-7e4e2000	Deferred        libsm.so.6
ELF	7e500000-7e58b000	Deferred        winex11<elf>
  \-PE	7e510000-7e58b000	\               winex11
ELF	7e5f0000-7e618000	Deferred        libexpat.so.1
ELF	7e618000-7e650000	Deferred        libfontconfig.so.1
ELF	7e650000-7e669000	Deferred        libz.so.1
ELF	7e669000-7e703000	Deferred        libfreetype.so.6
ELF	7e721000-7e790000	Deferred        shlwapi<elf>
  \-PE	7e730000-7e790000	\               shlwapi
ELF	7e790000-7e8ab000	Deferred        oleaut32<elf>
  \-PE	7e7b0000-7e8ab000	\               oleaut32
ELF	7e8ab000-7e923000	Deferred        rpcrt4<elf>
  \-PE	7e8c0000-7e923000	\               rpcrt4
ELF	7e923000-7ea38000	Deferred        ole32<elf>
  \-PE	7e940000-7ea38000	\               ole32
ELF	7ea38000-7ea9d000	Deferred        advapi32<elf>
  \-PE	7ea40000-7ea9d000	\               advapi32
ELF	7ea9d000-7eba8000	Deferred        gdi32<elf>
  \-PE	7eab0000-7eba8000	\               gdi32
ELF	7eba8000-7ecef000	Deferred        user32<elf>
  \-PE	7ebc0000-7ecef000	\               user32
ELF	7ecef000-7ed86000	Deferred        msvcrt<elf>
  \-PE	7ed00000-7ed86000	\               msvcrt
ELF	7ed86000-7ed93000	Deferred        libnss_files.so.2
ELF	7ed93000-7edad000	Deferred        libnsl.so.1
ELF	7edad000-7edb6000	Deferred        libnss_compat.so.2
ELF	7efb6000-7efe2000	Deferred        libm.so.6
ELF	7efe2000-7efe6000	Deferred        libxinerama.so.1
ELF	7efe6000-7f000000	Deferred        version<elf>
  \-PE	7eff0000-7f000000	\               version
ELF	f73b3000-f73bf000	Deferred        libnss_nis.so.2
ELF	f73c0000-f73c5000	Deferred        libdl.so.2
ELF	f73c5000-f756f000	Deferred        libc.so.6
ELF	f7570000-f758b000	Deferred        libpthread.so.0
ELF	f758c000-f7590000	Deferred        libxau.so.6
ELF	f75a9000-f76eb000	Dwarf           libwine.so.1
ELF	f76ed000-f770f000	Deferred        ld-linux.so.2
ELF	f770f000-f7710000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	0000001f    0
	0000001e    0
	00000018    0
	00000017    0
	00000015    0
	00000010    0
	0000000f    0
00000012 winedevice.exe
	0000001a    0
	00000019    0
	00000014    0
	00000013    0
0000001b plugplay.exe
	00000020    0
	0000001d    0
	0000001c    0
00000021 explorer.exe
	00000022    0
00000023 GameHouse-Installer_am-mahjongmedley_gamehouse_.exe
	00000024    0
00000025 bstrapinstall.exe
	00000026    0
00000029 (D) C:\users\dougie\Temp\RarSFX0\bin\gameinstaller.exe
	0000002a    0 <==
System information:
    Wine build: wine-1.5.22
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 3.7.1-030701-generic
```

---

