---
title: "Running Day of the tentacle remastered (15.10)"
date: 2016-03-30
forum: Wine
---

### Post by castor_fou on 2016-03-30
Hello

I have just purchased the windows version of day of the tentacle remastered, said to be working under wine.

Installation was fine but launching the game I have the following error message :

```
Unhandled exception: unimplemented function msvcr110.dll.?name@type_info@@QBEPBDPAU__type_info_node@@@Z called in 32-bit code (0x7b8395fc).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7b8395fc ESP:0033fcc4 EBP:0033fd48 EFLAGS:00000212(   - --  I   -A- - )
 EAX:7b826975 EBX:7b8af000 ECX:0033fcf0 EDX:0033fd6c
 ESI:00000004 EDI:7e619558
Stack dump:
0x0033fcc4:  7bc36556 0033fcf0 7e5f4000 7e5fd0b0
0x0033fcd4:  0000000d 0033fd28 80000100 00000001
0x0033fce4:  00000000 7b8395fc 00000002 7e619558
0x0033fcf4:  7e61cac5 7e577a51 7e59514f 7e5fd0b0
0x0033fd04:  7bc68ad6 0033fd30 7bcbc000 7bcd78a0
0x0033fd14:  7e595176 0033fd40 0033fd40 7e5f4000
000c: sel=0067 base=00000000 limit=00000000 32-bit r-x
Backtrace:
=>0 0x7b8395fc in kernel32 (+0x295fc) (0x0033fd48)
  1 0x7e619527 in msvcr110 (+0x9526) (0x0033fd80)
  2 0x7e6157d9 in msvcr110 (+0x57d8) (0x0033fdb0)
  3 0x004f3103 in dott (+0xf3102) (0x0033fdb0)
  4 0x004f2f38 in dott (+0xf2f37) (0x0033fdcc)
  5 0x00602dff in dott (+0x202dfe) (0x0033fe08)
  6 0x005f3683 in dott (+0x1f3682) (0x0033fe50)
  7 0x7b85a72c call_process_entry+0xb() in kernel32 (0x0033fe68)
  8 0x7b85b73a in kernel32 (+0x4b739) (0x0033fe98)
  9 0x7bc74e90 call_thread_func_wrapper+0xb() in ntdll (0x0033feb8)
  10 0x7bc77c2f call_thread_func+0xce() in ntdll (0x0033ffa8)
  11 0x7bc74e6e RtlRaiseException+0x21() in ntdll (0x0033ffc8)
  12 0x7bc4cca7 call_dll_entry_point+0x756() in ntdll (0x0033ffe8)
  13 0xf75e915d wine_call_on_stack+0x1c() in libwine.so.1 (0x00000000)
  14 0xf75e92d0 wine_switch_to_stack+0x1f() in libwine.so.1 (0xffd542d8)
  15 0x7bc520e7 LdrInitializeThunk+0x336() in ntdll (0xffd54338)
  16 0x7b861333 __wine_kernel_init+0x872() in kernel32 (0xffd55498)
  17 0x7bc52663 __wine_process_init+0x162() in ntdll (0xffd55518)
  18 0xf75e6dc7 wine_init+0x306() in libwine.so.1 (0xffd55578)
  19 0x7bf00d52 main+0x81() in <wine-loader> (0xffd559c8)
  20 0xf73f273e __libc_start_main+0xdd() in libc.so.6 (0x00000000)
0x7b8395fc: addl	$12,%esp
Modules:
Module	Address			Debug info	Name (86 modules)
PE	  400000-  7d0000	Export          dott
PE	10000000-101e4000	Deferred        fmod
ELF	7b800000-7ba55000	Dwarf           kernel32<elf>
  \-PE	7b810000-7ba55000	\               kernel32
ELF	7bc00000-7bcd9000	Dwarf           ntdll<elf>
  \-PE	7bc10000-7bcd9000	\               ntdll
ELF	7bf00000-7bf04000	Dwarf           <wine-loader>
ELF	7d910000-7d946000	Deferred        uxtheme<elf>
  \-PE	7d920000-7d946000	\               uxtheme
ELF	7d946000-7d94d000	Deferred        libxfixes.so.3
ELF	7d94d000-7d958000	Deferred        libxcursor.so.1
ELF	7d958000-7d96a000	Deferred        libxi.so.6
ELF	7d96a000-7d96e000	Deferred        libxcomposite.so.1
ELF	7d96e000-7d97b000	Deferred        libxrandr.so.2
ELF	7d97b000-7d987000	Deferred        libxrender.so.1
ELF	7d987000-7d98e000	Deferred        libxxf86vm.so.1
ELF	7d98e000-7d992000	Deferred        libxinerama.so.1
ELF	7d992000-7d999000	Deferred        libxdmcp.so.6
ELF	7d999000-7d99d000	Deferred        libxau.so.6
ELF	7d99d000-7d9c2000	Deferred        libxcb.so.1
ELF	7d9c2000-7db0d000	Deferred        libx11.so.6
ELF	7db0d000-7db22000	Deferred        libxext.so.6
ELF	7db4f000-7dbdc000	Deferred        winex11<elf>
  \-PE	7db60000-7dbdc000	\               winex11
ELF	7dc5c000-7dc85000	Deferred        libexpat.so.1
ELF	7dc85000-7dcc8000	Deferred        libfontconfig.so.1
ELF	7dcc8000-7dcf4000	Deferred        libpng12.so.0
ELF	7dcf4000-7dd0f000	Deferred        libz.so.1
ELF	7dd0f000-7ddbc000	Deferred        libfreetype.so.6
ELF	7dde9000-7df14000	Deferred        oleaut32<elf>
  \-PE	7de00000-7df14000	\               oleaut32
ELF	7df14000-7e00c000	Deferred        comctl32<elf>
  \-PE	7df20000-7e00c000	\               comctl32
ELF	7e00c000-7e082000	Deferred        shlwapi<elf>
  \-PE	7e020000-7e082000	\               shlwapi
ELF	7e082000-7e2ab000	Deferred        shell32<elf>
  \-PE	7e090000-7e2ab000	\               shell32
ELF	7e2ab000-7e368000	Deferred        msvcp100<elf>
  \-PE	7e2d0000-7e368000	\               msvcp100
ELF	7e368000-7e49e000	Deferred        msvcp90<elf>
  \-PE	7e3a0000-7e49e000	\               msvcp90
ELF	7e49e000-7e4f5000	Deferred        msvcp110<elf>
  \-PE	7e4b0000-7e4f5000	\               msvcp110
ELF	7e4f5000-7e519000	Deferred        imm32<elf>
  \-PE	7e500000-7e519000	\               imm32
ELF	7e519000-7e551000	Deferred        msvcr100<elf>
  \-PE	7e520000-7e551000	\               msvcr100
ELF	7e551000-7e5fe000	Deferred        msvcrt<elf>
  \-PE	7e560000-7e5fe000	\               msvcrt
ELF	7e5fe000-7e638000	Dwarf           msvcr110<elf>
  \-PE	7e610000-7e638000	\               msvcr110
ELF	7e638000-7e755000	Deferred        opengl32<elf>
  \-PE	7e650000-7e755000	\               opengl32
ELF	7e755000-7e77f000	Deferred        msacm32<elf>
  \-PE	7e760000-7e77f000	\               msacm32
ELF	7e77f000-7e837000	Deferred        winmm<elf>
  \-PE	7e790000-7e837000	\               winmm
ELF	7e837000-7e85c000	Deferred        iphlpapi<elf>
  \-PE	7e840000-7e85c000	\               iphlpapi
ELF	7e85c000-7e891000	Deferred        ws2_32<elf>
  \-PE	7e860000-7e891000	\               ws2_32
ELF	7e891000-7e8ad000	Deferred        wsock32<elf>
  \-PE	7e8a0000-7e8ad000	\               wsock32
ELF	7e8d3000-7e94f000	Deferred        rpcrt4<elf>
  \-PE	7e8e0000-7e94f000	\               rpcrt4
ELF	7e94f000-7ea7c000	Deferred        ole32<elf>
  \-PE	7e970000-7ea7c000	\               ole32
ELF	7ea7c000-7eaea000	Deferred        advapi32<elf>
  \-PE	7ea90000-7eaea000	\               advapi32
ELF	7eaea000-7ec02000	Deferred        gdi32<elf>
  \-PE	7eb00000-7ec02000	\               gdi32
ELF	7ec02000-7ed50000	Deferred        user32<elf>
  \-PE	7ec10000-7ed50000	\               user32
ELF	7ed50000-7ed5e000	Deferred        libnss_files.so.2
ELF	7ed5e000-7ed6b000	Deferred        libnss_nis.so.2
ELF	7ed6b000-7ed86000	Deferred        libnsl.so.1
ELF	7ef86000-7efd3000	Deferred        libm.so.6
ELF	7efe7000-7f000000	Deferred        version<elf>
  \-PE	7eff0000-7f000000	\               version
ELF	f73d5000-f73da000	Deferred        libdl.so.2
ELF	f73da000-f7595000	Dwarf           libc.so.6
ELF	f7596000-f75b3000	Deferred        libpthread.so.0
ELF	f75b5000-f75bf000	Deferred        libnss_compat.so.2
ELF	f75e0000-f7796000	Dwarf           libwine.so.1
ELF	f7798000-f77bc000	Deferred        ld-linux.so.2
ELF	f77be000-f77bf000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	0000001e    0
	0000001d    0
	00000018    0
	00000016    0
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
0000002a explorer.exe
	0000002c    0
	0000002b    0
0000002d (D) C:\Program Files (x86)\Day of the Tentacle Remastered\Dott.exe
	0000002e    0 <==
System information:
    Wine build: wine-1.6.2
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 4.2.0-35-generic
```

Anyone having some solution for this?

---

