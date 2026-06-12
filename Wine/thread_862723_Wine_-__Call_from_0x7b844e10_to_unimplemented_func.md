---
title: "Wine -  Call from 0x7b844e10 to unimplemented function"
date: 2008-07-17
forum: Wine
---

### Post by daisuke666 on 2008-07-17
Hi guys,

I'm trying to launch a program and this error comes up in term.

```
fixme:advapi:CheckTokenMembership ((nil) 0x125078 0x32fe24) stub!
fixme:imagehlp:CheckSumMappedFile (0x550000, 35712, 0x32fdac, 0x32fdf8): stub
wine: Call from 0x7b844e10 to unimplemented function ntoskrnl.exe.KeInitializeEvent, aborting
wine: Unimplemented function ntoskrnl.exe.KeInitializeEvent called at address 0x7b844e10 (thread 001f), starting debugger...
Unhandled exception: unimplemented function ntoskrnl.exe.KeInitializeEvent called in 32-bit code (0x7b844e86).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7b844e86 ESP:7ec29864 EBP:7ec298c8 EFLAGS:00000212(   - 00      - -IA1)
 EAX:7b82ebb9 EBX:7b8b388c ECX:00000000 EDX:00450260
 ESI:00450260 EDI:7ee7ad80
Stack dump:
0x7ec29864:  7ec298f0 00000008 00000000 00000000
0x7ec29874:  80000100 00000001 00000000 7b844e10
0x7ec29884:  00000002 7edeeb20 7edf1a15 00000058
0x7ec29894:  004533c0 00000028 00453390 00000020
0x7ec298a4:  00000000 00000000 00000000 00000000
0x7ec298b4:  00000000 00000000 7edf893c 7ec2992c
Backtrace:
=>1 0x7b844e86 RaiseException+0x76(code=0x80000100, flags=0x1, nbargs=0x2, args=0x7ec298f0) [/home/dan/wine-1.1.0/dlls/kernel32/except.c:85] in kernel32 (0x7ec298c8)
  2 0x7edeeab5 __wine_spec_unimplemented_stub+0x35(module=0x7edeeb20, function=0x7edf1a15) [/home/dan/wine-1.1.0/dlls/winecrt0/stub.c:35] in ntoskrnl (0x7ec298f8)
  3 0x7ede8748 __wine_stub_KeInitializeInterrupt() in ntoskrnl (0x7ec2991c)
  4 0x00450e40 in xhvlcqwv.sys (+0xe40) (0x7ec29938)
  5 0x7ee790e0 ServiceMain+0x730(argc=0x0, argv=0x0) [/home/dan/wine-1.1.0/programs/winedevice/device.c:131] in winedevice (0x7ec299e8)
  6 0x7ee426c9 service_thread+0x169(arg=0x1108d0) [/home/dan/wine-1.1.0/dlls/advapi32/service.c:427] in advapi32 (0x7ec29a38)
  7 0x7bc6bcde call_thread_entry_point+0xe() in ntdll (0x7ec29a48)
  8 0x7bc6c372 call_thread_func+0x42(rtl_func=<register EDI not in topmost frame>, arg=<register ESI not in topmost frame>) [/home/dan/wine-1.1.0/dlls/ntdll/thread.c:386] in ntdll (0x7ec29ae8)
  9 0x7bc6c5a2 in ntdll (+0x5c5a2) (0x7ec2a3d8)
  10 0xf7e1c4fb start_thread+0xcb() in libpthread.so.0 (0x7ec2a4c8)
0x7b844e86 RaiseException+0x76 [/home/dan/wine-1.1.0/dlls/kernel32/except.c:85] in kernel32: movl	0xfffffffc(%ebp),%ebx
85	}
Modules:
Module	Address			Debug info	Name (31 modules)
PE	  450000-  458b80	Export          xhvlcqwv.sys
ELF	7b800000-7b930000	Dwarf           kernel32<elf>
  \-PE	7b820000-7b930000	\               kernel32
ELF	7bc00000-7bca4000	Dwarf           ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7ea9b000-7eab0000	Deferred        hal<elf>
  \-PE	7eaa0000-7eab0000	\               hal
ELF	7eab0000-7eb1a000	Deferred        msvcrt<elf>
  \-PE	7eac0000-7eb1a000	\               msvcrt
ELF	7ec2b000-7ec3e000	Deferred        libresolv.so.2
ELF	7ec3e000-7ec5c000	Deferred        iphlpapi<elf>
  \-PE	7ec40000-7ec5c000	\               iphlpapi
ELF	7ec5c000-7ecbe000	Deferred        rpcrt4<elf>
  \-PE	7ec70000-7ecbe000	\               rpcrt4
ELF	7edcf000-7ee07000	Dwarf           ntoskrnl<elf>
  \-PE	7ede0000-7ee07000	\               ntoskrnl
ELF	7ee07000-7ee59000	Dwarf           advapi32<elf>
  \-PE	7ee10000-7ee59000	\               advapi32
ELF	7ee59000-7ee64000	Deferred        libnss_files.so.2
ELF	7ee67000-7ee7b000	Dwarf           winedevice<elf>
  \-PE	7ee70000-7ee7b000	\               winedevice
ELF	7ee7b000-7ee93000	Deferred        libnsl.so.1
ELF	7eea0000-7eeaa000	Deferred        libnss_nis.so.2
ELF	7eeaa000-7eeb3000	Deferred        libnss_compat.so.2
ELF	7efdb000-7f000000	Deferred        libm.so.6
ELF	f7cc3000-f7cc7000	Deferred        libdl.so.2
ELF	f7cc7000-f7e16000	Deferred        libc.so.6
ELF	f7e17000-f7e2f000	Export          libpthread.so.0
ELF	f7e2f000-f7f65000	Deferred        libwine.so.1
ELF	f7f67000-f7f86000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000c 
	0000001e    0
	0000001d    0
	00000019    0
	00000015    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000016    0
	00000014    0
	00000011    0
	00000010    0
0000001a (D) C:\windows\system32\winedevice.exe
	0000001f    0 <==
	0000001c    0
	0000001b    0
Backtrace:
=>1 0x7b844e86 RaiseException+0x76(code=0x80000100, flags=0x1, nbargs=0x2, args=0x7ec298f0) [/home/dan/wine-1.1.0/dlls/kernel32/except.c:85] in kernel32 (0x7ec298c8)
  2 0x7edeeab5 __wine_spec_unimplemented_stub+0x35(module=0x7edeeb20, function=0x7edf1a15) [/home/dan/wine-1.1.0/dlls/winecrt0/stub.c:35] in ntoskrnl (0x7ec298f8)
  3 0x7ede8748 __wine_stub_KeInitializeInterrupt() in ntoskrnl (0x7ec2991c)
  4 0x00450e40 in xhvlcqwv.sys (+0xe40) (0x7ec29938)
  5 0x7ee790e0 ServiceMain+0x730(argc=0x0, argv=0x0) [/home/dan/wine-1.1.0/programs/winedevice/device.c:131] in winedevice (0x7ec299e8)
  6 0x7ee426c9 service_thread+0x169(arg=0x1108d0) [/home/dan/wine-1.1.0/dlls/advapi32/service.c:427] in advapi32 (0x7ec29a38)
  7 0x7bc6bcde call_thread_entry_point+0xe() in ntdll (0x7ec29a48)
  8 0x7bc6c372 call_thread_func+0x42(rtl_func=<register EDI not in topmost frame>, arg=<register ESI not in topmost frame>) [/home/dan/wine-1.1.0/dlls/ntdll/thread.c:386] in ntdll (0x7ec29ae8)
  9 0x7bc6c5a2 in ntdll (+0x5c5a2) (0x7ec2a3d8)
  10 0xf7e1c4fb start_thread+0xcb() in libpthread.so.0 (0x7ec2a4c8)
wine: Call from 0x7b844e10 to unimplemented function ntoskrnl.exe.KeInitializeInterrupt, aborting
wine: Call from 0x7b844e10 to unimplemented function ntoskrnl.exe.KeInitializeMutant, aborting

```

---

### Post by Sef on 2008-07-17
Moved to WINE forum.

---

### Post by daisuke666 on 2008-07-17
Oops sorry, I didn't see this forum. Will remember for next time.

---

