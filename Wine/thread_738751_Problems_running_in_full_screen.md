---
title: "Problems running in full screen"
date: 2008-03-28
forum: Wine
---

### Post by Zaneyard on 2008-03-28
Both Starcraft Brood War, and Counter Strike: Source, when ran in fullscreen mode, give me my monitor's "Cannot display this video mode" this is the monitor saying this because I have seen it other places than in Linux.

Stoof:
Wine Version 0.9.58
This is the terminal output from running Brood War, as is.
```
john@zaneyard:~/.wine/drive_c/Program Files/Starcraft$ wine StarCraft.exe
fixme:spoolsv:serv_main (0 (nil))
err:service:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
fixme:ntoskrnl:KeInitializeSpinLock 0x248198
wine: Call from 0x7b840fa0 to unimplemented function ntoskrnl.exe.KeInitializeEvent, aborting
wine: Unimplemented function ntoskrnl.exe.KeInitializeEvent called at address 0x7b840fa0 (thread 0011), starting debugger...
Unhandled exception: unimplemented function ntoskrnl.exe.KeInitializeEvent called in 32-bit code (0x7b84101a).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b84101a ESP:0035fe14 EBP:0035fe78 EFLAGS:00000202(   - 00      - - I1)
 EAX:7b82c171 EBX:7b8ac8a0 ECX:00000000 EDX:0035fe90
 ESI:0035fe90 EDI:7ffdf000
Stack dump:
0x0035fe14:  0035fe90 00000008 7bca1208 80000100
0x0035fe24:  00000001 00000000 7b840fa0 00000002
0x0035fe34:  7ee5f5a0 7ee62495 0035fea8 7ee77375
0x0035fe44:  7ee680a9 00000000 00000000 0035ff20
0x0035fe54:  b7f5219c 00000000 7ee77374 0035fe90
0x0035fe64:  b7e564dc 00000000 7b840faa 00000000
Backtrace:
=>1 0x7b84101a RaiseException+0x7a() in kernel32 (0x0035fe78)
  2 0x7ee5f541 in ntoskrnl (+0xf541) (0x0035fe98)
  3 0x7ee593b0 in ntoskrnl (+0x93b0) (0x0035ff08)
  4 0x7b86f7f9 in kernel32 (+0x4f7f9) (0x0035ffe8)
  5 0xb7e591cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7b84101a RaiseException+0x7a in kernel32: subl        $4,%esp
Modules:
Module  Address                 Debug info      Name (22 modules)
PE        240000-  24e280       Deferred        stcp2v30.sys
ELF     7b800000-7b926000       Export          kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bca2000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca2000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7edc6000-7eddb000       Deferred        hal<elf>
  \-PE  7edd0000-7eddb000       \               hal
ELF     7eddb000-7ee40000       Deferred        msvcrt<elf>
  \-PE  7edf0000-7ee40000       \               msvcrt
ELF     7ee40000-7ee78000       Export          ntoskrnl<elf>
  \-PE  7ee50000-7ee78000       \               ntoskrnl
ELF     7ee78000-7ee83000       Deferred        libnss_files.so.2
ELF     7ee83000-7ee9b000       Deferred        libnsl.so.1
ELF     7ee9b000-7eea4000       Deferred        libnss_compat.so.2
ELF     7efcf000-7eff4000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7cdf000-b7ce3000       Deferred        libdl.so.2
ELF     b7ce3000-b7e2d000       Deferred        libc.so.6
ELF     b7e2e000-b7e46000       Deferred        libpthread.so.0
ELF     b7e52000-b7f66000       Export          libwine.so.1
ELF     b7f68000-b7f84000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
        00000009    0
0000000a 
        0000000b    0
00000010 (D) C:\windows\system32\drivers\stcp2v30.sys
        00000011    0 <==
Backtrace:
=>1 0x7b84101a RaiseException+0x7a() in kernel32 (0x0035fe78)
  2 0x7ee5f541 in ntoskrnl (+0xf541) (0x0035fe98)
  3 0x7ee593b0 in ntoskrnl (+0x93b0) (0x0035ff08)
  4 0x7b86f7f9 in kernel32 (+0x4f7f9) (0x0035ffe8)
  5 0xb7e591cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
wine: Call from 0x7b840fa0 to unimplemented function ntoskrnl.exe.KeInitializeInterrupt, aborting
fixme:ntoskrnl:KeInitializeSpinLock 0x110b58
err:winedevice:ServiceMain driver L"vstor2-ws60" failed to load
fixme:advapi:SetSecurityInfo stub
Xlib:  extension "XFree86-DRI" missing on display ":2.0".
fixme:win:EnumDisplayDevicesW ((null),0,0x34f488,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8

```

This is set up globally with Windows XP as the OS setting.
Direct 3D is Hardware and pixel shaders are enabled.
I am using the ALSA sound driver

I have Warcraft III: The Frozen Throne installed, runs fullscreen no problems.
Starcraft runs in the virtual window fine, but does not display fullscreen.
CS:S runs very slow in window, but does not display in fullscreen.

this thread[http://ubuntuforums.org/showthread.php?t=737673]("http://ubuntuforums.org/showthread.php?t=737673") details some of the methods I have tried to get CS:S to run in fullscreen. Hopefully if it gets running in fullscreen the framerate problems will go away too...

I have searched many places in this forum, winehq, and google for a solution to this problem, but I cannot find one.

---

### Post by Zaneyard on 2008-03-29
after reading bug reports for a while I think I figured out that this is an unresolved problem regarding DirectDraw, and the Radeon drivers.
Time to get me a new graphics card...

---

