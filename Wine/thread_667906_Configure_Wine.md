---
title: "Configure Wine"
date: 2008-01-14
forum: Wine
---

### Post by GreaterCore on 2008-01-14
Dear all,

Currently I am trying to run Wine from the Gnome "Start menu", but every time I click on "Configure Wine" on the list, it does not load up.

Any ideas how to get it to work?

---

### Post by sowelie on 2008-01-14
Try launching it from the terminal.  Check the output for error messages and post here if you need help.

```
winecfg
```

---

### Post by GreaterCore on 2008-01-15
After running "winecfg" this is the mess that I see:

```
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/username', starting in the Windows directory.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
wine: Unhandled page fault on read access to 0x000000b8 at address 0x7e44c4c9 (thread 000b), starting debugger...
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.
Usage:
        winedbg [ [ --gdb ] [ prog-name [ prog-args ] | <num> | file.mdmp | --help ]

```

Any idea what's going on?

---

### Post by hikaricore on 2008-01-15
Try:

> wineprefixcreate

This should run upon installation but sometime it does not.
This should create the directory structure in your home directory, assuming the drive is not full or damaged.

---

### Post by GreaterCore on 2008-01-15
Now since I have run the "wineprefixcreate", I am bombarded with an even greater list of error messages...

```
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
wine: Unhandled page fault on read access to 0x000000b8 at address 0x7e44c4c9 (thread 000b), starting debugger...
Unhandled exception: page fault on read access to 0x000000b8 in 32-bit code (0x7e44c4c9).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e44c4c9 ESP:0034eca0 EBP:0034ecc8 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:00000000 ECX:7c03bd68 EDX:00000000
 ESI:00000000 EDI:7c046eb0
Stack dump:
0x0034eca0:  0003fff4 00000000 0000004c 00000007
0x0034ecb0:  7c046eb0 00000000 00000000 00000000
0x0034ecc0:  7c046eb0 7c01cb48 0034ecf8 7e67c705
0x0034ecd0:  7c046eb0 00000000 00000000 00000000
0x0034ece0:  7c01cbf8 00000190 7c03bd68 7e89b588
0x0034ecf0:  00000033 7e8a0358 0034ed28 7e67b97e
Backtrace:
=>1 0x7e44c4c9 in r200_dri.so (+0x584c9) (0x0034ecc8)
  2 0x7e67c705 in libgl.so.1 (+0x2c705) (0x0034ecf8)
  3 0x7e67b97e glXCreateContext+0x3e() in libgl.so.1 (0x0034ed28)
  4 0x7e864c1c in winex11 (+0x34c1c) (0x0034edb8)
  5 0x7e867a66 X11DRV_setup_opengl_visual+0x3c() in winex11 (0x0034eeb8)
  6 0x7e877514 in winex11 (+0x47514) (0x0034f098)
  7 0x7e88817c in winex11 (+0x5817c) (0x0034f0b8)
  8 0x7bc42ebd call_dll_entry_point+0x15() in ntdll (0x0034f0d8)
  9 0x7bc4537a in ntdll (+0x3537a) (0x0034f168)
  10 0x7bc45614 in ntdll (+0x35614) (0x0034f1a8)
  11 0x7bc47ca3 LdrLoadDll+0x67() in ntdll (0x0034f1c8)
  12 0x7b8623d2 in kernel32 (+0x423d2) (0x0034f438)
  13 0x7b8626ab LoadLibraryExW+0x43() in kernel32 (0x0034f458)
  14 0x7b86278a LoadLibraryExA+0x43() in kernel32 (0x0034f478)
  15 0x7b8627c1 LoadLibraryA+0x2d() in kernel32 (0x0034f498)
  16 0x7eb69c15 in gdi32 (+0x19c15) (0x0034f628)
  17 0x7eb63940 CreateDCW+0x60() in gdi32 (0x0034f8d8)
  18 0x7ec10e25 CreateIconFromResourceEx+0x6c1() in user32 (0x0034f9a8)
  19 0x7ec113e4 in user32 (+0x313e4) (0x0034fa18)
  20 0x7ec13d5a LoadImageW+0x45f() in user32 (0x0034fab8)
  21 0x7ec14548 LoadImageA+0x1c0() in user32 (0x0034fbb8)
  22 0x7ec146fa LoadCursorA+0x55() in user32 (0x0034fbe8)
  23 0x7ec0888e in user32 (+0x2888e) (0x0034fc18)
  24 0x7ec088e1 in user32 (+0x288e1) (0x0034fc38)
  25 0x7ec7dc7e in user32 (+0x9dc7e) (0x0034fce8)
  26 0x7ec9176c in user32 (+0xb176c) (0x0034fd08)
  27 0x7bc42ebd call_dll_entry_point+0x15() in ntdll (0x0034fd28)
  28 0x7bc4537a in ntdll (+0x3537a) (0x0034fdb8)
  29 0x7bc45614 in ntdll (+0x35614) (0x0034fdf8)
  30 0x7bc45699 in ntdll (+0x35699) (0x0034fe38)
  31 0x7bc45699 in ntdll (+0x35699) (0x0034fe78)
  32 0x7bc45699 in ntdll (+0x35699) (0x0034feb8)
  33 0x7bc47f9f LdrInitializeThunk+0x27a() in ntdll (0x0034ff08)
  34 0x7b86eb0a in kernel32 (+0x4eb0a) (0x0034ffe8)
  35 0xb7e2d1cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7e44c4c9: movl        0xb8(%esi),%eax
Modules:
Module  Address                 Debug info      Name (49 modules)
ELF     7b800000-7b925000       Export          kernel32<elf>
  \-PE  7b820000-7b925000       \               kernel32
ELF     7bc00000-7bca1000       Export          ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e3ea000-7e3f4000       Deferred        libdrm.so.2
ELF     7e3f4000-7e650000       Export          r200_dri.so
ELF     7e650000-7e6da000       Export          libgl.so.1
ELF     7e6da000-7e6df000       Deferred        libxdmcp.so.6
ELF     7e6df000-7e6e2000       Deferred        libxau.so.6
ELF     7e6e2000-7e7d3000       Deferred        libx11.so.6
ELF     7e7d3000-7e7e1000       Deferred        libxext.so.6
ELF     7e7e1000-7e7e6000       Deferred        libxxf86vm.so.1
ELF     7e7e6000-7e7fe000       Deferred        libice.so.6
ELF     7e7fe000-7e806000       Deferred        libsm.so.6
ELF     7e817000-7e8a1000       Export          winex11<elf>
  \-PE  7e830000-7e8a1000       \               winex11
ELF     7e930000-7e950000       Deferred        libexpat.so.1
ELF     7e950000-7e97b000       Deferred        libfontconfig.so.1
ELF     7e97b000-7e990000       Deferred        libz.so.1
ELF     7e990000-7ea00000       Deferred        libfreetype.so.6
ELF     7ea00000-7ea14000       Deferred        lz32<elf>
  \-PE  7ea10000-7ea14000       \               lz32
ELF     7ea14000-7ea2d000       Deferred        version<elf>
  \-PE  7ea20000-7ea2d000       \               version
ELF     7ea2d000-7eaec000       Deferred        comctl32<elf>
  \-PE  7ea40000-7eaec000       \               comctl32
ELF     7eaec000-7eb35000       Deferred        advapi32<elf>
  \-PE  7eb00000-7eb35000       \               advapi32
ELF     7eb35000-7ebcc000       Export          gdi32<elf>
  \-PE  7eb50000-7ebcc000       \               gdi32
ELF     7ebcc000-7ed03000       Export          user32<elf>
  \-PE  7ebe0000-7ed03000       \               user32
ELF     7ed03000-7ed5a000       Deferred        shlwapi<elf>
  \-PE  7ed10000-7ed5a000       \               shlwapi
ELF     7ed5a000-7ee5e000       Deferred        shell32<elf>
  \-PE  7ed70000-7ee5e000       \               shell32
ELF     7ee5e000-7ee79000       Deferred        wineboot<elf>
  \-PE  7ee60000-7ee79000       \               wineboot
ELF     7ee79000-7ee91000       Deferred        libnsl.so.1
ELF     7ee91000-7ee9a000       Deferred        libnss_compat.so.2
ELF     7efca000-7efef000       Deferred        libm.so.6
ELF     7eff5000-7f000000       Deferred        libnss_files.so.2
ELF     b7ca3000-b7cad000       Deferred        libnss_nis.so.2
ELF     b7cae000-b7cb2000       Deferred        libdl.so.2
ELF     b7cb2000-b7dfc000       Deferred        libc.so.6
ELF     b7dfd000-b7e15000       Deferred        libpthread.so.0
ELF     b7e26000-b7f3a000       Export          libwine.so.1
ELF     b7f3c000-b7f58000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a (D) c:\windows\system32\wineboot.exe
        0000000b    0 <==
00000008 
        00000009    0
Backtrace:
=>1 0x7e44c4c9 in r200_dri.so (+0x584c9) (0x0034ecc8)
  2 0x7e67c705 in libgl.so.1 (+0x2c705) (0x0034ecf8)
  3 0x7e67b97e glXCreateContext+0x3e() in libgl.so.1 (0x0034ed28)
  4 0x7e864c1c in winex11 (+0x34c1c) (0x0034edb8)
  5 0x7e867a66 X11DRV_setup_opengl_visual+0x3c() in winex11 (0x0034eeb8)
  6 0x7e877514 in winex11 (+0x47514) (0x0034f098)
  7 0x7e88817c in winex11 (+0x5817c) (0x0034f0b8)
  8 0x7bc42ebd call_dll_entry_point+0x15() in ntdll (0x0034f0d8)
  9 0x7bc4537a in ntdll (+0x3537a) (0x0034f168)
  10 0x7bc45614 in ntdll (+0x35614) (0x0034f1a8)
  11 0x7bc47ca3 LdrLoadDll+0x67() in ntdll (0x0034f1c8)
  12 0x7b8623d2 in kernel32 (+0x423d2) (0x0034f438)
  13 0x7b8626ab LoadLibraryExW+0x43() in kernel32 (0x0034f458)
  14 0x7b86278a LoadLibraryExA+0x43() in kernel32 (0x0034f478)
  15 0x7b8627c1 LoadLibraryA+0x2d() in kernel32 (0x0034f498)
  16 0x7eb69c15 in gdi32 (+0x19c15) (0x0034f628)
  17 0x7eb63940 CreateDCW+0x60() in gdi32 (0x0034f8d8)
  18 0x7ec10e25 CreateIconFromResourceEx+0x6c1() in user32 (0x0034f9a8)
  19 0x7ec113e4 in user32 (+0x313e4) (0x0034fa18)
  20 0x7ec13d5a LoadImageW+0x45f() in user32 (0x0034fab8)
  21 0x7ec14548 LoadImageA+0x1c0() in user32 (0x0034fbb8)
  22 0x7ec146fa LoadCursorA+0x55() in user32 (0x0034fbe8)
  23 0x7ec0888e in user32 (+0x2888e) (0x0034fc18)
  24 0x7ec088e1 in user32 (+0x288e1) (0x0034fc38)
  25 0x7ec7dc7e in user32 (+0x9dc7e) (0x0034fce8)
  26 0x7ec9176c in user32 (+0xb176c) (0x0034fd08)
  27 0x7bc42ebd call_dll_entry_point+0x15() in ntdll (0x0034fd28)
  28 0x7bc4537a in ntdll (+0x3537a) (0x0034fdb8)
  29 0x7bc45614 in ntdll (+0x35614) (0x0034fdf8)
  30 0x7bc45699 in ntdll (+0x35699) (0x0034fe38)
  31 0x7bc45699 in ntdll (+0x35699) (0x0034fe78)
  32 0x7bc45699 in ntdll (+0x35699) (0x0034feb8)
  33 0x7bc47f9f LdrInitializeThunk+0x27a() in ntdll (0x0034ff08)
  34 0x7b86eb0a in kernel32 (+0x4eb0a) (0x0034ffe8)
  35 0xb7e2d1cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
wine: Unhandled page fault on read access to 0x000000b8 at address 0x7e6974c9 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x000000b8 in 32-bit code (0x7e6974c9).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e6974c9 ESP:0033ed20 EBP:0033ed48 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:00000000 ECX:7c037048 EDX:00000000
 ESI:00000000 EDI:7c045a08
Stack dump:
0x0033ed20:  0003fff4 00000000 0000004c 00000007
0x0033ed30:  7c045a08 00000000 00000000 00000000
0x0033ed40:  7c045a08 7c019740 0033ed78 7e8c7705
0x0033ed50:  7c045a08 00000000 00000000 00000000
0x0033ed60:  7c0197f0 00000190 7c037048 7eae6588
0x0033ed70:  00000033 7eaeb358 0033eda8 7e8c697e
Backtrace:
=>1 0x7e6974c9 in r200_dri.so (+0x584c9) (0x0033ed48)
  2 0x7e8c7705 in libgl.so.1 (+0x2c705) (0x0033ed78)
  3 0x7e8c697e glXCreateContext+0x3e() in libgl.so.1 (0x0033eda8)
  4 0x7eaafc1c in winex11 (+0x3fc1c) (0x0033ee38)
  5 0x7eab2a66 X11DRV_setup_opengl_visual+0x3c() in winex11 (0x0033ef38)
  6 0x7eac2514 in winex11 (+0x52514) (0x0033f118)
  7 0x7ead317c in winex11 (+0x6317c) (0x0033f138)
  8 0x7bc42ebd call_dll_entry_point+0x15() in ntdll (0x0033f158)
  9 0x7bc4537a in ntdll (+0x3537a) (0x0033f1e8)
  10 0x7bc45614 in ntdll (+0x35614) (0x0033f228)
  11 0x7bc47ca3 LdrLoadDll+0x67() in ntdll (0x0033f248)
  12 0x7b8623d2 in kernel32 (+0x423d2) (0x0033f4b8)
  13 0x7b8626ab LoadLibraryExW+0x43() in kernel32 (0x0033f4d8)
  14 0x7b86278a LoadLibraryExA+0x43() in kernel32 (0x0033f4f8)
  15 0x7b8627c1 LoadLibraryA+0x2d() in kernel32 (0x0033f518)
  16 0x7ecd9c15 in gdi32 (+0x19c15) (0x0033f6a8)
  17 0x7ecd3940 CreateDCW+0x60() in gdi32 (0x0033f958)
  18 0x7ed80e25 CreateIconFromResourceEx+0x6c1() in user32 (0x0033fa28)
  19 0x7ed813e4 in user32 (+0x313e4) (0x0033fa98)
  20 0x7ed83d5a LoadImageW+0x45f() in user32 (0x0033fb38)
  21 0x7ed84548 LoadImageA+0x1c0() in user32 (0x0033fc38)
  22 0x7ed846fa LoadCursorA+0x55() in user32 (0x0033fc68)
  23 0x7ed7888e in user32 (+0x2888e) (0x0033fc98)
  24 0x7ed788e1 in user32 (+0x288e1) (0x0033fcb8)
  25 0x7ededc7e in user32 (+0x9dc7e) (0x0033fd68)
  26 0x7ee0176c in user32 (+0xb176c) (0x0033fd88)
  27 0x7bc42ebd call_dll_entry_point+0x15() in ntdll (0x0033fda8)
  28 0x7bc4537a in ntdll (+0x3537a) (0x0033fe38)
  29 0x7bc45614 in ntdll (+0x35614) (0x0033fe78)
  30 0x7bc45699 in ntdll (+0x35699) (0x0033feb8)
  31 0x7bc47f9f LdrInitializeThunk+0x27a() in ntdll (0x0033ff08)
  32 0x7b86eb0a in kernel32 (+0x4eb0a) (0x0033ffe8)
  33 0xb7dfa1cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7e6974c9: movl        0xb8(%esi),%eax
Modules:
Module  Address                 Debug info      Name (39 modules)
ELF     7b800000-7b925000       Export          kernel32<elf>
  \-PE  7b820000-7b925000       \               kernel32
ELF     7bc00000-7bca1000       Export          ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e635000-7e63f000       Deferred        libdrm.so.2
ELF     7e63f000-7e89b000       Export          r200_dri.so
ELF     7e89b000-7e925000       Export          libgl.so.1
ELF     7e925000-7e92a000       Deferred        libxdmcp.so.6
ELF     7e92a000-7e92d000       Deferred        libxau.so.6
ELF     7e92d000-7ea1e000       Deferred        libx11.so.6
ELF     7ea1e000-7ea2c000       Deferred        libxext.so.6
ELF     7ea2c000-7ea31000       Deferred        libxxf86vm.so.1
ELF     7ea31000-7ea49000       Deferred        libice.so.6
ELF     7ea49000-7ea51000       Deferred        libsm.so.6
ELF     7ea62000-7eaec000       Export          winex11<elf>
  \-PE  7ea70000-7eaec000       \               winex11
ELF     7eb7b000-7eb9b000       Deferred        libexpat.so.1
ELF     7eb9b000-7ebc6000       Deferred        libfontconfig.so.1
ELF     7ebc6000-7ebdb000       Deferred        libz.so.1
ELF     7ebdb000-7ec4b000       Deferred        libfreetype.so.6
ELF     7ec5c000-7eca5000       Deferred        advapi32<elf>
  \-PE  7ec70000-7eca5000       \               advapi32
ELF     7eca5000-7ed3c000       Export          gdi32<elf>
  \-PE  7ecc0000-7ed3c000       \               gdi32
ELF     7ed3c000-7ee73000       Export          user32<elf>
  \-PE  7ed50000-7ee73000       \               user32
ELF     7ee73000-7ee88000       Deferred        rundll32<elf>
  \-PE  7ee80000-7ee88000       \               rundll32
ELF     7efa7000-7efb2000       Deferred        libnss_files.so.2
ELF     7efb2000-7efca000       Deferred        libnsl.so.1
ELF     7efca000-7efef000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7c71000-b7c7a000       Deferred        libnss_compat.so.2
ELF     b7c7b000-b7c7f000       Deferred        libdl.so.2
ELF     b7c7f000-b7dc9000       Deferred        libc.so.6
ELF     b7dca000-b7de2000       Deferred        libpthread.so.0
ELF     b7df3000-b7f07000       Export          libwine.so.1
ELF     b7f09000-b7f25000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) c:\windows\system32\rundll32.exe
        00000009    0 <==
Backtrace:
=>1 0x7e6974c9 in r200_dri.so (+0x584c9) (0x0033ed48)
  2 0x7e8c7705 in libgl.so.1 (+0x2c705) (0x0033ed78)
  3 0x7e8c697e glXCreateContext+0x3e() in libgl.so.1 (0x0033eda8)
  4 0x7eaafc1c in winex11 (+0x3fc1c) (0x0033ee38)
  5 0x7eab2a66 X11DRV_setup_opengl_visual+0x3c() in winex11 (0x0033ef38)
  6 0x7eac2514 in winex11 (+0x52514) (0x0033f118)
  7 0x7ead317c in winex11 (+0x6317c) (0x0033f138)
  8 0x7bc42ebd call_dll_entry_point+0x15() in ntdll (0x0033f158)
  9 0x7bc4537a in ntdll (+0x3537a) (0x0033f1e8)
  10 0x7bc45614 in ntdll (+0x35614) (0x0033f228)
  11 0x7bc47ca3 LdrLoadDll+0x67() in ntdll (0x0033f248)
  12 0x7b8623d2 in kernel32 (+0x423d2) (0x0033f4b8)
  13 0x7b8626ab LoadLibraryExW+0x43() in kernel32 (0x0033f4d8)
  14 0x7b86278a LoadLibraryExA+0x43() in kernel32 (0x0033f4f8)
  15 0x7b8627c1 LoadLibraryA+0x2d() in kernel32 (0x0033f518)
  16 0x7ecd9c15 in gdi32 (+0x19c15) (0x0033f6a8)
  17 0x7ecd3940 CreateDCW+0x60() in gdi32 (0x0033f958)
  18 0x7ed80e25 CreateIconFromResourceEx+0x6c1() in user32 (0x0033fa28)
  19 0x7ed813e4 in user32 (+0x313e4) (0x0033fa98)
  20 0x7ed83d5a LoadImageW+0x45f() in user32 (0x0033fb38)
  21 0x7ed84548 LoadImageA+0x1c0() in user32 (0x0033fc38)
  22 0x7ed846fa LoadCursorA+0x55() in user32 (0x0033fc68)
  23 0x7ed7888e in user32 (+0x2888e) (0x0033fc98)
  24 0x7ed788e1 in user32 (+0x288e1) (0x0033fcb8)
  25 0x7ededc7e in user32 (+0x9dc7e) (0x0033fd68)
  26 0x7ee0176c in user32 (+0xb176c) (0x0033fd88)
  27 0x7bc42ebd call_dll_entry_point+0x15() in ntdll (0x0033fda8)
  28 0x7bc4537a in ntdll (+0x3537a) (0x0033fe38)
  29 0x7bc45614 in ntdll (+0x35614) (0x0033fe78)
  30 0x7bc45699 in ntdll (+0x35699) (0x0033feb8)
  31 0x7bc47f9f LdrInitializeThunk+0x27a() in ntdll (0x0033ff08)
  32 0x7b86eb0a in kernel32 (+0x4eb0a) (0x0033ffe8)
  33 0xb7dfa1cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)

```

Any clues to how to fix this?

Thanks.

---

### Post by hikaricore on 2008-01-15
My only thoughts are this:

**> [B]Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".**

1. Have you properly installed your video drivers?  This shouldn't cause WINE to crash, but it very well could.[/B]

2. For any reason are you attemping to run a 32bit version of WINE on a 64bit Linux installation or vise versa?

3. Hmm...  You may want to try completely removing (and purging) WINE and reinstalling it. 
Something may have gone terribly terribly wrong on the installation.

---

### Post by GreaterCore on 2008-01-16
Dear all,

I have tried reinstalling wine a few times but that still did not bring any effect. I do suspect it is my graphics drivers, since I can't seem to get OpenGL to run properly. However, I did manage to get dual-head up, and can run emulator games pretty well.

How do I go about reinstalling my graphics drivers properly? It is a "ATI M9 with 64MB DDR", but it seems the proprietary drivers are not working properly, and neither is the free ones available.

I do hope to run some of my windows programs like game maker and the sorts on it to test out some new development.

Thanks all.

---

### Post by Equiflux on 2008-01-27
> **hikaricore said:**
> Try:



This should run upon installation but sometime it does not.
This should create the directory structure in your home directory, assuming the drive is not full or damaged.

Thanks. I had a similar problem, but that fixed it!

---

