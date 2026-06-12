---
title: "[SOLVED] Diablo 1"
date: 2008-02-14
forum: Wine
---

### Post by DemiAlbedo on 2008-02-14
I recently installed ubuntu gutsy 7.10 onto my laptop and so far it is great. Lately I have ventured into gaming and have downloaded WINE to help me play window games. The game I am interested in playing is Diablo 1. I have gone through the WINE installation and after hours and hours of searching the internet I was finally able to get diablo installed  . The problem I run into right now is when diablo boots up it shows the blizzard logo then shuts off right away. When you hit any key to try and skip the cinematic it just shuts down, if you let the logo cinematic play it will shut down once it is done loading the cinematic. 

Here is the terminal output for when I start up diablo and when it shuts down.

[email]scott@scott-laptop:~/.wine[/email]/drive_c/Program Files/Diablo$ wine diablo.exe
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
[email]scott@scott-laptop:~/.wine[/email]/drive_c/Program Files/Diablo$ Xlib:  extension "XFree86-DRI" missing on display ":1.0".
fixme:win:EnumDisplayDevicesW ((null),0,0x34f850,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:msg:pack_message WM_NCPAINT hdc packing not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x12fd20)->(1,(nil)): Stub
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on ATI IXP Modem, disabling mixer
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x12fd20)->(1,(nil)): Stub
wine: Unhandled page fault on read access to 0x0180c000 at address 0x7e4df8 (thread 0011), starting debugger...
Unhandled exception: page fault on read access to 0x0180c000 in 32-bit code (0x007e4df8).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:007e4df8 ESP:0034f278 EBP:7edfafb8 EFLAGS:00010212(   - 00      - RIA1)
 EAX:00000000 EBX:00000000 ECX:00020026 EDX:0034f388
 ESI:0180bfff EDI:01721b43
Stack dump:
0x0034f278:  007d0118 00000013 0034f35c 00000023
0x0034f288:  00000000 0034f2d8 016801a4 7edfaeb5
0x0034f298:  7edfaeb5 016801a4 0168008c 44444353
0x0034f2a8:  44444444 1500b5d0 00010020 3d442023
0x0034f2b8:  00000097 1500b5f0 00000000 1500b5d0
0x0034f2c8:  00000001 00000974 0000025d 003c1630
Backtrace:
=>1 0x007e4df8 (0x7edfafb8)
0x007e4df8: movl        0x0(%esi),%eax
Modules:
Module  Address                 Debug info      Name (102 modules)
PE        400000-  6b4000       Deferred        diablo
PE       13f0000- 140a000       Deferred        smackw32
PE      10000000-10048000       Deferred        diabloui
PE      15000000-15041000       Deferred        storm
ELF     7b800000-7b925000       Deferred        kernel32<elf>
  \-PE  7b820000-7b925000       \               kernel32
ELF     7bc00000-7bca1000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7dc95000-7dca9000       Deferred        midimap<elf>
  \-PE  7dca0000-7dca9000       \               midimap
ELF     7dca9000-7dccf000       Deferred        msacm32<elf>
  \-PE  7dcb0000-7dccf000       \               msacm32
ELF     7dccf000-7dce6000       Deferred        msacm32<elf>
  \-PE  7dcd0000-7dce6000       \               msacm32
ELF     7dce6000-7ddac000       Deferred        libasound.so.2
ELF     7ddac000-7dde1000       Deferred        winealsa<elf>
  \-PE  7ddc0000-7dde1000       \               winealsa
ELF     7dde1000-7de6d000       Deferred        winmm<elf>
  \-PE  7ddf0000-7de6d000       \               winmm
ELF     7de6d000-7deb7000       Deferred        dsound<elf>
  \-PE  7de70000-7deb7000       \               dsound
ELF     7dfe4000-7e0d4000       Deferred        wined3d<elf>
  \-PE  7e000000-7e0d4000       \               wined3d
ELF     7e0d4000-7e128000       Deferred        ddraw<elf>
  \-PE  7e0e0000-7e128000       \               ddraw
ELF     7e128000-7e179000       Deferred        libgcrypt.so.11
ELF     7e179000-7e17d000       Deferred        libgpg-error.so.0
ELF     7e17d000-7e18d000       Deferred        libtasn1.so.3
ELF     7e18d000-7e195000       Deferred        libkrb5support.so.0
ELF     7e195000-7e1c3000       Deferred        libcrypt.so.1
ELF     7e1c3000-7e233000       Deferred        libgnutls.so.13
ELF     7e233000-7e258000       Deferred        libk5crypto.so.3
ELF     7e258000-7e2e0000       Deferred        libkrb5.so.3
ELF     7e2e0000-7e309000       Deferred        libgssapi_krb5.so.2
ELF     7e309000-7e33e000       Deferred        libcups.so.2
ELF     7e36e000-7e381000       Deferred        libresolv.so.2
ELF     7e381000-7e39f000       Deferred        iphlpapi<elf>
  \-PE  7e390000-7e39f000       \               iphlpapi
ELF     7e39f000-7e3fd000       Deferred        rpcrt4<elf>
  \-PE  7e3b0000-7e3fd000       \               rpcrt4
ELF     7e3fd000-7e49c000       Deferred        ole32<elf>
  \-PE  7e410000-7e49c000       \               ole32
ELF     7e49f000-7e4a1000       Deferred        libkeyutils.so.1
ELF     7e4c1000-7e4f3000       Deferred        uxtheme<elf>
  \-PE  7e4d0000-7e4f3000       \               uxtheme
ELF     7e4f3000-7e4fc000       Deferred        libxcursor.so.1
ELF     7e4fc000-7e519000       Deferred        imm32<elf>
  \-PE  7e500000-7e519000       \               imm32
ELF     7e519000-7e51e000       Deferred        libxfixes.so.3
ELF     7e51e000-7e526000       Deferred        libxrender.so.1
ELF     7e526000-7e529000       Deferred        libcom_err.so.2
ELF     7e532000-7e5d2000       Deferred        libgl.so.1
ELF     7e5d2000-7e5d7000       Deferred        libxdmcp.so.6
ELF     7e5d7000-7e5da000       Deferred        libxau.so.6
ELF     7e5da000-7e6cb000       Deferred        libx11.so.6
ELF     7e6cb000-7e6d9000       Deferred        libxext.so.6
ELF     7e6d9000-7e6de000       Deferred        libxxf86vm.so.1
ELF     7e6de000-7e6f6000       Deferred        libice.so.6
ELF     7e6f6000-7e6fe000       Deferred        libsm.so.6
ELF     7e701000-7e704000       Deferred        libxcomposite.so.1
ELF     7e704000-7e70a000       Deferred        libxrandr.so.2
ELF     7e70a000-7e799000       Deferred        winex11<elf>
  \-PE  7e720000-7e799000       \               winex11
ELF     7e7eb000-7e80b000       Deferred        libexpat.so.1
ELF     7e80b000-7e836000       Deferred        libfontconfig.so.1
ELF     7e842000-7e857000       Deferred        libz.so.1
ELF     7e857000-7e8c7000       Deferred        libfreetype.so.6
ELF     7e8c7000-7e92c000       Deferred        msvcrt<elf>
  \-PE  7e8e0000-7e92c000       \               msvcrt
ELF     7e92c000-7e945000       Deferred        crtdll<elf>
  \-PE  7e930000-7e945000       \               crtdll
ELF     7e945000-7e959000       Deferred        lz32<elf>
  \-PE  7e950000-7e959000       \               lz32
ELF     7e959000-7e972000       Deferred        version<elf>
  \-PE  7e960000-7e972000       \               version
ELF     7e972000-7e9a7000       Deferred        winspool<elf>
  \-PE  7e980000-7e9a7000       \               winspool
ELF     7e9a7000-7ea46000       Deferred        comdlg32<elf>
  \-PE  7e9b0000-7ea46000       \               comdlg32
ELF     7ea46000-7eb05000       Deferred        comctl32<elf>
  \-PE  7ea50000-7eb05000       \               comctl32
ELF     7eb05000-7eb5c000       Deferred        shlwapi<elf>
  \-PE  7eb10000-7eb5c000       \               shlwapi
ELF     7eb5c000-7ec60000       Deferred        shell32<elf>
  \-PE  7eb70000-7ec60000       \               shell32
ELF     7ec60000-7ecaa000       Deferred        advapi32<elf>
  \-PE  7ec70000-7ecaa000       \               advapi32
ELF     7ecaa000-7ed41000       Deferred        gdi32<elf>
  \-PE  7ecc0000-7ed41000       \               gdi32
ELF     7ed41000-7ee78000       Deferred        user32<elf>
  \-PE  7ed60000-7ee78000       \               user32
ELF     7ee78000-7ee83000       Deferred        libnss_files.so.2
ELF     7ee83000-7ee9b000       Deferred        libnsl.so.1
ELF     7ee9b000-7eea4000       Deferred        libnss_compat.so.2
ELF     7efcf000-7eff4000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7ce6000-b7cea000       Deferred        libdl.so.2
ELF     b7cea000-b7e34000       Deferred        libc.so.6
ELF     b7e35000-b7e4d000       Deferred        libpthread.so.0
ELF     b7e59000-b7f6d000       Deferred        libwine.so.1
ELF     b7f6f000-b7f8b000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000b    0
0000000c 
        0000000f    0
        0000000e    0
        0000000d    0
00000010 (D) C:\Program Files\Diablo\Diablo.exe
        00000016    1
        00000015   15
        00000011    0 <==
00000012 
        00000014    0
        00000013    0
Backtrace:
=>1 0x007e4df8 (0x7edfafb8)
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet

Any suggestions about how to solve this particular problem would be much appreciated.

---

### Post by Sugi on 2008-02-14
Try looking into PlayOnLinux.  The application runs with WINE and setups scripts for each game.  The program does all the work for you.  It has a complete GUI and everything.  It's extremely easy to use.

[www.playonlinux.com]("www.playonlinux.com")

If you do install playonlinx, think about reinstall diablo.  It should work with PlayOnLinux and it can help you set everything up through playonlinx through wine.

You may want to look through wine and see when the game was last support in wine.  Maybe it will only work in later versions.


Sugi

---

### Post by DemiAlbedo on 2008-02-14
Thanks for the tip I just installed PlayonLinux. It is a very nice program with an easy to understand interface, however I am still hitting the same error. The game begins to load but then shuts down right after the blizzard logo is displayed. If I deleted the .wine folder I can get past the logo and watch the first cinematic, however I still can't boot into the game. People suggest running Diablo with wine .0.9.45 so I have playonlinux use 0.9.45 with Diablo, but still nothing.

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 1
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:1
wine: Unhandled page fault on write access to 0x0125c000 at address 0x7e0480 (thread 000b), starting debugger...
Unhandled exception: page fault on write access to 0x0125c000 in 32-bit code (0x007e0480).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:007e0480 ESP:0034f2a0 EBP:0034f360 EFLAGS:00010206(   - 00      - RIP1)
 EAX:205f5f5f EBX:007e0078 ECX:00000000 EDX:0000002e
 ESI:017c1014 EDI:0125c000
Stack dump:
0x0034f2a0:  00000000 0125b500 0125b500 00000000
0x0034f2b0:  017c0510 00000000 7e0033d4 00000032
0x0034f2c0:  00cc0020 7e00418c 001331f8 0000006c
0x0034f2d0:  00000001 00000000 0034f3b8 7bc60fa9
0x0034f2e0:  0034f31c 7bc84b3c 001331f8 00000000
0x0034f2f0:  7bc6b56d 00001b8a 00000280 01210000
Backtrace:
=>1 0x007e0480 (0x0034f360)
  2 0x1500612d in storm (+0x612d) (0x00000280)
  3 0x00000000 (0x00000000)
0x007e0480: movl        %eax,0x0(%edi)
Modules:
Module  Address                 Debug info      Name (102 modules)
PE        400000-  6b4000       Deferred        diablo
PE       13f0000- 140a000       Deferred        smackw32
PE      10000000-10048000       Deferred        diabloui
PE      15000000-15041000       Export          storm
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7db81000-7db96000       Deferred        midimap<elf>
  \-PE  7db90000-7db96000       \               midimap
ELF     7db96000-7dbbc000       Deferred        msacm32<elf>
  \-PE  7dba0000-7dbbc000       \               msacm32
ELF     7dbbc000-7dbd4000       Deferred        msacm32<elf>
  \-PE  7dbc0000-7dbd4000       \               msacm32
ELF     7dbd4000-7dc9a000       Deferred        libasound.so.2
ELF     7dc9a000-7dcd0000       Deferred        winealsa<elf>
  \-PE  7dcb0000-7dcd0000       \               winealsa
ELF     7dcd0000-7dd5e000       Deferred        winmm<elf>
  \-PE  7dce0000-7dd5e000       \               winmm
ELF     7dd5e000-7dda8000       Deferred        dsound<elf>
  \-PE  7dd70000-7dda8000       \               dsound
ELF     7ded5000-7dfb0000       Deferred        wined3d<elf>
  \-PE  7def0000-7dfb0000       \               wined3d
ELF     7dfb0000-7e005000       Deferred        ddraw<elf>
  \-PE  7dfc0000-7e005000       \               ddraw
ELF     7e005000-7e056000       Deferred        libgcrypt.so.11
ELF     7e056000-7e05a000       Deferred        libgpg-error.so.0
ELF     7e05a000-7e06a000       Deferred        libtasn1.so.3
ELF     7e06a000-7e072000       Deferred        libkrb5support.so.0
ELF     7e072000-7e0a0000       Deferred        libcrypt.so.1
ELF     7e0a0000-7e110000       Deferred        libgnutls.so.13
ELF     7e110000-7e135000       Deferred        libk5crypto.so.3
ELF     7e135000-7e1bd000       Deferred        libkrb5.so.3
ELF     7e1bd000-7e1e6000       Deferred        libgssapi_krb5.so.2
ELF     7e1e6000-7e21b000       Deferred        libcups.so.2
ELF     7e24c000-7e25f000       Deferred        libresolv.so.2
ELF     7e261000-7e263000       Deferred        libkeyutils.so.1
ELF     7e26c000-7e28a000       Deferred        iphlpapi<elf>
  \-PE  7e270000-7e28a000       \               iphlpapi
ELF     7e28a000-7e2e3000       Deferred        rpcrt4<elf>
  \-PE  7e2a0000-7e2e3000       \               rpcrt4
ELF     7e2e3000-7e384000       Deferred        ole32<elf>
  \-PE  7e2f0000-7e384000       \               ole32
ELF     7e385000-7e388000       Deferred        libcom_err.so.2
ELF     7e395000-7e3c7000       Deferred        uxtheme<elf>
  \-PE  7e3a0000-7e3c7000       \               uxtheme
ELF     7e3c7000-7e3d0000       Deferred        libxcursor.so.1
ELF     7e3d0000-7e3ed000       Deferred        imm32<elf>
  \-PE  7e3e0000-7e3ed000       \               imm32
ELF     7e3ed000-7e3f5000       Deferred        libxrender.so.1
ELF     7e402000-7e4a2000       Deferred        libgl.so.1
ELF     7e4a2000-7e4a7000       Deferred        libxdmcp.so.6
ELF     7e4a7000-7e4aa000       Deferred        libxau.so.6
ELF     7e4aa000-7e59b000       Deferred        libx11.so.6
ELF     7e59b000-7e5a9000       Deferred        libxext.so.6
ELF     7e5a9000-7e5ae000       Deferred        libxxf86vm.so.1
ELF     7e5ae000-7e5c6000       Deferred        libice.so.6
ELF     7e5c6000-7e5ce000       Deferred        libsm.so.6
ELF     7e5d0000-7e5d5000       Deferred        libxfixes.so.3
ELF     7e5d5000-7e5db000       Deferred        libxrandr.so.2
ELF     7e5db000-7e665000       Deferred        winex11<elf>
  \-PE  7e5f0000-7e665000       \               winex11
ELF     7e6c2000-7e6e2000       Deferred        libexpat.so.1
ELF     7e6e2000-7e70d000       Deferred        libfontconfig.so.1
ELF     7e70d000-7e722000       Deferred        libz.so.1
ELF     7e722000-7e792000       Deferred        libfreetype.so.6
ELF     7e792000-7e7f9000       Deferred        msvcrt<elf>
  \-PE  7e7a0000-7e7f9000       \               msvcrt
ELF     7e7f9000-7e813000       Deferred        crtdll<elf>
  \-PE  7e800000-7e813000       \               crtdll
ELF     7e813000-7e827000       Deferred        lz32<elf>
  \-PE  7e820000-7e827000       \               lz32
ELF     7e827000-7e841000       Deferred        version<elf>
  \-PE  7e830000-7e841000       \               version
ELF     7e841000-7e876000       Deferred        winspool<elf>
  \-PE  7e850000-7e876000       \               winspool
ELF     7e876000-7e917000       Deferred        comdlg32<elf>
  \-PE  7e880000-7e917000       \               comdlg32
ELF     7e917000-7e9d5000       Deferred        comctl32<elf>
  \-PE  7e920000-7e9d5000       \               comctl32
ELF     7e9d5000-7ea2e000       Deferred        shlwapi<elf>
  \-PE  7e9e0000-7ea2e000       \               shlwapi
ELF     7ea2e000-7eb31000       Deferred        shell32<elf>
  \-PE  7ea40000-7eb31000       \               shell32
ELF     7eb31000-7eb79000       Deferred        advapi32<elf>
  \-PE  7eb40000-7eb79000       \               advapi32
ELF     7eb79000-7eb84000       Deferred        libgcc_s.so.1
ELF     7ec77000-7ed38000       Deferred        gdi32<elf>
  \-PE  7ec90000-7ed38000       \               gdi32
ELF     7ed38000-7ee76000       Deferred        user32<elf>
  \-PE  7ed50000-7ee76000       \               user32
ELF     7ee76000-7ee81000       Deferred        libnss_files.so.2
ELF     7ee81000-7ee99000       Deferred        libnsl.so.1
ELF     7ee99000-7eea2000       Deferred        libnss_compat.so.2
ELF     7efce000-7eff3000       Deferred        libm.so.6
ELF     7eff5000-7efff000       Deferred        libnss_nis.so.2
ELF     b7d04000-b7d08000       Deferred        libdl.so.2
ELF     b7d08000-b7e52000       Deferred        libc.so.6
ELF     b7e53000-b7e6b000       Deferred        libpthread.so.0
ELF     b7e78000-b7f8c000       Deferred        libwine.so.1
ELF     b7f8e000-b7faa000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
        0000000e    0
        0000000d    0
0000000a (D) C:\Program Files\Diablo\Diablo.exe
        00000010    1
        0000000f   15
        0000000b    0 <==


I do think I am doing better because there is not some error displayed at the bottom of the terminal paste. I still get 
Xlib:  extension "XFree86-DRI" missing on display ":1.0". error. Could that be the problem?

---

### Post by Sugi on 2008-02-14
Have you tired this?

Did you install Diablo through PlayOnLinux?  Or If you already installed it within linux, try LiveInstall through PlayOnLinux?

Try this?
PlayOnLinux > Tools > Manage Wine Versions > Assign > Drop Down Menu to "Diablo" > 0.9.45 (Note: if 0.9.45 is NOT in the drop down menu, try others and then type 0.9.45 in that box and it will download it for you. It should work after that.  > Run > Enjoy :)

There you go, you should be set.

After all of that, and that still doesn't do the trick try
 Tools > Install DirectX
I am not sure if it will help, but it will not hurt.  I can tell you that.  But I doubt Diablo 1 will need DirectX but you can always try.


Sugi

---

### Post by DemiAlbedo on 2008-02-14
I tried using playonlinux and still the same thing happens. I uninstalled Diablo then reinstalled it through playonlinux and the problem is still persisting.  I used the liveinstall feature and setup the shortcuts and installed diablo, I also installed wine 0.9.45 and assigned it to diablo, but that is still not doing anything. As a side bonus i installed directx hoping that would solve it but still nothing.

Here are some interesting things I have noticed 
1. This error appears if I try and run diablo through the terminal, fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet. This error is not shown in the terminal if I run diablo through playonlinux

2. When I start playonlinux I get this error "you don't seem to have 3D acceleration ! we advise you install and enable it." I'm sure my card is working because i'm using compiz right now.

3. When I run diablo or playonlinux I keep getting this error code in the terminal "Xlib:  extension "XFree86-DRI" missing on display ":1.0" Think that could have something to do with diablo shutting down?

I have my laptop dual booted with windows xp, so as a test I booted to xp to test the game and it works fine. I thought maybe it was not installing correctly or the disk was damaged, but thats not the case.

Any suggestions on what I should try now?

---

### Post by yabbadabbadont on 2008-02-14
Disable compiz and try again.

---

### Post by DemiAlbedo on 2008-02-14
How can I disable compiz without uninstalling or deleting it? Is there an easy way to just temporally disable it so that I can turn it on when I want to

---

### Post by DemiAlbedo on 2008-02-14
I figured out how to disable compiz without uninstalling it or deleting it. I found a program called compiz-switch. It allows you to turn of compiz with one click, however that is still not solving the problem. Diablo boots, blizzard logo comes up, when logo is done it closes. 

Here is the output for diablo when I load it with playonlinux and have compiz disabled. Hope this helps.

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
wine: Unhandled page fault on write access to 0x0125c000 at address 0x7e0480 (thread 000b), starting debugger...
Unhandled exception: page fault on write access to 0x0125c000 in 32-bit code (0x007e0480).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:007e0480 ESP:0034f2a0 EBP:0034f360 EFLAGS:00210206(   - 00      - RIP1)
 EAX:205f5f5f EBX:007e0078 ECX:00000000 EDX:0000002e
 ESI:017c1014 EDI:0125c000
Stack dump:
0x0034f2a0:  00000000 0125b500 0125b500 00000000
0x0034f2b0:  017c0510 00000000 7e0023d4 00000032
0x0034f2c0:  00cc0020 7e00318c 00133f08 0000006c
0x0034f2d0:  00000001 7c035e18 7c0439e0 0034f31c
0x0034f2e0:  7e4e7803 7c0439e0 00133f08 00000000
0x0034f2f0:  7e596b2c 00000001 00000280 01210000
Backtrace:
=>1 0x007e0480 (0x0034f360)
  2 0x1500612d in storm (+0x612d) (0x00000280)
  3 0x00000000 (0x00000000)
0x007e0480: movl        %eax,0x0(%edi)
Modules:
Module  Address                 Debug info      Name (101 modules)
PE        400000-  6b4000       Deferred        diablo
PE       13f0000- 140a000       Deferred        smackw32
PE      10000000-10048000       Deferred        diabloui
PE      15000000-15041000       Export          storm
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7dc42000-7dc57000       Deferred        midimap<elf>
  \-PE  7dc50000-7dc57000       \               midimap
ELF     7dc57000-7dc7d000       Deferred        msacm32<elf>
  \-PE  7dc60000-7dc7d000       \               msacm32
ELF     7dc7d000-7dc95000       Deferred        msacm32<elf>
  \-PE  7dc80000-7dc95000       \               msacm32
ELF     7dc95000-7dccf000       Deferred        wineoss<elf>
  \-PE  7dca0000-7dccf000       \               wineoss
ELF     7dccf000-7dd5d000       Deferred        winmm<elf>
  \-PE  7dce0000-7dd5d000       \               winmm
ELF     7dd5d000-7dda7000       Deferred        dsound<elf>
  \-PE  7dd70000-7dda7000       \               dsound
ELF     7ded4000-7dfaf000       Deferred        wined3d<elf>
  \-PE  7def0000-7dfaf000       \               wined3d
ELF     7dfaf000-7e004000       Deferred        ddraw<elf>
  \-PE  7dfc0000-7e004000       \               ddraw
ELF     7e004000-7e055000       Deferred        libgcrypt.so.11
ELF     7e055000-7e059000       Deferred        libgpg-error.so.0
ELF     7e059000-7e069000       Deferred        libtasn1.so.3
ELF     7e069000-7e071000       Deferred        libkrb5support.so.0
ELF     7e071000-7e09f000       Deferred        libcrypt.so.1
ELF     7e09f000-7e10f000       Deferred        libgnutls.so.13
ELF     7e10f000-7e134000       Deferred        libk5crypto.so.3
ELF     7e134000-7e1bc000       Deferred        libkrb5.so.3
ELF     7e1bc000-7e1e5000       Deferred        libgssapi_krb5.so.2
ELF     7e1e5000-7e21a000       Deferred        libcups.so.2
ELF     7e24b000-7e25e000       Deferred        libresolv.so.2
ELF     7e260000-7e262000       Deferred        libkeyutils.so.1
ELF     7e26b000-7e289000       Deferred        iphlpapi<elf>
  \-PE  7e270000-7e289000       \               iphlpapi
ELF     7e289000-7e2e2000       Deferred        rpcrt4<elf>
  \-PE  7e2a0000-7e2e2000       \               rpcrt4
ELF     7e2e2000-7e383000       Deferred        ole32<elf>
  \-PE  7e2f0000-7e383000       \               ole32
ELF     7e384000-7e387000       Deferred        libcom_err.so.2
ELF     7e394000-7e3c6000       Deferred        uxtheme<elf>
  \-PE  7e3a0000-7e3c6000       \               uxtheme
ELF     7e3c6000-7e3cf000       Deferred        libxcursor.so.1
ELF     7e3cf000-7e3ec000       Deferred        imm32<elf>
  \-PE  7e3e0000-7e3ec000       \               imm32
ELF     7e3ec000-7e3f4000       Deferred        libxrender.so.1
ELF     7e401000-7e4a1000       Deferred        libgl.so.1
ELF     7e4a1000-7e4a6000       Deferred        libxdmcp.so.6
ELF     7e4a6000-7e4a9000       Deferred        libxau.so.6
ELF     7e4a9000-7e59a000       Deferred        libx11.so.6
ELF     7e59a000-7e5a8000       Deferred        libxext.so.6
ELF     7e5a8000-7e5ad000       Deferred        libxxf86vm.so.1
ELF     7e5ad000-7e5c5000       Deferred        libice.so.6
ELF     7e5c5000-7e5cd000       Deferred        libsm.so.6
ELF     7e5cf000-7e5d4000       Deferred        libxfixes.so.3
ELF     7e5d4000-7e5da000       Deferred        libxrandr.so.2
ELF     7e5da000-7e664000       Deferred        winex11<elf>
  \-PE  7e5f0000-7e664000       \               winex11
ELF     7e6c2000-7e6e2000       Deferred        libexpat.so.1
ELF     7e6e2000-7e70d000       Deferred        libfontconfig.so.1
ELF     7e70d000-7e722000       Deferred        libz.so.1
ELF     7e722000-7e792000       Deferred        libfreetype.so.6
ELF     7e792000-7e7f9000       Deferred        msvcrt<elf>
  \-PE  7e7a0000-7e7f9000       \               msvcrt
ELF     7e7f9000-7e813000       Deferred        crtdll<elf>
  \-PE  7e800000-7e813000       \               crtdll
ELF     7e813000-7e827000       Deferred        lz32<elf>
  \-PE  7e820000-7e827000       \               lz32
ELF     7e827000-7e841000       Deferred        version<elf>
  \-PE  7e830000-7e841000       \               version
ELF     7e841000-7e876000       Deferred        winspool<elf>
  \-PE  7e850000-7e876000       \               winspool
ELF     7e876000-7e917000       Deferred        comdlg32<elf>
  \-PE  7e880000-7e917000       \               comdlg32
ELF     7e917000-7e9d5000       Deferred        comctl32<elf>
  \-PE  7e920000-7e9d5000       \               comctl32
ELF     7e9d5000-7ea2e000       Deferred        shlwapi<elf>
  \-PE  7e9e0000-7ea2e000       \               shlwapi
ELF     7ea2e000-7eb31000       Deferred        shell32<elf>
  \-PE  7ea40000-7eb31000       \               shell32
ELF     7eb31000-7eb79000       Deferred        advapi32<elf>
  \-PE  7eb40000-7eb79000       \               advapi32
ELF     7eb79000-7eb84000       Deferred        libgcc_s.so.1
ELF     7ec77000-7ed38000       Deferred        gdi32<elf>
  \-PE  7ec90000-7ed38000       \               gdi32
ELF     7ed38000-7ee76000       Deferred        user32<elf>
  \-PE  7ed50000-7ee76000       \               user32
ELF     7ee76000-7ee81000       Deferred        libnss_files.so.2
ELF     7ee81000-7ee99000       Deferred        libnsl.so.1
ELF     7ee99000-7eea2000       Deferred        libnss_compat.so.2
ELF     7efce000-7eff3000       Deferred        libm.so.6
ELF     7eff3000-7effd000       Deferred        libnss_nis.so.2
ELF     b7d12000-b7d16000       Deferred        libdl.so.2
ELF     b7d16000-b7e60000       Deferred        libc.so.6
ELF     b7e61000-b7e79000       Deferred        libpthread.so.0
ELF     b7e86000-b7f9a000       Deferred        libwine.so.1
ELF     b7f9c000-b7fb8000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
        0000000e    0
        0000000d    0
0000000a (D) Z:\windows\Program Files\Diablo\Diablo.exe
        00000014    1
        00000013   15
        00000011   15
        0000000b    0 <==

I am also still getting the error "enabling 3d accelerator" when I turn playonlinux on with compiz disabled.

---

### Post by yabbadabbadont on 2008-02-14
I'm guessing that you haven't checked the WINE appdb for this game...

From the appdb entry:
> **DirectDraw Mode**
You must have DirectDrawRenderer in the registry set to "gdi" (which is the default) for Diablo to work. If you have changed it to "opengl" at any point then the game will crash after the Blizzard logos.

There are also comments about having to replace ddraw.dll.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3498](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3498)

---

### Post by DemiAlbedo on 2008-02-14
I did check out Wine application database, but I run into a sight problem when trying to use the ddraw.dll. I can't find where to put it. Once I install diablo I went to the folder to replace the ddraw.dll file with the patched one, however there is no ddraw.dll file there. I found a ddraw.dll file in the windows/system32 folder so I tried replacing that and still same problem. Playonlinux also has a function to change the directdraw render of any application to gdi. Tools -> Wine Booster -> DirectDrawRender. When you check that it says that the default is already gdi. Just out of curiosity where are you suppose to put the hacked ddraw.dll file?

If anyone has some more suggestions I would appreciate it. 

This has started to become a headache

---

### Post by yabbadabbadont on 2008-02-15
I think one of the reports in the appdb said to drop it into the same directory as the Diablo executable.  Normal Windows behavior is to use the dll located in the same directory as the exe first, then search the path, so it should be used if you put it there.  You may also have to get into winecfg and add an override for the dll, but I would try the game without the override first.

---

### Post by DemiAlbedo on 2008-02-15
Today I tried starting from scratch. I uninstalled Diablo, Wine, and Playonlinux. I read on winehq ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=3498](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3498)) That Diablo has been tested using wine version 0.9.49 and it works. So I reinstalled wine and went to version 0.9.49 instead of 0.9.55. Then I reinstalled Playonlinux and reinstalled my Diablo through that. I installed to the typical c: drive/program file/ directory and everything went fine. I hit a font error when I tried to install playonlinux however. I got the patched ddraw.dll ([http://madewokherd.nfshost.com/worms/](http://madewokherd.nfshost.com/worms/)) and put it into c: drive/program file/diablo/ directory. The directory were I installed diablo and where the exe is, however it still crashes after the blizzard logo. I used reg editor with playonlinux and found that the default DirecDrawRender was set to gdi. I ran wine booster anyways for saftey and it said diablo was defaulted to gdi. 

I tried to do the dll override in winecfg but in the libraries there is no ddraw.dll. How do i do a ddraw.dll override if it is not in the libraries?

Once I get home I will try to get it working again, but if anyone has any new ideas or suggestions feel free to post.

---

### Post by DemiAlbedo on 2008-02-17
Yes thats right, solved, after several long long hours trying to get diablo to work I finally solved it. I tried everything from wine 0.9.45, 0.9.46, 0.9.49, and 0.9.55(all versions of wine that are reported to support diablo 1). If you read all the post then you can see that I tried every suggestion and everything I could think of. I tried playonlinux, crossover, sidenet, cedega, and a few other programs, however they are all extensions of wine. One can conclude that if wine won't work then sister programs that use wine will also not work. . .but I still gave it all a shot. I tried a new program call VMWARE and it worked perfectly. 

VMWARE is a program that allows you to install windows xp and run it off of your desktop. It is not an emulator program like wine. . .VMWARE INSTALLS WINDOWS. Its like having picture in picture on a TV. I have Ubuntu installed however within Ubuntu I run windows xp in a small window. In that window I can play any game I want from the comfort of my Ubuntu desktop. With VMWARE you can play any game you want with ease. 

Only thing to note is that VMWARE installs windows onto your computer, its not emulator that tries to mimic windows. Which means in order to install it you need window disks with a windows COA. I happen to work at a computer store so it was easy for me to get a hold of windows xp disks and a legit COA. 

It can be a little tough to set up VMWARE because you need the disks and a COA, however I rank it the best program to run games with. 

I recommend to anyone who plays games that you AT LEAST read up on VMWARE and what it is about.

---

### Post by chipmunken on 2009-10-19
OK ok this thread is old.. but I came across it when Goggling a problem with wine... And for the solution of DemiAlbedo I strongly recommend looking at Virtual Box fron Sun instead of VMware.. If your into Linux and open source that is :D..

I do the same thing as DemiAlbedo just I run it under Virtual Box

1. Its free
2. sun > vmware
3. sun has now an experimental open GL support in Virtual Box

---

### Post by cariboo on 2009-10-19
You are replying to a thread that is marked solved. THis thread is closed.

---

