---
title: "Wine always starts with an error."
date: 2014-09-19
forum: Wine
---

### Post by Robbyx on 2014-09-19
Does anyone know how to stop the unhandled exception whenever I start Wine on Ubuntu 14.04 with gnome 3

```
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00000000 ESP:0034fe0c EBP:0034fe60 EFLAGS:00010216(  R- --  I   -A-P- )
 EAX:0034fe3c EBX:7b8b5000 ECX:00240000 EDX:7ba59e70
 ESI:7ffdf000 EDI:00000000
Stack dump:
0x0034fe0c:  0024597c 0034fe3c 00015810 00245958
0x0034fe1c:  7ffdf000 7b8b5000 00000000 00000000
0x0034fe2c:  00000000 00000000 00000000 00000000
0x0034fe3c:  00000000 00000000 00000000 00000000
0x0034fe4c:  00000000 00000000 00000000 00000000
0x0034fe5c:  00000000 0034fe78 7b85e5cc 7ffdf000
Backtrace:
=>0 0x00000000 (0x0034fe60)
  1 0x7b85e5cc call_process_entry+0xb() in kernel32 (0x0034fe78)
  2 0x7b85f653 in kernel32 (+0x4f652) (0x0034feb8)
  3 0x7bc799b0 call_thread_func_wrapper+0xb() in ntdll (0x0034fed8)
  4 0x7bc7c93d call_thread_func+0x7c() in ntdll (0x0034ffa8)
  5 0x7bc7998e RtlRaiseException+0x21() in ntdll (0x0034ffc8)
  6 0x7bc4e8fe call_dll_entry_point+0x7ed() in ntdll (0x0034ffe8)
  7 0xb756b50d wine_call_on_stack+0x1c() in libwine.so.1 (0x00000000)
  8 0xb756b5cb wine_switch_to_stack+0x2a() in libwine.so.1 (0xbf8ab148)
  9 0x7bc541e2 LdrInitializeThunk+0x3a1() in ntdll (0xbf8ab1a8)
  10 0x7b865bdd __wine_kernel_init+0xa0c() in kernel32 (0xbf8ac2c8)
  11 0x7bc547a3 __wine_process_init+0x192() in ntdll (0xbf8ac358)
  12 0xb7568c70 wine_init+0x30f() in libwine.so.1 (0xbf8ac3b8)
  13 0x7bf00fdc main+0xfb() in <wine-loader> (0xbf8ac808)
  14 0xb738fa83 __libc_start_main+0xf2() in libc.so.6 (0x00000000)
0x00000000: -- no code accessible --
Modules:
Module	Address			Debug info	Name (23 modules)
PE	  240000-  24a000	Deferred        lmirfsdriver.sys
ELF	7b800000-7ba5b000	Dwarf           kernel32<elf>
  \-PE	7b810000-7ba5b000	\               kernel32
ELF	7bc00000-7bcdb000	Dwarf           ntdll<elf>
  \-PE	7bc10000-7bcdb000	\               ntdll
ELF	7bf00000-7bf04000	Dwarf           <wine-loader>
ELF	7ec73000-7ed1b000	Deferred        msvcrt<elf>
  \-PE	7ec90000-7ed1b000	\               msvcrt
ELF	7ed1b000-7ed65000	Deferred        ntoskrnl<elf>
  \-PE	7ed20000-7ed65000	\               ntoskrnl
ELF	7ed65000-7ed72000	Deferred        libnss_files.so.2
ELF	7ed72000-7ed7e000	Deferred        libnss_nis.so.2
ELF	7ed7e000-7ed97000	Deferred        libnsl.so.1
ELF	7ed97000-7eda0000	Deferred        libnss_compat.so.2
ELF	7efa0000-7efe6000	Deferred        libm.so.6
ELF	7efe8000-7f000000	Deferred        hal<elf>
  \-PE	7eff0000-7f000000	\               hal
ELF	b7376000-b7526000	Dwarf           libc.so.6
ELF	b7526000-b752b000	Deferred        libdl.so.2
ELF	b752c000-b7548000	Deferred        libpthread.so.0
ELF	b7562000-b7717000	Dwarf           libwine.so.1
ELF	b7719000-b773b000	Deferred        ld-linux.so.2
ELF	b773b000-b773c000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 ntdll.dll
	00000009    0
0000000a wineboot.exe
	0000000b    0
0000000e services.exe
	00000021    0
	00000020    0
	0000001a    0
	00000018    0
	00000010    0
	0000000f    0
00000014 explorer.exe
	0000001f    0
	00000015    0
00000016 winedevice.exe
	0000001c    0
	0000001b    0
	00000017    0
0000001d ramaint.exe
	00000023    0
	00000022    0
	0000001e    0
00000024 (D) C:\windows\system32\drivers\LMIRfsDriver.sys
	00000025    0 <==
System information:
    Wine build: wine-1.6.2
    Platform: i386
    Host system: Linux
    Host version: 3.13.0-35-generic
```

---

