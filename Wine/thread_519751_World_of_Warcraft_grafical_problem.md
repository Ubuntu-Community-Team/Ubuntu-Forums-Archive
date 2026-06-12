---
title: "World of Warcraft grafical problem"
date: 2007-08-07
forum: Wine
---

### Post by piva.francesco on 2007-08-07
Greetings !

I have read a lot on the internet on HowTo install WoW, on Ubuntu.
I still did not find any good answer for my problem, maybe it's just a childish one. But still I do not succeed in playing / launching in a proper way WoW.

First of all I have followed step, by step this Tutorial.

> [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Then what happens I tried this script in order to launch WoW in another Terminal:

> [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

But the answer I get from this last test, is that World of Warcraft cannot find the graphical accelerator. I press yes and it freezes my laptop and cannot restart X or switch to another terminal.

this is what I get with the script. 

> 

*@*:~$ ./script-wow.sh 

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux FayaLocks 2.6.20-16-generic #2 SMP Thu Jun 7 20:
19:32 UTC 2007 i686
Build Date: 04 April 2007
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.3.log", Time: Tue Aug  7 17:12:18 2007
(==) Using config file: "/etc/X11/xorg.conf"
(**) RADEON(0): RADEONPreInit
(**) RADEON(0): RADEONScreenInit d0000000 0
(**) RADEON(0): Map: 0xd0000000, 0x08000000
(**) RADEON(0): RADEONSave
(**) RADEON(0): RADEONSaveMode(0x81f5e98)
(**) RADEON(0): Read: 0x00180006 0x0002003d 0x00000000
(**) RADEON(0): Read: rd=6, fd=61, pd=2
(**) RADEON(0): RADEONSaveMode returns 0x81f5e98
(**) RADEON(0): RADEONInitMemoryMap() : 
(**) RADEON(0):   mem_size         : 0x08000000
(**) RADEON(0):   MC_FB_LOCATION   : 0xd7ffd000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0): RADEONModeInit()
1280x800       68.90  1280 1296 1328 1408   800  801  804  816 (24,32)
1280x800       68.90  1280 1296 1328 1408   800  801  804  816 (24,32)
(**) RADEON(0): Pitch = 10485920 bytes (virtualX = 1280, displayWidth = 1280)
(**) RADEON(0): RADEONInit returns 0x81f6848
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81f6848)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0xd7ffd000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): GRPH_BUFFER_CNTL from 30004c4c to 20167c7c
(**) RADEON(0): RADEONSaveScreen(0)
(**) RADEON(0): Setting up initial surfaces
(**) RADEON(0): Initializing fb layer
(**) RADEON(0): Setting up accel memmap
(**) RADEON(0): Initializing backing store
(**) RADEON(0): Setting up final surfaces
(**) RADEON(0): Initializing Acceleration
(**) RADEON(0): EngineInit (32/32)
(**) RADEON(0): Pitch for acceleration = 160
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): Initializing DPMS
(**) RADEON(0): Initializing Cursor
(**) RADEON(0): Initializing color map
(**) RADEON(0): Initializing DGA
(**) RADEON(0): Initializing Xv
(**) RADEON(0): RADEONScreenInit finished
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
seventh@FayaLocks:~$ Synaptics DeviceOn called
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from li
st!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from li
st!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from l
ist!
(**) RADEON(0): RADEONSaveScreen(2)
Xlib:  extension "GLX" missing on display ":3.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problem
s
Xlib:  extension "GLX" missing on display ":3.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problem
s
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support
 !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support
 !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support
 !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support
 !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support
 !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support
 !
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33edac,0x00000000), stub!
Xlib:  extension "GLX" missing on display ":3.0".
err:d3d:InitAdapters Failed to create a fake opengl context to find fbconfigs fo
rmats
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl
Synaptics DeviceOff called
(**) RADEON(0): RADEONLeaveVT
(**) RADEON(0): RADEONRestore
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81f5e98)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0x1fff0000
(**) RADEON(0):   MC_AGP_LOCATION  : 0x27ff2000
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x00180006 0x0002003d 0x00000000 (0x0000a700)
(**) RADEON(0): Wrote: rd=6, fd=61, pd=2
(**) RADEON(0): Ok, leaving now...
(**) RADEON(0): RADEONEnterVT
(**) RADEON(0): RADEONModeInit()
1280x800       68.90  1280 1296 1328 1408   800  801  804  816 (24,32)
1280x800       68.90  1280 1296 1328 1408   800  801  804  816 (24,32)
(**) RADEON(0): Pitch = 10485920 bytes (virtualX = 1280, displayWidth = 1280)
(**) RADEON(0): RADEONInit returns 0x81f6848
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81f6848)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0xd7ffd000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): GRPH_BUFFER_CNTL from 30004c4c to 20167c7c
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): RADEONSaveScreen(2)
Synaptics DeviceOn called
Synaptics DeviceOff called
(**) RADEON(0): RADEONLeaveVT
(**) RADEON(0): RADEONRestore
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81f5e98)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0x1fff0000
(**) RADEON(0):   MC_AGP_LOCATION  : 0x27ff2000
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x00180006 0x0002003d 0x00000000 (0x0000a700)
(**) RADEON(0): Wrote: rd=6, fd=61, pd=2
(**) RADEON(0): Ok, leaving now...
(**) RADEON(0): RADEONEnterVT
(**) RADEON(0): RADEONModeInit()
1280x800       68.90  1280 1296 1328 1408   800  801  804  816 (24,32)
1280x800       68.90  1280 1296 1328 1408   800  801  804  816 (24,32)
(**) RADEON(0): Pitch = 10485920 bytes (virtualX = 1280, displayWidth = 1280)
(**) RADEON(0): RADEONInit returns 0x81f6848
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81f6848)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0xd7ffd000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): GRPH_BUFFER_CNTL from 30004c4c to 20167c7c
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): RADEONSaveScreen(2)
Synaptics DeviceOn called
Synaptics DeviceOff called
(**) RADEON(0): RADEONLeaveVT
(**) RADEON(0): RADEONRestore
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81f5e98)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0x1fff0000
(**) RADEON(0):   MC_AGP_LOCATION  : 0x27ff2000
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x00180006 0x0002003d 0x00000000 (0x0000a700)
(**) RADEON(0): Wrote: rd=6, fd=61, pd=2
(**) RADEON(0): Ok, leaving now...





Moreover, when I stop the script, my cpu and ram are still hyper active.
I would realy like to make my WoW run under my Ubuntu Machine.


Hope the information I gave you are enough, don't hesitate to ask me some further information in order to make a good job 

Regards,



fp

---

### Post by Sammi on 2007-08-07
One of us must be very confused, because there is no mention of running any kind of bash script in that guide. Can you please tell me were you got that script from?

Anyway, to me it seems like your ATI Radeon drivers are borked. You should try following this guide to fix them: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by hikaricore on 2007-08-07
> **Sammi said:**
> One of us must be very confused, because there is no mention of running any kind of bash script in that guide. Can you please tell me we're you got that script from?

Anyway, to me it seems like your ATI Radeon drivers are borked. You should try following this guide to fix them: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I believe the OP may be referring to the script that used to be on that page showing how to start a new X session for running the game.    Where did that old thing go anyway?  O.o

---

### Post by piva.francesco on 2007-08-08
I have found this tutorial of the script here :

> [http://ubuntuforums.org/showthread.php?t=312482](http://ubuntuforums.org/showthread.php?t=312482)

I will try later the tutorial on the link.

Regards,

fp

---

### Post by tuxcantfly on 2007-08-08
Well you could always just use standard Xorg for games, and make sure that you invoke worldofwarcraft with the -opengl parameter.

---

### Post by piva.francesco on 2007-08-08
Cheers,

I have tried another technique to launch WoW.exe and this is the result I got.

> *@*:~$ wine .wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.e
xe -opengl
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problem
s
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problem
s
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support
 !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support
 !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support
 !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support
 !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support
 !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support
 !
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33edac,0x00000000), stub!
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:InitAdapters Failed to create a fake opengl context to find fbconfigs fo
rmats
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl
wine: Unhandled page fault on read access to 0x00000000 at address 0x7d73db44 (t
hread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7
d73db44).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7d73db44 ESP:0033f0b0 EBP:0033f108 EFLAGS:00010202(   - 00      - -RI1)
 EAX:0033f0d4 EBX:7d74f718 ECX:7d74fe94 EDX:00000000
 ESI:00000000 EDI:7d74fe90
Stack dump:
0x0033f0b0:  7d74fe90 00000009 0033f0f8 00110000
0x0033f0c0:  7bc30faf 7d74fe90 7d74f718 0033f0fc
0x0033f0d0:  7d738065 0033f140 0033f340 0033f540
0x0033f0e0:  0033f560 0033f568 0033f56c 0033f570
0x0033f0f0:  0033f574 0033f578 0033f588 00c48d7e
0x0033f100:  00000000 00c48d7c 0033f738 0056b0e7
Backtrace:
=>1 0x7d73db44 in d3d9 (+0xdb44) (0x0033f108)
  2 0x0056b0e7 in wow (+0x16b0e7) (0x0033f738)
  3 0x00605a5a in wow (+0x205a5a) (0x0033fb6c)
  4 0x006020de in wow (+0x2020de) (0x0033fbf8)
  5 0x00405712 in wow (+0x5712) (0x0033fe5c)
  6 0x00405816 in wow (+0x5816) (0x0033fe6c)
  7 0x00405868 in wow (+0x5868) (0x0033ff08)
  8 0x7b874c3e in kernel32 (+0x54c3e) (0x0033ffe8)
  9 0xb7e95af7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7d73db44: movl        0x0(%edx),%ecx
Modules:
Module  Address                 Debug info      Name (97 modules)
PE        340000-  3a9000       Deferred        divxdecoder
PE        400000-  cee000       Export          wow
PE      10000000-10090000       Deferred        fmod
ELF     7b800000-7b929000       Export          kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d5f8000-7d60d000       Deferred        psapi<elf>
  \-PE  7d600000-7d60d000       \               psapi
ELF     7d60d000-7d657000       Deferred        dbghelp<elf>
  \-PE  7d620000-7d657000       \               dbghelp
ELF     7d657000-7d722000       Deferred        wined3d<elf>
  \-PE  7d670000-7d722000       \               wined3d
ELF     7d722000-7d750000       Export          d3d9<elf>
  \-PE  7d730000-7d750000       \               d3d9
ELF     7d799000-7d7cb000       Deferred        uxtheme<elf>
  \-PE  7d7a0000-7d7cb000       \               uxtheme
ELF     7d7cb000-7d7e0000       Deferred        midimap<elf>
  \-PE  7d7d0000-7d7e0000       \               midimap
ELF     7d7e0000-7d7f8000       Deferred        msacm32<elf>
  \-PE  7d7f0000-7d7f8000       \               msacm32
ELF     7d7f8000-7d834000       Deferred        wineoss<elf>
  \-PE  7d800000-7d834000       \               wineoss
ELF     7d836000-7d83b000       Deferred        libxfixes.so.3
ELF     7d83b000-7d844000       Deferred        libxcursor.so.1
ELF     7d844000-7d84a000       Deferred        libxrandr.so.2
ELF     7d84a000-7d852000       Deferred        libxrender.so.1
ELF     7d852000-7d8db000       Deferred        winex11<elf>
  \-PE  7d860000-7d8db000       \               winex11
ELF     7d991000-7d9b1000       Deferred        libexpat.so.1
ELF     7d9b1000-7d9dc000       Deferred        libfontconfig.so.1
ELF     7d9dc000-7d9f0000       Deferred        libz.so.1
ELF     7d9f0000-7da5b000       Deferred        libfreetype.so.6
ELF     7da5b000-7db18000       Deferred        comctl32<elf>
  \-PE  7da60000-7db18000       \               comctl32
ELF     7db18000-7dc16000       Deferred        shell32<elf>
  \-PE  7db30000-7dc16000       \               shell32
ELF     7dc16000-7dc6f000       Deferred        shlwapi<elf>
  \-PE  7dc20000-7dc6f000       \               shlwapi
ELF     7dc6f000-7dc8f000       Deferred        mpr<elf>
  \-PE  7dc80000-7dc8f000       \               mpr
ELF     7dc8f000-7dcd9000       Deferred        wininet<elf>
  \-PE  7dca0000-7dcd9000       \               wininet
ELF     7dcd9000-7dd32000       Deferred        rpcrt4<elf>
  \-PE  7dcf0000-7dd32000       \               rpcrt4
ELF     7dd32000-7ddd1000       Deferred        ole32<elf>
  \-PE  7dd40000-7ddd1000       \               ole32
ELF     7ddd1000-7de38000       Deferred        msvcrt<elf>
  \-PE  7dde0000-7de38000       \               msvcrt
ELF     7de38000-7de5e000       Deferred        msacm32<elf>
  \-PE  7de40000-7de5e000       \               msacm32
ELF     7de5e000-7de7b000       Deferred        imm32<elf>
  \-PE  7de70000-7de7b000       \               imm32
ELF     7de7b000-7de8f000       Deferred        lz32<elf>
  \-PE  7de80000-7de8f000       \               lz32
ELF     7de8f000-7dea9000       Deferred        version<elf>
  \-PE  7dea0000-7dea9000       \               version
ELF     7df0e000-7e794000       Deferred        libglcore.so.1
ELF     7e794000-7e799000       Deferred        libxdmcp.so.6
ELF     7e799000-7e819000       Deferred        libglu.so.1
ELF     7e819000-7e8a5000       Deferred        libgl.so.1
ELF     7e8a5000-7e996000       Deferred        libx11.so.6
ELF     7e996000-7e9a4000       Deferred        libxext.so.6
ELF     7e9a4000-7e9a9000       Deferred        libxxf86vm.so.1
ELF     7e9a9000-7e9c1000       Deferred        libice.so.6
ELF     7e9c1000-7ea42000       Deferred        opengl32<elf>
  \-PE  7e9e0000-7ea42000       \               opengl32
ELF     7ea42000-7ea55000       Deferred        libresolv.so.2
ELF     7ea55000-7ea73000       Deferred        iphlpapi<elf>
  \-PE  7ea60000-7ea73000       \               iphlpapi
ELF     7ea73000-7eaa0000       Deferred        ws2_32<elf>
  \-PE  7ea80000-7eaa0000       \               ws2_32
ELF     7eaa0000-7eaba000       Deferred        wsock32<elf>
  \-PE  7eab0000-7eaba000       \               wsock32
ELF     7eaba000-7eb02000       Deferred        advapi32<elf>
  \-PE  7ead0000-7eb02000       \               advapi32
ELF     7eb02000-7eb0e000       Deferred        libgcc_s.so.1
ELF     7eb0e000-7eb11000       Deferred        libxau.so.6
ELF     7eb11000-7eb1a000       Deferred        libsm.so.6
ELF     7ec04000-7ecc4000       Deferred        gdi32<elf>
  \-PE  7ec20000-7ecc4000       \               gdi32
ELF     7ecc4000-7ee01000       Deferred        user32<elf>
  \-PE  7ece0000-7ee01000       \               user32
ELF     7ee01000-7ee8f000       Deferred        winmm<elf>
  \-PE  7ee10000-7ee8f000       \               winmm
ELF     7efa1000-7efac000       Deferred        libnss_files.so.2
ELF     7efac000-7efb6000       Deferred        libnss_nis.so.2
ELF     7efb6000-7efcd000       Deferred        libnsl.so.1
ELF     7efcd000-7eff4000       Deferred        libm.so.6
ELF     7eff4000-7eff6000       Deferred        libnvidia-tls.so.1
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7d25000-b7d29000       Deferred        libdl.so.2
ELF     b7d29000-b7e6a000       Deferred        libc.so.6
ELF     b7e6b000-b7e82000       Deferred        libpthread.so.0
ELF     b7e8e000-b7fa2000       Export          libwine.so.1
ELF     b7fa4000-b7fbf000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) Z:\home\seventh\.wine\drive_c\Program Files\World of Warcraft\WoW.e
xe
        0000000d    0
        00000009    0 <==




I based myself on the stuff I found here.

> [http://russellthedigitalninja.com/wordpress/?p=9](http://russellthedigitalninja.com/wordpress/?p=9)


Hope this can help. I'll be doing the ATI brokent driver procedure and tell you if it works.


Regards.


fp

---

### Post by piva.francesco on 2007-08-08
I have tried the procedure and it blocks when I get to type fglrxinfo and I get this:

> :~$ fglrxinfo
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!




Any clues ?


Regards,


fp

---

### Post by piva.francesco on 2007-08-08
Hey there !

I have followed what was on the tutorial you gave me, after reboot I succeed in launching WoW.exe, wonderful grafics etc...
Although I have a slight problem: I launch WoW, log-in, select my character, then when I finally get into the game, after a few seconds, my computer freezes. I can't even do "Control+Alt+Backspace" in order to kill X.
Does any of you have a clue ?

Best regards

EDIT : now I tried again to launch WoW but all I get is a lousy infinite error :

> fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!
FGLTexMgr: open of shared memory object failed (Permission denied)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!

Can someone please help me ?

Thank you


Best regards

fp

---

### Post by Sammi on 2007-08-08
> **hikaricore said:**
> I believe the OP may be referring to the script that used to be on that page showing how to start a new X session for running the game.    Where did that old thing go anyway?  O.oI decided that it was not very important and served mostly as annoying clutter, so I removed it. But there's still a link to the tread where it came from. 


@piva.francesco
I'm pretty sure your problem has to do with your ATI graphics card. We see a lot of those problems on this forum, and sadly far to few solutions.

If you've done everything mentioned in the guide I linked to, then just about the last thing you can do, is to send a mail to ATI to tell them to stop making such crappy Linux drivers. Oh and please vote with your money the next time you buy a graphics card, by buying from a Linux friendly supplier, like Intel or Nvidia. Sorry for the harsh tone. I'm very worn out by all the ATI related problems we see here.

---

### Post by douglett on 2007-11-26
> **piva.francesco said:**
> I have tried the procedure and it blocks when I get to type fglrxinfo and I get this:




Any clues ?


Regards,


fp

I'm getting the same thing.  I had WoW working for the longest time but recently updated my nvidia video card drivers (169.04) because of problems with Gutsy locking up and now WoW no longer works.

---

### Post by hikaricore on 2007-11-26
You don't use ATI drivers... fglrxinfo won't do anything for you...

---

