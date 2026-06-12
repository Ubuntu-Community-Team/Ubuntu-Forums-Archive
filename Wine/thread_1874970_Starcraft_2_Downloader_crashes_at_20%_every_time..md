---
title: "Starcraft 2 Downloader crashes at 20% every time."
date: 2011-11-04
forum: Wine
---

### Post by kanazky on 2011-11-04
My blizzard downloader works fine for about 20% then it crashes every time.

I have wine, playonlinux (aur), winetricks. Ive installed many fonts, vc2008 vc2005 vc2005express, wine_gekco.

I have setup the mad audio trick.

The process goes zombie and does nothing till I force it to quit.

Anyone had this problem and know of a fix?

Currently:
Gnome 3
GDM

---

### Post by kanazky on 2011-11-04
Here is the output when it fails:
> 
wine: Unhandled page fault on read access to 0x8356804a at address 0x7eda0dfc (thread 003f), starting debugger...
Unhandled exception: page fault on read access to 0x8356804a in 32-bit code (0x7eda0dfc).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7eda0dfc ESP:00a5a528 EBP:00a5a590 EFLAGS:00010212(  R- --  I   -A- - )
 EAX:00000002 EBX:7edd9ff4 ECX:0000f840 EDX:8356804a
 ESI:029d0988 EDI:00002087
Stack dump:
0x00a5a528:  00a5a694 029d0a40 00002087 7edc632f
0x00a5a538:  00000005 03281448 00000028 00000000
0x00a5a548:  00000000 0000000e 7bcb5ff4 00a5a694
0x00a5a558:  00000002 01a5a5ac 00000000 029d0a14
0x00a5a568:  7edd9ff4 00a5a5bc 00000000 00000000
0x00a5a578:  f7619e20 00000000 7bc373d1 7edd9ff4
Backtrace:
=>0 0x7eda0dfc in wininet (+0x10dfc) (0x00a5a590)
  1 0x7eda14be in wininet (+0x114bd) (0x00a5a620)
  2 0x7edb44b6 InternetReadFileExA+0x65() in wininet (0x00a5a670)
  3 0x004261e3 in installer (+0x261e2) (0x00a5e9d0)
  4 0x00438e96 in installer (+0x38e95) (0x7b86c650)
0x7eda0dfc: movl	0x0(%edx),%ecx
Modules:
Module	Address			Debug info	Name (116 modules)
PE	  400000-  546000	Export          installer
PE	 1040000- 112a000	Deferred        nss3
PE	61700000-61782000	Deferred        mozsqlite3
PE	61e40000-61e4c000	Deferred        mozalloc
PE	622c0000-622cd000	Deferred        plds4
PE	64240000-6425a000	Deferred        nssutil3
PE	64f40000-64f75000	Deferred        nspr4
PE	66680000-666a7000	Deferred        smime3
PE	69c40000-6af87000	Deferred        xul
PE	6ce40000-6ce4d000	Deferred        plc4
PE	70180000-7046f000	Deferred        mozjs
PE	70840000-70872000	Deferred        ssl3
ELF	7b800000-7b9c3000	Deferred        kernel32<elf>
  \-PE	7b810000-7b9c3000	\               kernel32
ELF	7bc00000-7bcd2000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcd2000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7d8ac000-7d8cb000	Deferred        hnetcfg<elf>
  \-PE	7d8b0000-7d8cb000	\               hnetcfg
ELF	7d8de000-7d8f3000	Deferred        t2embed<elf>
  \-PE	7d8e0000-7d8f3000	\               t2embed
ELF	7d8f3000-7d907000	Deferred        psapi<elf>
  \-PE	7d900000-7d907000	\               psapi
ELF	7d907000-7d96a000	Deferred        dbghelp<elf>
  \-PE	7d910000-7d96a000	\               dbghelp
ELF	7d96a000-7d995000	Deferred        msacm32<elf>
  \-PE	7d970000-7d995000	\               msacm32
ELF	7d995000-7da3e000	Deferred        winmm<elf>
  \-PE	7d9a0000-7da3e000	\               winmm
ELF	7da3e000-7dad9000	Deferred        msvcrt<elf>
  \-PE	7da50000-7dad9000	\               msvcrt
ELF	7dad9000-7dbf4000	Deferred        mshtml<elf>
  \-PE	7daf0000-7dbf4000	\               mshtml
ELF	7dbf4000-7dc2a000	Deferred        usp10<elf>
  \-PE	7dc00000-7dc2a000	\               usp10
ELF	7dc2a000-7dcaf000	Deferred        urlmon<elf>
  \-PE	7dc30000-7dcaf000	\               urlmon
ELF	7dce9000-7dd04000	Deferred        wsock32<elf>
  \-PE	7dcf0000-7dd04000	\               wsock32
ELF	7dd04000-7dd66000	Deferred        ieframe<elf>
  \-PE	7dd10000-7dd66000	\               ieframe
ELF	7dd66000-7dda6000	Deferred        libjpeg.so.8
ELF	7dda9000-7ddc7000	Deferred        pdh<elf>
  \-PE	7ddb0000-7ddc7000	\               pdh
ELF	7ddc7000-7de58000	Deferred        windowscodecs<elf>
  \-PE	7ddd0000-7de58000	\               windowscodecs
ELF	7de58000-7de6f000	Deferred        libresolv.so.2
ELF	7de6f000-7de76000	Deferred        libnss_dns.so.2
ELF	7de7c000-7de97000	Deferred        libgcc_s.so.1
ELF	7deda000-7df10000	Deferred        uxtheme<elf>
  \-PE	7dee0000-7df10000	\               uxtheme
ELF	7df10000-7df15000	Deferred        libxfixes.so.3
ELF	7df15000-7df1e000	Deferred        libxcursor.so.1
ELF	7df4f000-7df78000	Deferred        libexpat.so.1
ELF	7df78000-7dfa6000	Deferred        libfontconfig.so.1
ELF	7dfa6000-7dfb3000	Deferred        libxi.so.6
ELF	7dfb3000-7dfba000	Deferred        libxrandr.so.2
ELF	7dfba000-7dfc2000	Deferred        libxrender.so.1
ELF	7dfc2000-7dfc7000	Deferred        libxxf86vm.so.1
ELF	7dfc7000-7dfeb000	Deferred        imm32<elf>
  \-PE	7dfd0000-7dfeb000	\               imm32
ELF	7dfeb000-7e003000	Deferred        libxcb.so.1
ELF	7e003000-7e01a000	Deferred        libice.so.6
ELF	7e01a000-7e152000	Deferred        libx11.so.6
ELF	7e152000-7e160000	Deferred        libxext.so.6
ELF	7e160000-7e210000	Deferred        winex11<elf>
  \-PE	7e170000-7e210000	\               winex11
ELF	7e210000-7e220000	Deferred        libbz2.so.1.0
ELF	7e220000-7e2b9000	Deferred        libfreetype.so.6
ELF	7e2da000-7e3e6000	Deferred        oleaut32<elf>
  \-PE	7e2f0000-7e3e6000	\               oleaut32
ELF	7e3e6000-7e41a000	Deferred        ws2_32<elf>
  \-PE	7e3f0000-7e41a000	\               ws2_32
ELF	7e41a000-7e43d000	Deferred        iphlpapi<elf>
  \-PE	7e420000-7e43d000	\               iphlpapi
ELF	7e43d000-7e451000	Deferred        msimg32<elf>
  \-PE	7e440000-7e451000	\               msimg32
ELF	7e451000-7e4cf000	Deferred        rpcrt4<elf>
  \-PE	7e460000-7e4cf000	\               rpcrt4
ELF	7e4cf000-7e5f6000	Deferred        ole32<elf>
  \-PE	7e4f0000-7e5f6000	\               ole32
ELF	7e5f6000-7e633000	Deferred        winspool<elf>
  \-PE	7e600000-7e633000	\               winspool
ELF	7e633000-7e733000	Deferred        comdlg32<elf>
  \-PE	7e640000-7e733000	\               comdlg32
ELF	7e733000-7e836000	Deferred        comctl32<elf>
  \-PE	7e740000-7e836000	\               comctl32
ELF	7e836000-7ea5d000	Deferred        shell32<elf>
  \-PE	7e840000-7ea5d000	\               shell32
ELF	7ea5d000-7eace000	Deferred        shlwapi<elf>
  \-PE	7ea70000-7eace000	\               shlwapi
ELF	7eace000-7eb36000	Deferred        advapi32<elf>
  \-PE	7eae0000-7eb36000	\               advapi32
ELF	7eb36000-7ebf1000	Deferred        gdi32<elf>
  \-PE	7eb40000-7ebf1000	\               gdi32
ELF	7ebf1000-7ed41000	Deferred        user32<elf>
  \-PE	7ec00000-7ed41000	\               user32
ELF	7ed41000-7ed67000	Deferred        mpr<elf>
  \-PE	7ed50000-7ed67000	\               mpr
ELF	7ed67000-7ed7c000	Deferred        libz.so.1
ELF	7ed7c000-7edf0000	Dwarf           wininet<elf>
  \-PE	7ed90000-7edf0000	\               wininet
ELF	7efb5000-7efdf000	Deferred        libm.so.6
ELF	7efe1000-7efe6000	Deferred        libxdmcp.so.6
ELF	7efe6000-7f000000	Deferred        version<elf>
  \-PE	7eff0000-7f000000	\               version
ELF	f7430000-f743d000	Deferred        libnss_files.so.2
ELF	f743f000-f7444000	Deferred        libdl.so.2
ELF	f7444000-f75c0000	Deferred        libc.so.6
ELF	f75c0000-f75db000	Deferred        libpthread.so.0
ELF	f75dd000-f75e0000	Deferred        libxau.so.6
ELF	f75f1000-f75f5000	Deferred        libuuid.so.1
ELF	f75f5000-f75fc000	Deferred        libsm.so.6
ELF	f75fc000-f7740000	Dwarf           libwine.so.1
ELF	f7741000-f7762000	Deferred        ld-linux.so.2
ELF	f7762000-f7763000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 explorer.exe
	00000009    0
0000000e services.exe
	0000003a    0
	00000039    0
	0000001d    0
	00000015    0
	00000010    0
	0000000f    0
00000012 winedevice.exe
	00000019    0
	00000014    0
	00000013    0
0000001a plugplay.exe
	0000001f    0
	0000001c    0
	0000001b    0
00000022 (D) C:\installer.exe
	00000137    0
	0000003f    0 <==
	0000003c    0
	00000038    0
	00000037    0
	00000036    0
	00000035    0
	00000034    0
	00000033    0
	00000032    0
	00000031    0
	00000030    0
	0000002f    0
	0000002e    0
	0000002b    0
	0000002a    0
	00000029    0
	00000026    0
	00000025    0
	00000024    0
	00000023    0
Backtrace:
=>0 0x7eda0dfc in wininet (+0x10dfc) (0x00a5a590)
  1 0x7eda14be in wininet (+0x114bd) (0x00a5a620)
  2 0x7edb44b6 InternetReadFileExA+0x65() in wininet (0x00a5a670)
  3 0x004261e3 in installer (+0x261e2) (0x00a5e9d0)
  4 0x00438e96 in installer (+0x38e95) (0x7b86c650)



---

