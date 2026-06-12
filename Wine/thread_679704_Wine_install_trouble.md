---
title: "Wine install trouble"
date: 2008-01-27
forum: Wine
---

### Post by tsali on 2008-01-27
Running Ubuntu 7.10
Installed wine from add/remove programs list.
Rebooted the computer.

Tried to click "Configure Wine" - no response

Opened Terminal and typed: 'winecfg' - received a massive listing of page faults and errors.

Tried again using 'sudo winecfg' - same massive list of errors

I have tried uninstalling and re-installing. I have tried 'dpkg-reconfigure'

So, in keeping with the instruction in the sticky above:

   1. Wine version - wine-0.9.46
   2. Terminal output - 
```
sudo winecfg
wine: creating configuration directory '/home/chuck/.wine'...
wine: Unhandled page fault on read access to 0x00000000 at address 0xb7d5acb3 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0xb7d5acb3).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7d5acb3 ESP:0033ee7c EBP:0033ee98 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:b7e1dff4 ECX:00000000 EDX:00000000
 ESI:00000033 EDI:00000000
Stack dump:
0x0033ee7c:  b7d5a9e5 00000000 00000048 00000048
0x0033ee8c:  7eb1488c 00000033 00000000 0033ef18
0x0033ee9c:  7eadc7c2 00000000 00000048 7c01bc98
0x0033eeac:  00000001 7c038790 00000000 00000000
0x0033eebc:  00000000 7c01bc98 7c03ccd8 00000048
0x0033eecc:  0033efd4 0033ef28 0033efc4 0033efa4
Backtrace:
=>1 0xb7d5acb3 strlen+0x33() in libc.so.6 (0x0033ee98)
  2 0x7eadc7c2 has_opengl+0x7c2() [/build/buildd/wine-0.9.46/dlls/winex11.drv/opengl.c:331] in winex11 (0x0033ef18)
  3 0x7eadd0e0 X11DRV_setup_opengl_visual+0x130(display=0x7c038790) [/build/buildd/wine-0.9.46/dlls/winex11.drv/opengl.c:3384] in winex11 (0x0033eff8)
  4 0x7eaf03a4 DllMain+0xbc4(hinst=0x7eaa0000, reason=0x1, reserved=0x0) [/build/buildd/wine-0.9.46/dlls/winex11.drv/x11drv_main.c:483] in winex11 (0x0033f158)
  5 0x7eb01173 __wine_spec_dll_entry+0xb3(inst=0x7eaa0000, reason=<register ESI not in topmost frame>, reserved=<register EDI not in topmost frame>) [/build/buildd/wine-0.9.46/dlls/winecrt0/dll_entry.c:40] in winex11 (0x0033f178)
  6 0x7bc41cf5 call_dll_entry_point+0x15() in ntdll (0x0033f198)
  7 0x7bc436bd MODULE_InitDLL+0x8d(wm=<register EDI not in topmost frame>, reason=<register ESI not in topmost frame>, lpReserved=0x0) [/build/buildd/wine-0.9.46/dlls/ntdll/loader.c:890] in ntdll (0x0033f228)
  8 0x7bc43d14 process_attach+0x174(wm=<register EDI not in topmost frame>, lpReserved=0x0) [/build/buildd/wine-0.9.46/dlls/ntdll/loader.c:963] in ntdll (0x0033f278)
  9 0x7bc45ac7 LdrLoadDll+0x87(path_name=0x11cc50, flags=0x0, libname=0x33f524, hModule=0x33f4f8) [/build/buildd/wine-0.9.46/dlls/ntdll/loader.c:1916] in ntdll (0x0033f2a8)
  10 0x7b865de0 load_library+0x120(libname=<register EDI not in topmost frame>, flags=<register ESI not in topmost frame>) [/build/buildd/wine-0.9.46/dlls/kernel32/module.c:870] in kernel32 (0x0033f508)
  11 0x7b865ff0 LoadLibraryExW+0x50(libnameW=<register ESI not in topmost frame>, hfile=0x0, flags=0x0) [/build/buildd/wine-0.9.46/dlls/kernel32/module.c:927] in kernel32 (0x0033f538)
  12 0x7b866113 LoadLibraryExA+0x43(libname=0x33f6c8, hfile=0x0, flags=0x0) [/build/buildd/wine-0.9.46/dlls/kernel32/module.c:907] in kernel32 (0x0033f558)
  13 0x7b86614d LoadLibraryA+0x2d(libname=0x33f6c8) [/build/buildd/wine-0.9.46/dlls/kernel32/module.c:960] in kernel32 (0x0033f578)
  14 0x7ecd7014 DRIVER_load_driver+0x1e4(name=0x33f744) [/build/buildd/wine-0.9.46/dlls/gdi32/driver.c:253] in gdi32 (0x0033f6f8)
  15 0x7ecd15e0 CreateDCW+0x60(driver=<is not available>, device=0x0, output=0x0, initData=0x0) [/build/buildd/wine-0.9.46/dlls/gdi32/dc.c:706] in gdi32 (0x0033f9a8)
  16 0x7ed84120 CreateIconFromResourceEx+0x420(bits=0x7ee294fc, cbSize=0x134, bIcon=0x0, dwVersion=0x30000, width=0x20, height=0x20, cFlag=0x8040) [/build/buildd/wine-0.9.46/dlls/user32/cursoricon.c:725] in user32 (0x0033fa48)
  17 0x7ed84b37 CURSORICON_Load+0x3c7(hInstance=0x7ed60000, name=0x7f00, width=0x20, height=0x20, colors=0x1, fCursor=0x1, loadflags=0x8040) [/build/buildd/wine-0.9.46/dlls/user32/cursoricon.c:996] in user32 (0x0033fac8)
  18 0x7ed85ddb LoadImageW+0x3fb(hinst=<register ESI not in topmost frame>, name=0x7f00, type=0x2, desiredx=0x20, desiredy=0x20, loadflags=<is not available>) [/build/buildd/wine-0.9.46/dlls/user32/cursoricon.c:2302] in user32 (0x0033fb68)
  19 0x7ed86376 LoadImageA+0x56(hinst=0x0, name=0x7f00, type=0x2, desiredx=0x0, desiredy=0x0, loadflags=0x8040) [/build/buildd/wine-0.9.46/dlls/user32/cursoricon.c:2231] in user32 (0x0033fc48)
  20 0x7ed86867 LoadCursorA+0x97(hInstance=<register EDI not in topmost frame>, name=<register ESI not in topmost frame>) [/build/buildd/wine-0.9.46/dlls/user32/cursoricon.c:1685] in user32 (0x0033fc78)
  21 0x7ed7b40f register_builtin+0x7f(descr=<register ESI not in topmost frame>) [/build/buildd/wine-0.9.46/dlls/user32/class.c:379] in user32 (0x0033fc98)
  22 0x7ed7b45d CLASS_RegisterBuiltinClasses+0x1d() [/build/buildd/wine-0.9.46/dlls/user32/class.c:406] in user32 (0x0033fcb8)
  23 0x7edf1602 DllMain+0x182(inst=0x7ed60000, reason=0x1, reserved=0x1) [/build/buildd/wine-0.9.46/dlls/user32/user_main.c:228] in user32 (0x0033fd38)
  24 0x7ee060a3 __wine_spec_dll_entry+0xb3(inst=0x7ed60000, reason=<register ESI not in topmost frame>, reserved=<register EDI not in topmost frame>) [/build/buildd/wine-0.9.46/dlls/winecrt0/dll_entry.c:40] in user32 (0x0033fd58)
  25 0x7bc41cf5 call_dll_entry_point+0x15() in ntdll (0x0033fd78)
  26 0x7bc436bd MODULE_InitDLL+0x8d(wm=<register EDI not in topmost frame>, reason=<register ESI not in topmost frame>, lpReserved=0x1) [/build/buildd/wine-0.9.46/dlls/ntdll/loader.c:890] in ntdll (0x0033fe08)
  27 0x7bc43d14 process_attach+0x174(wm=<register EDI not in topmost frame>, lpReserved=0x1) [/build/buildd/wine-0.9.46/dlls/ntdll/loader.c:963] in ntdll (0x0033fe58)
  28 0x7bc43c42 process_attach+0xa2(wm=<register EDI not in topmost frame>, lpReserved=0x1) [/build/buildd/wine-0.9.46/dlls/ntdll/loader.c:955] in ntdll (0x0033fea8)
  29 0x7bc467c6 LdrInitializeThunk+0x2b6(unknown1=0x0, unknown2=0x0, unknown3=0x0, unknown4=0x0) [/build/buildd/wine-0.9.46/dlls/ntdll/loader.c:2316] in ntdll (0x0033ff08)
  30 0x7b874c4a start_process+0xba(arg=0x0) [/build/buildd/wine-0.9.46/dlls/kernel32/process.c:829] in kernel32 (0x0033ffe8)
  31 0xb7e4c9d7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0xb7d5acb3 strlen+0x33 in libc.so.6: movl       0x0(%eax),%ecx
Modules:
Module  Address                 Debug info      Name (41 modules)
ELF     7b800000-7b929000       Dwarf           kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Dwarf           ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e6bb000-7e8e5000       Deferred        unichrome_dri.so
ELF     7e8e5000-7e8ef000       Deferred        libdrm.so.2
ELF     7e8ef000-7e8f4000       Deferred        libxfixes.so.3
ELF     7e8f4000-7e8f7000       Deferred        libxdamage.so.1
ELF     7e8f7000-7e958000       Deferred        libgl.so.1
ELF     7e958000-7e95d000       Deferred        libxdmcp.so.6
ELF     7e95d000-7e960000       Deferred        libxau.so.6
ELF     7e960000-7ea51000       Deferred        libx11.so.6
ELF     7ea51000-7ea5f000       Deferred        libxext.so.6
ELF     7ea5f000-7ea64000       Deferred        libxxf86vm.so.1
ELF     7ea64000-7ea7c000       Deferred        libice.so.6
ELF     7ea7c000-7ea84000       Deferred        libsm.so.6
ELF     7ea8f000-7eb1a000       Dwarf           winex11<elf>
  \-PE  7eaa0000-7eb1a000       \               winex11
ELF     7eb7a000-7eb9a000       Deferred        libexpat.so.1
ELF     7eb9a000-7ebc5000       Deferred        libfontconfig.so.1
ELF     7ebc5000-7ebda000       Deferred        libz.so.1
ELF     7ebda000-7ec4a000       Deferred        libfreetype.so.6
ELF     7ec55000-7ec9e000       Deferred        advapi32<elf>
  \-PE  7ec60000-7ec9e000       \               advapi32
ELF     7ec9e000-7ed39000       Dwarf           gdi32<elf>
  \-PE  7ecb0000-7ed39000       \               gdi32
ELF     7ed39000-7ee77000       Dwarf           user32<elf>
  \-PE  7ed60000-7ee77000       \               user32
ELF     7ee77000-7ee8c000       Deferred        rundll32<elf>
  \-PE  7ee80000-7ee8c000       \               rundll32
ELF     7efaf000-7efb9000       Deferred        libnss_files.so.2
ELF     7efb9000-7efd0000       Deferred        libnsl.so.1
ELF     7efd0000-7eff5000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7ce1000-b7ce9000       Deferred        libnss_compat.so.2
ELF     b7cea000-b7cee000       Deferred        libdl.so.2
ELF     b7cee000-b7e22000       Export          libc.so.6
ELF     b7e23000-b7e3a000       Deferred        libpthread.so.0
ELF     b7e45000-b7f59000       Dwarf           libwine.so.1
ELF     b7f5a000-b7f76000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) c:\windows\system32\rundll32.exe
        00000009    0 <==
wine: wineprefixcreate failed while creating '/home/chuck/.wine'.
chuck@AsusC3:~$ wineserver: could not save registry branch to /home/chuck/.wine-iMcDan/system.reg : No such file or directory
wineserver: could not save registry branch to /home/chuck/.wine-iMcDan/user.reg : No such file or directory

```
   3. Wine configuration - no configuration; unable to run wine config
   4. Hardware specs/drivers - from installation report:
```
umame -a: Linux AsusC3 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux
lspci -nn: 00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8623 [Apollo CLE266] [1106:3123]
lspci -nn: 00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP] [1106:b091]
lspci -nn: 00:09.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. IEEE 1394 Host Controller [1106:3044] (rev 80)
lspci -nn: 00:0f.0 RAID bus controller [0104]: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller [1106:3149] (rev 80)
lspci -nn: 00:0f.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
lspci -nn: 00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
lspci -nn: 00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
lspci -nn: 00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
lspci -nn: 00:10.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
lspci -nn: 00:10.4 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 86)
lspci -nn: 00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South] [1106:3227]
lspci -nn: 00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 60)
lspci -nn: 00:11.6 Communication controller [0780]: VIA Technologies, Inc. AC'97 Modem Controller [1106:3068] (rev 80)
lspci -nn: 00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 78)
lspci -nn: 01:00.0 VGA compatible controller [0300]: VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics [1106:3122] (rev 03)
lspci -vnn: 00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8623 [Apollo CLE266] [1106:3123]
lspci -vnn: 	Subsystem: ASUSTeK Computer Inc. Unknown device [1043:8155]
lspci -vnn: 	Flags: bus master, 66MHz, medium devsel, latency 8
lspci -vnn: 	Memory at e0000000 (32-bit, prefetchable) [size=64M]
lspci -vnn: 	Capabilities: [a0] AGP version 2.0
lspci -vnn: 	Capabilities: [c0] Power Management version 2
lspci -vnn: 
lspci -vnn: 00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP] [1106:b091] (prog-if 00 [Normal decode])
lspci -vnn: 	Flags: bus master, 66MHz, medium devsel, latency 0
lspci -vnn: 	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
lspci -vnn: 	Memory behind bridge: e8000000-e9ffffff
lspci -vnn: 	Prefetchable memory behind bridge: e4000000-e7ffffff
lspci -vnn: 	Capabilities: [80] Power Management version 2
lspci -vnn: 
lspci -vnn: 00:09.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. IEEE 1394 Host Controller [1106:3044] (rev 80) (prog-if 10 [OHCI])
lspci -vnn: 	Subsystem: ASUSTeK Computer Inc. A8V Deluxe or A8N-VM CSM Mainboard [1043:808a]
lspci -vnn: 	Flags: bus master, medium devsel, latency 32, IRQ 11
lspci -vnn: 	Memory at ea000000 (32-bit, non-prefetchable) [size=2K]
lspci -vnn: 	I/O ports at 9000 [size=128]
lspci -vnn: 	Capabilities: [50] Power Management version 2
lspci -vnn: 
lspci -vnn: 00:0f.0 RAID bus controller [0104]: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller [1106:3149] (rev 80)
lspci -vnn: 	Subsystem: ASUSTeK Computer Inc. A7V600/K8V Deluxe/K8V-X/A8V Deluxe motherboard [1043:80ed]
lspci -vnn: 	Flags: bus master, medium devsel, latency 32, IRQ 11
lspci -vnn: 	I/O ports at 9400 [size=8]
lspci -vnn: 	I/O ports at 9800 [size=4]
lspci -vnn: 	I/O ports at 9c00 [size=8]
lspci -vnn: 	I/O ports at a000 [size=4]
lspci -vnn: 	I/O ports at a400 [size=16]
lspci -vnn: 	I/O ports at a800 [size=256]
lspci -vnn: 	Capabilities: [c0] Power Management version 2
lspci -vnn: 
lspci -vnn: 00:0f.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06) (prog-if 8a [Master SecP PriP])
lspci -vnn: 	Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard [1043:80ed]
lspci -vnn: 	Flags: bus master, medium devsel, latency 32, IRQ 10
lspci -vnn: 	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
lspci -vnn: 	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
lspci -vnn: 	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
lspci -vnn: 	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
lspci -vnn: 	I/O ports at ac00 [size=16]
lspci -vnn: 	Capabilities: [c0] Power Management version 2
lspci -vnn: 
lspci -vnn: 00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81) (prog-if 00 [UHCI])
lspci -vnn: 	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038]
lspci -vnn: 	Flags: bus master, medium devsel, latency 32, IRQ 10
lspci -vnn: 	I/O ports at b000 [size=32]
lspci -vnn: 	Capabilities: [80] Power Management version 2
lspci -vnn: 
lspci -vnn: 00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81) (prog-if 00 [UHCI])
lspci -vnn: 	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038]
lspci -vnn: 	Flags: bus master, medium devsel, latency 32, IRQ 10
lspci -vnn: 	I/O ports at b400 [size=32]
lspci -vnn: 	Capabilities: [80] Power Management version 2
lspci -vnn: 
lspci -vnn: 00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81) (prog-if 00 [UHCI])
lspci -vnn: 	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038]
lspci -vnn: 	Flags: bus master, medium devsel, latency 32, IRQ 11
lspci -vnn: 	I/O ports at b800 [size=32]
lspci -vnn: 	Capabilities: [80] Power Management version 2
lspci -vnn: 
lspci -vnn: 00:10.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81) (prog-if 00 [UHCI])
lspci -vnn: 	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038]
lspci -vnn: 	Flags: bus master, medium devsel, latency 32, IRQ 11
lspci -vnn: 	I/O ports at bc00 [size=32]
lspci -vnn: 	Capabilities: [80] Power Management version 2
lspci -vnn: 
lspci -vnn: 00:10.4 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 86) (prog-if 20 [EHCI])
lspci -vnn: 	Subsystem: VIA Technologies, Inc. USB 2.0 [1106:3104]
lspci -vnn: 	Flags: bus master, medium devsel, latency 32, IRQ 11
lspci -vnn: 	Memory at ea001000 (32-bit, non-prefetchable) [size=256]
lspci -vnn: 	Capabilities: [80] Power Management version 2
lspci -vnn: 
lspci -vnn: 00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South] [1106:3227]
lspci -vnn: 	Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard [1043:80ed]
lspci -vnn: 	Flags: bus master, stepping, medium devsel, latency 0
lspci -vnn: 	Capabilities: [c0] Power Management version 2
lspci -vnn: 
lspci -vnn: 00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 60)
lspci -vnn: 	Subsystem: ASUSTeK Computer Inc. Unknown device [1043:810d]
lspci -vnn: 	Flags: medium devsel, IRQ 11
lspci -vnn: 	I/O ports at c000 [size=256]
lspci -vnn: 	Capabilities: [c0] Power Management version 2
lspci -vnn: 
lspci -vnn: 00:11.6 Communication controller [0780]: VIA Technologies, Inc. AC'97 Modem Controller [1106:3068] (rev 80)
lspci -vnn: 	Flags: medium devsel, IRQ 11
lspci -vnn: 	I/O ports at c400 [size=256]
lspci -vnn: 	Capabilities: [d0] Power Management version 2
lspci -vnn: 
lspci -vnn: 00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 78)
lspci -vnn: 	Subsystem: ASUSTeK Computer Inc. Unknown device [1043:80ff]
lspci -vnn: 	Flags: bus master, medium devsel, latency 32, IRQ 10
lspci -vnn: 	I/O ports at c800 [size=256]
lspci -vnn: 	Memory at ea002000 (32-bit, non-prefetchable) [size=256]
lspci -vnn: 	Capabilities: [40] Power Management version 2
lspci -vnn: 
lspci -vnn: 01:00.0 VGA compatible controller [0300]: VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics [1106:3122] (rev 03) (prog-if 00 [VGA])
lspci -vnn: 	Subsystem: ASUSTeK Computer Inc. Unknown device [1043:8155]
lspci -vnn: 	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 10
lspci -vnn: 	Memory at e4000000 (32-bit, prefetchable) [size=64M]
lspci -vnn: 	Memory at e8000000 (32-bit, non-prefetchable) [size=16M]
lspci -vnn: 	[virtual] Expansion ROM at e9000000 [disabled] [size=64K]
lspci -vnn: 	Capabilities: [60] Power Management version 2
lspci -vnn: 	Capabilities: [70] AGP version 2.0
lspci -vnn: 
modulemap: 1106:3123 via_agp
modulemap: 1106:3044 ohci1394
modulemap: 1106:3149 sata_via
modulemap: 1106:0571 via82cxxx
modulemap: 1106:3038 uhci_hcd
modulemap: 1106:3038 uhci_hcd
modulemap: 1106:3038 uhci_hcd
modulemap: 1106:3038 uhci_hcd
modulemap: 1106:3104 ehci_hcd
modulemap: 1106:3059 snd_via82xx
modulemap: 1106:3065 via_rhine
modulemap: 1106:3122 vt8623fb
lsmod: Module                  Size  Used by
lsmod: ipv6                  273892  10 
lsmod: af_packet              24840  2 
lsmod: binfmt_misc            12936  1 
lsmod: via                    43904  2 
lsmod: drm                    83348  3 via
lsmod: rfcomm                 42136  2 
lsmod: l2cap                  26240  11 rfcomm
lsmod: bluetooth              57060  4 rfcomm,l2cap
lsmod: ppdev                  10244  0 
lsmod: cpufreq_stats           7232  0 
lsmod: cpufreq_ondemand        9612  0 
lsmod: freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
lsmod: cpufreq_powersave       2688  0 
lsmod: cpufreq_userspace       5280  0 
lsmod: cpufreq_conservative     8072  0 
lsmod: sbs                    19592  0 
lsmod: button                  8976  0 
lsmod: container               5504  0 
lsmod: dock                   10656  0 
lsmod: video                  18060  0 
lsmod: ac                      6148  0 
lsmod: battery                11012  0 
lsmod: sbp2                   24072  0 
lsmod: lp                     12580  0 
lsmod: snd_via82xx            29336  1 
lsmod: snd_pcm_oss            44672  0 
lsmod: snd_mixer_oss          17664  1 snd_pcm_oss
lsmod: snd_via82xx_modem      16264  0 
lsmod: snd_ac97_codec        100644  2 snd_via82xx,snd_via82xx_modem
lsmod: ac97_bus                3200  1 snd_ac97_codec
lsmod: snd_seq_dummy           4740  0 
lsmod: snd_pcm                80388  4 snd_via82xx,snd_pcm_oss,snd_via82xx_modem,snd_ac97_codec
lsmod: snd_seq_oss            33152  0 
lsmod: snd_mpu401_uart         9600  1 snd_via82xx
lsmod: parport_pc             37412  1 
lsmod: snd_seq_midi            9600  0 
lsmod: parport                37448  3 ppdev,lp,parport_pc
lsmod: pcspkr                  4224  0 
lsmod: snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
lsmod: serio_raw               8068  0 
lsmod: snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
lsmod: analog                 13344  0 
lsmod: gameport               16776  2 snd_via82xx,analog
lsmod: psmouse                39952  0 
lsmod: snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
lsmod: snd_timer              24324  2 snd_pcm,snd_seq
lsmod: snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lsmod: usbhid                 29536  0 
lsmod: i2c_viapro             10004  0 
lsmod: snd                    54660  14 snd_via82xx,snd_pcm_oss,snd_mixer_oss,snd_via82xx_modem,snd_ac97_codec,snd_pcm,snd_seq_oss,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lsmod: soundcore               8800  1 snd
lsmod: snd_page_alloc         11400  3 snd_via82xx,snd_via82xx_modem,snd_pcm
lsmod: hid                    28928  1 usbhid
lsmod: vt8623fb               18560  0 
lsmod: i2c_core               26112  1 i2c_viapro
lsmod: ide_cd                 32672  0 
lsmod: cdrom                  37536  1 ide_cd
lsmod: svgalib                10624  1 vt8623fb
lsmod: vgastate               11008  1 vt8623fb
lsmod: via_agp                11264  1 
lsmod: agpgart                35016  2 drm,via_agp
lsmod: shpchp                 34580  0 
lsmod: pci_hotplug            32704  1 shpchp
lsmod: evdev                  11136  4 
lsmod: ext3                  133896  1 
lsmod: jbd                    60456  1 ext3
lsmod: mbcache                 9732  1 ext3
lsmod: sg                     36764  0 
lsmod: sd_mod                 30336  3 
lsmod: floppy                 60004  0 
lsmod: via_rhine              25992  0 
lsmod: mii                     6528  1 via_rhine
lsmod: via82cxxx              10372  0 [permanent]
lsmod: ide_core              116804  2 ide_cd,via82cxxx
lsmod: ehci_hcd               36492  0 
lsmod: uhci_hcd               26640  0 
lsmod: usbcore               138632  4 usbhid,ehci_hcd,uhci_hcd
lsmod: ata_generic             8452  0 
lsmod: sata_via               12548  2 
lsmod: libata                125168  2 ata_generic,sata_via
lsmod: scsi_mod              147084  4 sbp2,sg,sd_mod,libata
lsmod: ohci1394               36528  0 
lsmod: ieee1394               96312  2 sbp2,ohci1394
lsmod: thermal                14344  0 
lsmod: processor              32072  1 thermal
lsmod: fan                     5764  0 
lsmod: fuse                   47124  1 
lsmod: apparmor               40728  0 
lsmod: commoncap               8320  1 apparmor
df: Filesystem           1K-blocks      Used Available Use% Mounted on
df: /dev/sda1            238971552   3749992 223082448   2% /
df: varrun                  241424        88    241336   1% /var/run
df: varlock                 241424         0    241424   0% /var/lock
df: udev                    241424        68    241356   1% /dev
df: devshm                  241424         0    241424   0% /dev/shm
df: lrm                     241424     34696    206728  15% /lib/modules/2.6.22-14-generic/volatile
free:              total       used       free     shared    buffers     cached
free: Mem:        482852     450788      32064          0      11536     217840
free: -/+ buffers/cache:     221412     261440
free: Swap:      1413680          0    1413680
cardctl status: /usr/bin/report-hw: 50: cardctl: not found
cardctl ident: /usr/bin/report-hw: 51: cardctl: not found
/proc/cpuinfo: processor	: 0
/proc/cpuinfo: vendor_id	: CentaurHauls
/proc/cpuinfo: cpu family	: 6
/proc/cpuinfo: model		: 7
/proc/cpuinfo: model name	: VIA Samuel 2
/proc/cpuinfo: stepping	: 3
/proc/cpuinfo: cpu MHz		: 800.083
/proc/cpuinfo: cache size	: 64 KB
/proc/cpuinfo: fdiv_bug	: no
/proc/cpuinfo: hlt_bug		: no
/proc/cpuinfo: f00f_bug	: no
/proc/cpuinfo: coma_bug	: no
/proc/cpuinfo: fpu		: yes
/proc/cpuinfo: fpu_exception	: yes
/proc/cpuinfo: cpuid level	: 1
/proc/cpuinfo: wp		: yes
/proc/cpuinfo: flags		: fpu de tsc msr cx8 mtrr pge mmx 3dnow up
/proc/cpuinfo: bogomips	: 1602.42
/proc/cpuinfo: clflush size	: 32
/proc/cpuinfo: 
/proc/ioports: 0000-001f : dma1
/proc/ioports: 0020-0021 : pic1
/proc/ioports: 0040-0043 : timer0
/proc/ioports: 0050-0053 : timer1
/proc/ioports: 0060-006f : keyboard
/proc/ioports: 0070-0077 : rtc
/proc/ioports: 0080-008f : dma page reg
/proc/ioports: 00a0-00a1 : pic2
/proc/ioports: 00c0-00df : dma2
/proc/ioports: 00f0-00ff : fpu
/proc/ioports: 0170-0177 : 0000:00:0f.1
/proc/ioports: 01f0-01f7 : 0000:00:0f.1
/proc/ioports:   01f0-01f7 : ide0
/proc/ioports: 0376-0376 : 0000:00:0f.1
/proc/ioports: 0378-037a : parport0
/proc/ioports: 03c0-03df : vga+
/proc/ioports: 03f2-03f5 : floppy
/proc/ioports: 03f6-03f6 : 0000:00:0f.1
/proc/ioports:   03f6-03f6 : ide0
/proc/ioports: 03f7-03f7 : floppy DIR
/proc/ioports: 03f8-03ff : serial
/proc/ioports: 0cf8-0cff : PCI conf1
/proc/ioports: 4000-407f : pnp 00:02
/proc/ioports:   4000-4003 : ACPI PM1a_EVT_BLK
/proc/ioports:   4008-400b : ACPI PM_TMR
/proc/ioports:   4010-4015 : ACPI CPU throttle
/proc/ioports:   4020-4023 : ACPI GPE0_BLK
/proc/ioports: 40f0-40f1 : ACPI PM1a_CNT_BLK
/proc/ioports: 5000-500f : pnp 00:02
/proc/ioports:   5000-5007 : vt596_smbus
/proc/ioports: 9000-907f : 0000:00:09.0
/proc/ioports: 9400-9407 : 0000:00:0f.0
/proc/ioports:   9400-9407 : libata
/proc/ioports: 9800-9803 : 0000:00:0f.0
/proc/ioports:   9800-9803 : libata
/proc/ioports: 9c00-9c07 : 0000:00:0f.0
/proc/ioports:   9c00-9c07 : libata
/proc/ioports: a000-a003 : 0000:00:0f.0
/proc/ioports:   a000-a003 : libata
/proc/ioports: a400-a40f : 0000:00:0f.0
/proc/ioports:   a400-a40f : libata
/proc/ioports: a800-a8ff : 0000:00:0f.0
/proc/ioports:   a800-a8ff : sata_via
/proc/ioports: ac00-ac0f : 0000:00:0f.1
/proc/ioports:   ac00-ac07 : ide0
/proc/ioports:   ac08-ac0f : ide1
/proc/ioports: b000-b01f : 0000:00:10.0
/proc/ioports:   b000-b01f : uhci_hcd
/proc/ioports: b400-b41f : 0000:00:10.1
/proc/ioports:   b400-b41f : uhci_hcd
/proc/ioports: b800-b81f : 0000:00:10.2
/proc/ioports:   b800-b81f : uhci_hcd
/proc/ioports: bc00-bc1f : 0000:00:10.3
/proc/ioports:   bc00-bc1f : uhci_hcd
/proc/ioports: c000-c0ff : 0000:00:11.5
/proc/ioports:   c000-c0ff : VIA8237
/proc/ioports: c400-c4ff : 0000:00:11.6
/proc/ioports: c800-c8ff : 0000:00:12.0
/proc/ioports:   c800-c8ff : via-rhine
/proc/iomem: 00000000-0009d3ff : System RAM
/proc/iomem:   00000000-00000000 : Crash kernel
/proc/iomem: 0009d400-0009ffff : reserved
/proc/iomem: 000a0000-000bffff : Video RAM area
/proc/iomem: 000c0000-000cf1ff : Video ROM
/proc/iomem: 000d0000-000d3fff : pnp 00:00
/proc/iomem: 000f0000-000fffff : System ROM
/proc/iomem: 00100000-1dfeffff : System RAM
/proc/iomem:   00100000-002f7de5 : Kernel code
/proc/iomem:   002f7de6-003dce83 : Kernel data
/proc/iomem: 1dff0000-1dff2fff : ACPI Non-volatile Storage
/proc/iomem: 1dff3000-1dffffff : ACPI Tables
/proc/iomem: e0000000-e3ffffff : 0000:00:00.0
/proc/iomem: e4000000-e7ffffff : PCI Bus #01
/proc/iomem:   e4000000-e7ffffff : 0000:01:00.0
/proc/iomem:     e4000000-e7ffffff : vt8623fb
/proc/iomem: e8000000-e9ffffff : PCI Bus #01
/proc/iomem:   e8000000-e8ffffff : 0000:01:00.0
/proc/iomem:     e8000000-e8ffffff : vt8623fb
/proc/iomem:   e9000000-e900ffff : 0000:01:00.0
/proc/iomem: ea000000-ea0007ff : 0000:00:09.0
/proc/iomem:   ea000000-ea0007ff : ohci1394
/proc/iomem: ea001000-ea0010ff : 0000:00:10.4
/proc/iomem:   ea001000-ea0010ff : ehci_hcd
/proc/iomem: ea002000-ea0020ff : 0000:00:12.0
/proc/iomem:   ea002000-ea0020ff : via-rhine
/proc/iomem: fec00000-fec00fff : reserved
/proc/iomem: fee00000-fee00fff : reserved
/proc/iomem: ffff0000-ffffffff : reserved
/proc/interrupts:            CPU0       
/proc/interrupts:   0:     344871    XT-PIC-XT        timer
/proc/interrupts:   1:       4994    XT-PIC-XT        i8042
/proc/interrupts:   2:          0    XT-PIC-XT        cascade
/proc/interrupts:   6:          5    XT-PIC-XT        floppy
/proc/interrupts:   7:          0    XT-PIC-XT        parport0
/proc/interrupts:   8:          3    XT-PIC-XT        rtc
/proc/interrupts:   9:          1    XT-PIC-XT        acpi
/proc/interrupts:  10:     306933    XT-PIC-XT        uhci_hcd:usb1, uhci_hcd:usb2, eth0, via@pci:0000:01:00.0
/proc/interrupts:  11:      17041    XT-PIC-XT        ohci1394, sata_via, uhci_hcd:usb3, uhci_hcd:usb4, ehci_hcd:usb5, VIA8237
/proc/interrupts:  12:          4    XT-PIC-XT        i8042
/proc/interrupts:  14:      32102    XT-PIC-XT        ide0
/proc/interrupts: NMI:          0 
/proc/interrupts: LOC:          0 
/proc/interrupts: ERR:          0
/proc/interrupts: MIS:          0
/proc/meminfo: MemTotal:       482852 kB
/proc/meminfo: MemFree:         32064 kB
/proc/meminfo: Buffers:         11536 kB
/proc/meminfo: Cached:         217840 kB
/proc/meminfo: SwapCached:          0 kB
/proc/meminfo: Active:         264940 kB
/proc/meminfo: Inactive:       127340 kB
/proc/meminfo: HighTotal:           0 kB
/proc/meminfo: HighFree:            0 kB
/proc/meminfo: LowTotal:       482852 kB
/proc/meminfo: LowFree:         32064 kB
/proc/meminfo: SwapTotal:     1413680 kB
/proc/meminfo: SwapFree:      1413680 kB
/proc/meminfo: Dirty:             124 kB
/proc/meminfo: Writeback:           0 kB
/proc/meminfo: AnonPages:      162912 kB
/proc/meminfo: Mapped:          59632 kB
/proc/meminfo: Slab:            15500 kB
/proc/meminfo: SReclaimable:     8028 kB
/proc/meminfo: SUnreclaim:       7472 kB
/proc/meminfo: PageTables:       2040 kB
/proc/meminfo: NFS_Unstable:        0 kB
/proc/meminfo: Bounce:              0 kB
/proc/meminfo: CommitLimit:   1655104 kB
/proc/meminfo: Committed_AS:   627444 kB
/proc/meminfo: VmallocTotal:   540664 kB
/proc/meminfo: VmallocUsed:     86924 kB
/proc/meminfo: VmallocChunk:   453292 kB
/proc/bus/input/devices: I: Bus=0017 Vendor=0001 Product=0001 Version=0100
/proc/bus/input/devices: N: Name="Macintosh mouse button emulation"
/proc/bus/input/devices: P: Phys=
/proc/bus/input/devices: S: Sysfs=/class/input/input0
/proc/bus/input/devices: U: Uniq=
/proc/bus/input/devices: H: Handlers=mouse0 event0 
/proc/bus/input/devices: B: EV=7
/proc/bus/input/devices: B: KEY=70000 0 0 0 0 0 0 0 0
/proc/bus/input/devices: B: REL=3
/proc/bus/input/devices: 
/proc/bus/input/devices: I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
/proc/bus/input/devices: N: Name="AT Translated Set 2 keyboard"
/proc/bus/input/devices: P: Phys=isa0060/serio0/input0
/proc/bus/input/devices: S: Sysfs=/class/input/input1
/proc/bus/input/devices: U: Uniq=
/proc/bus/input/devices: H: Handlers=kbd event1 
/proc/bus/input/devices: B: EV=120013
/proc/bus/input/devices: B: KEY=4 2000000 3802078 f840d001 feffffdf ffefffff ffffffff fffffffe
/proc/bus/input/devices: B: MSC=10
/proc/bus/input/devices: B: LED=7
/proc/bus/input/devices: 
/proc/bus/input/devices: I: Bus=0003 Vendor=046d Product=c00e Version=0110
/proc/bus/input/devices: N: Name="Logitech USB-PS/2 Optical Mouse"
/proc/bus/input/devices: P: Phys=usb-0000:00:10.0-1/input0
/proc/bus/input/devices: S: Sysfs=/class/input/input2
/proc/bus/input/devices: U: Uniq=
/proc/bus/input/devices: H: Handlers=mouse1 event2 
/proc/bus/input/devices: B: EV=7
/proc/bus/input/devices: B: KEY=70000 0 0 0 0 0 0 0 0
/proc/bus/input/devices: B: REL=103
/proc/bus/input/devices: 
/proc/bus/input/devices: I: Bus=0010 Vendor=001f Product=0001 Version=0100
/proc/bus/input/devices: N: Name="PC Speaker"
/proc/bus/input/devices: P: Phys=isa0061/input0
/proc/bus/input/devices: S: Sysfs=/class/input/input3
/proc/bus/input/devices: U: Uniq=
/proc/bus/input/devices: H: Handlers=kbd event3 
/proc/bus/input/devices: B: EV=40001
/proc/bus/input/devices: B: SND=6
/proc/bus/input/devices: 
/proc/bus/input/devices: I: Bus=0019 Vendor=0000 Product=0002 Version=0000
/proc/bus/input/devices: N: Name="Power Button (FF)"
/proc/bus/input/devices: P: Phys=button_power/button/input0
/proc/bus/input/devices: S: Sysfs=/class/input/input4
/proc/bus/input/devices: U: Uniq=
/proc/bus/input/devices: H: Handlers=kbd event4 
/proc/bus/input/devices: B: EV=3
/proc/bus/input/devices: B: KEY=100000 0 0 0
/proc/bus/input/devices: 
/proc/bus/input/devices: I: Bus=0019 Vendor=0000 Product=0001 Version=0000
/proc/bus/input/devices: N: Name="Power Button (CM)"
/proc/bus/input/devices: P: Phys=PNP0C0C/button/input0
/proc/bus/input/devices: S: Sysfs=/class/input/input5
/proc/bus/input/devices: U: Uniq=
/proc/bus/input/devices: H: Handlers=kbd event5 
/proc/bus/input/devices: B: EV=3
/proc/bus/input/devices: B: KEY=100000 0 0 0
/proc/bus/input/devices: 
/proc/bus/input/devices: I: Bus=0019 Vendor=0000 Product=0003 Version=0000
/proc/bus/input/devices: N: Name="Sleep Button (CM)"
/proc/bus/input/devices: P: Phys=PNP0C0E/button/input0
/proc/bus/input/devices: S: Sysfs=/class/input/input6
/proc/bus/input/devices: U: Uniq=
/proc/bus/input/devices: H: Handlers=kbd event6 
/proc/bus/input/devices: B: EV=3
/proc/bus/input/devices: B: KEY=4000 0 0 0 0
/proc/bus/input/devices: 
dmidecode: # dmidecode 2.9
dmidecode: SMBIOS 2.3 present.
dmidecode: 50 structures occupying 1430 bytes.
dmidecode: Table at 0x000F0800.
dmidecode: 
dmidecode: Handle 0x0000, DMI type 0, 20 bytes
dmidecode: BIOS Information
dmidecode: 	Vendor: Phoenix Technologies, LTD
dmidecode: 	Version: ASUS C3V ACPI BIOS Revision 1004
dmidecode: 	Release Date: 01/06/2005
dmidecode: 	Address: 0xE0000
dmidecode: 	Runtime Size: 128 kB
dmidecode: 	ROM Size: 512 kB
dmidecode: 	Characteristics:
dmidecode: 		PCI is supported
dmidecode: 		PNP is supported
dmidecode: 		APM is supported
dmidecode: 		BIOS is upgradeable
dmidecode: 		BIOS shadowing is allowed
dmidecode: 		ESCD support is available
dmidecode: 		Boot from CD is supported
dmidecode: 		Selectable boot is supported
dmidecode: 		BIOS ROM is socketed
dmidecode: 		EDD is supported
dmidecode: 		5.25"/360 KB floppy services are supported (int 13h)
dmidecode: 		5.25"/1.2 MB floppy services are supported (int 13h)
dmidecode: 		3.5"/720 KB floppy services are supported (int 13h)
dmidecode: 		3.5"/2.88 MB floppy services are supported (int 13h)
dmidecode: 		Print screen service is supported (int 5h)
dmidecode: 		8042 keyboard services are supported (int 9h)
dmidecode: 		Serial services are supported (int 14h)
dmidecode: 		Printer services are supported (int 17h)
dmidecode: 		CGA/mono video services are supported (int 10h)
dmidecode: 		ACPI is supported
dmidecode: 		USB legacy is supported
dmidecode: 		AGP is supported
dmidecode: 		LS-120 boot is supported
dmidecode: 		ATAPI Zip drive boot is supported
dmidecode: 		BIOS boot specification is supported
dmidecode: 
dmidecode: Handle 0x0001, DMI type 1, 25 bytes
dmidecode: System Information
dmidecode: 	Manufacturer: ASUSTek Computer INC. 
dmidecode: 	Product Name: C3V
dmidecode: 	Version: 1.xx
dmidecode: 	Serial Number: 123456789000
dmidecode: 	UUID: 002985F3-01A1-1010-AA9C-87B3ECFEAEDF
dmidecode: 	Wake-up Type: Power Switch
dmidecode: 
dmidecode: Handle 0x0002, DMI type 177, 69 bytes
dmidecode: OEM-specific Type
dmidecode: 	Header and Data:
dmidecode: 		B1 45 02 00 00 13 D4 F5 E2 01 01 00 FF 80 43 10
dmidecode: 		65 30 06 11 1F 10 00 00 00 00 03 08 09 0E 03 00
dmidecode: 		40 82 73 39 00 00 00 00 00 00 00 00 00 00 00 00
dmidecode: 		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
dmidecode: 		00 00 00 00 01
dmidecode: 	Strings:
dmidecode: 		VIA3177-MAC
dmidecode: 
dmidecode: Handle 0x0003, DMI type 2, 8 bytes
dmidecode: Base Board Information
dmidecode: 	Manufacturer: ASUSTek Computer INC. 
dmidecode: 	Product Name: C3V
dmidecode: 	Version: 1.xx
dmidecode: 	Serial Number: 123456789000
dmidecode: 
dmidecode: Handle 0x0004, DMI type 3, 17 bytes
dmidecode: Chassis Information
dmidecode: 	Manufacturer: ASUSTek Computer INC. 
dmidecode: 	Type: Desktop
dmidecode: 	Lock: Not Present
dmidecode: 	Version: Chassis Version
dmidecode: 	Serial Number: EVAL
dmidecode: 	Asset Tag: 123456789000
dmidecode: 	Boot-up State: Safe
dmidecode: 	Power Supply State: Safe
dmidecode: 	Thermal State: Safe
dmidecode: 	Security Status: None
dmidecode: 	OEM Information: 0x00000000
dmidecode: 
dmidecode: Handle 0x0005, DMI type 4, 35 bytes
dmidecode: Processor Information
dmidecode: 	Socket Designation: No Socket
dmidecode: 	Type: Central Processor
dmidecode: 	Family: Alpha 21164a
dmidecode: 	Manufacturer: VIA
dmidecode: 	ID: 73 06 00 00 35 30 80 00
dmidecode: 	Version: VIA C3
dmidecode: 	Voltage: 1.6 V
dmidecode: 	External Clock: 133 MHz
dmidecode: 	Max Speed: 800 MHz
dmidecode: 	Current Speed: 800 MHz
dmidecode: 	Status: Populated, Enabled
dmidecode: 	Upgrade: None
dmidecode: 	L1 Cache Handle: 0x0009
dmidecode: 	L2 Cache Handle: 0x000A
dmidecode: 	L3 Cache Handle: Not Provided
dmidecode: 	Serial Number:  
dmidecode: 	Asset Tag:  
dmidecode: 	Part Number:  
dmidecode: 
dmidecode: Handle 0x0006, DMI type 5, 20 bytes
dmidecode: Memory Controller Information
dmidecode: 	Error Detecting Method: None
dmidecode: 	Error Correcting Capabilities:
dmidecode: 		None
dmidecode: 	Supported Interleave: One-way Interleave
dmidecode: 	Current Interleave: Four-way Interleave
dmidecode: 	Maximum Memory Module Size: 1024 MB
dmidecode: 	Maximum Total Memory Size: 2048 MB
dmidecode: 	Supported Speeds:
dmidecode: 		70 ns
dmidecode: 		60 ns
dmidecode: 	Supported Memory Types:
dmidecode: 		DIMM
dmidecode: 	Memory Module Voltage: 5.0 V
dmidecode: 	Associated Memory Slots: 2
dmidecode: 		0x0007
dmidecode: 		0x0008
dmidecode: 	Enabled Error Correcting Capabilities: None
dmidecode: 
dmidecode: Handle 0x0007, DMI type 6, 12 bytes
dmidecode: Memory Module Information
dmidecode: 	Socket Designation: A0
dmidecode: 	Bank Connections: 0
dmidecode: 	Current Speed: 60 ns
dmidecode: 	Type: DIMM
dmidecode: 	Installed Size: 256 MB (Single-bank Connection)
dmidecode: 	Enabled Size: 256 MB (Single-bank Connection)
dmidecode: 	Error Status: OK
dmidecode: 
dmidecode: Handle 0x0008, DMI type 6, 12 bytes
dmidecode: Memory Module Information
dmidecode: 	Socket Designation: A1
dmidecode: 	Bank Connections: 2
dmidecode: 	Current Speed: 60 ns
dmidecode: 	Type: DIMM
dmidecode: 	Installed Size: 256 MB (Single-bank Connection)
dmidecode: 	Enabled Size: 256 MB (Single-bank Connection)
dmidecode: 	Error Status: OK
dmidecode: 
dmidecode: Handle 0x0009, DMI type 7, 19 bytes
dmidecode: Cache Information
dmidecode: 	Socket Designation: L1 Cache
dmidecode: 	Configuration: Enabled, Not Socketed, Level 1
dmidecode: 	Operational Mode: Write Back
dmidecode: 	Location: Internal
dmidecode: 	Installed Size: 128 KB
dmidecode: 	Maximum Size: 128 KB
dmidecode: 	Supported SRAM Types:
dmidecode: 		Synchronous
dmidecode: 	Installed SRAM Type: Synchronous
dmidecode: 	Speed: Unknown
dmidecode: 	Error Correction Type: Single-bit ECC
dmidecode: 	System Type: Data
dmidecode: 	Associativity: 4-way Set-associative
dmidecode: 
dmidecode: Handle 0x000A, DMI type 7, 19 bytes
dmidecode: Cache Information
dmidecode: 	Socket Designation: L2 Cache
dmidecode: 	Configuration: Enabled, Not Socketed, Level 2
dmidecode: 	Operational Mode: Write Back
dmidecode: 	Location: External
dmidecode: 	Installed Size: 64 KB
dmidecode: 	Maximum Size: 64 KB
dmidecode: 	Supported SRAM Types:
dmidecode: 		Synchronous
dmidecode: 	Installed SRAM Type: Synchronous
dmidecode: 	Speed: Unknown
dmidecode: 	Error Correction Type: Single-bit ECC
dmidecode: 	System Type: Unified
dmidecode: 	Associativity: 4-way Set-associative
dmidecode: 
dmidecode: Handle 0x000B, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: PRIMARY IDE
dmidecode: 	Internal Connector Type: On Board IDE
dmidecode: 	External Reference Designator: Not Specified
dmidecode: 	External Connector Type: None
dmidecode: 	Port Type: Other
dmidecode: 
dmidecode: Handle 0x000C, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: SECONDARY IDE
dmidecode: 	Internal Connector Type: On Board IDE
dmidecode: 	External Reference Designator: Not Specified
dmidecode: 	External Connector Type: None
dmidecode: 	Port Type: Other
dmidecode: 
dmidecode: Handle 0x000D, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: FDD
dmidecode: 	Internal Connector Type: On Board Floppy
dmidecode: 	External Reference Designator: Not Specified
dmidecode: 	External Connector Type: None
dmidecode: 	Port Type: 8251 FIFO Compatible
dmidecode: 
dmidecode: Handle 0x000E, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: COM1
dmidecode: 	Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
dmidecode: 	External Reference Designator:  
dmidecode: 	External Connector Type: DB-9 male
dmidecode: 	Port Type: Serial Port 16450 Compatible
dmidecode: 
dmidecode: Handle 0x000F, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: LPT1
dmidecode: 	Internal Connector Type: DB-25 female
dmidecode: 	External Reference Designator:  
dmidecode: 	External Connector Type: DB-25 female
dmidecode: 	Port Type: Parallel Port ECP/EPP
dmidecode: 
dmidecode: Handle 0x0010, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: PS/2 Keyboard
dmidecode: 	Internal Connector Type: PS/2
dmidecode: 	External Reference Designator:  
dmidecode: 	External Connector Type: PS/2
dmidecode: 	Port Type: Keyboard Port
dmidecode: 
dmidecode: Handle 0x0011, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: PS/2 Mouse
dmidecode: 	Internal Connector Type: PS/2
dmidecode: 	External Reference Designator:  
dmidecode: 	External Connector Type: PS/2
dmidecode: 	Port Type: Mouse Port
dmidecode: 
dmidecode: Handle 0x0012, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: Not Specified
dmidecode: 	Internal Connector Type: None
dmidecode: 	External Reference Designator: USB1
dmidecode: 	External Connector Type: Other
dmidecode: 	Port Type: USB
dmidecode: 
dmidecode: Handle 0x0013, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: Not Specified
dmidecode: 	Internal Connector Type: None
dmidecode: 	External Reference Designator: USB2
dmidecode: 	External Connector Type: Other
dmidecode: 	Port Type: USB
dmidecode: 
dmidecode: Handle 0x0014, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: Not Specified
dmidecode: 	Internal Connector Type: None
dmidecode: 	External Reference Designator: USB3
dmidecode: 	External Connector Type: Other
dmidecode: 	Port Type: USB
dmidecode: 
dmidecode: Handle 0x0015, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: Not Specified
dmidecode: 	Internal Connector Type: None
dmidecode: 	External Reference Designator: USB4
dmidecode: 	External Connector Type: Other
dmidecode: 	Port Type: USB
dmidecode: 
dmidecode: Handle 0x0016, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: Not Specified
dmidecode: 	Internal Connector Type: None
dmidecode: 	External Reference Designator: USB5
dmidecode: 	External Connector Type: Other
dmidecode: 	Port Type: USB
dmidecode: 
dmidecode: Handle 0x0017, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: Not Specified
dmidecode: 	Internal Connector Type: None
dmidecode: 	External Reference Designator: USB6
dmidecode: 	External Connector Type: Other
dmidecode: 	Port Type: USB
dmidecode: 
dmidecode: Handle 0x0018, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: Not Specified
dmidecode: 	Internal Connector Type: None
dmidecode: 	External Reference Designator: USB7
dmidecode: 	External Connector Type: Other
dmidecode: 	Port Type: USB
dmidecode: 
dmidecode: Handle 0x0019, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: Not Specified
dmidecode: 	Internal Connector Type: None
dmidecode: 	External Reference Designator: USB8
dmidecode: 	External Connector Type: Other
dmidecode: 	Port Type: USB
dmidecode: 
dmidecode: Handle 0x001A, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: Not Specified
dmidecode: 	Internal Connector Type: None
dmidecode: 	External Reference Designator: VIDEO
dmidecode: 	External Connector Type: DB-15 female
dmidecode: 	Port Type: Video Port
dmidecode: 
dmidecode: Handle 0x001B, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: Not Specified
dmidecode: 	Internal Connector Type: None
dmidecode: 	External Reference Designator: Line In
dmidecode: 	External Connector Type: None
dmidecode: 	Port Type: Audio Port
dmidecode: 
dmidecode: Handle 0x001C, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: Line Out
dmidecode: 	Internal Connector Type: None
dmidecode: 	External Reference Designator: Line Out
dmidecode: 	External Connector Type: Mini Jack (headphones)
dmidecode: 	Port Type: Audio Port
dmidecode: 
dmidecode: Handle 0x001D, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: Mic In
dmidecode: 	Internal Connector Type: None
dmidecode: 	External Reference Designator: Mic In
dmidecode: 	External Connector Type: Mini Jack (headphones)
dmidecode: 	Port Type: Audio Port
dmidecode: 
dmidecode: Handle 0x001E, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: CD In
dmidecode: 	Internal Connector Type: On Board Sound Input From CD-ROM
dmidecode: 	External Reference Designator: CD In
dmidecode: 	External Connector Type: None
dmidecode: 	Port Type: Audio Port
dmidecode: 
dmidecode: Handle 0x001F, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: Aux In
dmidecode: 	Internal Connector Type: On Board Sound Input From CD-ROM
dmidecode: 	External Reference Designator: Aux In
dmidecode: 	External Connector Type: None
dmidecode: 	Port Type: Audio Port
dmidecode: 
dmidecode: Handle 0x0020, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: Front Panel
dmidecode: 	Internal Connector Type: Other
dmidecode: 	External Reference Designator: Front Panel
dmidecode: 	External Connector Type: None
dmidecode: 	Port Type: Audio Port
dmidecode: 
dmidecode: Handle 0x0021, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: Not Specified
dmidecode: 	Internal Connector Type: None
dmidecode: 	External Reference Designator: ETHERNET
dmidecode: 	External Connector Type: RJ-45
dmidecode: 	Port Type: Network Port
dmidecode: 
dmidecode: Handle 0x0022, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: Not Specified
dmidecode: 	Internal Connector Type: None
dmidecode: 	External Reference Designator: Joystick
dmidecode: 	External Connector Type: DB-15 female
dmidecode: 	Port Type: Joystick Port
dmidecode: 
dmidecode: Handle 0x0023, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: Not Specified
dmidecode: 	Internal Connector Type: None
dmidecode: 	External Reference Designator: IE1394_1
dmidecode: 	External Connector Type: IEEE 1394
dmidecode: 	Port Type: Firewire (IEEE P1394)
dmidecode: 
dmidecode: Handle 0x0024, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: Not Specified
dmidecode: 	Internal Connector Type: None
dmidecode: 	External Reference Designator: IE1394_2
dmidecode: 	External Connector Type: IEEE 1394
dmidecode: 	Port Type: Firewire (IEEE P1394)
dmidecode: 
dmidecode: Handle 0x0025, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: SATA1
dmidecode: 	Internal Connector Type: On Board IDE
dmidecode: 	External Reference Designator: Not Specified
dmidecode: 	External Connector Type: None
dmidecode: 	Port Type: Other
dmidecode: 
dmidecode: Handle 0x0026, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: SATA2
dmidecode: 	Internal Connector Type: On Board IDE
dmidecode: 	External Reference Designator: Not Specified
dmidecode: 	External Connector Type: None
dmidecode: 	Port Type: Other
dmidecode: 
dmidecode: Handle 0x0027, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: Not Specified
dmidecode: 	Internal Connector Type: None
dmidecode: 	External Reference Designator: MIDI
dmidecode: 	External Connector Type: DB-15 female
dmidecode: 	Port Type: MIDI Port
dmidecode: 
dmidecode: Handle 0x0028, DMI type 9, 13 bytes
dmidecode: System Slot Information
dmidecode: 	Designation: PCI1
dmidecode: 	Type: 32-bit PCI
dmidecode: 	Current Usage: Available
dmidecode: 	Length: Short
dmidecode: 	ID: 1
dmidecode: 	Characteristics:
dmidecode: 		5.0 V is provided
dmidecode: 		3.3 V is provided
dmidecode: 		PME signal is supported
dmidecode: 
dmidecode: Handle 0x0029, DMI type 13, 22 bytes
dmidecode: BIOS Language Information
dmidecode: 	Installable Languages: 3
dmidecode: 		n|US|iso8859-1
dmidecode: 		n|US|iso8859-1
dmidecode: 		r|CA|iso8859-1
dmidecode: 	Currently Installed Language: n|US|iso8859-1
dmidecode: 
dmidecode: Handle 0x002A, DMI type 16, 15 bytes
dmidecode: Physical Memory Array
dmidecode: 	Location: System Board Or Motherboard
dmidecode: 	Use: System Memory
dmidecode: 	Error Correction Type: None
dmidecode: 	Maximum Capacity: 2 GB
dmidecode: 	Error Information Handle: Not Provided
dmidecode: 	Number Of Devices: 2
dmidecode: 
dmidecode: Handle 0x002B, DMI type 17, 27 bytes
dmidecode: Memory Device
dmidecode: 	Array Handle: 0x002A
dmidecode: 	Error Information Handle: Not Provided
dmidecode: 	Total Width: 64 bits
dmidecode: 	Data Width: 64 bits
dmidecode: 	Size: 256 MB
dmidecode: 	Form Factor: DIMM
dmidecode: 	Set: None
dmidecode: 	Locator: A0
dmidecode: 	Bank Locator: Bank0/1
dmidecode: 	Type: Unknown
dmidecode: 	Type Detail: None
dmidecode: 	Speed: Unknown
dmidecode: 	Manufacturer: None
dmidecode: 	Serial Number: None
dmidecode: 	Asset Tag: None
dmidecode: 	Part Number: None
dmidecode: 
dmidecode: Handle 0x002C, DMI type 17, 27 bytes
dmidecode: Memory Device
dmidecode: 	Array Handle: 0x002A
dmidecode: 	Error Information Handle: Not Provided
dmidecode: 	Total Width: 64 bits
dmidecode: 	Data Width: 64 bits
dmidecode: 	Size: 256 MB
dmidecode: 	Form Factor: DIMM
dmidecode: 	Set: None
dmidecode: 	Locator: A1
dmidecode: 	Bank Locator: Bank2/3
dmidecode: 	Type: Unknown
dmidecode: 	Type Detail: None
dmidecode: 	Speed: Unknown
dmidecode: 	Manufacturer: None
dmidecode: 	Serial Number: None
dmidecode: 	Asset Tag: None
dmidecode: 	Part Number: None
dmidecode: 
dmidecode: Handle 0x002D, DMI type 19, 15 bytes
dmidecode: Memory Array Mapped Address
dmidecode: 	Starting Address: 0x00000000000
dmidecode: 	Ending Address: 0x0001FFFFFFF
dmidecode: 	Range Size: 512 MB
dmidecode: 	Physical Array Handle: 0x002A
dmidecode: 	Partition Width: 0
dmidecode: 
dmidecode: Handle 0x002E, DMI type 20, 19 bytes
dmidecode: Memory Device Mapped Address
dmidecode: 	Starting Address: 0x00000000000
dmidecode: 	Ending Address: 0x0000FFFFFFF
dmidecode: 	Range Size: 256 MB
dmidecode: 	Physical Device Handle: 0x002B
dmidecode: 	Memory Array Mapped Address Handle: 0x002D
dmidecode: 	Partition Row Position: 1
dmidecode: 
dmidecode: Handle 0x002F, DMI type 20, 19 bytes
dmidecode: Memory Device Mapped Address
dmidecode: 	Starting Address: 0x00010000000
dmidecode: 	Ending Address: 0x0001FFFFFFF
dmidecode: 	Range Size: 256 MB
dmidecode: 	Physical Device Handle: 0x002C
dmidecode: 	Memory Array Mapped Address Handle: 0x002D
dmidecode: 	Partition Row Position: 1
dmidecode: 
dmidecode: Handle 0x0030, DMI type 32, 11 bytes
dmidecode: System Boot Information
dmidecode: 	Status: No errors detected
dmidecode: 
dmidecode: Handle 0x0031, DMI type 127, 4 bytes
dmidecode: End Of Table
dmidecode: 
```

   5. Other Wine applications - none

Any help would be greatly appreciated.

---

