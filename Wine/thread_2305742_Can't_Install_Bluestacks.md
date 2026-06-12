---
title: "Can't Install Bluestacks"
date: 2015-12-08
forum: Wine
---

### Post by Darth4212 on 2015-12-08
I am trying to install Bluestacks and when I start it says ```
The program rundll32.exe has encountered a serious problem and needs to close. We are sorry for the inconvience
```
I then click on "Show Details" and it says 
```
Unhandled exception: page fault on read access to 0x7d9bedc8 in 32-bit code (0x10001025).Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:10001025 ESP:0033f564 EBP:0033f588 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:7d9bed80 EBX:00000000 ECX:0033f57c EDX:00000000
 ESI:0033f834 EDI:00148028
Stack dump:
0x0033f564:  00148028 0033f57c 00000002 0033f834
0x0033f574:  00000001 0033f616 00000000 00000000
0x0033f584:  92e32251 0033fc70 10002544 00000002
0x0033f594:  00148028 1001e2f8 0033f834 0033fa3c
0x0033f5a4:  0033f5c0 00220728 00000000 00220748
0x0033f5b4:  00220748 0033fa3c 00000643 000008b8
000c: sel=0067 base=00000000 limit=00000000 32-bit r-x
Backtrace:
=>0 0x10001025 in msia752.tmp (+0x1025) (0x0033f588)
  1 0x10002544 in msia752.tmp (+0x2543) (0x0033fc70)
  2 0x10003b71 in msia752.tmp (+0x3b70) (0x0033fcb8)
  3 0x7effccf6 wWinMain+0x2d5() in rundll32 (0x0033fd68)
  4 0x7effd3ec wmain+0xdb() in rundll32 (0x0033fe08)
  5 0x7effd2f4 in rundll32 (+0xd2f3) (0x0033fe48)
  6 0x7b85a72c call_process_entry+0xb() in kernel32 (0x0033fe68)
  7 0x7b85b73a in kernel32 (+0x4b739) (0x0033fe98)
  8 0x7bc74e90 call_thread_func_wrapper+0xb() in ntdll (0x0033feb8)
  9 0x7bc77c2f call_thread_func+0xce() in ntdll (0x0033ffa8)
  10 0x7bc74e6e RtlRaiseException+0x21() in ntdll (0x0033ffc8)
  11 0x7bc4cca7 call_dll_entry_point+0x756() in ntdll (0x0033ffe8)
  12 0xf752a15d wine_call_on_stack+0x1c() in libwine.so.1 (0x00000000)
  13 0xf752a2d0 wine_switch_to_stack+0x1f() in libwine.so.1 (0xffa19868)
  14 0x7bc520e7 LdrInitializeThunk+0x336() in ntdll (0xffa198c8)
  15 0x7b861333 __wine_kernel_init+0x872() in kernel32 (0xffa1aa28)
  16 0x7bc52663 __wine_process_init+0x162() in ntdll (0xffa1aaa8)
  17 0xf7527dc7 wine_init+0x306() in libwine.so.1 (0xffa1ab08)
  18 0x7bf00d52 main+0x81() in <wine-loader> (0xffa1af58)
  19 0xf732672e __libc_start_main+0xdd() in libc.so.6 (0x00000000)
0x10001025: call	*0x48(%eax)
Modules:
Module	Address			Debug info	Name (93 modules)
PE	10000000-1002e000	Export          msia752.tmp
PE	6d500000-6df26000	Deferred        libmono-2.0-x86
ELF	79f48000-7b800000	Deferred        libicudata.so.55
ELF	7b800000-7ba55000	Dwarf           kernel32<elf>
  \-PE	7b810000-7ba55000	\               kernel32
ELF	7bc00000-7bcd9000	Dwarf           ntdll<elf>
  \-PE	7bc10000-7bcd9000	\               ntdll
ELF	7bf00000-7bf04000	Dwarf           <wine-loader>
ELF	7d129000-7d153000	Deferred        msacm32<elf>
  \-PE	7d130000-7d153000	\               msacm32
ELF	7d153000-7d20b000	Deferred        winmm<elf>
  \-PE	7d160000-7d20b000	\               winmm
ELF	7d20b000-7d240000	Deferred        ws2_32<elf>
  \-PE	7d210000-7d240000	\               ws2_32
ELF	7d240000-7d2ed000	Deferred        msvcrt<elf>
  \-PE	7d250000-7d2ed000	\               msvcrt
ELF	7d2ed000-7d332000	Deferred        libxslt.so.1
ELF	7d332000-7d350000	Deferred        libgcc_s.so.1
ELF	7d4c7000-7d65d000	Deferred        libicuuc.so.55
ELF	7d65d000-7d838000	Deferred        libxml2.so.2
ELF	7d85d000-7d872000	Deferred        mswsock<elf>
  \-PE	7d860000-7d872000	\               mswsock
ELF	7d872000-7d92a000	Deferred        msxml3<elf>
  \-PE	7d880000-7d92a000	\               msxml3
ELF	7dac3000-7daf9000	Deferred        uxtheme<elf>
  \-PE	7dad0000-7daf9000	\               uxtheme
ELF	7daf9000-7db70000	Deferred        wininet<elf>
  \-PE	7db00000-7db70000	\               wininet
ELF	7dbe4000-7dc05000	Deferred        cabinet<elf>
  \-PE	7dbf0000-7dc05000	\               cabinet
ELF	7dc05000-7dc2c000	Deferred        mpr<elf>
  \-PE	7dc10000-7dc2c000	\               mpr
ELF	7dc2c000-7dd24000	Deferred        comctl32<elf>
  \-PE	7dc30000-7dd24000	\               comctl32
ELF	7dd24000-7dd9a000	Deferred        shlwapi<elf>
  \-PE	7dd30000-7dd9a000	\               shlwapi
ELF	7dd9a000-7dfc3000	Deferred        shell32<elf>
  \-PE	7ddb0000-7dfc3000	\               shell32
ELF	7dfc3000-7e0ee000	Deferred        oleaut32<elf>
  \-PE	7dfe0000-7e0ee000	\               oleaut32
ELF	7e0ee000-7e16a000	Deferred        rpcrt4<elf>
  \-PE	7e100000-7e16a000	\               rpcrt4
ELF	7e16a000-7e297000	Deferred        ole32<elf>
  \-PE	7e180000-7e297000	\               ole32
ELF	7e297000-7e332000	Deferred        urlmon<elf>
  \-PE	7e2a0000-7e332000	\               urlmon
ELF	7e332000-7e41e000	Deferred        msi<elf>
  \-PE	7e340000-7e41e000	\               msi
ELF	7e41e000-7e442000	Deferred        imm32<elf>
  \-PE	7e420000-7e442000	\               imm32
ELF	7e464000-7e46b000	Deferred        libxfixes.so.3
ELF	7e46b000-7e476000	Deferred        libxcursor.so.1
ELF	7e476000-7e488000	Deferred        libxi.so.6
ELF	7e488000-7e48c000	Deferred        libxcomposite.so.1
ELF	7e48c000-7e499000	Deferred        libxrandr.so.2
ELF	7e499000-7e4a5000	Deferred        libxrender.so.1
ELF	7e4a5000-7e4ac000	Deferred        libxxf86vm.so.1
ELF	7e4ac000-7e4b0000	Deferred        libxinerama.so.1
ELF	7e4b0000-7e4b7000	Deferred        libxdmcp.so.6
ELF	7e4b7000-7e4bb000	Deferred        libxau.so.6
ELF	7e4bb000-7e4e0000	Deferred        libxcb.so.1
ELF	7e4e0000-7e62b000	Deferred        libx11.so.6
ELF	7e62b000-7e640000	Deferred        libxext.so.6
ELF	7e640000-7e654000	Deferred        psapi<elf>
  \-PE	7e650000-7e654000	\               psapi
ELF	7e67a000-7e707000	Deferred        winex11<elf>
  \-PE	7e680000-7e707000	\               winex11
ELF	7e75b000-7e784000	Deferred        libexpat.so.1
ELF	7e784000-7e7c7000	Deferred        libfontconfig.so.1
ELF	7e7c7000-7e7f3000	Deferred        libpng12.so.0
ELF	7e7f3000-7e80e000	Deferred        libz.so.1
ELF	7e80e000-7e8bb000	Deferred        libfreetype.so.6
ELF	7e8f5000-7e963000	Deferred        advapi32<elf>
  \-PE	7e900000-7e963000	\               advapi32
ELF	7e963000-7ea7b000	Deferred        gdi32<elf>
  \-PE	7e970000-7ea7b000	\               gdi32
ELF	7ea7b000-7ebc9000	Deferred        user32<elf>
  \-PE	7ea90000-7ebc9000	\               user32
ELF	7ebc9000-7ebd7000	Deferred        libnss_files.so.2
ELF	7ebd7000-7ebe4000	Deferred        libnss_nis.so.2
ELF	7ebe4000-7ebff000	Deferred        libnsl.so.1
ELF	7ebff000-7ec09000	Deferred        libnss_compat.so.2
ELF	7ef79000-7efc6000	Deferred        libm.so.6
ELF	7efd2000-7efeb000	Deferred        version<elf>
  \-PE	7efe0000-7efeb000	\               version
ELF	7efeb000-7f000000	Dwarf           rundll32<elf>
  \-PE	7eff0000-7f000000	\               rundll32
ELF	f7309000-f730e000	Deferred        libdl.so.2
ELF	f730e000-f74c9000	Dwarf           libc.so.6
ELF	f74ca000-f74e7000	Deferred        libpthread.so.0
ELF	f7521000-f76d7000	Dwarf           libwine.so.1
ELF	f76d9000-f76fd000	Deferred        ld-linux.so.2
ELF	f76ff000-f7700000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	0000001e    0
	0000001d    0
	00000014    0
	00000010    0
	0000000f    0
00000012 winedevice.exe
	0000001c    0
	00000019    0
	00000017    0
	00000013    0
0000001a plugplay.exe
	00000020    0
	0000001f    0
	0000001b    0
00000022 explorer.exe
	00000024    0
	00000023    0
00000028 BlueStacks-ThinInstaller_0.10.7.5601.exe
	0000002a    0
	00000029    0
0000002c BlueStacks-ThinInstaller_0.10.7.5601.exe
	00000031    0
	00000030    0
	0000002e    0
	0000002d    0
00000032 msiexec.exe
	00000035    0
	00000034    0
	00000033    0
00000036 (D) C:\windows\system32\rundll32.exe
	00000037    0 <==
System information:
    Wine build: wine-1.6.2
    Platform: i386
    Host system: Linux
    Host version: 4.2.0-19-generic
```

---

