---
title: "Very low FPS in Soldier Of Fortune 2."
date: 2008-06-22
forum: Wine
---

### Post by Gerlads Mod on 2008-06-22
I am having some REALLY low FPS in SOF2.
I am getting around 1-3 FPS on the lowest possible graphics.
I used to be able to play this on medium graphics on Windows.
Someone please help!

**Wine version:** wine-1.0

**Terminal output:**
Command: WINEDEBUG=fps nice -20 wine sof2.exe
```

err:winedevice:ServiceMain driver L"cdrbsdrv" failed to load
wine: Call from 0x7b844b20 to unimplemented function ntoskrnl.exe.KeInitializeMutex, aborting
wine: Unimplemented function ntoskrnl.exe.KeInitializeMutex called at address 0x7b844b20 (thread 0023), starting debugger...
Unhandled exception: unimplemented function ntoskrnl.exe.KeInitializeMutex called in 32-bit code (0x7b844b96).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b844b96 ESP:7ec2c864 EBP:7ec2c8c8 EFLAGS:00200212(   - 00      - -IA1)
 EAX:7b82eb09 EBX:7b8b3884 ECX:00000000 EDX:001118d8
 ESI:001118d8 EDI:7edff770
Stack dump:
0x7ec2c864:  7ec2c8f0 00000008 7ec2c934 7ec2c890
0x7ec2c874:  80000100 00000001 00000000 7b844b20
0x7ec2c884:  00000002 7ee05b00 7ee08a30 00000000
0x7ec2c894:  00000000 00000000 00000000 00000000
0x7ec2c8a4:  00000000 00000000 00000000 00000000
0x7ec2c8b4:  00000000 00000000 00000000 00000001
Backtrace:
=>1 0x7b844b96 in kernel32 (+0x24b96) (0x7ec2c8c8)
  2 0x7ee05a95 in ntoskrnl (+0x15a95) (0x7ec2c8f8)
  3 0x7edff794 in ntoskrnl (+0xf794) (0x7ec2c938)
  4 0x7eea40d0 in winedevice (+0x40d0) (0x7ec2c9e8)
  5 0x7ee59359 in advapi32 (+0x29359) (0x7ec2ca38)
  6 0x7bc6aeae call_thread_entry_point+0xe() in ntdll (0x7ec2ca48)
  7 0x7bc6b542 in ntdll (+0x5b542) (0x7ec2cae8)
  8 0x7bc6b772 in ntdll (+0x5b772) (0x7ec2d3d8)
  9 0xb7dd44fb start_thread+0xcb() in libpthread.so.0 (0x7ec2d4c8)
0x7b844b96: movl	0xfffffffc(%ebp),%ebx
Modules:
Module	Address			Debug info	Name (31 modules)
PE	  450000-  454680	Deferred        elbycdio.sys
ELF	7b800000-7b92d000	Export          kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Export          ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7eab3000-7eb1d000	Deferred        msvcrt<elf>
  \-PE	7eac0000-7eb1d000	\               msvcrt
ELF	7ec2e000-7ec41000	Deferred        libresolv.so.2
ELF	7ec41000-7ec56000	Deferred        hal<elf>
  \-PE	7ec50000-7ec56000	\               hal
ELF	7ec56000-7ec74000	Deferred        iphlpapi<elf>
  \-PE	7ec60000-7ec74000	\               iphlpapi
ELF	7ec74000-7ecd5000	Deferred        rpcrt4<elf>
  \-PE	7ec80000-7ecd5000	\               rpcrt4
ELF	7ede6000-7ee1e000	Export          ntoskrnl<elf>
  \-PE	7edf0000-7ee1e000	\               ntoskrnl
ELF	7ee1e000-7ee70000	Export          advapi32<elf>
  \-PE	7ee30000-7ee70000	\               advapi32
ELF	7ee70000-7ee88000	Deferred        libnsl.so.1
ELF	7ee88000-7ee91000	Deferred        libnss_compat.so.2
ELF	7ee92000-7eea6000	Export          winedevice<elf>
  \-PE	7eea0000-7eea6000	\               winedevice
ELF	7efc6000-7efeb000	Deferred        libm.so.6
ELF	7eff5000-7f000000	Deferred        libnss_files.so.2
ELF	b7c70000-b7c7a000	Deferred        libnss_nis.so.2
ELF	b7c7b000-b7c7f000	Deferred        libdl.so.2
ELF	b7c7f000-b7dce000	Deferred        libc.so.6
ELF	b7dcf000-b7de7000	Export          libpthread.so.0
ELF	b7dfc000-b7f32000	Deferred        libwine.so.1
ELF	b7f34000-b7f50000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000a 
	0000000b    0
0000000c 
	00000022    0
	00000014    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000019    0
	00000018    0
	00000017    0
	00000016    0
	00000015    0
	00000011    0
	00000010    0
0000001f (D) c:\windows\system32\winedevice.exe
	00000023    0 <==
	00000021    0
	00000020    0
Backtrace:
=>1 0x7b844b96 in kernel32 (+0x24b96) (0x7ec2c8c8)
  2 0x7ee05a95 in ntoskrnl (+0x15a95) (0x7ec2c8f8)
  3 0x7edff794 in ntoskrnl (+0xf794) (0x7ec2c938)
  4 0x7eea40d0 in winedevice (+0x40d0) (0x7ec2c9e8)
  5 0x7ee59359 in advapi32 (+0x29359) (0x7ec2ca38)
  6 0x7bc6aeae call_thread_entry_point+0xe() in ntdll (0x7ec2ca48)
  7 0x7bc6b542 in ntdll (+0x5b542) (0x7ec2cae8)
  8 0x7bc6b772 in ntdll (+0x5b772) (0x7ec2d3d8)
  9 0xb7dd44fb start_thread+0xcb() in libpthread.so.0 (0x7ec2d4c8)
wine: Call from 0x7b844b20 to unimplemented function ntoskrnl.exe.KeInitializeQueue, aborting
wine: Call from 0x7b844b20 to unimplemented function ntoskrnl.exe.KeInitializeSemaphore, aborting
err:winedevice:ServiceMain driver L"SCDEmu" failed to load
err:ole:CoGetClassObject class {5959df60-2911-11d1-b049-0020af30269a} not registered
err:ole:CoGetClassObject no class object {5959df60-2911-11d1-b049-0020af30269a} could be created for context 0x1
fixme:dinput:DllCanUnloadNow (void): stub

```

**Wine configuration:**
OS version: Windows 98/XP (FPS stays the same)
Sound setting: AlSA
Graphics settings checked:
Allow DirectX apps to stop the mouse from leaving the window.
Allow the Window manager to control the window.
Screen res: 96 DPI

**Hardware specs:**
Computer: Dell Inspirion E1505 notebook.
1 GB RAM
Intel 945GM video card.

Why is this happening and how can I fix it?
Thanks.

---

