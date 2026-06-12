---
title: "serious error with wine while playing poker"
date: 2022-04-28
forum: Wine
---

### Post by myles_gallacher on 2022-04-28
this is what happened while trying to log in to party pker.............,back trace text
```
Unhandled exception: page fault on execute access to 0x00000004 in 32-bit code (0x00000004).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00000004 ESP:0033fcd4 EBP:0033fce8 EFLAGS:00010216(  R- --  I   -A-P- )
 EAX:00000000 EBX:7b63d000 ECX:0033fcc0 EDX:00000000
 ESI:00115520 EDI:00000000
Stack dump:
0x0033fcd4:  7b47a216 0033fd00 7b477324 0033fd00
0x0033fce4:  7eca9000 0033fd78 7ec93164 7eca1cc8
0x0033fcf4:  0033fd80 7ec8bfcd 7ec93164 00000002
0x0033fd04:  0033fd54 00000000 00002710 0033fd30
0x0033fd14:  7eca9000 00000000 7ec915f2 00115520
0x0033fd24:  7eca9cec 00113428 001134b8 00110a60
Backtrace:
=>0 0x00000004 (0x0033fce8)
  1 0x7ec93164 service_start+0x3f3() in services (0x0033fd78)
  2 0x7ec8b8c2 main+0x401() in services (0x0033fe78)
  3 0x7eca0e04 svcctl_svcctl_QueryServiceConfigEx+0x723() in services (0x0033feb8)
  4 0x7b463652 call_process_entry+0x11() in kernel32 (0x0033fed8)
  5 0x7b4658ce ExitProcess+0x226d() in kernel32 (0x0033ffd8)
  6 0x7b46365e call_process_entry+0x1d() in kernel32 (0x0033ffec)
0x00000004: -- no code accessible --
Modules:
Module	Address			Debug info	Name (24 modules)
ELF	7b400000-7b7f8000	Dwarf           kernel32<elf>
  \-PE	7b420000-7b7f8000	\               kernel32
ELF	7bc00000-7bd00000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bd00000	\               ntdll
ELF	7c000000-7c004000	Deferred        <wine-loader>
ELF	7eb44000-7eb62000	Deferred        libgcc_s.so.1
ELF	7eb62000-7eb7a000	Deferred        userenv<elf>
  \-PE	7eb70000-7eb7a000	\               userenv
ELF	7eb7a000-7ebf3000	Deferred        advapi32<elf>
  \-PE	7eb90000-7ebf3000	\               advapi32
ELF	7ebf3000-7ec78000	Deferred        rpcrt4<elf>
  \-PE	7ec00000-7ec78000	\               rpcrt4
ELF	7ec78000-7ecaa000	Dwarf           services<elf>
  \-PE	7ec80000-7ecaa000	\               services
ELF	7ecaa000-7ecbe000	Deferred        libnss_files.so.2
ELF	7ecbe000-7ecd9000	Deferred        libnsl.so.1
ELF	7ecd9000-7ece7000	Deferred        libnss_nis.so.2
ELF	7eefe000-7f000000	Deferred        libm.so.6
ELF	b7b83000-b7b88000	Deferred        libdl.so.2
ELF	b7b88000-b7d64000	Deferred        libc.so.6
ELF	b7d64000-b7d84000	Deferred        libpthread.so.0
ELF	b7d8f000-b7d99000	Deferred        libnss_compat.so.2
ELF	b7d9b000-b7f52000	Dwarf           libwine.so.1
ELF	b7f54000-b7f7c000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 ntdll.dll
	00000009    0
0000000a wineboot.exe
	0000000b    0
0000000e (D) C:\windows\system32\services.exe
	0000002b    0
	0000002a    0
	00000023    0
	00000020    0
	0000001b    0
	00000013    0
	00000010    0
	0000000f    0 <==
00000011 winedevice.exe
	00000018    0
	00000017    0
	00000016    0
	00000012    0
00000019 plugplay.exe
	0000001d    0
	0000001c    0
	0000001a    0
0000001e winedevice.exe
	00000028    0
	00000022    0
	00000021    0
	0000001f    0
00000024 InstallAssistService.exe
	0000002c    0
	00000025    0
00000026 explorer.exe
	00000031    0
	00000030    0
	0000002f    0
	00000027    0
System information:
    Wine build: wine-4.0
    Platform: i386
    Version: Windows 7
    Host system: Linux
    Host version: 5.4.0-109-generic
```

---

### Post by QIII on 2022-04-28
Moved to the Wine sub-forum as a more appropriate location.

---

### Post by DuckHook on 2022-04-28
I find WINE to be increasingly problematic when running 32&#8209;bit apps, ever since Canonical deprecated 32&#8209;bit code. I have been able to work around some of these problems by running Bionic in a container, then WINE on top of that. Bionic was still reasonably 32&#8209;bit friendly. But, for most people, that's an ungainly way to get something to work. Besides, such workarounds have a clear end date: when Bionic falls out of support.

You might be better off asking for help in the WINE forums. They are the WINE experts.

---

