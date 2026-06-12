---
title: "wine error after reboot"
date: 2008-08-06
forum: Wine
---

### Post by Meesterarend on 2008-08-06
I have a problem that wine stop working after a hardreboot, wine was runing the program that chrashed. I've tried all the usual stuf like uninstalling, deleting .wine, and even a new user but still nothing.

Here are the output when I try to install a program:

>  wine-auto DVDFab5030.exe
err:module:DelayLoadFailureHook failed to delay load setupapi.dll.InstallHinfSectionW
wine: Call from 0x7b844f00 to unimplemented function setupapi.dll.InstallHinfSectionW, aborting
wine: Unimplemented function setupapi.dll.InstallHinfSectionW called at address 0x7b844f00 (thread 000b), starting debugger...
Unhandled exception: unimplemented function setupapi.dll.InstallHinfSectionW called in 32-bit code (0x7b844f76).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7b844f76 ESP:0033ecd4 EBP:0033ed38 EFLAGS:00000212(   - 00      - -IA1)
 EAX:7b82ec99 EBX:7b8b4b48 ECX:00000000 EDX:7ed60954
 ESI:7ed60954 EDI:7ed60918
Stack dump:
0x0033ecd4:  0033ed64 00000008 7b8ad89f 0000000c
0x0033ece4:  80000100 00000001 00000000 7b844f00
0x0033ecf4:  00000002 7ed60918 7ed60954 00000001
0x0033ed04:  7b92eb30 7b8ad89f 7b8ad819 0033ed50
0x0033ed14:  7ffd8c00 7ffd8bf8 0033ed28 001108d8
0x0033ed24:  000d000c 001a0018 0033ed50 7b8b4b48
Backtrace:
=>1 0x7b844f76 in kernel32 (+0x24f76) (0x0033ed38)
  2 0x7b86660b DelayLoadFailureHook+0x5b() in kernel32 (0x0033ed78)
  3 0x7ed5c625 in wineboot (+0xc625) (0x0033ed98)
  4 0x7ed58fe8 in wineboot (+0x8fe8) (0x0033eec8)
  5 0x7ed5ba66 main+0xf16() in wineboot (0x0033fed8)
  6 0x7ed5c68b in wineboot (+0xc68b) (0x0033ff08)
  7 0x7b878047 in kernel32 (+0x58047) (0x0033ffe8)
0x7b844f76: movl	0xfffffffc(%ebp),%ebx
Modules:
Module	Address			Debug info	Name (25 modules)
ELF	7b800000-7b931000	Export          kernel32<elf>
  \-PE	7b820000-7b931000	\               kernel32
ELF	7bc00000-7bca6000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca6000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e915000-7e936000	Deferred        libexpat.so.1
ELF	7e936000-7e960000	Deferred        libfontconfig.so.1
ELF	7e960000-7e975000	Deferred        libz.so.1
ELF	7e975000-7e9e5000	Deferred        libfreetype.so.6
ELF	7eaa9000-7eb47000	Deferred        gdi32<elf>
  \-PE	7eac0000-7eb47000	\               gdi32
ELF	7ecf5000-7ed47000	Deferred        advapi32<elf>
  \-PE	7ed00000-7ed47000	\               advapi32
ELF	7ed47000-7ed63000	Export          wineboot<elf>
  \-PE	7ed50000-7ed63000	\               wineboot
ELF	7ed63000-7ed7b000	Deferred        libnsl.so.1
ELF	7ed7b000-7ed84000	Deferred        libnss_compat.so.2
ELF	7efc5000-7efea000	Deferred        libm.so.6
ELF	7eff5000-7f000000	Deferred        libnss_files.so.2
ELF	f7c75000-f7c79000	Deferred        libdl.so.2
ELF	f7c79000-f7dc8000	Deferred        libc.so.6
ELF	f7dc8000-f7de0000	Deferred        libpthread.so.0
ELF	f7de5000-f7def000	Deferred        libnss_nis.so.2
ELF	f7df7000-f7f2d000	Deferred        libwine.so.1
ELF	f7f2f000-f7f4e000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000a (D) C:\windows\system32\wineboot.exe
	0000000b    0 <==
0000000c 
	0000000e    0
	0000000d    0
Backtrace:
=>1 0x7b844f76 in kernel32 (+0x24f76) (0x0033ed38)
  2 0x7b86660b DelayLoadFailureHook+0x5b() in kernel32 (0x0033ed78)
  3 0x7ed5c625 in wineboot (+0xc625) (0x0033ed98)
  4 0x7ed58fe8 in wineboot (+0x8fe8) (0x0033eec8)
  5 0x7ed5ba66 main+0xf16() in wineboot (0x0033fed8)
  6 0x7ed5c68b in wineboot (+0xc68b) (0x0033ff08)
  7 0x7b878047 in kernel32 (+0x58047) (0x0033ffe8)
            
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
err:module:attach_process_dlls "gdi32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\frans\\Desktop\\install\\DVDFab5030.exe" failed, status c0000005

winecfg gives this:

> 
 winecfg
err:module:attach_process_dlls "gdi32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\winecfg.exe" failed, status c0000005


any ideas 

I tried placing the gdi32.dll file in the wine systems folder also but still no luck :(

---

### Post by woaiwojia on 2008-12-09
> ** said:**
> 
i met the same problem.any ideas

---

