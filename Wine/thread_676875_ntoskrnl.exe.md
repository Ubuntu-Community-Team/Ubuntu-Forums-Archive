---
title: "ntoskrnl.exe"
date: 2008-01-24
forum: Wine
---

### Post by constchar* on 2008-01-24
Could anyone explain to me why wine keeps doing this after 0.9.52
and how to fix it, or at least suppress it?

After 0.9.52, the release they added AutoRun I believe, everytime I
start Wine I get a huge dump of error messages like this before the
Wine starts anything, although I've had the ALSA messages on the bottom
the whole time I've used Wine.

Thanks!

```

wine: Call from 0x7b844b90 to unimplemented function ntoskrnl.exe.KeInitializeEvent, aborting
wine: Unimplemented function ntoskrnl.exe.KeInitializeEvent called at address 0x7b844b90 (thread 001a), starting debugger...
Unhandled exception: unimplemented function ntoskrnl.exe.KeInitializeEvent called in 32-bit code (0x7b844c08).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b844c08 ESP:7eccb874 EBP:7eccb8d8 EFLAGS:00000212(   - 00      - -IA1)
 EAX:7b82f411 EBX:7b8b1888 ECX:00000000 EDX:001112a0
 ESI:001112a0 EDI:001111e8
Stack dump:
0x7eccb874:  7eccb900 00000008 00000000 00000000
0x7eccb884:  80000100 00000001 00000000 7b844b90
0x7eccb894:  00000002 7edfdae0 7ee009d5 00000058
0x7eccb8a4:  00487714 0000001e 004876fc 00000016
0x7eccb8b4:  00000000 00000000 00000000 00000000
0x7eccb8c4:  00000000 00000000 7ee0791c 7eccb950
Backtrace:
=>1 0x7b844c08 RaiseException+0x78(code=0x80000100, flags=0x1, nbargs=0x2, args=0x7eccb900) [/home/jimmy/wine-0.9.53/dlls/kernel32/except.c:85] in kernel32 (0x7eccb8d8)
  2 0x7edfda85 __wine_spec_unimplemented_stub+0x35(module=0x7edfdae0, function=0x7ee009d5) [/home/jimmy/wine-0.9.53/dlls/winecrt0/stub.c:35] in ntoskrnl (0x7eccb908)
  3 0x7edf7968 __wine_stub_KeInitializeInterrupt() in ntoskrnl (0x7eccb958)
  4 0x7ee9c7d7 ServiceMain+0x4d7(argc=0x0, argv=0x0) [/home/jimmy/wine-0.9.53/programs/winedevice/device.c:82] in winedevice (0x7eccb9d8)
  5 0x7ee51447 service_thread+0x207(arg=0x1108c0) [/home/jimmy/wine-0.9.53/dlls/advapi32/service.c:426] in advapi32 (0x7eccba28)
  6 0x7bc68cde call_thread_entry_point+0xe() in ntdll (0x7eccba38)
  7 0x7bc69a02 call_thread_func+0x42(rtl_func=<register EDI not in topmost frame>, arg=<register ESI not in topmost frame>) [/home/jimmy/wine-0.9.53/dlls/ntdll/thread.c:401] in ntdll (0x7eccbad8)
  8 0x7bc69cc2 start_thread+0x232(info=<register ESI not in topmost frame>) [/home/jimmy/wine-0.9.53/dlls/ntdll/thread.c:482] in ntdll (0x7eccc3d8)
  9 0xb7db846b start_thread+0xcb() in libpthread.so.0 (0x7eccc4c8)
  10 0xb7d3b6de __clone+0x5e() in libc.so.6 (0x00000000)
0x7b844c08 RaiseException+0x78 [/home/jimmy/wine-0.9.53/dlls/kernel32/except.c:85] in kernel32: movl    0xfffffffc(%ebp),%ebx
85      }
Modules:
Module  Address                 Debug info      Name (26 modules)
PE        460000-  49b000       Deferred        vmm.sys
ELF     7b800000-7b92b000       Dwarf           kernel32<elf>
  \-PE  7b820000-7b92b000       \               kernel32
ELF     7bc00000-7bca2000       Dwarf           ntdll<elf>
  \-PE  7bc10000-7bca2000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7eb3e000-7eb53000       Deferred        hal<elf>
  \-PE  7eb40000-7eb53000       \               hal
ELF     7eb53000-7ebbc000       Deferred        msvcrt<elf>
  \-PE  7eb60000-7ebbc000       \               msvcrt
ELF     7edde000-7ee16000       Dwarf           ntoskrnl<elf>
  \-PE  7edf0000-7ee16000       \               ntoskrnl
ELF     7ee16000-7ee62000       Dwarf           advapi32<elf>
  \-PE  7ee20000-7ee62000       \               advapi32
ELF     7ee62000-7ee6d000       Deferred        libnss_files.so.2
ELF     7ee6d000-7ee77000       Deferred        libnss_nis.so.2
ELF     7ee77000-7ee80000       Deferred        libnss_compat.so.2
ELF     7ee8a000-7ee9e000       Dwarf           winedevice<elf>
  \-PE  7ee90000-7ee9e000       \               winedevice
ELF     7efbd000-7efe2000       Deferred        libm.so.6
ELF     7efe8000-7f000000       Deferred        libnsl.so.1
ELF     b7c64000-b7c68000       Deferred        libdl.so.2
ELF     b7c68000-b7db2000       Export          libc.so.6
ELF     b7db3000-b7dcb000       Export          libpthread.so.0
ELF     b7de9000-b7efd000       Deferred        libwine.so.1
ELF     b7eff000-b7f1b000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000017 (D) c:\windows\system32\winedevice.exe
        0000001a    0 <==
        00000019    0
        00000018    0
00000013
        00000016    0
        00000015    0
        00000014    0
0000000f
        00000012    0
        00000011    0
        00000010    0
0000000c
        0000000e    0
        0000000d    0
0000000a
        0000000b    0
00000008
        00000009    0
Backtrace:
=>1 0x7b844c08 RaiseException+0x78(code=0x80000100, flags=0x1, nbargs=0x2, args=0x7eccb900) [/home/jimmy/wine-0.9.53/dlls/kernel32/except.c:85] in kernel32 (0x7eccb8d8)
  2 0x7edfda85 __wine_spec_unimplemented_stub+0x35(module=0x7edfdae0, function=0x7ee009d5) [/home/jimmy/wine-0.9.53/dlls/winecrt0/stub.c:35] in ntoskrnl (0x7eccb908)
  3 0x7edf7968 __wine_stub_KeInitializeInterrupt() in ntoskrnl (0x7eccb958)
  4 0x7ee9c7d7 ServiceMain+0x4d7(argc=0x0, argv=0x0) [/home/jimmy/wine-0.9.53/programs/winedevice/device.c:82] in winedevice (0x7eccb9d8)
  5 0x7ee51447 service_thread+0x207(arg=0x1108c0) [/home/jimmy/wine-0.9.53/dlls/advapi32/service.c:426] in advapi32 (0x7eccba28)
  6 0x7bc68cde call_thread_entry_point+0xe() in ntdll (0x7eccba38)
  7 0x7bc69a02 call_thread_func+0x42(rtl_func=<register EDI not in topmost frame>, arg=<register ESI not in topmost frame>) [/home/jimmy/wine-0.9.53/dlls/ntdll/thread.c:401] in ntdll (0x7eccbad8)
  8 0x7bc69cc2 start_thread+0x232(info=<register ESI not in topmost frame>) [/home/jimmy/wine-0.9.53/dlls/ntdll/thread.c:482] in ntdll (0x7eccc3d8)
  9 0xb7db846b start_thread+0xcb() in libpthread.so.0 (0x7eccc4c8)
  10 0xb7d3b6de __clone+0x5e() in libc.so.6 (0x00000000)
wine: Call from 0x7b844b90 to unimplemented function ntoskrnl.exe.KeInitializeInterrupt, aborting
wine: Call from 0x7b844b90 to unimplemented function ntoskrnl.exe.KeInitializeMutant, aborting
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL snd_card0
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM snd_card0
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM snd_card0

```

---

### Post by happyhamster on 2008-01-24
Are you still able to run regedit? If so, take a look at 

HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run

or just do a search for "Run" and see what else is starting when running wine.

---

### Post by constchar* on 2008-01-24
Zip, nothing.
I even checked the StartUp entries under ~/.wine/drive_c/Windows/Profiles/WhateverUserNamesSuchAsAllUsers/Start Menu/Programs/StartUp
and they don't have any shortcuts in there.

It seems like the 0.9.4x series was relatively stable and functional but the
newer 0.9.5x series seems to be really buggy, or is it just me?

---

